# VisualSource V4 Documentation

**VisualSource (VS)** is a node-based visual scripting language built for [RetroStudio](https://retrostudio.net) — a mid-2015 era Roblox game development environment. Instead of writing code, you connect visual **Blocks** together to build game logic, which is then compiled to Luau automatically.

---

## What is VisualSource?

VisualSource lets you build scripts by connecting blocks on a visual canvas. Each block represents an action, event, condition, or value — and by wiring them together, you create fully functional game scripts without writing a single line of code.

Under the hood, every script is compiled to **Luau** (Roblox's scripting language), so you get the full power of scripting with the simplicity of a visual interface.

---

## Key Concepts

| Concept | Description |
|---|---|
| **Block** | The fundamental unit. Each block has a type, inputs, and outputs. |
| **Input** | A value fed into a block (literal, variable reference, or object path). |
| **Output** | A named variable slot produced by a block, used as input by other blocks. |
| **ChildBlocks** | Blocks that run sequentially inside a parent block (the "body"). |
| **Event Block** | A block that fires asynchronously when something happens in-game. |
| **Root Block** | A block with no parent — runs automatically at script start. |

---

## Script Contexts

Scripts in VisualSource run in one of three contexts:

- **Server Script** — Runs on the server. Has full access to all players and game state.
- **Local Script** — Runs on the client. Has access to `LocalPlayer` and client-side events.
- **Module Script** — Required by other scripts. Returns a value.

> Some blocks are restricted to a specific context. Check each block's **Context** field before using it.

---

## Getting Started

1. [**Script Format**](core-concepts/script-format.md) — Learn the human-readable and encoded formats
2. [**Number Encoding**](core-concepts/number-encoding.md) — Understand how numbers are stored in VS
3. [**Value Types**](core-concepts/value-types.md) — All supported data types
4. [**Block Reference**](blocks/README.md) — Every block, categorized
5. [**Game Hierarchy**](instances/README.md) — Services and instances reference
6. [**Examples**](examples/README.md) — Common patterns and real scripts
