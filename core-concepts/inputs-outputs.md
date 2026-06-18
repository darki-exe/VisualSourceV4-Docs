# Inputs & Outputs

Understanding how data flows between blocks is fundamental to VisualSource. Blocks communicate through **inputs** (values a block receives) and **outputs** (values a block produces).

---

## Inputs

Every block input has three components:

```
<InputName> <value_type> <value>
```

### value_type 0 — Literal

A hardcoded value written directly into the script.

```
Text 0 Hello world
Time 0 A
Enabled 0 true
Position 0 0,A,0
Color 0 FF,0,0
```

### value_type 1 — Variable Reference

References the **output variable** of another block. The value is whatever that block produced at runtime.

```
Number1 1 my_result
Object 1 player_ref
Text 1 formatted_name
```

The value `my_result`, `player_ref`, etc. must exactly match the output variable name declared in another block's `Outputs`.

### value_type 2 — Object Path

A dot-separated path to an instance in the game hierarchy.

```
Object 2 game.Workspace.Part
Object 2 game.Players.LocalPlayer
Object 2 game.Lighting
```

---

## Outputs

Outputs declare named variable slots that other blocks can reference:

```
Outputs <OutputName> <VariableName>
```

- `OutputName` — the slot name as defined by the block type (e.g. `Player`, `Result`, `Value`)
- `VariableName` — the identifier used by other blocks in `value_type 1` inputs

### Example

```
Block Type PlayerAdded Name Player Added1 ... Outputs Player player
```

The block produces an output named `Player` (the slot), stored in variable `player`. Another block can then reference it:

```
Block Type Print Name Print1 ... Inputs Text 1 player ...
```

### Multiple Outputs

Some blocks produce multiple outputs:

```
Outputs Result result X x Y y Z z
```

Each output is a name-variable pair, one after another.

### Empty Outputs

If a block produces no outputs, write `Outputs` with nothing after it:

```
Outputs
```

---

## Data Flow Example

Here's how data flows in a simple chain:

```
[RandomNumber]
  Outputs: Result → rng

[SetVariable1]
  Inputs: Value 1 rng     ← references RandomNumber's output
  Outputs: (none)
```

In decoded format:
```
Block Type RandomNumber Name Random Number1 VisualPosition -0.36B,-1.7D ChildBlocks Set Variable1 ElseChildBlock nil Inputs Minimum 0 0 Maximum 0 A Outputs Result rng  Block Type SetVariable1 Name Set Variable1 VisualPosition -0.36B,-0.1F4 ChildBlocks ElseChildBlock nil Inputs Value 1 rng Outputs VariableName my_variable
```

---

## ChildBlocks and ElseChildBlock

These fields control **execution flow**, not data flow:

- `ChildBlocks` — a space-separated list of block **names** that run sequentially inside this block
- `ElseChildBlock` — the block name that runs when an `If` condition is false, or `nil` if none

```
Block Type If Name If1 ... ChildBlocks Action1 Action2 ElseChildBlock ElseAction1 ...
```

This means: run `Action1` then `Action2` if the condition is true; run `ElseAction1` if false.

---

## Root Blocks

Any block that is **not listed** in any other block's `ChildBlocks` is a **root block**. Root blocks execute automatically when the script starts. Event blocks (`PlayerAdded`, `Heartbeat`, `PartTouched`, etc.) are always root blocks and fire asynchronously when their event occurs.

---

## Subroutines (DoNotRun)

The `DoNotRun` block marks a section as a **named subroutine** — it will not run unless explicitly called by an `ExecuteBlock` block. This is how you define reusable logic that runs on demand.

```
Block Type DoNotRun Name My Subroutine ...
Block Type ExecuteBlock Name Execute1 ... Inputs BlockName 0 My Subroutine ...
```
