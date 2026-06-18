# Events

Event blocks fire **asynchronously** when something happens in-game. They are always **root blocks** — they sit at the top of a block chain and trigger automatically when their condition is met, without needing to be called.

> Unlike Action blocks, Event blocks are never sequentially chained into — they wait indefinitely and fire each time their event occurs.

---

## Documented Blocks

| Block | Visual Name | Description |
|---|---|---|
| [`PlayerAdded`](PlayerAdded.md) | Player Added | Fires when a player joins the game |

---

## How Event Blocks Work

Event blocks internally call `:Connect()` on a Roblox signal. The VS runtime wraps this using `Util.addEvent()`, which:

1. Connects the event listener
2. Stores the connection so it can be disconnected later via `DisconnectEvent`
3. Executes the block's `ChildBlocks` each time the event fires, passing output variables into the environment

### BumpEnvironment

Most event blocks have `BumpEnvironment = true`. This means each time the event fires, the child blocks run in a **fresh scoped environment** — variables produced by the event (like `player`) don't bleed into other event invocations.

---

## Common Event Patterns

### Player Lifecycle
```
PlayerAdded → CharacterAdded → (do something per spawn)
PlayerRemoving → (cleanup)
```

### Touch Detection
```
PartTouched → GetPlayerFromCharacter → (reward / kick / etc.)
```

### Heartbeat / Frame Loop
```
Heartbeat → (per-frame logic)
```

---

## Context Notes

- Most event blocks work in **All Scripts**, but some are **Local Only** (e.g. `RenderStepped`, keyboard input events) since they rely on client-side signals.
- `BindToClose` only makes practical sense in **Server Scripts** — it fires before the server shuts down.
- `PlayerAdded` already fires for players currently in the game when the script starts (the internal loop handles this).
