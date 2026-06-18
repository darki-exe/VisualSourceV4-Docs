# Decoding Scripts

This page explains exactly how an encoded VisualSource script is turned back into the internal binary decoded format.

---

## The Pipeline

```
Encoded string  →  [1] Parse header  →  [2] Base93 decode  →  [3] Deflate decompress
```

Decoding is the exact reverse of encoding. The output is the **internal binary format** using `\x1a`/`\x1b` separators — not human-readable text. See [Binary Decoded Format](binary-format.md) for how to parse that result.

---

## Step 1 — Parse the Header

An encoded script looks like one of these two forms:

**With control characters (RetroStudio native):**
```
\x1a0000000000000004\x1b<base93_payload>
```

**Without control characters (HTTP / plain text variant):**
```
0000000000000004<base93_payload>
```

### Parsing procedure

1. Strip all characters below `0x20` **except** `\x1a` (0x1A) and `\x1b` (0x1B), which are used as markers.
2. Skip any leading `\x1a` or `\x1b` characters.
3. Read consecutive digit characters — this is the **version string** (e.g. `0000000000000004`).
4. Skip any non-base93 characters after the version.
5. Everything remaining is the **base93 payload**.

```python
VALID_BASE93 = set(
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz"
    "0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ "
)

def parse_header(text: str):
    # 1. Clean control chars (keep \x1a and \x1b for version detection)
    clean = ''
    for c in text:
        cp = ord(c)
        if cp >= 0x20 or cp in (0x09, 0x0A, 0x0D, 0x1A, 0x1B):
            clean += c
    clean = clean.strip()

    # 2. Skip leading markers
    i = 0
    while i < len(clean) and ord(clean[i]) in (0x1A, 0x1B):
        i += 1

    # 3. Read version digits
    j = i
    while j < len(clean) and clean[j].isdigit():
        j += 1
    version_str = clean[i:j] if (j - i) >= 4 else None

    # 4. Skip to start of base93 payload
    k = j
    while k < len(clean) and clean[k] not in VALID_BASE93:
        k += 1

    # 5. Extract payload (only valid base93 chars)
    payload = ''.join(c for c in clean[k:] if c in VALID_BASE93)

    return version_str, payload
```

### Version routing

| Version | Format | Action |
|---|---|---|
| `0000000000000001` or `0000000000000002` | LZW legacy | use legacy LZW decoder |
| `0000000000000003` or `0000000000000004` or higher | deflate + base93 | use modern decoder (steps 2–3) |
| `None` / unrecognized | assume modern | attempt deflate + base93 |

---

## Step 2 — Base93 Decode

The payload string is decoded back into compressed bytes.

### Charset (CHARS_OLD)

```
ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ 
```

Build an index lookup table (char → value):

```python
CHARS_OLD = list("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ ")

IDX_OLD = [255] * 256
for i, c in enumerate(CHARS_OLD):
    IDX_OLD[ord(c)] = i
```

### Algorithm

The decoder reads the payload two characters at a time. Each pair encodes a value 0–8648 (93² - 1). The number of bits that value represents is determined by comparing it against the threshold 456:

- If `value & 8191 > 456` → this pair encodes **13 bits**
- Otherwise → this pair encodes **14 bits**

```python
def base93_decode(s: str, idx: list) -> bytes:
    out = []
    pair_end = (len(s) // 2) * 2
    queue = 0
    nbits = 0

    for i in range(0, pair_end, 2):
        v1 = idx[ord(s[i])]
        v2 = idx[ord(s[i + 1])]
        if v1 == 255 or v2 == 255:
            raise ValueError(f"Invalid base93 char at index {i}")
        val = v1 + v2 * 93
        queue = (queue + val * (1 << nbits)) & 0xFFFFFFFF
        if (val & 8191) > 456:
            nbits += 13
        else:
            nbits += 14
        while nbits >= 8:
            out.append(queue & 0xFF)
            queue = (queue >> 8) & 0xFFFFFFFF
            nbits -= 8

    # handle trailing single char
    if pair_end < len(s):
        v = idx[ord(s[-1])]
        if v == 255:
            raise ValueError(f"Invalid base93 char at end: '{s[-1]}'")
        queue = (queue + v * (1 << nbits)) & 0xFFFFFFFF
        if nbits > 0:
            out.append(queue & 0xFF)

    return bytes(out)
```

### Charset fallback

Some older version-4 files were encoded with an alternate charset (`CHARS_NEW`) that starts at `B` instead of `A`:

```python
CHARS_NEW = list("BCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ ")
```

If decoding with `CHARS_OLD` raises an error, retry with `CHARS_NEW` before giving up:

```python
for idx in (IDX_OLD, IDX_NEW):
    try:
        raw_bytes = base93_decode(payload, idx)
        break
    except Exception:
        pass
```

---

## Step 3 — Deflate Decompress

The raw bytes from step 2 are decompressed using raw deflate:

```python
import zlib

def decompress_deflate(data: bytes) -> str:
    for wbits in (-15, 15, 47):
        try:
            return zlib.decompress(data, wbits=wbits).decode('utf-8', errors='replace')
        except Exception:
            pass
    raise ValueError('Deflate decompression failed')
```

The decoder tries three modes in order for compatibility:

| wbits | Mode |
|---|---|
| `-15` | Raw deflate (current format) |
| `15` | Zlib-wrapped deflate |
| `47` | Gzip |

In practice, all version-3 and version-4 scripts use raw deflate (`-15`). The other modes are safety fallbacks.

