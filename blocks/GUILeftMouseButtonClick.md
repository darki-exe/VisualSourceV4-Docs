# `GUILeftMouseButtonClick`

> **Category:** Input  
> **Visual Name:** GUI Left Click  
> **Context:** All Scripts  
> **Flags:** `Event`

---

## Overview

`GUILeftMouseButtonClick` fires each time a player **left-clicks a specific GUI button**. It listens to the `MouseButton1Click` signal on a `GuiButton` instance, which fires when the left mouse button is pressed and released over the button (a complete click, not just press-down).

This is the primary way to add interactivity to GUI buttons in VisualSource — shop buttons, menu items, action triggers, confirmation dialogs, and more. It is almost always used inside a **Local Script** since GUI interaction is a client-side event.

---

## Block Metadata

| Field | Value |
|---|---|
| **Internal Type Name** | `GUILeftMouseButtonClick` |
| **Visual Name** | GUI Left Click |
| **Description** | Runs connected blocks when a button is left clicked. |
| **Context** | All Scripts |
| **Flag** | `Event` |
| **IsEvent** | `true` |
| **BumpEnvironment** | `true` |
| **AutoExecuteChildren** | `false` |
| **ServerLocalSwitch** | `false` |
| **Preview Display** | `Execute when mouse left clicks on`, `!GUIButton` |
| **Alternate Names** | `"MouseButton1Click"` |

---

## Inputs

| Name | Type | Allowed Types | Description |
|---|---|---|---|
| `GUIButton` | `Object` | `GuiButton` | The GUI button to listen on. Must be a `GuiButton` instance — this includes `TextButton` and `ImageButton`, which both inherit from `GuiButton`. |

> **Important:** The `AllowedTypes` field restricts this input to `{"GuiButton"}`. Connecting a `Frame`, `Label`, or other non-button GUI element will not work — `MouseButton1Click` only exists on `GuiButton` subclasses.

---

## Outputs

This block has **no outputs**. The click event carries no data — it simply signals that a click happened. If you need to know *who* clicked (in a server context), you need a different approach (e.g. `RemoteEvent` from a LocalScript).

| Name | Type Hint | Description |
|---|---|---|
| *(none)* | — | — |

---

## Internal Behavior

From the decompiled source (`GUILeftMouseButtonClick.lua`):

```lua
local module = {
    AutoExecuteChildren = false,
    BumpEnvironment = true,
    IsEvent = true,
    VisualName = "GUI Left Click",
    Description = "Runs connected blocks when a button is left clicked.",
    AlternateNames = {"MouseButton1Click"},
    PreviewDisplay = {"Execute when mouse left clicks on ", "!GUIButton"},
    Inputs = {
        GUIButton = {
            VariableType = "Object",
            ListOrder = 1,
            AllowedTypes = {"GuiButton"},
        },
    },
    Outputs = {},
}

function module.ServerExecute(blockData, env, executeChildren, inputs, errorHandler)
    Util.addEvent(env, blockData.Outputs.EventConnection,
        inputs.GUIButton.MouseButton1Click:Connect(function()
            return executeChildren(blockData.ChildBlocks, env, errorHandler, module.BumpEnvironment, nil)
        end)
    )
end

module.LocalExecute = module.ServerExecute
```

**Key behaviors:**

1. **Connects to `GuiButton.MouseButton1Click`** — this signal fires when the full left-click cycle (press + release) completes over the button.
2. **No output data** — the callback receives no arguments, so `nil` is passed as the output environment. Child blocks can't access "who clicked" from this block alone.
3. **`BumpEnvironment = true`** — each click fires in a fresh scope, so rapid clicks don't interfere with each other.
4. **Event stored via `Util.addEvent`** — tracked and disconnectable via `DisconnectEvent`.

---

## Luau Equivalent

```lua
-- In a LocalScript
local button = script.Parent  -- or any path to the GuiButton

button.MouseButton1Click:Connect(function()
    -- your logic here
    print("Button clicked!")
end)
```

In VisualSource (Local Script):

```
Block Type GUILeftMouseButtonClick Name GUI Left Click1 VisualPosition 0,0
  ChildBlocks Print1
  ElseChildBlock nil
  Inputs
    GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.Button
  Outputs
```

---

## VS Script Format

### Syntax Reference

