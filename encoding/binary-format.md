# Binary Decoded Format

After decoding an encoded script, the result is **not human-readable text** — it is a string in the **internal binary format** that uses the control characters `\x1a` (ASCII 26, SUB) and `\x1b` (ASCII 27, ESC) as structural separators.

This format is produced by RetroStudio's `SaveModule.lua` and consumed by the `LoadModules/`.

---

## The Two Separators

| Character | ASCII | Name | Role |
|---|---|---|---|
| `\x1a` | 26 | SUB | Separates **objects** and **property keys** |
| `\x1b` | 27 | ESC | Separates **values** within a property |

How they differ:

- `\x1a\x1a` → begins a new top-level object (`Editor`, `Block`, `Comment`)
- `\x1a` (alone) → begins a new property inside an object (`Type`, `Name`, `Inputs`, etc.)
- `\x1b` → separates a property key from its value, and separates multiple values within a property

---

## Overall Structure

```
\x1a\x1a<ObjectType>\x1a<Prop>\x1b<Val>\x1a<Prop>\x1b<Val1>\x1b<Val2>...
\x1a\x1a<ObjectType>\x1a<Prop>\x1b<Val>...
```

A complete script always follows this order:

1. One `Editor` section (always first)
2. One `Block` entry per block
3. One `Comment` entry per comment (after all blocks)

---

## Editor Section

```
\x1a\x1aEditor\x1aCameraPosition\x1b<x,y>\x1aCameraZoom\x1b<zoom>
```

| Property | Value | Example |
|---|---|---|
| `CameraPosition` | `X,Y` in hex-encoded floats | `0,0` or `-0.1F4,0.C8` |
| `CameraZoom` | zoom level hex-encoded | `0.1C2` |

Expanded for readability:
```
\x1a\x1a Editor
\x1a CameraPosition \x1b 0,0
\x1a CameraZoom     \x1b 0.1C2
```

---

## Block Section

```
\x1a\x1aBlock
\x1aType\x1b<TypeName>
\x1aName\x1b<BlockName>
\x1aVisualPosition\x1b<x,y>
\x1aChildBlocks\x1b<Name1>\x1b<Name2>...
\x1aElseChildBlock\x1bnil
\x1aInputs\x1b<InputName>\x1b<value_type>\x1b<value>[\x1b<data_type>]...
\x1aOutputs\x1b<OutputName>\x1b<VarName>...
```

### Required Properties

Every `Block` section must include all of these properties, in this order:

| Property | Content |
|---|---|
| `Type` | Internal block type name (e.g. `Print`, `If`, `PlayerAdded`) |
| `Name` | Unique instance name (e.g. `Print1`, `If Block1`) |
| `VisualPosition` | X,Y canvas coordinates, hex-encoded (e.g. `-0.36B,-0.271`) |
| `ChildBlocks` | Child block names separated by `\x1b`, or `nil` if empty |
| `ElseChildBlock` | Else branch block name, or `nil` |
| `Inputs` | Input tokens (see below) |
| `Outputs` | Output tokens (see below) |

### Input Format

Each input occupies 2 or 3 `\x1b`-separated tokens depending on the `value_type`:

**value_type `0` — Literal:**
```
\x1b<InputName>\x1b0\x1b<value>
```

**value_type `1` — Any/Tuple (includes data_type):**
```
\x1b<InputName>\x1b1\x1b<value>\x1b<data_type>
```

**value_type `2` — Variable reference (output from another block):**
```
\x1b<InputName>\x1b2\x1b<variable_name>
```

> **Important:** `value_type 2` in the binary format means **variable reference** (an output from another block). This is different from the human-readable format, where `1` is variable reference and `2` is object path.

If a block has no inputs, write `\x1aInputs` with no `\x1b` tokens after it.

### Output Format

```
\x1b<OutputSlotName>\x1b<VarName>
```

Multiple outputs are concatenated:
```
\x1aOutputs\x1bResult\x1bresult\x1bX\x1bx\x1bY\x1by
```

