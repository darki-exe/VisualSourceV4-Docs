# Encoding Scripts

This page explains exactly how a VisualSource script is turned into the compact encoded string that RetroStudio stores and transmits.

---

## The Pipeline

```
Binary decoded string  →  [1] Deflate compress  →  [2] Base93 encode  →  [3] Add version header
```

Every encoded VS script is the result of these three operations applied in order. Decoding reverses them exactly.

The input to step 1 is not plain text — it is the **internal binary format** using `\x1a`/`\x1b` separators. See [Binary Decoded Format](binary-format.md) for how that string is structured.

---

## Step 1 — Deflate Compress

The binary decoded string is compressed using **raw deflate** (no zlib or gzip wrapper).

The compression level depends on the length of the UTF-8 bytes:

| Input size | Compression level |
|---|---|
| < 2048 bytes | 7 |
| 2048 – 65536 bytes | 5 |
| > 65536 bytes | 3 |

```python
import zlib

def compress_deflate(text: str) -> bytes:
    data = text.encode('utf-8')
    n = len(data)
    if n < 2048:
        level = 7
    elif n > 65536:
        level = 3
    else:
        level = 5
    return zlib.compress(data, level=level, wbits=-15)  # wbits=-15 = raw deflate
```

> **wbits=-15** is the critical flag. It produces raw deflate with no header or checksum. Using `wbits=15` (zlib) or `wbits=47` (gzip) will produce bytes the decoder cannot read.

---

## Step 2 — Base93 Encode

The compressed bytes are encoded into a printable ASCII string using a custom **Base93** alphabet.

### Charset (CHARS_OLD)

```
ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ 
```

93 characters total (index 0–92). The last character is a space.

This is the same charset used by `Base93.lua` (the `entry` table), confirmed from the decompiled Lua source.

### Algorithm

The encoder reads the compressed bytes and packs them into pairs of Base93 characters. Each pair encodes either 13 or 14 bits depending on the intermediate value:

```python
CHARS_OLD = list("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ ")

def base93_encode(data: bytes) -> str:
    result = []
    queue = 0
    nbits = 0

    for byte in data:
        queue += byte * (1 << nbits)
        nbits += 8
        while nbits > 13:
            masked = queue & 8191          # read 13 bits
            if masked > 456:
                queue >>= 13
                nbits -= 13
            else:
                masked = queue & 16383     # read 14 bits instead
                queue >>= 14
                nbits -= 14
            result.append(CHARS_OLD[masked % 93])
            result.append(CHARS_OLD[masked // 93])

    # flush remaining bits
    if nbits > 0:
        result.append(CHARS_OLD[queue % 93])
        if nbits > 7 or queue > 92:
            result.append(CHARS_OLD[queue // 93])

    return ''.join(result)
```

**Key rule:** if the 13-bit value is ≤ 456, the encoder reads 14 bits instead. This is what allows 93² = 8649 possible pairs to cover all bit patterns efficiently. The decoder uses the same threshold to know how many bits each pair represents.

---

## Step 3 — Add Version Header

The final encoded string is prefixed with a version identifier.

**With control characters (RetroStudio native format):**
```
\x1a + "0000000000000004" + \x1b + <base93_payload>
```

**Without control characters (HTTP / plain text variant):**
```
"0000000000000004" + <base93_payload>
```

| Part | Value | Notes |
|---|---|---|
| `\x1a` | ASCII 26 (SUB) | Start-of-file marker |
| `0000000000000004` | 16-digit version string | Always `4` for current format |
| `\x1b` | ASCII 27 (ESC) | Separator |
| base93 payload | variable length | the encoded compressed data |

The decoder handles both forms — with and without the control char markers.

---

## Full Encode Function

```python
import zlib

CHARS_OLD = list("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[]^_`{|}~ ")
VS_VERSION = '0000000000000004'

def base93_encode(data: bytes) -> str:
    result = []
    queue = 0
    nbits = 0
    for byte in data:
        queue += byte * (1 << nbits)
        nbits += 8
        while nbits > 13:
            masked = queue & 8191
            if masked > 456:
                queue >>= 13
                nbits -= 13
            else:
                masked = queue & 16383
                queue >>= 14
                nbits -= 14
            result.append(CHARS_OLD[masked % 93])
            result.append(CHARS_OLD[masked // 93])
    if nbits > 0:
        result.append(CHARS_OLD[queue % 93])
        if nbits > 7 or queue > 92:
            result.append(CHARS_OLD[queue // 93])
    return ''.join(result)

def compress_deflate(text: str) -> bytes:
    data = text.encode('utf-8')
    n = len(data)
    level = 7 if n < 2048 else (3 if n > 65536 else 5)
    return zlib.compress(data, level=level, wbits=-15)

def encode(binary_decoded: str, include_control_chars: bool = True) -> str:
    """
    Encodes the internal binary decoded string (with \x1a/\x1b separators)
    into a VS encoded string.
    """
    compressed = compress_deflate(binary_decoded)
    payload    = base93_encode(compressed)
    if include_control_chars:
        return '\x1a' + VS_VERSION + '\x1b' + payload
    else:
        return VS_VERSION + payload
```

---

## What the Input Looks Like

The `binary_decoded` string passed to `encode()` is the internal binary format built by the serializer — **not** the human-readable format. For example:

```
\x1a\x1aEditor\x1aCameraPosition\x1b0,0\x1aCameraZoom\x1b0.1C2\x1a\x1aBlock\x1aType\x1bPrint\x1aName\x1bPrint1\x1aVisualPosition\x1b-1.1F4,-0.1F4\x1aChildBlocks\x1bnil\x1aElseChildBlock\x1bnil\x1aInputs\x1bText\x1b0\x1bHello world\x1aOutputs
```

See [Binary Decoded Format](binary-format.md) for how to build this string.

---

## API Usage

If you are using the RetroStudio backend, you can encode via HTTP:

```
POST /encode
Content-Type: application/json

{
  "text": "<your decoded script here>",
  "keep_original": true
}
```

Response:

```json
{
  "output": "0000000000000004<base93_payload>",
  "stats": {
    "input_chars": 180,
    "compressed_bytes": 92,
    "output_chars": 130
  }
}
```

Set `keep_original: false` to get the version without `\x1a`/`\x1b` markers.

---

## Legacy Format (Versions 1–2)

Older scripts used **LZW compression + a custom base93 encoding** instead of deflate. These can be decoded but encoding always produces version 4 format. See [Legacy Format](legacy.md) for details.

Do not use legacy encoding for new scripts.

---

## Common Mistakes

**Using the wrong wbits:** `zlib.compress(data, wbits=15)` wraps in a zlib header. The decoder expects raw deflate (`wbits=-15`). The output will be unreadable.

**Using the wrong charset:** There is a second charset (`CHARS_NEW`) that shifts one character. It is only used as a fallback during decode for older files. Always use `CHARS_OLD` when encoding.

**Forgetting the version header:** The decoder reads the version number to decide which decompression path to take. Without the `0000000000000004` prefix the decoder may fail or treat the script as legacy format.

**Double-encoding:** If your input already starts with `0000000000000004` or `\x1a`, it is already encoded. Encoding it again will produce a broken nested payload.

**Passing human-readable text instead of binary format:** The encoder input must be the binary string with `\x1a`/`\x1b` separators, not the space-separated human-readable format. Passing human-readable text will encode and compress fine but the result will not load correctly in RetroStudio.
