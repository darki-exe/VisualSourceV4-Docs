# `CloneObject`

> **Category:** Actions  
> **Visual Name:** Clone Object  
> **Context:** All Scripts  
> **Flags:** `Auto Execute`

---

## Overview

`CloneObject` creates an exact copy of any instance in the game hierarchy and places it into a specified parent. The cloned object is a deep copy — all descendants, properties, and scripts are duplicated. The block outputs a reference to the newly created clone, which can be used by subsequent blocks to modify it.

This is one of the most commonly used blocks in VisualSource for dynamic object creation — spawning enemies, duplicating tools, creating visual effects from templates, and more.

---

## Block Metadata

| Field | Value |
|---|---|
| **Internal Type Name** | `CloneObject` |
| **Visual Name** | Clone Object |
| **Description** | Clones an object. |
| **Context** | All Scripts |
| **Flag** | `Auto Execute` |
| **IsEvent** | `false` |
| **BumpEnvironment** | `false` |
| **AutoExecuteChildren** | `true` |
| **ServerLocalSwitch** | `false` |
| **Preview Display** | `!Object`, `, parent to `, `!Parent` |
| **Alternate Names** | *(none)* |

---

## Inputs

| Name | Type | Description | Accepted Values |
|---|---|---|---|
| `Object` | `Object` | The instance to clone. Can be any `Instance` in the game hierarchy. | Any Instance reference — variable (`value_type 1`) or path (`value_type 2`) |
| `Parent` | `Object` | Where to place the clone. Accepts `Instance` or `nil`. If `nil`, the clone is parented to `nil` (unparented — it exists but is not in the hierarchy). | `Instance`, `nil` — variable, path, or literal `nil` |

> **`Parent` Allowed Types:** `{"Instance", "nil"}` — explicitly allows `nil` as a valid value, unlike most Object inputs.

---

## Outputs

| Name | Type Hint | Description |
|---|---|---|
| `NewObject` | `Instance` | A reference to the newly created clone. Use this to modify the clone with `SetObjectProperty`, move it, destroy it, or pass it to other blocks. |

---

## Internal Behavior

From the decompiled source (`CloneObject.lua`):

```lua
-- Module definition
local module = {
    AutoExecuteChildren = true,
    BumpEnvironment = false,
    IsEvent = false,
    ServerLocalSwitch = false,
    VisualName = "Clone Object",
    Description = "Clones an object.",
    Inputs = {
        Object = { VariableType = "Object", ListOrder = 1 },
        Parent = { VariableType = "Object", ListOrder = 2, AllowedTypes = {"Instance", "nil"} },
    },
    Outputs = {
        NewObject = { ListOrder = 1, TypeHints = {"Instance"} },
    },
}

function module.ServerExecute(blockData, env, executeChildren, inputs, errorHandler)
    local Object = inputs.Object

    -- Attempt to clone
    local clone = Object:Clone()

    -- Write clone reference to output variable
    Util.writeVariable(blockData.Outputs.NewObject, clone, env)

    -- On failure: print error (e.g. non-clonable instance)
    -- Util.printError(script, `Unable to create an Instance of type "{Object.ClassName}"`, ...)
end

module.LocalExecute = module.ServerExecute  -- Same logic client-side
```

**Key behaviors:**
- Calls `:Clone()` on the input object — identical to Luau's `Instance:Clone()`
- If `Parent` is not `nil`, the clone is automatically parented after creation
- If the object cannot be cloned (e.g. certain locked services), an error is printed to the VS output and execution continues
- The clone is written into the `NewObject` output variable so downstream blocks can reference it

---

## Luau Equivalent

```lua
-- Basic clone
local clone = someInstance:Clone()
clone.Parent = game.Workspace

-- With nil parent (hidden from hierarchy)
local hiddenClone = someInstance:Clone()
-- hiddenClone.Parent remains nil
```

In VisualSource, this becomes:

```
Block Type CloneObject Name Clone Object1 VisualPosition 0,0
  ChildBlocks <next_block>
  ElseChildBlock nil
  Inputs
    Object 2 game.Workspace.TemplatePart
    Parent 2 game.Workspace
  Outputs
    NewObject cloned_part
```

---

## VS Script Format

### Syntax Reference

