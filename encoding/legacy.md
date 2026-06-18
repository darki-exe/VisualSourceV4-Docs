# Legacy Format (Versions 1–2)

Scripts encoded with VisualSource versions 1 and 2 use a completely different pipeline from the modern format. Instead of deflate + base93, they use **LZW compression** with a custom escape scheme and a segmented base93 encoding.

> **You will never need to encode in this format.** All new scripts use version 4. This page exists so you can decode old scripts if you encounter them.

---

## How to Recognize a Legacy Script

After stripping the version header (see [Decoding](decode.md)), the body of a legacy script always contains a `|` character:

```
<lengths>|<lzw_data>
```

For example:
```
0000000000000001  →  version 1
3,5,2|ABCabc...  →  body with | separator
```

A version-4 payload never contains `|` in a meaningful position — it only has base93 characters from `CHARS_OLD`.

In code, the `decode()` function routes automatically:

```python
v_num = int(version_str) if version_str else None
if v_num is not None and v_num <= 2:
    result = legacy_decode(body)   # LZW path
else:
    result = modern_decode(body)   # deflate + base93 path
```

---

## The Full Pipeline

```
Decoded text
    → [1] Escape special chars
    → [2] LZW compress → list of (code_length, code) tokens
    → [3] Group tokens by code_length into segments
    → [4] Encode each code as big-endian base93 string
    → [5] Build header: comma-separated segment lengths
    → [6] Concatenate: "<lengths>|<segments...>"
```

---

## The Base Alphabet

Legacy format uses the same 93-character alphabet as the modern format, but reads it differently. Instead of the bit-packing scheme used in v4, each LZW code is converted to a **big-endian base93 string** of a fixed character length.

```
ASCII 32–126, excluding " (34) and \ (92)
→ 93 printable characters, indexed 0–92
```

```python
table_fwd = {}  # char → int
table_rev = {}  # int → char
idx = 0
for i in range(32, 128):
    if i not in (34, 92):       # skip " and \
        ch = chr(i)
        table_fwd[ch] = idx
        table_rev[idx] = ch
        idx += 1
# table now has 93 entries: index 0 = ' ', 1 = '!', 2 = '#', etc.
```

Converting a code to a base93 string of exact length `n` (big-endian):

```python
def to_base93_str(val, length):
    result = []
    v = val
    for _ in range(length):
        result.append(table_rev[v % 93])
        v //= 93
    return ''.join(reversed(result))
```

Converting a base93 string back to an integer:

```python
def to_base10(s):
    val = 0
    for i, c in enumerate(reversed(s)):
        val += (93 ** i) * table_fwd.get(c, 0)
    return val
```

---

## Step 1 — Escape Special Characters

