# `PlayerAdded`

> **Category:** Events  
> **Visual Name:** Player Added  
> **Context:** All Scripts  
> **Flags:** `Event`

---

## Overview

`PlayerAdded` is one of the most fundamental blocks in VisualSource. It fires each time a **new player joins the game**, and immediately runs all connected child blocks with the joining player as an output. It is always a **root block** — it sits at the top of a chain and waits indefinitely, firing every time someone joins.

A critical detail: this block also **retroactively fires for players already in the game** when the script first starts. This means you don't need separate logic to handle players who joined before the script loaded.

---

## Block Metadata

| Field | Value |
|---|---|
| **Internal Type Name** | `PlayerAdded` |
| **Visual Name** | Player Added |
| **Description** | Runs connected blocks when a player joins the game. |
| **Context** | All Scripts |
| **Flag** | `Event` |
| **IsEvent** | `true` |
| **BumpEnvironment** | `true` |
| **AutoExecuteChildren** | `false` |
| **ServerLocalSwitch** | `false` |
| **Preview Display** | `Outputs to`, `!Player` |
| **Alternate Names** | `"Joined"` |

---

## Inputs

This block has **no inputs**. It listens to `Players.PlayerAdded` globally — no configuration is needed.

| Name | Type | Description |
|---|---|---|
| *(none)* | — | — |

---

## Outputs

| Name | Type Hint | Description |
|---|---|---|
| `Player` | `Player` | The `Player` instance of the player who just joined. Use this to access their `Name`, `UserId`, `Backpack`, `Character`, leaderstats, etc. |

---

## Internal Behavior

From the decompiled source (`PlayerAdded.lua`):

```lua
local module = {
    AutoExecuteChildren = false,
    BumpEnvironment = true,
    IsEvent = true,
    VisualName = "Player Added",
    Description = "Runs connected blocks when a player joins the game.",
    AlternateNames = {"Joined"},
    Inputs = {},
    Outputs = {
        Player = { ListOrder = 1, TypeHints = {"Player"} },
    },
}

local Players = game:GetService("Players")

function module.ServerExecute(blockData, env, executeChildren, inputs, errorHandler)
    -- Connect to future players joining
    Util.addEvent(env, blockData.Outputs.EventConnection,
        Players.PlayerAdded:Connect(function(player)
            local outputEnv = {}
            outputEnv[tostring(blockData.Outputs.Player)] = player
            return executeChildren(blockData.ChildBlocks, env, errorHandler, module.BumpEnvironment, outputEnv)
        end)
    )

    -- Retroactively fire for players already in the game
    for _, player in Players:GetPlayers() do
        executeChildren(blockData.ChildBlocks, env, errorHandler, module.BumpEnvironment, {
            [tostring(blockData.Outputs.Player)] = player,
        })
    end
end

module.LocalExecute = module.ServerExecute
```

**Key behaviors:**

1. **Connects to `Players.PlayerAdded`** — fires every time a new player joins from this point forward.
2. **Retroactive execution** — loops through `Players:GetPlayers()` at script start and runs child blocks for any player already in the server. This ensures you never miss players who joined before the script loaded.
3. **`BumpEnvironment = true`** — each player join creates a fresh scoped environment. The `player` variable from one join doesn't interfere with another concurrent join.
4. **Event stored via `Util.addEvent`** — the connection is tracked and can be disconnected via the `DisconnectEvent` block.

---

## Luau Equivalent

```lua
local Players = game:GetService("Players")

local function onPlayerAdded(player)
    -- your logic here
    print("Player joined:", player.Name)
end

-- Connect to future joins
Players.PlayerAdded:Connect(onPlayerAdded)

-- Handle players already in game
for _, player in Players:GetPlayers() do
    onPlayerAdded(player)
end
```

In VisualSource, this entire pattern is handled automatically by the `PlayerAdded` block.

---

## VS Script Format

### Syntax Reference

```
Block Type PlayerAdded Name <UniqueName> VisualPosition <x>,<y> ChildBlocks <children...> ElseChildBlock nil Inputs Outputs Player <varname>
```

### Field-by-field Breakdown

