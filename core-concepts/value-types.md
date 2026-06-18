# Value Types

VisualSource supports the following data types for block inputs and outputs. Each type determines what kind of value a block can accept or produce.

---

## String

A sequence of text characters.

- Used for names, messages, property names, class names, etc.
- In literal inputs (`value_type 0`): written as plain text without quotes
- Example: `Text 0 Hello world`

---

## Number

A numeric value, either integer or decimal.

- Stored as hex-encoded values in scripts (see [Number Encoding](number-encoding.md))
- Example: `Time 0 A` → 10 seconds
- Example: `Amount 0 C8` → 200

---

## Bool

A boolean true/false value.

- Accepted values: `true` or `false`
- Example: `Enabled 0 true`
- Example: `Visible 0 false`

---

## Vector3

A 3D position or direction with X, Y, Z components.

- Written as comma-separated hex values: `X,Y,Z`
- Example: `Position 0 A,0,14` → Vector3(10, 0, 20)
- Example: `Direction 0 0,1,0` → Vector3(0, 1, 0) — pointing up

---

## Vector2

A 2D position with X, Y components.

- Written as comma-separated hex values: `X,Y`
- Example: `Size 0 64,64` → Vector2(100, 100)

---

## UDim2

A 2D size/position that combines scale (relative) and offset (pixels).

- Format: `scaleX,offsetX,scaleY,offsetY`
- Scale values are 0–1 (relative to parent size)
- Offset values are pixel amounts
- Example: `Size 0 1,0,1,0` → UDim2.new(1, 0, 1, 0) — full parent size

---

## Color3

An RGB color value.

- Written as comma-separated hex values: `R,G,B` (0–255 each)
- Example: `Color 0 FF,0,0` → Red
- Example: `Color 0 0,FF,80` → Green-teal

---

## BrickColor

A named color from the classic Roblox BrickColor palette.

- Written as the color name string
- Example: `BrickColor 0 Bright red`
- Example: `BrickColor 0 Medium blue`
- See the BrickColors reference for all valid names

---

## Object

A reference to an instance in the game hierarchy.

- In literal inputs (`value_type 0`): written as `nil` (no object)
- In object path inputs (`value_type 2`): written as a dot-separated path
- In variable reference inputs (`value_type 1`): written as an output variable name
- Example (path): `Object 2 game.Workspace.Part`
- Example (variable): `Object 1 my_player`

---

## Nil

Represents no value / empty / null.

- Written as `nil`
- Used when an object input should be empty
- Some blocks accept `nil` explicitly as a valid type

---

## Enum

A predefined set of named options for a specific property.

- Written as the enum value name (string)
- Example: `State 0 Jumping`
- Available values depend on which property is being set

---

## Any

Some blocks accept any type as input. These are marked with `VariableType = "Any"` in the block definition and will accept whatever value is connected.

---

## Type Hints

Block outputs often include **TypeHints** — these are informational hints about what type the output will likely be. They help you know what kind of input can receive the value. TypeHints are not strictly enforced, but connecting mismatched types may cause runtime errors.

Example:
```
Outputs Player player    -- TypeHint: Player
Outputs Result result    -- TypeHint: Any
```