If a block has no outputs: `\x1aOutputs` with no `\x1b` tokens after it.

---

## Comment Section

Comments come **after all blocks**, in the order they appear in the editor.

```
\x1a\x1aComment
\x1aPosition\x1b<x,y>
\x1aSize\x1b<w,h>
\x1aColor\x1b<R,G,B>
\x1aName\x1b<comment text>
```

All numeric values are hex-encoded. Color3 uses R,G,B in 0–FF range.

---

## Full Example

A script with a `PlayerAdded` block calling a `Print` block:

```
\x1a\x1aEditor\x1aCameraPosition\x1b0,0\x1aCameraZoom\x1b0.1C2\x1a\x1aBlock\x1aType\x1bPlayerAdded\x1aName\x1bPlayer Added1\x1aVisualPosition\x1b-0.36B,-0.271\x1aChildBlocks\x1bPrint1\x1aElseChildBlock\x1bnil\x1aInputs\x1aOutputs\x1bPlayer\x1bplayer\x1a\x1aBlock\x1aType\x1bPrint\x1aName\x1bPrint1\x1aVisualPosition\x1b-0.36B,0\x1aChildBlocks\x1bnil\x1aElseChildBlock\x1bnil\x1aInputs\x1bText\x1b0\x1bHello world\x1aOutputs
```

Expanded for readability:
```
\x1a\x1a Editor
  \x1a CameraPosition  \x1b 0,0
  \x1a CameraZoom      \x1b 0.1C2

\x1a\x1a Block
  \x1a Type            \x1b PlayerAdded
  \x1a Name            \x1b Player Added1
  \x1a VisualPosition  \x1b -0.36B,-0.271
  \x1a ChildBlocks     \x1b Print1
  \x1a ElseChildBlock  \x1b nil
  \x1a Inputs
  \x1a Outputs         \x1b Player \x1b player

\x1a\x1a Block
  \x1a Type            \x1b Print
  \x1a Name            \x1b Print1
  \x1a VisualPosition  \x1b -0.36B,0
  \x1a ChildBlocks     \x1b nil
  \x1a ElseChildBlock  \x1b nil
  \x1a Inputs          \x1b Text \x1b 0 \x1b Hello world
  \x1a Outputs
```

---

## How the LoadModule Parses It

`LoadModules/0000000000000004.lua` does exactly this:

```lua
-- 1. Split into top-level objects by the double separator \x1a\x1a
local objects = string.split(decoded, "\26\26")
table.remove(objects, 1)  -- remove the leading empty entry

for _, obj in objects do
    -- 2. Get the object type name (Editor, Block, Comment)
    local sep = string.find(obj, "\26")
    local objectType = string.sub(obj, 1, sep - 1)
    local rest = string.sub(obj, sep + 1)

    -- 3. Split into properties by \x1a
    for _, prop in string.split(rest, "\26") do
        -- 4. Split into key + values by \x1b
        local tokens = string.split(prop, "\27")
        local key = tokens[1]
        table.remove(tokens, 1)
        -- tokens now holds the values
    end
end
```

---

## Key Rules

- **Never** use `\x1a` or `\x1b` inside text values (block names, input values, etc.) — they are reserved as separators and will corrupt the parse
- The `Editor` section must **always** come first
- `ElseChildBlock` must **always** be present; use `nil` if there is no else branch
- Empty `ChildBlocks` must use `nil`, not an empty list
- The full binary string is assembled as `\x1a\x1a` + `(\x1a\x1a).join(parts)` — meaning it starts with `\x1a\x1a` and objects are separated by `\x1a\x1a`

---

## Bool Values in Binary Format

In the binary format, booleans are encoded as `"1"` (true) and `"0"` (false), **not** as `"true"`/`"false"`.

```
\x1bEnabled\x1b0\x1b1     -- Enabled = true
\x1bVisible\x1b0\x1b0     -- Visible = false
```

This is what `SaveModule.lua` produces (`formatValueIn` with `flag == "Bool"`).