```
Block Type GUILeftMouseButtonClick Name <UniqueName> VisualPosition <x>,<y> ChildBlocks <children...> ElseChildBlock nil Inputs GUIButton <vtype> <value> Outputs
```

### Field-by-field Breakdown

| Field | Example | Notes |
|---|---|---|
| `Type` | `GUILeftMouseButtonClick` | Internal block type — case-sensitive |
| `Name` | `GUI Left Click1` | Unique name within the script |
| `VisualPosition` | `-0.36B,0` | Hex-encoded canvas position |
| `ChildBlocks` | `Handle Click1` | Blocks that run on each click |
| `ElseChildBlock` | `nil` | Always `nil` for event blocks |
| `Inputs GUIButton` | `GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.BuyButton` | The button to listen on |
| `Outputs` | *(nothing after)* | No outputs — write `Outputs` with nothing |

---

## Examples

### Example 1 — Print a Message on Button Click

The simplest usage: print "Button clicked!" when the button is pressed.

**What it does:**
1. `GUILeftMouseButtonClick` fires when the button is clicked
2. `Print` outputs "Button clicked!" to the console

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type GUILeftMouseButtonClick Name GUI Left Click1 VisualPosition -0.36B,-0.271 ChildBlocks Print1 ElseChildBlock nil Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.MyButton Outputs  Block Type Print Name Print1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Text 0 Button clicked! Outputs
```

**Luau equivalent:**
```lua
-- LocalScript
local button = game.Players.LocalPlayer.PlayerGui.ScreenGui.MyButton
button.MouseButton1Click:Connect(function()
    print("Button clicked!")
end)
```

---

### Example 2 — Toggle a Frame Visible/Invisible

Show or hide a frame when a button is clicked using a variable to track state.

**What it does:**
1. Click fires
2. `GetObjectProperty` reads the current `Visible` property of the frame
3. `Not` inverts the boolean
4. `SetObjectProperty` writes the new visibility back

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type GUILeftMouseButtonClick Name GUI Left Click1 VisualPosition -0.36B,-0.6D6 ChildBlocks Get Visible1 ElseChildBlock nil Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.ToggleButton Outputs  Block Type GetObjectProperty Name Get Visible1 VisualPosition -0.36B,-0.3E8 ChildBlocks Invert1 ElseChildBlock nil Inputs Object 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.ContentFrame Property 0 Visible Outputs Value current_visible  Block Type Not Name Invert1 VisualPosition -0.36B,-0.0FA ChildBlocks Set Visible1 ElseChildBlock nil Inputs Bool 1 current_visible Outputs Result new_visible  Block Type SetObjectProperty Name Set Visible1 VisualPosition -0.36B,0.1EE ChildBlocks ElseChildBlock nil Inputs Object 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.ContentFrame Property 0 Visible Value 1 new_visible Outputs
```

**Luau equivalent:**
```lua
local toggleButton = game.Players.LocalPlayer.PlayerGui.ScreenGui.ToggleButton
local contentFrame = game.Players.LocalPlayer.PlayerGui.ScreenGui.ContentFrame

toggleButton.MouseButton1Click:Connect(function()
    local current_visible = contentFrame.Visible
    local new_visible = not current_visible
    contentFrame.Visible = new_visible
end)
```

---

### Example 3 — Shop Button: Buy an Item

A buy button that checks if the player has enough coins, then deducts them and gives the item. Uses a RemoteEvent to communicate the purchase to the server.