| Field | Example | Notes |
|---|---|---|
| `Type` | `PlayerAdded` | Internal block type |
| `Name` | `Player Added1` | Unique name within the script |
| `VisualPosition` | `-0.36B,-0.271` | Hex-encoded canvas position |
| `ChildBlocks` | `Print1 Give Sword1` | Blocks to run each time a player joins |
| `ElseChildBlock` | `nil` | Always `nil` for event blocks |
| `Inputs` | *(empty)* | No inputs — write `Inputs` with nothing after |
| `Outputs Player` | `Player player` | Variable name for the joined player |

---

## Examples

### Example 1 — Print Player Name on Join

The simplest use case: print the name of every player who joins.

**What it does:**
1. `PlayerAdded` fires when a player joins, outputs `player`
2. `GetObjectProperty` reads the `Name` property from `player`
3. `Print` outputs the name to the console

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.5DC ChildBlocks Get Name1 ElseChildBlock nil Inputs Outputs Player player  Block Type GetObjectProperty Name Get Name1 VisualPosition -0.36B,-0.2EE ChildBlocks Print1 ElseChildBlock nil Inputs Object 1 player Property 0 Name Outputs Value player_name  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 1 player_name Outputs
```

**Luau equivalent:**
```lua
game:GetService("Players").PlayerAdded:Connect(function(player)
    local player_name = player.Name
    print(player_name)
end)
```

---

### Example 2 — Create a Leaderstat on Join

Give every player a "Coins" leaderstat starting at 0 when they join.

**What it does:**
1. `PlayerAdded` fires with `player`
2. `CreateLeaderstat` creates a stat folder and adds "Coins" with value 0

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.271 ChildBlocks Create Leaderstat1 ElseChildBlock nil Inputs Outputs Player player  Block Type CreateLeaderstat Name Create Leaderstat1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Player 1 player StatName 0 Coins InitialValue 0 0 Outputs
```

**Luau equivalent:**
```lua
game:GetService("Players").PlayerAdded:Connect(function(player)
    local leaderstats = Instance.new("Folder")
    leaderstats.Name = "leaderstats"
    leaderstats.Parent = player

    local coins = Instance.new("IntValue")
    coins.Name = "Coins"
    coins.Value = 0
    coins.Parent = leaderstats
end)
```

---

### Example 3 — Clone a Tool into Backpack on Join

Give every joining player a sword from ServerStorage.

**What it does:**
1. `PlayerAdded` fires with `player`
2. `GetObjectProperty` reads `player.Backpack`
3. `CloneObject` clones the sword into the backpack

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.5DC ChildBlocks Get Backpack1 ElseChildBlock nil Inputs Outputs Player player  Block Type GetObjectProperty Name Get Backpack1 VisualPosition -0.36B,-0.2EE ChildBlocks Clone Sword1 ElseChildBlock nil Inputs Object 1 player Property 0 Backpack Outputs Value backpack  Block Type CloneObject Name Clone Sword1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.ServerStorage.Sword Parent 1 backpack Outputs NewObject sword
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

### Example 4 — Welcome Message + Coins

Print a welcome message and give 50 starting coins on join.

