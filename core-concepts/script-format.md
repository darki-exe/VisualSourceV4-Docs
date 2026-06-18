# Script Format

VisualSource scripts exist in two formats: **encoded** (compact, used for storage and transmission) and **decoded** (human-readable, used for editing and understanding).

---

## Encoded Format

Encoded scripts are compressed strings used by RetroStudio internally. They come in different versions:

| Version | Compression | Notes |
|---|---|---|
| 1–2 | Legacy LZW + base93 | Read-only support |
| 3+ | Deflate (zlib) + base93 | Current format |

**Version 4 structure:**

```
\x1a + "0000000000000004" + \x1b + <base93_payload>
```

Or without control characters (normal format):

```
0000000000000004 + <base93_payload>
```

The base93 character set uses printable ASCII characters to encode compressed binary data efficiently.

---

## Decoded (Human-Readable) Format

This is the format you read, write, and debug scripts in. Each block is on one line, all fields separated by plain spaces.

### Overall Structure

Every script starts with an **Editor header**, followed by one or more **Block definitions**, separated by two spaces.

```
Editor CameraPosition <x>,<y> CameraZoom <z>  Block Type <TypeName> Name <BlockName> VisualPosition <x>,<y> ChildBlocks ... ElseChildBlock ... Inputs ... Outputs ...
```

### Editor Header

```
Editor CameraPosition 0,0 CameraZoom 0.1C2
```

| Field | Description |
|---|---|
| `CameraPosition` | X,Y position of the camera on the canvas (hex-encoded) |
| `CameraZoom` | Zoom level of the canvas (hex-encoded) |

### Block Definition

```
Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Outputs Player player
```

| Field | Description |
|---|---|
| `Type` | The internal block type name (e.g. `PlayerAdded`, `If`, `Print`) |
| `Name` | A unique instance name for this block — used to reference it in `ChildBlocks` |
| `VisualPosition` | X,Y canvas coordinates (hex-encoded, controls block placement) |
| `ChildBlocks` | Space-separated list of block names that run inside this block |
| `ElseChildBlock` | The block that runs on the else branch (only for `If` blocks), or `nil` |
| `Inputs` | Input definitions (see below) |
| `Outputs` | Output definitions (see below) |

---

## Inputs

Inputs supply values to a block. Each input has three parts:

```
Inputs <InputName> <value_type> <value>
```

### Value Types

| value_type | Meaning | Example |
|---|---|---|
| `0` | Literal value | `Text 0 Hello world` |
| `1` | Variable reference (output from another block) | `Number1 1 my_result` |
| `2` | Object path | `Object 2 game.Workspace.Part` |

### Literal Value Examples

```
Time 0 A               -- Number literal: hex A = 10
Text 0 Hello world     -- String literal
Enabled 0 true         -- Bool literal
Color 0 FF,0,0         -- Color3: RGB 255,0,0
Position 0 A,14,1E     -- Vector3: 10, 20, 30
```

---

## Outputs

Outputs declare the variable names that other blocks can reference:

```
Outputs Player player
```

Multiple outputs:

```
Outputs Result result X x Y y
```

If a block has no outputs, write `Outputs` with nothing after it.

---

## Full Example

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Outputs Player player  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 0 Hello world Outputs
```

This script fires when a player joins, then prints "Hello world" to the output.

---

## Rules & Tips

- **Always** include the `Editor` header at the start.
- **Always** include `VisualPosition` on every block.
- Separate blocks with exactly **two spaces**, not newlines.
- Block names must be **unique** within a script.
- Empty field keywords (e.g. `ChildBlocks`, `Outputs`) must still be written even if they have no values.
- Never use `\x1a`, `\x1b`, or raw binary separators when writing scripts manually — the system handles encoding.
