# Block Reference

VisualSource V4 includes **331 blocks** across 6 categories. Each block has a type name, visual name, description, context restriction, optional flags, and defined inputs/outputs.

---

## Categories

| Category | Description |
|---|---|
| [Actions](actions.md) | Perform operations on objects, players, and the game world |
| [Events](events.md) | Listen for things that happen in-game asynchronously |
| [Input](input.md) | Detect keyboard, mouse, and GUI interaction |
| [Logic](logic.md) | Control flow: conditions, loops, variables, functions, tables |
| [Math](math.md) | Math operations, vectors, CFrame, Color3, random numbers |
| [Miscellaneous](misc.md) | Utilities, debug tools, services, JSON, plugins |

---

## Block Flags

Many blocks carry flags that describe their behavior:

| Flag | Meaning |
|---|---|
| `Event` | Fires asynchronously when something happens. Always a root block. |
| `Auto Execute` | Runs sequentially as part of a chain. |
| *(none)* | Control flow blocks like `If`, `ForLoop2` — structured execution. |

---

## Context Restrictions

| Context | Where it runs |
|---|---|
| `All Scripts` | Works in Server Scripts, Local Scripts, and Module Scripts |
| `Server Only` | Only works in Server Scripts |
| `Local Only` | Only works in Local Scripts |

---

## Reading Block Entries

Each block entry in the sub-pages follows this structure:

### `BlockTypeName`
**Visual Name:** What you see in the editor  
**Description:** What the block does  
**Context:** Which script types can use it  
**Flags:** `Event`, `Auto Execute`, or none  

**Inputs:**
| Name | Type | Description |
|---|---|---|
| ... | ... | ... |

**Outputs:**
| Name | Type Hint | Description |
|---|---|---|
| ... | ... | ... |

---

## Most Commonly Used Blocks

### For events:
- `PlayerAdded` — fires when a player joins
- `PlayerRemoving` — fires when a player leaves
- `PartTouched` — fires when a part is touched
- `Heartbeat` — fires every frame

### For flow control:
- `If` — conditional branching
- `ForLoop2` — numeric loop
- `WhileLoop3` — conditional loop
- `Wait` — pause execution

### For actions:
- `SetObjectProperty` — set any property on any object
- `GetObjectProperty` — read any property from any object
- `CreateObject` — create a new instance
- `DestroyObject` — remove an instance
- `CloneObject` — duplicate an instance

### For data:
- `SetVariable1` — assign a value to a variable
- `Print` — debug output
- `CreateTable` / `SetTableValue` / `GetTableValue` — work with tables