Before LZW compression, characters that cannot appear in the base alphabet (control characters, `"`, `\`) are escaped using a `\x7f` prefix byte and a substitution character.

The escape map covers codes 1–34, with three special cases for `"` (34), `\` (92), and DEL (127):

```python
specials = [34, 92, 127]
esc_map = {}
for i in range(1, 35):
    code = i if i <= 31 else (specials[i - 32] if i - 32 < len(specials) else i)
    c1, c2 = chr(code), chr(code + 31)
    esc_map[c1] = c2   # original → escaped substitute
    esc_map[c2] = c1   # escaped substitute → original (for unescape)
```

Escaping:

```python
def escape(s):
    out = []
    for c in s:
        if ord(c) < 32 or c in ('"', '\\'):
            out.append('\x7f')
            out.append(esc_map.get(c, c))
        else:
            out.append(c)
    return ''.join(out)
```

Unescaping (used during decode):

```python
def unescape(s):
    out, i = [], 0
    while i < len(s):
        if ord(s[i]) == 0x7F and i + 1 < len(s):
            out.append(esc_map.get(s[i + 1], s[i + 1]))
            i += 2
        else:
            out.append(s[i])
            i += 1
    return ''.join(out)
```

---

## Step 2 — LZW Compression

Standard LZW, initialized with the 93-character base alphabet. The dictionary starts with each single character mapped to its index (0–92), and grows as new patterns are found.

```python
lzw_table = dict(table_fwd)   # char → code
next_code = len(lzw_table)    # starts at 93
cur_code_len = 1              # minimum chars needed to represent current codes
tokens = []                   # output: list of (code_length, code)

prefix = ''
for ch in escaped_text:
    candidate = prefix + ch
    if candidate in lzw_table:
        prefix = candidate
    else:
        code = lzw_table[prefix]
        # code_length needed for this code in base93
        nl = needed_len(code)
        if nl > cur_code_len:
            cur_code_len = nl
        tokens.append((cur_code_len, code))
        lzw_table[candidate] = next_code
        next_code += 1
        prefix = ch

# flush last prefix
if prefix:
    code = lzw_table[prefix]
    nl = needed_len(code)
    if nl > cur_code_len:
        cur_code_len = nl
    tokens.append((cur_code_len, code))
```

`needed_len(code)` computes how many base93 characters are required to represent `code`:

```python
def needed_len(code):
    if code == 0:
        return 1
    n, p = 1, 93
    while code >= p:
        n += 1
        p *= 93
    return n
```

| code range | needed_len |
|---|---|
| 0–92 | 1 |
| 93–8648 | 2 |
| 8649–804356 | 3 |
| … | … |

---

## Step 3 — Segment by Code Length

Tokens are grouped into segments by their `code_length`. Each segment holds all tokens that use the same number of base93 characters per code:

```python
max_len = max(cl for cl, _ in tokens)
segments = {l: [] for l in range(1, max_len + 1)}
for cl, code in tokens:
    segments[cl].append(to_base93_str(code, cl))
```

---

## Step 4 — Build the Output

The final string is:

```
<count_seg1>,<count_seg2>,...,<count_segN>|<seg1><seg2>...<segN>
```

- `<count_segN>` — number of **codes** in segment N (not characters)
- `<segN>` — all codes concatenated; each code is exactly N base93 chars wide

```python
counts = [str(len(segments[l])) for l in range(1, max_len + 1)]
parts  = [''.join(segments[l]) for l in range(1, max_len + 1)]
output = ','.join(counts) + '|' + ''.join(parts)
```

**Example layout** for a script with tokens of length 1 and 2:

```
3,5|ABCabcde
^^ ^^
|  |
|  └─ 3 codes × 1 char = "ABC"   +   5 codes × 2 chars = "abcde" ... wait, 5×2=10
|
└─ counts: segment-1 has 3 codes, segment-2 has 5 codes
```

The content after `|` is all segments concatenated with no separator — the decoder knows each segment's byte length because `count × code_length` gives it exactly.

---

## Full Decode Function

```python
import re

def legacy_decode(body: str) -> str:
    # Build base alphabet
    table_fwd = {}
    table_rev = {}
    idx = 0
    for i in range(32, 128):
        if i not in (34, 92):
            ch = chr(i)
            table_fwd[idx] = ch
            table_rev[ch] = idx
            idx += 1

    # Escape map
    specials = [34, 92, 127]
    esc_map = {}
    for i in range(1, 35):
        code = i if i <= 31 else (specials[i - 32] if i - 32 < len(specials) else i)
        c1, c2 = chr(code), chr(code + 31)
        esc_map[c1] = c2
        esc_map[c2] = c1

    def unescape(s):
        out, i = [], 0
        while i < len(s):
            if ord(s[i]) == 0x7F and i + 1 < len(s):
                out.append(esc_map.get(s[i + 1], s[i + 1]))
                i += 2
            else:
                out.append(s[i])
                i += 1
        return ''.join(out)

    def to_base10(s):
        val = 0
        for i, c in enumerate(reversed(s)):
            val += (93 ** i) * table_rev.get(c, 0)
        return val

    # Parse header
    pipe_idx = body.find('|')
    if pipe_idx == -1:
        raise ValueError('Legacy format: missing | separator')

    header, content = body[:pipe_idx], body[pipe_idx + 1:]
    lengths = [int(m) for m in re.findall(r'\d+', header)]
    if not lengths:
        raise ValueError('Legacy format: no length values in header')

    # Split content into segments
    segments, pos = [], 0
    for i, length in enumerate(lengths):
        seg_len = length * (i + 1)   # count × code_length chars
        segments.append(content[pos:pos + seg_len])
        pos += seg_len

    # LZW decode
    d = dict(table_fwd)          # code → string
    next_code = len(d)
    result, prev = [], None

    for si, seg in enumerate(segments):
        code_len = si + 1
        for i in range(0, len(seg) - code_len + 1, code_len):
            code = to_base10(seg[i:i + code_len])
            if code in d:
                entry = d[code]
            elif prev is not None:
                entry = prev + prev[0]   # LZW edge case
            else:
                raise ValueError(f'Legacy LZW: bad code {code}')
            result.append(entry)
            if prev is not None:
                d[next_code] = prev + entry[0]
                next_code += 1
            prev = entry

    return unescape(''.join(result))
```

---

## Full Encode Function

```python
import re

def legacy_encode(text: str) -> str:
    table_fwd = {}
    table_rev = {}
    idx = 0
    for i in range(32, 128):
        if i not in (34, 92):
            ch = chr(i)
            table_fwd[ch] = idx
            table_rev[idx] = ch
            idx += 1

    specials = [34, 92, 127]
    esc_map = {}
    for i in range(1, 35):
        code = i if i <= 31 else (specials[i - 32] if i - 32 < len(specials) else i)
        c1, c2 = chr(code), chr(code + 31)
        esc_map[c1] = c2
        esc_map[c2] = c1

    def escape(s):
        out = []
        for c in s:
            if ord(c) < 32 or c in ('"', '\\'):
                out.append('\x7f')
                out.append(esc_map.get(c, c))
            else:
                out.append(c)
        return ''.join(out)

    def to_base93_str(val, length):
        result = []
        v = val
        for _ in range(length):
            result.append(table_rev[v % 93])
            v //= 93
        return ''.join(reversed(result))

    def needed_len(code):
        if code == 0:
            return 1
        n, p = 1, 93
        while code >= p:
            n += 1
            p *= 93
        return n

    lzw_table = dict(table_fwd)
    next_code = len(lzw_table)
    cur_code_len = 1
    tokens = []

    escaped = escape(text)
    prefix = ''
    for ch in escaped:
        candidate = prefix + ch
        if candidate in lzw_table:
            prefix = candidate
        else:
            code = lzw_table[prefix]
            nl = needed_len(code)
            if nl > cur_code_len:
                cur_code_len = nl
            tokens.append((cur_code_len, code))
            lzw_table[candidate] = next_code
            next_code += 1
            prefix = ch
    if prefix:
        code = lzw_table[prefix]
        nl = needed_len(code)
        if nl > cur_code_len:
            cur_code_len = nl
        tokens.append((cur_code_len, code))

    max_len = max((cl for cl, _ in tokens), default=1)
    segments = {l: [] for l in range(1, max_len + 1)}
    for cl, code in tokens:
        segments[cl].append(to_base93_str(code, cl))

    counts = [str(len(segments[l])) for l in range(1, max_len + 1)]
    parts  = [''.join(segments[l]) for l in range(1, max_len + 1)]
    return ','.join(counts) + '|' + ''.join(parts)
```

---

## Key Differences from Version 4

| | Version 1–2 (Legacy) | Version 4 (Modern) |
|---|---|---|
| Compression | LZW | Deflate (raw, `wbits=-15`) |
| Base encoding | Big-endian base93 per code | Bit-packed base93 (13/14 bits per pair) |
| Escape step | Yes (`\x7f` prefix) | No (deflate handles binary) |
| Body structure | `<counts>\|<segments>` | flat base93 string |
| Version string | `0000000000000001` or `...0002` | `0000000000000004` |
| Encode support | Yes (but don't use it) | Yes — always use this |
| Decode support | Yes | Yes |