**What it does:**
1. `PlayerAdded` fires with `player`
2. `GetObjectProperty` reads player's `Name`
3. `Concatenate` combines "Welcome, " + name
4. `Print` shows the message
5. `CreateLeaderstat` makes a "Coins" stat
6. `AddToLeaderstat` adds 50 coins (`32` in hex = 50)

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.9C4 ChildBlocks Get Name1 ElseChildBlock nil Inputs Outputs Player player  Block Type GetObjectProperty Name Get Name1 VisualPosition -0.36B,-0.6D6 ChildBlocks Welcome Msg1 ElseChildBlock nil Inputs Object 1 player Property 0 Name Outputs Value player_name  Block Type Concatenate Name Welcome Msg1 VisualPosition -0.36B,-0.3E8 ChildBlocks Print1 ElseChildBlock nil Inputs String1 0 Welcome,  String2 1 player_name Outputs Result welcome_text  Block Type Print Name Print1 VisualPosition -0.36B,-0.0FA ChildBlocks Create Coins1 ElseChildBlock nil Inputs Text 1 welcome_text Outputs  Block Type CreateLeaderstat Name Create Coins1 VisualPosition -0.36B,0.1EE ChildBlocks Add Starting Coins1 ElseChildBlock nil Inputs Player 1 player StatName 0 Coins InitialValue 0 0 Outputs  Block Type AddToLeaderstat Name Add Starting Coins1 VisualPosition -0.36B,0.4DC ChildBlocks ElseChildBlock nil Inputs Player 1 player StatName 0 Coins Amount 0 32 Outputs
```

**Luau equivalent:**
```lua
game:GetService("Players").PlayerAdded:Connect(function(player)
    local player_name = player.Name
    local welcome_text = "Welcome, " .. player_name
    print(welcome_text)

    -- leaderstats setup
    local leaderstats = Instance.new("Folder")
    leaderstats.Name = "leaderstats"
    leaderstats.Parent = player

    local coins = Instance.new("IntValue")
    coins.Name = "Coins"
    coins.Value = 0
    coins.Parent = leaderstats

    -- give starting coins
    local coinsValue = player.leaderstats.Coins
    coinsValue.Value = coinsValue.Value + 50  -- 0x32 = 50
end)
```

---

### Example 5 — Character Spawned (Nested PlayerAdded → CharacterAdded)

Run logic every time a player's character spawns (including after death).

**What it does:**
1. `PlayerAdded` fires → passes `player`
2. `CharacterAdded` is nested inside — it fires every time that player's character loads
3. `Print` confirms each spawn

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.5DC ChildBlocks Character Added1 ElseChildBlock nil Inputs Outputs Player player  Block Type CharacterAdded Name Character Added1 VisualPosition -0.36B,-0.2EE ChildBlocks Print Spawn1 ElseChildBlock nil Inputs Player 1 player Outputs Character character  Block Type Print Name Print Spawn1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 0 Character spawned! Outputs
```

**Luau equivalent:**
```lua
game:GetService("Players").PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        print("Character spawned!")
    end)
end)
```

---

## Common Mistakes

### ❌ Expecting the block to only fire for new joins

`PlayerAdded` will **also run immediately for players already in the game** when the script starts (due to the retroactive loop in the internal implementation). This is usually the desired behavior, but if you're not expecting it, it can cause duplicate logic.

**Fix:** If you need join-only behavior (not retroactive), this requires custom logic with a variable tracking which players have already been processed.

---

### ❌ Using this in a LocalScript expecting server-side effects

`PlayerAdded` works in Local Scripts, but the actions inside (like `CreateLeaderstat`) are server-only and will fail silently if called from a LocalScript.

**Fix:** Use `PlayerAdded` in a **Server Script** for anything that modifies the game state.

---

### ❌ Not naming the Player output variable

If you don't give the `Player` output a variable name, downstream blocks can't reference the player:

```
Outputs Player    -- WRONG: no variable name!
Outputs Player player    -- CORRECT
```

---

### ❌ Trying to access Character immediately on join

On join, a player's character may not exist yet — it loads asynchronously. Don't try to access `player.Character` directly inside `PlayerAdded` without checking for `CharacterAdded`.

```
-- Wrong: Character may be nil
GetObjectProperty: Object = player, Property = "Character"  -- may fail!

-- Correct: wait for character to load
PlayerAdded → CharacterAdded → (then access character)
```

---

## Related Blocks

| Block | Relationship |
|---|---|
| `PlayerRemoving` | Fires when a player leaves — use for cleanup |
| `CharacterAdded` | Fires when a player's character spawns — nest inside `PlayerAdded` |
| `GetObjectProperty` | Read any property from the `player` object (Name, UserId, etc.) |
| `CreateLeaderstat` | Most common first action on join |
| `AddToLeaderstat` | Add values to the stat created on join |
| `KickPlayer` | Remove a player — can be triggered conditionally on join |
| `CloneObject` | Give tools to players on join |
| `DisconnectEvent` | Disconnect the PlayerAdded listener when no longer needed |

---

## Notes

- **`BumpEnvironment = true`** means concurrent player joins won't share variable state. Each join has its own isolated `player` variable.
- In a **Local Script**, `PlayerAdded` still fires — but only for the local player joining (you won't receive events for other players from a LocalScript in Roblox).
- The alternate name `"Joined"` is used by the VS editor's search system — you can search for "Joined" to find this block.
- This block has no inputs by design — it is a global listener on `Players.PlayerAdded`, not scoped to any specific player.
