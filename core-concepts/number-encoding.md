# Number Encoding

VisualSource encodes all numbers in **hexadecimal** rather than decimal. This applies to literal values in block inputs, VisualPosition coordinates, and CameraZoom.

Understanding this encoding is essential when reading decoded scripts or writing your own.

---

## Integer Encoding

Integers are written as plain hex strings (uppercase or lowercase):

| Hex | Decimal |
|---|---|
| `A` | 10 |
| `C8` | 200 |
| `1E` | 30 |
| `64` | 100 |
| `3E8` | 1000 |
| `F` | 15 |

**Negative numbers** use a `-` prefix:

| Hex | Decimal |
|---|---|
| `-C8` | -200 |
| `-A` | -10 |

---

## Decimal Encoding

Decimal numbers use the format `int.frac`, where the fractional part is a hex value divided by 1000:

```
0.C8   →  0 + (200 / 1000)  =  0.2
1.1F4  →  1 + (500 / 1000)  =  1.5
0.7D   →  0 + (125 / 1000)  =  0.125
```

The fractional hex value ranges from `0` to `3E7` (0–999).

---

## Vector3 Encoding

Vector3 values use comma-separated hex components:

```
A,14,1E    →  Vector3(10, 20, 30)
0,0,0      →  Vector3(0, 0, 0)
-A,64,0    →  Vector3(-10, 100, 0)
```

---

## Color3 Encoding

Color3 components (R, G, B) are also hex, ranging from `0` to `FF` (0–255):

```
FF,0,0     →  Color3.fromRGB(255, 0, 0)   -- Red
0,FF,0     →  Color3.fromRGB(0, 255, 0)   -- Green
FF,FF,FF   →  Color3.fromRGB(255, 255, 255) -- White
0,0,0      →  Color3.fromRGB(0, 0, 0)     -- Black
```

---

## VisualPosition Coordinates

Canvas coordinates in `VisualPosition` and `CameraPosition` use the decimal encoding format:

```
VisualPosition -0.36B,0.271
```

Breaking it down:
- `-0.36B` → negative 0 + (875 / 1000) = **-0.875 units**
- `0.271` → 0 + (625 / 1000) = **0.625 units**

These units are multiplied by 172 pixels per unit to get canvas pixel positions, offset from the canvas origin at 4000 pixels.

---

## Quick Reference Table

| Type | Format | Example | Result |
|---|---|---|---|
| Integer | `HEX` | `C8` | 200 |
| Negative integer | `-HEX` | `-1E` | -30 |
| Decimal | `INT.FRAC` | `1.1F4` | 1.5 |
| Negative decimal | `-INT.FRAC` | `-0.C8` | -0.2 |
| Vector3 | `X,Y,Z` | `A,14,1E` | (10, 20, 30) |
| Color3 | `R,G,B` | `FF,80,0` | RGB(255, 128, 0) |

---

## Why Hex?

VisualSource uses hex encoding to keep the encoded script format compact. When scripts are compressed and stored, smaller text representations lead to smaller payloads. The encoding is entirely internal — when working in the visual editor, you always see normal decimal numbers.
