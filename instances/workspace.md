# Workspace

The Workspace is the container for all physical objects that exist in the 3D game world. Everything players can see and interact with physically must reside here.

**Path:** `game.Workspace`

---

## Properties

### Data
| Property | Type | Notes |
|---|---|---|
| `ClassName` | String | `"Workspace"` (read-only) |
| `Name` | String | `"Workspace"` |
| `Parent` | Object | `game` (DataModel) |
| `PrimaryPart` | Object | Reference to a Part |

### Behavior
| Property | Type | Default | Notes |
|---|---|---|---|
| `Archivable` | Bool | `true` | Whether this can be saved |
| `FallenPartsDestroyHeight` | Number | `-500` | Parts below this Y value are automatically destroyed |

---

## Notes

- All `Part`, `Model`, and physical game objects must be placed in Workspace to be visible and interactive.
- The `Camera` and `CurrentCamera` also reside inside Workspace.
- Objects that fall below `FallenPartsDestroyHeight` are automatically removed — useful for preventing memory leaks from falling parts.
- Player character models spawn as children of Workspace.

---

## Common Object Paths

```
game.Workspace                          -- The Workspace itself
game.Workspace.Part                     -- A Part named "Part"
game.Workspace.Model                    -- A Model named "Model"
game.Workspace.Model.HumanoidRootPart   -- Root part of a character model
```

---

## Example Usage

```
-- Set the FallenPartsDestroyHeight via SetObjectProperty
Block Type SetObjectProperty ...
  Inputs:
    Object  2  game.Workspace
    Property 0 FallenPartsDestroyHeight
    Value    0 -3E8         -- hex -1000
```
