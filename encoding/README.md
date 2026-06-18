# Encoding & Decoding

VisualSource scripts exist in two forms: **decoded** (human-readable, used for editing) and **encoded** (compact, used for storage and transmission).

---

## Pages

- [**Encode**](encode.md) — how to turn a decoded script into an encoded string
- [**Decode**](decode.md) — how to turn an encoded string back into a decoded script
- [**Binary Decoded Format**](binary-format.md) — the `\x1a`/`\x1b` separator structure used internally
- [**Legacy Format**](legacy.md) — v1–2 LZW format (read-only reference)

---

## Quick Summary

### Encode (decoded → encoded)

1. Serialize the script into the **internal binary format** (`\x1a`/`\x1b` separators)
2. Compress with **raw deflate** (`wbits=-15`)
3. Encode the compressed bytes with **Base93** (`CHARS_OLD` charset)
4. Prepend the version header: `\x1a0000000000000004\x1b`

### Decode (encoded → decoded)

1. Strip control chars, extract the **version string** and **base93 payload**
2. Decode the payload with **Base93** (try `CHARS_OLD` first, then `CHARS_NEW`)
3. Decompress with **raw deflate** (`wbits=-15`)
4. Result is the **internal binary format** (string with `\x1a`/`\x1b` separators)

---

## Format at a Glance

### Encoded string

```
\x1a 0000000000000004 \x1b <base93_payload>
 ^         ^           ^          ^
 |         |           |          |
SUB    version (v4)   ESC    encoded data
```

The `\x1a`/`\x1b` markers are optional — the decoder also accepts the version string without them.

### Binary decoded string (result after decode)

```
\x1a\x1a Editor \x1a CameraPosition \x1b 0,0 \x1a CameraZoom \x1b 0.1C2
\x1a\x1a Block  \x1a Type \x1b Print \x1a Name \x1b Print1 \x1a Inputs \x1b Text \x1b 0 \x1b Hello \x1a Outputs
```

See [Binary Decoded Format](binary-format.md) for the full specification.