**What it does:**
1. Click fires
2. `GetLeaderstat` reads current "Coins" value
3. `GreaterThanOrEqual` checks if coins ≥ 50 (`32` hex)
4. `If` — if true: fire remote to server; if false: show "Not enough coins" message

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type GUILeftMouseButtonClick Name GUI Left Click1 VisualPosition -0.36B,-0.9C4 ChildBlocks Get Coins1 ElseChildBlock nil Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.ShopGui.BuyButton Outputs  Block Type GetLeaderstat Name Get Coins1 VisualPosition -0.36B,-0.6D6 ChildBlocks Check Coins1 ElseChildBlock nil Inputs Player 2 game.Players.LocalPlayer StatName 0 Coins Outputs Value current_coins  Block Type GreaterThanOrEqual Name Check Coins1 VisualPosition -0.36B,-0.3E8 ChildBlocks Buy Check1 ElseChildBlock nil Inputs Number1 1 current_coins Number2 0 32 Outputs Result can_buy  Block Type If Name Buy Check1 VisualPosition -0.36B,-0.0FA ChildBlocks Fire Remote1 ElseChildBlock Show Error1 Inputs Condition 1 can_buy  Block Type RemoteFireServer2 Name Fire Remote1 VisualPosition -0.36B,0.1EE ChildBlocks ElseChildBlock nil Inputs RemoteEvent 2 game.ReplicatedStorage.BuyItem Parameters 0 Sword Outputs  Block Type SetObjectProperty Name Show Error1 VisualPosition 0.36B,0.1EE ChildBlocks ElseChildBlock nil Inputs Object 2 game.Players.LocalPlayer.PlayerGui.ShopGui.ErrorLabel Property 0 Text Value 0 Not enough coins! Outputs
```

**Luau equivalent:**
```lua
local buyButton = game.Players.LocalPlayer.PlayerGui.ShopGui.BuyButton
local buyRemote = game.ReplicatedStorage.BuyItem
local errorLabel = game.Players.LocalPlayer.PlayerGui.ShopGui.ErrorLabel

buyButton.MouseButton1Click:Connect(function()
    local current_coins = game.Players.LocalPlayer.leaderstats.Coins.Value
    local can_buy = current_coins >= 50  -- 0x32 = 50

    if can_buy then
        buyRemote:FireServer("Sword")
    else
        errorLabel.Text = "Not enough coins!"
    end
end)
```

---

### Example 4 — Cooldown Button (Prevent Rapid Clicks)

Disable the button for 3 seconds after each click to prevent spam.

**What it does:**
1. Click fires
2. `SetObjectProperty` sets `Active` to `false` (disables the button)
3. `Wait` waits 3 seconds (`3` hex = 3)
4. `SetObjectProperty` re-enables the button

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type GUILeftMouseButtonClick Name GUI Left Click1 VisualPosition -0.36B,-0.6D6 ChildBlocks Do Action1 ElseChildBlock nil Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.ActionButton Outputs  Block Type SetObjectProperty Name Do Action1 VisualPosition -0.36B,-0.3E8 ChildBlocks Disable Button1 ElseChildBlock nil Inputs Object 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.ActionButton Property 0 Active Value 0 false Outputs  Block Type Wait Name Wait Cooldown1 VisualPosition -0.36B,-0.0FA ChildBlocks Re-Enable1 ElseChildBlock nil Inputs Time 0 3 Outputs  Block Type SetObjectProperty Name Re-Enable1 VisualPosition -0.36B,0.1EE ChildBlocks ElseChildBlock nil Inputs Object 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.ActionButton Property 0 Active Value 0 true Outputs
```

**Luau equivalent:**
```lua
local actionButton = game.Players.LocalPlayer.PlayerGui.ScreenGui.ActionButton

actionButton.MouseButton1Click:Connect(function()
    actionButton.Active = false
    task.wait(3)
    actionButton.Active = true
end)
```

---

### Example 5 — Multiple Buttons, One Handler Per Button

Connect separate click listeners to multiple buttons (e.g. a settings menu).

**What it does:**
Each button is a separate `GUILeftMouseButtonClick` root block that handles its own logic independently.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type GUILeftMouseButtonClick Name Music Button1 VisualPosition -0.36B,-0.5DC ChildBlocks Toggle Music1 ElseChildBlock nil Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.SettingsGui.MusicButton Outputs  Block Type SetObjectProperty Name Toggle Music1 VisualPosition -0.36B,-0.2EE ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.BackgroundMusic Property 0 Playing Value 0 false Outputs  Block Type GUILeftMouseButtonClick Name SFX Button1 VisualPosition 0.36B,-0.5DC ChildBlocks Toggle SFX1 ElseChildBlock nil Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.SettingsGui.SFXButton Outputs  Block Type Print Name Toggle SFX1 VisualPosition 0.36B,-0.2EE ChildBlocks ElseChildBlock nil Inputs Text 0 SFX toggled Outputs
```

**Luau equivalent:**
```lua
local musicButton = game.Players.LocalPlayer.PlayerGui.SettingsGui.MusicButton
local sfxButton = game.Players.LocalPlayer.PlayerGui.SettingsGui.SFXButton

