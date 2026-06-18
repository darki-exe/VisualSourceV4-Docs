# Logic

Logic blocks handle **control flow**: conditions, loops, variables, functions, and tables. These are the structural backbone of any VisualSource script.

---

## Overview

| Block Type | Description |
|---|---|
| `If` | Conditional branching — run one set of blocks or another |
| `ForLoop2` | Numeric loop — run blocks N times |
| `WhileLoop3` | Conditional loop — run blocks while a condition is true |
| `SetVariable1` | Assign a value to a named variable |
| `GetVariable` | Read a variable by name |
| `DoNotRun` | Mark a section as a named subroutine |
| `ExecuteBlock` | Call a named subroutine |
| `Wait` | Pause execution for N seconds |
| `CreateTable` | Create a Luau table |
| `SetTableValue` | Set a key-value pair in a table |
| `GetTableValue` | Read a value from a table |
| `Return` | Return a value from a function |
| `Break` | Break out of a loop |
| `Continue` | Skip to the next loop iteration |

---

## Documented Blocks

*(Coming soon)*

---

## Key Patterns

### Conditional
```
If → (true branch) / ElseChildBlock → (false branch)
```

### Loop
```
ForLoop2 → (body runs N times)
WhileLoop3 → (body runs while condition is true)
```

### Variable
```
SetVariable1 → stores a value
GetVariable → retrieves it by name
```
