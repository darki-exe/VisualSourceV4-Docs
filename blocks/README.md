# Block Reference

VisualSource V4 includes **331 blocks** across 6 categories. Each category has its own folder with a description and a `Blocks/` subfolder containing deep documentation for individual blocks.

---

## Categories

| Category | Description |
|---|---|
| [Actions](Actions/) | Perform operations on objects, players, sounds, and the game world |
| [Events](Events/) | Listen for things that happen in-game asynchronously |
| [Input](Input/) | Detect keyboard, mouse, and GUI interaction |
| [Logic](Logic/) | Control flow: conditions, loops, variables, functions, tables |
| [Math](Math/) | Arithmetic, vectors, CFrame, Color3, random numbers |
| [Misc](Misc/) | Utilities, debug tools, services, JSON, plugins |

---

## Block Flags

| Flag | Meaning |
|---|---|
| `Event` | Fires asynchronously when something happens. Always a root block. |
| `Auto Execute` | Runs sequentially as part of a chain. |
| *(none)* | Control-flow blocks like `If`, `ForLoop2` — structured execution. |

---

## Context Restrictions

| Context | Where it runs |
|---|---|
| `All Scripts` | Works in Server Scripts, Local Scripts, and Module Scripts |
| `Server Only` | Only works in Server Scripts |
| `Local Only` | Only works in Local Scripts |