musicButton.MouseButton1Click:Connect(function()
    game.Workspace.BackgroundMusic.Playing = false
end)

sfxButton.MouseButton1Click:Connect(function()
    print("SFX toggled")
end)
```

> Each `GUILeftMouseButtonClick` block is an independent root block — they all run concurrently in the same script.

---

## Common Mistakes

### ❌ Connecting to a non-GuiButton instance

`MouseButton1Click` only exists on `GuiButton` (i.e., `TextButton` and `ImageButton`). Using a `Frame`, `TextLabel`, or `ImageLabel` will cause an error because those objects don't have that signal.

```
-- Wrong: Frame doesn't have MouseButton1Click
GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.MyFrame

-- Correct: use a TextButton or ImageButton
GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.MyTextButton
```

**Fix:** In Roblox Studio, ensure the GUI element is a `TextButton` or `ImageButton`. Convert `Frame` to `TextButton` if needed.

---

### ❌ Using this in a Server Script and expecting player identity

`GUILeftMouseButtonClick` fires on the client — in a server script, you don't know which player clicked. The block has no `Player` output.

```
-- In a Server Script:
GUILeftMouseButtonClick → AddToLeaderstat  -- WHICH player?? (unknown)
```

**Fix:** Use this block in a **LocalScript**, then fire a `RemoteEvent` to the server with the player's identity, and handle the server-side logic in a `RemoteRecieveServer2` block.

---

### ❌ Forgetting `Outputs` keyword with no values

Even when there are no outputs, you must write the `Outputs` keyword:

```
-- Wrong: missing Outputs keyword
... Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.Btn
-- (no Outputs line)

-- Correct:
... Inputs GUIButton 2 game.Players.LocalPlayer.PlayerGui.ScreenGui.Btn Outputs
```

---

### ❌ Connecting to a button that doesn't exist yet

If the button is inside a `ScreenGui` that's streamed in or loaded dynamically, the path may not resolve immediately. The block will error if it can't find the button.

**Fix:** Use `WaitForChild` (via `GetObjectProperty` with appropriate wait logic) or reference GUI from `StarterGui` only in LocalScripts where the GUI is guaranteed to be loaded.

---

### ❌ Using `GUILeftMouseButtonClick` instead of `ClickDetectorInteraction` for 3D parts

`GUILeftMouseButtonClick` is for 2D screen GUI buttons only. For clicking 3D parts in the world, use `ClickDetectorInteraction` (which requires a `ClickDetector` inside the part) instead.

---

## Comparison: Click vs Mouse Down vs Mouse Up

| Block | Signal | Fires When |
|---|---|---|
| `GUILeftMouseButtonClick` | `MouseButton1Click` | Full left click (press + release over button) |
| `GUILeftMouseButtonDown` | `MouseButton1Down` | Left button pressed down (no release needed) |
| `GUILeftMouseButtonUp` | `MouseButton1Up` | Left button released (even if pressed elsewhere) |

Use `MouseButton1Click` for most button actions — it's the safest because it only fires if the user releases the mouse while still over the button (consistent with standard UI expectations).

---

## Related Blocks

| Block | Relationship |
|---|---|
| `GUILeftMouseButtonDown` | Fires on press (not full click) |
| `GUILeftMouseButtonUp` | Fires on release |
| `GUIRightMouseButtonClick` | Right-click variant |
| `GUIMouseEnter` / `GUIMouseLeave` | Hover detection on any GUI |
| `ClickDetectorInteraction` | 3D world click detection (not GUI) |
| `SetObjectProperty` | Modify the button or other GUI after click |
| `RemoteFireServer2` | Send click event to server with player identity |
| `DisconnectEvent` | Stop listening for clicks |
| `If` | Conditional logic after a click |
| `Wait` | Add cooldowns after click |

---

## Notes

- `MouseButton1Click` requires a **complete** click — press and release over the button. If the player moves the mouse off the button before releasing, the signal does not fire.
- `BumpEnvironment = true` means each click invocation is isolated — rapid clicking creates independent execution threads that don't interfere.
- The alternate name `"MouseButton1Click"` reflects the underlying Roblox API signal, making it easier to find for developers familiar with Luau.
- In mobile, a tap over the button is equivalent to a left-click.