```
Block Type CloneObject Name <UniqueName> VisualPosition <x>,<y> ChildBlocks <children...> ElseChildBlock nil Inputs Object <vtype> <value> Parent <vtype> <value> Outputs NewObject <varname>
```

### Field-by-field Breakdown

| Field | Example | Notes |
|---|---|---|
| `Type` | `CloneObject` | The internal block type — must be exact |
| `Name` | `Clone Object1` | Unique name within the script |
| `VisualPosition` | `-0.36B,0` | Hex-encoded X,Y canvas position |
| `ChildBlocks` | `Move Clone1` | Block(s) to run after this block completes |
| `ElseChildBlock` | `nil` | Always `nil` for non-If blocks |
| `Inputs Object` | `Object 2 game.Workspace.Template` | The object to clone (path) |
| `Inputs Parent` | `Parent 2 game.Workspace` | Where to parent the clone |
| `Outputs NewObject` | `NewObject cloned` | Variable name for downstream use |

---

## Examples

### Example 1 — Clone a Template Part into Workspace

Clone a part named "Template" from workspace and place it back in workspace.

**What it does:**
1. Clones `game.Workspace.Template`
2. Parents the clone to `game.Workspace`
3. Prints "Cloned!" to confirm

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type CloneObject Name Clone Object1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs Object 2 game.Workspace.Template Parent 2 game.Workspace Outputs NewObject cloned_part  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 0 Cloned! Outputs
```

**Luau equivalent:**
```lua
local clone = game.Workspace.Template:Clone()
clone.Parent = game.Workspace
print("Cloned!")
```

---

### Example 2 — Clone with Reference, Then Move It

Clone a template and immediately reposition the clone using `SetObjectProperty`.

**What it does:**
1. Clones `game.Workspace.SpawnTemplate`
2. Sets the `Position` property of the clone to `(0, 10, 0)`
3. Prints the clone's name

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type CloneObject Name Clone Object1 VisualPosition -0.36B,-0.5DC ChildBlocks Set Position1 ElseChildBlock nil Inputs Object 2 game.Workspace.SpawnTemplate Parent 2 game.Workspace Outputs NewObject new_part  Block Type SetObjectProperty Name Set Position1 VisualPosition -0.36B,-0.2EE ChildBlocks Print1 ElseChildBlock nil Inputs Object 1 new_part Property 0 Position Value 0 0,A,0 Outputs  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 0 Part spawned at 0,10,0 Outputs
```

**Luau equivalent:**
```lua
local new_part = game.Workspace.SpawnTemplate:Clone()
new_part.Parent = game.Workspace
new_part.Position = Vector3.new(0, 10, 0)
print("Part spawned at 0,10,0")
```

> **Note:** `A` in hex = 10. So `0,A,0` = `Vector3.new(0, 10, 0)`.

---

### Example 3 — Clone a Tool and Give It to a Player on Join

When a player joins, clone a tool from `ServerStorage` and place it in their `Backpack`.

**What it does:**
1. `PlayerAdded` fires when a player joins, outputs `player`
2. `GetObjectProperty` reads the player's `Backpack`
3. `CloneObject` clones the sword from ServerStorage into their backpack

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.5DC ChildBlocks Get Backpack1 ElseChildBlock nil Inputs Outputs Player player  Block Type GetObjectProperty Name Get Backpack1 VisualPosition -0.36B,-0.2EE ChildBlocks Clone Sword1 ElseChildBlock nil Inputs Object 1 player Property 0 Backpack Outputs Value backpack  Block Type CloneObject Name Clone Sword1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.ServerStorage.Sword Parent 1 backpack Outputs NewObject equipped_sword
```

**Luau equivalent:**
```lua
game:GetService("Players").PlayerAdded:Connect(function(player)
    local backpack = player.Backpack
    local sword = game.ServerStorage.Sword:Clone()
    sword.Parent = backpack
end)
```

---

### Example 4 — Clone with nil Parent (Hidden Clone)

Create a clone without immediately placing it in the hierarchy. Useful for preparing an object before deciding where to put it.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type CloneObject Name Clone Object1 VisualPosition -0.36B,-0.271 ChildBlocks Set Parent1 ElseChildBlock nil Inputs Object 2 game.ServerStorage.Effect Parent 0 nil Outputs NewObject hidden_clone  Block Type SetObjectProperty Name Set Parent1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 1 hidden_clone Property 0 Parent Value 2 game.Workspace Outputs
```

