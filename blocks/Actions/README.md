# Actions

Action blocks **perform operations** on game objects, players, sounds, terrain, and services. Most are `Auto Execute` — they run inline as part of a sequential block chain.

> Some blocks marked *(Yields)* pause execution until the operation completes before moving to the next block.

---

## Documented Blocks

| Block | Visual Name | Description |
|---|---|---|
| [`CloneObject`](CloneObject.md) | Clone Object | Clones an instance and parents it |

---

## Common Action Patterns

### Object Lifecycle
Create → Clone → Modify → Destroy

```
CreateObject → CloneObject → SetObjectProperty → DestroyObject
```

### Player Actions
```
PlayerAdded → GetObjectProperty (Name) → AddToLeaderstat
```

---

## Flags

All Action blocks are either:

- **`Auto Execute`** — Runs sequentially in a chain, may produce outputs
- **`Event`** flag on a few action-adjacent blocks (e.g. `AnimationStopped`, `PromptGamepassPurchaseFinished`)

---

## Context Notes

Most action blocks work in **All Scripts**. A few are restricted:

- Server-only blocks involve `BanPlayer`, `KickPlayer`, administrative operations
- Local-only blocks involve camera and local player state
