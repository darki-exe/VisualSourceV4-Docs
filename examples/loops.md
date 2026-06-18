# Loops

Examples for repeating actions using For loops, While loops, and looping through object children.

---

## For Loop — Count 1 to 10

Runs 10 times, printing the current iteration number each time.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type ForLoop2 Name For Loop1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Initial 0 1 Increment 0 1 Maximum 0 A Outputs IterationNumber i  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 1 i Outputs
```

**What it does:**
- Starts at 1, increments by 1, runs until reaching 10 (`A` hex)
- `IterationNumber` output (variable `i`) holds the current count each iteration

---

## For Loop — Count Down

Count from 10 down to 1 by using a negative increment.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type ForLoop2 Name For Loop1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Initial 0 A Increment 0 -1 Maximum 0 1 Outputs IterationNumber i  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 1 i Outputs
```

> Initial = `A` (10), Increment = `-1`, Maximum = `1`

---

## While Loop — Wait Until Condition

Runs a `Wait` block in a loop until a condition is met. (Example: loop while health is above 0)

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type WhileLoop3 Name While Loop1 VisualPosition -0.36B,-0.271 ChildBlocks Wait1 ElseChildBlock nil Inputs Value 1 1 health ComparisonType 0 Greater Value 2 0 0  Block Type Wait Name Wait1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Time 0 1 Outputs
```

**Comparison Types:**

| Value | Meaning |
|---|---|
| `Equal` | `==` |
| `NotEqual` | `~=` |
| `Greater` | `>` |
| `Less` | `<` |
| `GreaterEqual` | `>=` |
| `LessEqual` | `<=` |

---

## Loop Through Children

Iterate over every child of an object.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type LoopThroughChildren Name Loop Children1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Object 2 game.Workspace.Model Outputs Child child  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 1 child Outputs
```

**What it does:**
- Iterates over every direct child of `game.Workspace.Model`
- `Child` output (variable `child`) holds each child instance on each iteration

---

## Loop Through Descendants

Iterate over every descendant (children, grandchildren, etc.) of an object.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type LoopThroughDescendants Name Loop Descendants1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Object 2 game.Workspace Outputs Descendant desc  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 1 desc Outputs
```

---

## For Loop — Repeat Action N Times

Destroy all children of a folder 5 times (practical: spawn N enemies).

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type ForLoop2 Name For Loop1 VisualPosition -0.36B,-0.271 ChildBlocks Clone1 ElseChildBlock nil Inputs Initial 0 1 Increment 0 1 Maximum 0 5 Outputs IterationNumber i  Block Type CloneObject Name Clone1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.EnemyTemplate Parent 2 game.Workspace Outputs NewObject new_enemy
```

> `Maximum 0 5` — hex `5` = 5, so this runs 5 times and clones `EnemyTemplate` into Workspace each time.

---

## Break Out of a Loop

Use `BreakLoop` inside a loop's `ChildBlocks` to stop iteration early.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type ForLoop2 Name For Loop1 VisualPosition -0.36B,-0.5DC ChildBlocks If1 ElseChildBlock nil Inputs Initial 0 1 Increment 0 1 Maximum 0 64 Outputs IterationNumber i  Block Type If Name If1 VisualPosition -0.36B,-0.2EE ChildBlocks Break1 ElseChildBlock nil Inputs Value 1 1 i ComparisonType 0 Equal Value 2 0 A  Block Type BreakLoop Name Break1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Outputs
```

**What it does:** Loops from 1 to 100 (`64` hex), but breaks when `i` equals 10 (`A` hex).