---

## Output — Binary Decoded String

The result of step 3 is the **internal binary format**, not human-readable text. It uses `\x1a` and `\x1b` as structural separators:

```
\x1a\x1aEditor\x1aCameraPosition\x1b0,0\x1aCameraZoom\x1b0.1C2\x1a\x1aBlock\x1aType\x1bPrint...
```

See [Binary Decoded Format](binary-format.md) for how to parse this string into blocks, inputs, outputs, and editor data.

---

## Full Decode Function

```python
import zlib

CHARS_OLD = list("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ ")
CHARS_NEW = list("BCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ ")

VALID_BASE93 = set(
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz"
    "0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ "
)

def _make_idx(chars):
    idx = [255] * 256
    for i, c in enumerate(chars):
        idx[ord(c)] = i
    return idx

IDX_OLD = _make_idx(CHARS_OLD)
IDX_NEW = _make_idx(CHARS_NEW)

def base93_decode(s, idx):
    out = []
    pair_end = (len(s) // 2) * 2
    queue = 0
    nbits = 0
    for i in range(0, pair_end, 2):
        v1 = idx[ord(s[i])]
        v2 = idx[ord(s[i + 1])]
        if v1 == 255 or v2 == 255:
            raise ValueError(f"Invalid base93 char at index {i}")
        val = v1 + v2 * 93
        queue = (queue + val * (1 << nbits)) & 0xFFFFFFFF
        if (val & 8191) > 456:
            nbits += 13
        else:
            nbits += 14
        while nbits >= 8:
            out.append(queue & 0xFF)
            queue = (queue >> 8) & 0xFFFFFFFF
            nbits -= 8
    if pair_end < len(s):
        v = idx[ord(s[-1])]
        if v == 255:
            raise ValueError(f"Invalid base93 char at end")
        queue = (queue + v * (1 << nbits)) & 0xFFFFFFFF
        if nbits > 0:
            out.append(queue & 0xFF)
    return bytes(out)

def decompress_deflate(data):
    for wbits in (-15, 15, 47):
        try:
            return zlib.decompress(data, wbits=wbits).decode('utf-8', errors='replace')
        except Exception:
            pass
    raise ValueError('Deflate decompression failed')

def decode(text: str) -> str:
    """
    Decodes an encoded VS string.
    Returns the internal binary decoded string (with \x1a/\x1b separators).
    """
    # Step 1: parse header
    clean = ''
    for c in text:
        cp = ord(c)
        if cp >= 0x20 or cp in (0x09, 0x0A, 0x0D, 0x1A, 0x1B):
            clean += c
    clean = clean.strip()

    i = 0
    while i < len(clean) and ord(clean[i]) in (0x1A, 0x1B):
        i += 1
    j = i
    while j < len(clean) and clean[j].isdigit():
        j += 1
    version_str = clean[i:j] if (j - i) >= 4 else None
    k = j
    while k < len(clean) and clean[k] not in VALID_BASE93:
        k += 1
    payload = ''.join(c for c in clean[k:] if c in VALID_BASE93)

    # Step 2: base93 decode (try both charsets)
    raw_bytes = None
    for idx in (IDX_OLD, IDX_NEW):
        try:
            raw_bytes = base93_decode(payload, idx)
            break
        except Exception:
            pass
    if raw_bytes is None:
        raise ValueError('Base93 decode failed with both charsets')

    # Step 3: deflate decompress
    return decompress_deflate(raw_bytes)
```

---

## Detecting If a String Is Already Decoded

A binary decoded string always starts with `\x1a\x1a`. An encoded string always starts with `\x1a` followed by digits, or directly with `000000000000000`. Check the prefix before attempting to decode to avoid double-decoding.

```python
def is_encoded(text: str) -> bool:
    t = text.lstrip()
    return t.startswith('\x1a') or t.startswith('000000000000000')

def is_binary_decoded(text: str) -> bool:
    return '\x1a\x1a' in text[:64] or (text.startswith('\x1a') and '\x1b' not in text[:20])
```

---

## API Usage

If you are using the RetroStudio backend:

```
POST /decode
Content-Type: application/json

{
  "text": "0000000000000004<base93_payload>",
  "keep_original": true
}
```

Response:

```json
{
  "output": "<binary decoded string with \x1a/\x1b separators>",
  "stats": {
    "version": "0000000000000004",
    "output_chars": 180
  }
}
```

Set `keep_original: false` to sanitize non-printable characters in the output (replaces them with spaces) — useful if you need human-readable text.

---

## Legacy Format (Versions 1–2)

Legacy scripts have a version number of `0000000000000001` or `0000000000000002`. Their payload uses LZW compression with a different structure. The modern `decode()` function handles this path automatically based on the version number. See [Legacy Format](legacy.md) for details.

---

## Common Mistakes

**Stripping `\x1a`/`\x1b` before parsing:** These control chars are needed to locate the version string boundary. Strip them only after the version has been read.

**Treating the output as UTF-8 text:** The binary decoded result contains `\x1a` and `\x1b` control characters as structural separators. They are not display characters and must be handled as delimiters, not stripped.

**Stopping after one charset attempt:** Some valid files encoded with `CHARS_NEW` will fail with `CHARS_OLD`. Always retry with the alternate charset before raising an error.

**Checking for `== None` on the decoded bytes:** The decoder may produce `b''` (empty bytes) for a valid empty script. Use `is None` not `== None` or truthiness checks.