**Luau equivalent:**
```lua
-- Clone without parenting first
local hidden_clone = game.ServerStorage.Effect:Clone()
-- hidden_clone.Parent = nil (already)

-- Later, parent it
hidden_clone.Parent = game.Workspace
```

> **When to use nil parent:** Prevents child scripts from running until you're ready. Parent the clone last for predictable behavior.

---

### Example 5 — Clone on Touch (Spawn Effect)

Every time a part is touched, clone a particle effect at the touch point.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PartTouched Name Part Touched1 VisualPosition -0.36B,-0.5DC ChildBlocks Clone Effect1 ElseChildBlock nil Inputs Part 2 game.Workspace.TriggerPart Outputs otherPart touching_part  Block Type CloneObject Name Clone Effect1 VisualPosition -0.36B,-0.2EE ChildBlocks Destroy After1 ElseChildBlock nil Inputs Object 2 game.ServerStorage.SparksEffect Parent 2 game.Workspace Outputs NewObject spawned_effect  Block Type DestroyObject Name Destroy After1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 1 spawned_effect Outputs
```

**Luau equivalent:**
```lua
game.Workspace.TriggerPart.Touched:Connect(function(otherPart)
    local effect = game.ServerStorage.SparksEffect:Clone()
    effect.Parent = game.Workspace
    effect:Destroy()
end)
```

---

## Common Mistakes

### ❌ Cloning from nil / destroyed object

If `Object` refers to something that no longer exists or was destroyed, the block will error:

```
-- Wrong: Template was destroyed before clone
Block Type DestroyObject ... Inputs Object 2 game.Workspace.Template ...
Block Type CloneObject ... Inputs Object 2 game.Workspace.Template ...  -- Template is gone!
```

**Fix:** Always clone from `ServerStorage` or `ReplicatedStorage` — never from `Workspace` if that object might be destroyed.

---

### ❌ Forgetting to use the `NewObject` output

If you don't assign an output variable name, you can't reference the clone later:

```
-- Wrong: no variable name for the clone
Outputs NewObject    -- empty output name!
```

**Fix:** Always give `NewObject` a variable name:
```
Outputs NewObject my_clone
```

---

### ❌ Parenting to nil and forgetting to parent later

A clone with `nil` parent is not visible or accessible in the hierarchy. If you forget to parent it, it's effectively lost:

```
Inputs Parent 0 nil   -- clone is hidden
-- ... no SetObjectProperty to set Parent later
```

**Fix:** Either set the parent directly in `CloneObject`, or use `SetObjectProperty` immediately after with `Property 0 Parent`.

---

### ❌ Using value_type 0 (literal) for an Object input

You cannot hardcode an object reference as a literal (value_type 0) — objects must come from a path (value_type 2) or variable (value_type 1):

```
-- Wrong
Object 0 game.Workspace.Part   -- value_type 0 is for strings/numbers/bools!

-- Correct
Object 2 game.Workspace.Part   -- value_type 2 = object path
Object 1 my_variable           -- value_type 1 = variable reference
```

---

## Related Blocks

| Block | Relationship |
|---|---|
| `CreateObject` | Creates a new empty instance from scratch (no template needed) |
| `DestroyObject` | Remove a clone or any instance when done |
| `SetObjectProperty` | Modify properties of the cloned object |
| `GetObjectProperty` | Read a property from the clone (e.g. its `Name`) |
| `FindFirstChild` | Find a specific child inside the cloned object |
| `MoveModelTo` | Reposition a cloned model |
| `PlayerAdded` | Common event to trigger giving cloned tools to players |
| `PartTouched` | Common event to trigger cloning effects on touch |

---

## Notes

- `CloneObject` performs a **deep clone** — all descendants are copied, including Scripts, LocalScripts, and values inside the object.
- Cloned scripts **do not run** until the clone is parented into the `DataModel` (game hierarchy). Parenting to `nil` keeps scripts dormant.
- If cloning from `ServerStorage` on the client (LocalScript), the object may not be accessible. Use `ReplicatedStorage` for client-accessible templates.
- The `AllowedTypes` for `Parent` explicitly includes `"nil"`, which means the VS editor will accept `nil` as a valid parent without warning.
