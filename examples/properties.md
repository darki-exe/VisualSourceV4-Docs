# Properties

Examples for reading and writing object properties using `GetObjectProperty` and `SetObjectProperty`.

---

## Set a Part's Color

Change the `BrickColor` of a part named "Part" in Workspace.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type SetObjectProperty Name Set Color1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 BrickColor Value 0 Bright red Outputs
```

---

## Set a Part's Transparency

Make a part 50% transparent. Transparency is a Number from 0 (opaque) to 1 (invisible).

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type SetObjectProperty Name Set Transparency1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 Transparency Value 0 0.1F4 Outputs
```

> `0.1F4` hex = 0 + (500 / 1000) = **0.5**

---

## Set a Part's Size

Resize a part to 10 × 5 × 10 studs.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type SetObjectProperty Name Set Size1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 Size Value 0 A,5,A Outputs
```

> `A,5,A` = Vector3(10, 5, 10)

---

## Set a Part's Position

Move a part to coordinates (0, 10, 50).

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type SetObjectProperty Name Set Position1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 Position Value 0 0,A,32 Outputs
```

> `0,A,32` = Vector3(0, 10, 50) — hex `32` = 50

---

## Make a Part Uncollidable

Disable collision on a part (CanCollide = false).

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type SetObjectProperty Name Set CanCollide1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 CanCollide Value 0 false Outputs
```

---

## Anchor a Part

Lock a part in place so physics don't move it (Anchored = true).

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type SetObjectProperty Name Anchor1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 Anchored Value 0 true Outputs
```

---

## Read a Part's Position

Get the current position of a part and store it in a variable.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type GetObjectProperty Name Get Position1 VisualPosition -0.36B,0 ChildBlocks Print1 ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 Position Outputs Value part_position  Block Type Print Name Print1 VisualPosition -0.36B,0.271 ChildBlocks ElseChildBlock nil Inputs Text 1 part_position Outputs
```

---

## Read a Player's Health

Get the `Health` of a humanoid from a player's character.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type PlayerAdded Name Player Added1 VisualPosition -0.36B,-0.5DC ChildBlocks Get Character1 ElseChildBlock nil Inputs Outputs Player player  Block Type GetObjectProperty Name Get Character1 VisualPosition -0.36B,-0.2EE ChildBlocks Get Humanoid1 ElseChildBlock nil Inputs Object 1 player Property 0 Character Outputs Value character  Block Type FindFirstChildOfClass Name Get Humanoid1 VisualPosition -0.36B,0 ChildBlocks Get Health1 ElseChildBlock nil Inputs Object 1 character ClassName 0 Humanoid Outputs Result humanoid  Block Type GetObjectProperty Name Get Health1 VisualPosition -0.36B,0.2EE ChildBlocks Print1 ElseChildBlock nil Inputs Object 1 humanoid Property 0 Health Outputs Value health  Block Type Print Name Print1 VisualPosition -0.36B,0.5DC ChildBlocks ElseChildBlock nil Inputs Text 1 health Outputs
```

---

## Tween a Property

Smoothly animate a property over time using `TweenObjectProperty`.

```
Editor CameraPosition 0,0 CameraZoom 0.1C2  Block Type TweenObjectProperty Name Tween1 VisualPosition -0.36B,0 ChildBlocks ElseChildBlock nil Inputs Object 2 game.Workspace.Part Property 0 Transparency EndValue 0 0.1F4 Duration 0 1 EasingStyle 0 Linear EasingDirection 0 Out Outputs
```

This smoothly animates `Transparency` from its current value to `0.5` over `1` second.

---

## Common Property Names

| Property | Type | Used On |
|---|---|---|
| `Name` | String | Any Instance |
| `Parent` | Object | Any Instance |
| `Transparency` | Number (0–1) | BasePart |
| `BrickColor` | BrickColor | BasePart |
| `Color` | Color3 | BasePart |
| `Anchored` | Bool | BasePart |
| `CanCollide` | Bool | BasePart |
| `Position` | Vector3 | BasePart |
| `Size` | Vector3 | BasePart |
| `Material` | Enum | BasePart |
| `Health` | Number | Humanoid |
| `MaxHealth` | Number | Humanoid |
| `WalkSpeed` | Number | Humanoid |
| `JumpPower` | Number | Humanoid |
| `Text` | String | TextLabel, TextButton |
| `Visible` | Bool | GuiObject |
| `Enabled` | Bool | Script, GUI |
