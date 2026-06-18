# Property Reference

Complete listing of every instance available in RetroStudio and all their readable/writable properties. Use these with `GetObjectProperty` and `SetObjectProperty` blocks.

---

## How to Use This Reference

```
Block Type SetObjectProperty Name Set1 VisualPosition 0,0 ChildBlocks ElseChildBlock nil
  Inputs Object 2 game.Workspace.Part Property 0 BrickColor Value 0 Bright red Outputs
```

- **`Object`** — the instance (path or variable reference)
- **`Property`** — property name exactly as listed below (case-sensitive)
- **`Value`** — the new value (type must match the property's type)

Properties marked **`(can't change)`** are read-only.

---

## Type Quick Reference

| Type | Example Value |
|---|---|
| `String` | `Hello world` |
| `Number` | `A` (hex = 10), `0.1F4` (hex = 0.5) |
| `Bool` | `true` or `false` |
| `Vector3` | `A,14,1E` → (10, 20, 30) |
| `Vector2` | `40,40` → (64, 64) |
| `UDim2` | `1,0,1,0` → full size |
| `Color3` | `FF,0,0` → red |
| `BrickColor` | `Bright red` |
| `Object` | path or variable |
| `Enum` | named string from allowed list |

---

## Instances

### Accoutrement

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `AttachmentForward` | Vector3 | |
| `AttachmentPos` | Vector3 | |
| `AttachmentRight` | Vector3 | |
| `AttachmentUp` | Vector3 | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### Animation

| Property | Type | Notes |
|---|---|---|
| `AnimationId` | String | |
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### Backpack

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### BillboardGui

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `Adornee` | Object | |
| `AlwaysOnTop` | Bool | |
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `ExtentsOffset` | Vector3 | |
| `Name` | String | |
| `Parent` | Object | |
| `Size` | UDim2 | |
| `SizeOffset` | Vector2 | |
| `StudsOffset` | Vector3 | |

---

### BindableEvent

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### BindableFunction

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### BlockMesh

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Offset` | Vector3 | |
| `Parent` | Object | |
| `Scale` | Vector3 | |
| `VertexColor` | Vector3 | |

---

### BodyAngularVelocity

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `P` | Number | |
| `Parent` | Object | |
| `angularvelocity` | Vector3 | |
| `maxTorque` | Vector3 | |

---

### BodyColors

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `HeadColor` | BrickColor | |
| `LeftArmColor` | BrickColor | |
| `LeftLegColor` | BrickColor | |
| `Name` | String | |
| `Parent` | Object | |
| `RightArmColor` | BrickColor | |
| `RightLegColor` | BrickColor | |
| `TorsoColor` | BrickColor | |

---

### BodyForce

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `force` | Vector3 | |

---

### BodyGyro

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `D` | Number | |
| `Name` | String | |
| `P` | Number | |
| `Parent` | Object | |
| `maxTorque` | Vector3 | |

---

### BodyPosition

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `D` | Number | |
| `Name` | String | |
| `P` | Number | |
| `Parent` | Object | |
| `maxForce` | Vector3 | |
| `position` | Vector3 | |

---

### BodyThrust

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `force` | Vector3 | |
| `location` | Vector3 | |

---

### BodyVelocity

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `P` | Number | |
| `Parent` | Object | |
| `maxForce` | Vector3 | |
| `velocity` | Vector3 | |

---

### BoolValue

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | Bool | |

---

### BrickColorValue

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | BrickColor | |

---

### CFrameValue

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### CharacterMesh

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `BaseTextureId` | Number | |
| `BodyPart` | Enum | `Head \| Torso \| LeftArm \| RightArm \| LeftLeg \| RightLeg` |
| `ClassName` | String | can't change |
| `MeshId` | Number | |
| `Name` | String | |
| `OverlayTextureId` | Number | |
| `Parent` | Object | |

---

### ClickDetector

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `MaxActivationDistance` | Number | |
| `Name` | String | |
| `Parent` | Object | |

---

### Color3Value

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | Color3 | |

---

### Configuration

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### CornerWedgePart

| Property | Type | Notes |
|---|---|---|
| `Anchored` | Bool | |
| `Archivable` | Bool | |
| `BackSurface` | Enum | `Smooth \| Glue \| Weld \| Studs \| Inlet \| Universal \| Hinge \| Motor \| SteppingMotor \| SmoothNoOutlines` |
| `BottomSurface` | Enum | same options |
| `BrickColor` | BrickColor | |
| `CanCollide` | Bool | |
| `ClassName` | String | can't change |
| `FrontSurface` | Enum | same options |
| `LeftSurface` | Enum | same options |
| `Locked` | Bool | |
| `Material` | Enum | `Brick \| Cobblestone \| Concrete \| CorrodedMetal \| DiamondPlate \| Fabric \| Foil \| Granite \| Grass \| Ice \| Marble \| Metal \| Neon \| Pebble \| Plastic \| Sand \| Slate \| Wood \| WoodPlanks` |
| `Name` | String | |
| `Orientation` | Vector3 | |
| `Parent` | Object | |
| `Position` | Vector3 | |
| `Reflectance` | Number | 0–1 |
| `RightSurface` | Enum | same options |
| `RotVelocity` | Vector3 | |
| `Size` | Vector3 | |
| `TopSurface` | Enum | same options |
| `Transparency` | Number | 0–1 |
| `Velocity` | Vector3 | |

---

### CylinderMesh

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Offset` | Vector3 | |
| `Parent` | Object | |
| `Scale` | Vector3 | |
| `VertexColor` | Vector3 | |

---

### Decal

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Face` | Enum | `Top \| Bottom \| Front \| Back \| Right \| Left` |
| `Name` | String | |
| `Parent` | Object | |
| `Texture` | String | asset URL |
| `Transparency` | Number | 0–1 |
| `ZIndex` | Number | |

---

### Dialog

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `ConversationDistance` | Number | |
| `GoodbyeDialog` | String | |
| `InUse` | Bool | |
| `InitialPrompt` | String | |
| `Name` | String | |
| `Parent` | Object | |
| `Purpose` | Enum | `Quest \| Shop \| Help` |
| `Tone` | Enum | `Neutral \| Friendly \| Enemy` |

---

### DialogChoice

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `GoodbyeDialog` | String | |
| `Name` | String | |
| `Parent` | Object | |
| `ResponseDialog` | String | |
| `UserDialog` | String | |

---

### Fire

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color` | Color3 | primary flame color |
| `Enabled` | Bool | |
| `Heat` | Number | |
| `Name` | String | |
| `Parent` | Object | |
| `SecondaryColor` | Color3 | tip color |
| `Size` | Number | |

---

### Flag

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `CanBeDropped` | Bool | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `GripForward` | Vector3 | |
| `GripPos` | Vector3 | |
| `GripRight` | Vector3 | |
| `GripUp` | Vector3 | |
| `Name` | String | |
| `Parent` | Object | |
| `RequiresHandle` | Bool | |
| `TeamColor` | BrickColor | |
| `TextureId` | String | |
| `ToolTip` | String | |

---

### FlagStand

Inherits all BasePart properties (see **Part**) plus:

| Property | Type | Notes |
|---|---|---|
| `Shape` | Enum | `Ball \| Block \| Cylinder` |
| `TeamColor` | BrickColor | |

---

### FloorWire

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `CycleOffset` | Number | |
| `From` | Object | |
| `Name` | String | |
| `Parent` | Object | |
| `StudsBetweenTextures` | Number | |
| `Texture` | String | |
| `TextureSize` | Vector2 | |
| `To` | Object | |
| `Transparency` | Number | |
| `Velocity` | Number | |
| `Visible` | Bool | |
| `WireRadius` | Number | |

---

### Folder

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### ForceField

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### Frame

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `AnchorPoint` | Vector2 | |
| `Archivable` | Bool | |
| `BackgroundColor3` | Color3 | |
| `BackgroundTransparency` | Number | 0–1 |
| `BorderColor3` | Color3 | |
| `BorderSizePixel` | Number | |
| `ClassName` | String | can't change |
| `ClipsDescendants` | Bool | |
| `Draggable` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Position` | UDim2 | |
| `Rotation` | Number | degrees |
| `Size` | UDim2 | |
| `SizeConstraint` | Enum | `RelativeXY \| RelativeXX \| RelativeYY` |
| `Style` | Enum | `Custom \| ChatBlue \| RobloxSquare \| RobloxRound \| ChatGreen \| ChatRed \| CornerButton` |
| `Visible` | Bool | |
| `ZIndex` | Number | |

---

### Handles

| Property | Type | Notes |
|---|---|---|
| `Adornee` | Object | |
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Faces` | String | |
| `Name` | String | |
| `Parent` | Object | |
| `Style` | Enum | `Resize \| Movement` |
| `Transparency` | Number | |
| `Visible` | Bool | |

---

### Hat

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `AttachmentForward` | Vector3 | |
| `AttachmentPos` | Vector3 | |
| `AttachmentRight` | Vector3 | |
| `AttachmentUp` | Vector3 | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### Hint

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Text` | String | shown in top bar |

---

### Humanoid

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `AutoRotate` | Bool | |
| `ClassName` | String | can't change |
| `Health` | Number | current HP |
| `Jump` | Bool | trigger a jump |
| `JumpPower` | Number | |
| `LeftLeg` | Object | |
| `MaxHealth` | Number | |
| `Name` | String | |
| `Parent` | Object | |
| `PlatformStand` | Bool | |
| `RightLeg` | Object | |
| `Sit` | Bool | |
| `TargetPoint` | Vector3 | |
| `WalkSpeed` | Number | studs/sec, default 16 |
| `WalkToPart` | Object | |
| `WalkToPoint` | Vector3 | |

---

### ImageButton

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `AnchorPoint` | Vector2 | |
| `Archivable` | Bool | |
| `AutoButtonColor` | Bool | |
| `BackgroundColor3` | Color3 | |
| `BackgroundTransparency` | Number | |
| `BorderColor3` | Color3 | |
| `BorderSizePixel` | Number | |
| `ClassName` | String | can't change |
| `ClipsDescendants` | Bool | |
| `Draggable` | Bool | |
| `Image` | String | asset URL |
| `ImageColor3` | Color3 | |
| `ImageRectOffset` | Vector2 | |
| `ImageRectSize` | Vector2 | |
| `ImageTransparency` | Number | |
| `Modal` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Position` | UDim2 | |
| `Rotation` | Number | |
| `Selected` | Bool | |
| `Size` | UDim2 | |
| `SizeConstraint` | Enum | `RelativeXY \| RelativeXX \| RelativeYY` |
| `Style` | Enum | `Custom \| RobloxButtonDefault \| RobloxButton \| RobloxRoundButton \| RobloxRoundDefaultButton \| RobloxRoundDropdownButton` |
| `Visible` | Bool | |
| `ZIndex` | Number | |

---

### ImageLabel

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `AnchorPoint` | Vector2 | |
| `Archivable` | Bool | |
| `BackgroundColor3` | Color3 | |
| `BackgroundTransparency` | Number | |
| `BorderColor3` | Color3 | |
| `BorderSizePixel` | Number | |
| `ClassName` | String | can't change |
| `ClipsDescendants` | Bool | |
| `Draggable` | Bool | |
| `Image` | String | asset URL |
| `ImageColor3` | Color3 | |
| `ImageRectOffset` | Vector2 | |
| `ImageRectSize` | Vector2 | |
| `ImageTransparency` | Number | |
| `Name` | String | |
| `Parent` | Object | |
| `Position` | UDim2 | |
| `Rotation` | Number | |
| `Size` | UDim2 | |
| `SizeConstraint` | Enum | `RelativeXY \| RelativeXX \| RelativeYY` |
| `Visible` | Bool | |
| `ZIndex` | Number | |

---

### IntValue

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | Number | integer only |

---

### LocalScript

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Disabled` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `UseLocalVariables` | Bool | |

---

### ManualWeld

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Part0` | Object | |
| `Part1` | Object | |

---

### Message

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Text` | String | shown in chat area |

---

### Model

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `PrimaryPart` | Object | |

---

### ModuleScript

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `UseLocalVariables` | Bool | |

---

### Motor

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `CurrentAngle` | Number | |
| `DesiredAngle` | Number | |
| `Enabled` | Bool | |
| `MaxVelocity` | Number | |
| `Name` | String | |
| `Parent` | Object | |
| `Part0` | Object | |
| `Part1` | Object | |

---

### Motor6D

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `CurrentAngle` | Number | |
| `DesiredAngle` | Number | |
| `Enabled` | Bool | |
| `MaxVelocity` | Number | |
| `Name` | String | |
| `Parent` | Object | |
| `Part0` | Object | |
| `Part1` | Object | |

---

### NumberValue

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | Number | |

---

### ObjectValue

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | Object | |

---

### Pants

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Name` | String | |
| `PantsTemplate` | String | asset URL |
| `Parent` | Object | |

---

### Part

The most common instance. All BasePart-like instances (Seat, SpawnLocation, WedgePart, etc.) share these properties.

| Property | Type | Notes |
|---|---|---|
| `Anchored` | Bool | locks in place, ignores physics |
| `Archivable` | Bool | |
| `BackSurface` | Enum | `Smooth \| Glue \| Weld \| Studs \| Inlet \| Universal \| Hinge \| Motor \| SteppingMotor \| SmoothNoOutlines` |
| `BackSurfaceInput` | Enum | `NoInput \| LeftTread \| RightTread \| Constant` |
| `BottomSurface` | Enum | same surface options |
| `BottomSurfaceInput` | Enum | same input options |
| `BrickColor` | BrickColor | color name |
| `CanCollide` | Bool | enables/disables collision |
| `ClassName` | String | can't change |
| `FormFactor` | Enum | `Symmetric \| Brick \| Plate \| Custom` |
| `FrontSurface` | Enum | same surface options |
| `FrontSurfaceInput` | Enum | same input options |
| `LeftSurface` | Enum | same surface options |
| `LeftSurfaceInput` | Enum | same input options |
| `Locked` | Bool | locks selection in editor |
| `Material` | Enum | `Brick \| Cobblestone \| Concrete \| CorrodedMetal \| DiamondPlate \| Fabric \| Foil \| Granite \| Grass \| Ice \| Marble \| Metal \| Neon \| Pebble \| Plastic \| Sand \| Slate \| Wood \| WoodPlanks` |
| `Name` | String | |
| `Orientation` | Vector3 | rotation in degrees (X, Y, Z) |
| `Parent` | Object | |
| `Position` | Vector3 | world position |
| `Reflectance` | Number | 0–1 |
| `RightSurface` | Enum | same surface options |
| `RightSurfaceInput` | Enum | same input options |
| `RotVelocity` | Vector3 | angular velocity |
| `Shape` | Enum | `Ball \| Block \| Cylinder` |
| `Size` | Vector3 | width, height, depth in studs |
| `TopSurface` | Enum | same surface options |
| `TopSurfaceInput` | Enum | same input options |
| `Transparency` | Number | 0 = opaque, 1 = invisible |
| `Velocity` | Vector3 | linear velocity |

---

### ParticleEmitter

| Property | Type | Notes |
|---|---|---|
| `Acceleration` | Vector3 | |
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color` | Color3 | |
| `Enabled` | Bool | |
| `Lifetime` | Vector2 | min,max seconds |
| `LightEmission` | Number | 0–1 |
| `Name` | String | |
| `Parent` | Object | |
| `Rate` | Number | particles/sec |
| `RotSpeed` | Vector2 | min,max deg/sec |
| `Rotation` | Vector2 | min,max start rotation |
| `Size` | Number | |
| `Speed` | Vector2 | min,max |
| `SpreadAngle` | Vector2 | |
| `Texture` | String | asset URL |
| `Transparency` | Number | |
| `ZOffset` | Number | |

---

### PointLight

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `Brightness` | Number | |
| `ClassName` | String | can't change |
| `Color` | Color3 | |
| `Enabled` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Range` | Number | studs |
| `Shadows` | Bool | |

---

### RemoteEvent

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### RemoteFunction

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### RocketPropulsion

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `CartoonFactor` | Number | |
| `ClassName` | String | can't change |
| `MaxSpeed` | Number | |
| `MaxThrust` | Number | |
| `MaxTorque` | Vector3 | |
| `Name` | String | |
| `Parent` | Object | |
| `Target` | Object | |
| `TargetOffset` | Vector3 | |
| `TargetRadius` | Number | |
| `ThrustD` | Number | |
| `ThrustP` | Number | |
| `TurnD` | Number | |
| `TurnP` | Number | |

---

### ScreenGui

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `ResetOnSpawn` | Bool | |

---

### Script

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Disabled` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `UseLocalVariables` | Bool | |

---

### ScrollingFrame

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `AnchorPoint` | Vector2 | |
| `Archivable` | Bool | |
| `BackgroundColor3` | Color3 | |
| `BackgroundTransparency` | Number | |
| `BorderColor3` | Color3 | |
| `BorderSizePixel` | Number | |
| `BottomImage` | String | |
| `CanvasPosition` | Vector2 | |
| `CanvasSize` | UDim2 | |
| `ClassName` | String | can't change |
| `ClipsDescendants` | Bool | |
| `Draggable` | Bool | |
| `MidImage` | String | |
| `Name` | String | |
| `Parent` | Object | |
| `Position` | UDim2 | |
| `Rotation` | Number | |
| `ScrollBarThickness` | Number | |
| `ScrollingEnabled` | Bool | |
| `Size` | UDim2 | |
| `SizeConstraint` | Enum | `RelativeXY \| RelativeXX \| RelativeYY` |
| `TopImage` | String | |
| `Visible` | Bool | |
| `ZIndex` | Number | |

---

### Seat

Inherits all Part properties plus:

| Property | Type | Notes |
|---|---|---|
| `Disabled` | Bool | prevents players from sitting |

---

### SelectionBox

| Property | Type | Notes |
|---|---|---|
| `Adornee` | Object | |
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `LineThickness` | Number | |
| `Name` | String | |
| `Parent` | Object | |
| `SurfaceColor3` | Color3 | |
| `SurfaceTransparency` | Number | |
| `Transparency` | Number | |
| `Visible` | Bool | |

---

### SelectionPartLasso

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Humanoid` | Object | |
| `Name` | String | |
| `Parent` | Object | |
| `Part` | Object | |
| `Transparency` | Number | |
| `Visible` | Bool | |

---

### SelectionPointLasso

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Humanoid` | Object | |
| `Name` | String | |
| `Parent` | Object | |
| `Point` | Vector3 | |
| `Transparency` | Number | |
| `Visible` | Bool | |

---

### SelectionSphere

| Property | Type | Notes |
|---|---|---|
| `Adornee` | Object | |
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Name` | String | |
| `Parent` | Object | |
| `SurfaceColor3` | Color3 | |
| `SurfaceTransparency` | Number | |
| `Transparency` | Number | |
| `Visible` | Bool | |

---

### Shirt

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Name` | String | |
| `Parent` | Object | |
| `ShirtTemplate` | String | asset URL |

---

### ShirtGraphic

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Graphic` | String | asset URL |
| `Name` | String | |
| `Parent` | Object | |

---

### Skin

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `SkinColor` | BrickColor | |

---

### Sky

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `CelestialBodiesShown` | Bool | |
| `ClassName` | String | can't change |
| `MoonAngularSize` | Number | |
| `MoonTextureId` | String | |
| `Name` | String | |
| `Parent` | Object | |
| `SkyboxBk` | String | back face asset URL |
| `SkyboxDn` | String | down face |
| `SkyboxFt` | String | front face |
| `SkyboxLf` | String | left face |
| `SkyboxRt` | String | right face |
| `SkyboxUp` | String | up face |
| `StarCount` | Number | |
| `SunAngularSize` | Number | |
| `SunTextureId` | String | |

---

### Smoke

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color` | Color3 | |
| `Enabled` | Bool | |
| `Name` | String | |
| `Opacity` | Number | 0–1 |
| `Parent` | Object | |
| `RiseVelocity` | Number | |
| `Size` | Number | |

---

### Sound

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Looped` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Pitch` | Number | 1 = normal pitch |
| `PlayOnRemove` | Bool | |
| `Playing` | Bool | set true to play |
| `SoundId` | String | asset URL |
| `TimePosition` | Number | playback position in seconds |
| `Volume` | Number | 0–1 |

---

### Sparkles

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `SparkleColor` | Color3 | |

---

### SpawnLocation

Inherits all Part properties plus:

| Property | Type | Notes |
|---|---|---|
| `AllowTeamChangeOnTouch` | Bool | |
| `Duration` | Number | forcefield duration on spawn |
| `Neutral` | Bool | allows any team |
| `TeamColor` | BrickColor | restricts to this team's color |

---

### SpecialMesh

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `MeshId` | String | asset URL |
| `MeshType` | Enum | `Head \| Torso \| Wedge \| Sphere \| Cylinder \| FileMesh \| Brick` |
| `Name` | String | |
| `Offset` | Vector3 | |
| `Parent` | Object | |
| `Scale` | Vector3 | |
| `TextureId` | String | asset URL |
| `VertexColor` | Vector3 | |

---

### SpotLight

| Property | Type | Notes |
|---|---|---|
| `Angle` | Number | cone angle in degrees (0–180) |
| `Archivable` | Bool | |
| `Brightness` | Number | |
| `ClassName` | String | can't change |
| `Color` | Color3 | |
| `Enabled` | Bool | |
| `Face` | Enum | `Top \| Bottom \| Front \| Back \| Right \| Left` |
| `Name` | String | |
| `Parent` | Object | |
| `Range` | Number | studs |
| `Shadows` | Bool | |

---

### StarterGear

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |

---

### StringValue

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | String | |

---

### SurfaceGui

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Adornee` | Object | |
| `AlwaysOnTop` | Bool | |
| `Archivable` | Bool | |
| `CanvasSize` | Vector2 | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `Face` | Enum | `Top \| Bottom \| Front \| Back \| Right \| Left` |
| `Name` | String | |
| `Parent` | Object | |

---

### SurfaceLight

| Property | Type | Notes |
|---|---|---|
| `Angle` | Number | degrees |
| `Archivable` | Bool | |
| `Brightness` | Number | |
| `ClassName` | String | can't change |
| `Color` | Color3 | |
| `Enabled` | Bool | |
| `Face` | Enum | `Top \| Bottom \| Front \| Back \| Right \| Left` |
| `Name` | String | |
| `Parent` | Object | |
| `Range` | Number | studs |
| `Shadows` | Bool | |

---

### Team

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `AutoAssignable` | Bool | auto-assigns new players |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `TeamColor` | BrickColor | unique color per team |

---

### TextBox

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `AnchorPoint` | Vector2 | |
| `Archivable` | Bool | |
| `BackgroundColor3` | Color3 | |
| `BackgroundTransparency` | Number | |
| `BorderColor3` | Color3 | |
| `BorderSizePixel` | Number | |
| `ClassName` | String | can't change |
| `ClearTextOnFocus` | Bool | |
| `ClipsDescendants` | Bool | |
| `Draggable` | Bool | |
| `Font` | Enum | `Legacy \| Arial \| ArialBold \| SourceSans \| SourceSansBold` |
| `FontSize` | Enum | `Size8 \| Size9 \| Size10 \| Size11 \| Size12 \| Size14 \| Size18 \| Size24 \| Size28 \| Size32 \| Size36 \| Size42 \| Size48` |
| `MultiLine` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Position` | UDim2 | |
| `Rotation` | Number | |
| `Size` | UDim2 | |
| `SizeConstraint` | Enum | `RelativeXY \| RelativeXX \| RelativeYY` |
| `Text` | String | |
| `TextColor3` | Color3 | |
| `TextScaled` | Bool | |
| `TextStrokeColor3` | Color3 | |
| `TextStrokeTransparency` | Number | |
| `TextTransparency` | Number | |
| `TextWrapped` | Bool | |
| `TextXAlignment` | Enum | `Left \| Center \| Right` |
| `TextYAlignment` | Enum | `Top \| Center \| Bottom` |
| `Visible` | Bool | |
| `ZIndex` | Number | |

---

### TextButton

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `AnchorPoint` | Vector2 | |
| `Archivable` | Bool | |
| `AutoButtonColor` | Bool | |
| `BackgroundColor3` | Color3 | |
| `BackgroundTransparency` | Number | |
| `BorderColor3` | Color3 | |
| `BorderSizePixel` | Number | |
| `ClassName` | String | can't change |
| `ClipsDescendants` | Bool | |
| `Draggable` | Bool | |
| `Font` | Enum | `Legacy \| Arial \| ArialBold \| SourceSans \| SourceSansBold` |
| `FontSize` | Enum | `Size8 \| Size9 \| ... \| Size48` |
| `Modal` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Position` | UDim2 | |
| `Rotation` | Number | |
| `Selected` | Bool | |
| `Size` | UDim2 | |
| `SizeConstraint` | Enum | `RelativeXY \| RelativeXX \| RelativeYY` |
| `Style` | Enum | `Custom \| RobloxButtonDefault \| RobloxButton \| RobloxRoundButton \| RobloxRoundDefaultButton \| RobloxRoundDropdownButton` |
| `Text` | String | |
| `TextColor3` | Color3 | |
| `TextScaled` | Bool | |
| `TextStrokeColor3` | Color3 | |
| `TextStrokeTransparency` | Number | |
| `TextTransparency` | Number | |
| `TextWrapped` | Bool | |
| `TextXAlignment` | Enum | `Left \| Center \| Right` |
| `TextYAlignment` | Enum | `Top \| Center \| Bottom` |
| `Visible` | Bool | |
| `ZIndex` | Number | |

---

### TextLabel

| Property | Type | Notes |
|---|---|---|
| `AbsolutePosition` | String | can't change |
| `AbsoluteSize` | Vector2 | can't change |
| `Active` | Bool | |
| `AnchorPoint` | Vector2 | |
| `Archivable` | Bool | |
| `BackgroundColor3` | Color3 | |
| `BackgroundTransparency` | Number | |
| `BorderColor3` | Color3 | |
| `BorderSizePixel` | Number | |
| `ClassName` | String | can't change |
| `ClipsDescendants` | Bool | |
| `Draggable` | Bool | |
| `Font` | Enum | `Legacy \| Arial \| ArialBold \| SourceSans \| SourceSansBold` |
| `FontSize` | Enum | `Size8 \| Size9 \| ... \| Size48` |
| `Name` | String | |
| `Parent` | Object | |
| `Position` | UDim2 | |
| `Rotation` | Number | |
| `Size` | UDim2 | |
| `SizeConstraint` | Enum | `RelativeXY \| RelativeXX \| RelativeYY` |
| `Text` | String | |
| `TextColor3` | Color3 | |
| `TextScaled` | Bool | |
| `TextStrokeColor3` | Color3 | |
| `TextStrokeTransparency` | Number | |
| `TextTransparency` | Number | |
| `TextWrapped` | Bool | |
| `TextXAlignment` | Enum | `Left \| Center \| Right` |
| `TextYAlignment` | Enum | `Top \| Center \| Bottom` |
| `Visible` | Bool | |
| `ZIndex` | Number | |

---

### Texture

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Color3` | Color3 | |
| `Face` | Enum | `Top \| Bottom \| Front \| Back \| Right \| Left` |
| `Name` | String | |
| `OffsetStudsU` | Number | |
| `OffsetStudsV` | Number | |
| `Parent` | Object | |
| `StudsPerTileU` | Number | |
| `StudsPerTileV` | Number | |
| `Texture` | String | asset URL |
| `Transparency` | Number | |
| `ZIndex` | Number | |

---

### Tool

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `CanBeDropped` | Bool | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `GripForward` | Vector3 | |
| `GripPos` | Vector3 | hold position offset |
| `GripRight` | Vector3 | |
| `GripRotation` | Vector3 | |
| `GripUp` | Vector3 | |
| `Name` | String | |
| `Parent` | Object | |
| `RequiresHandle` | Bool | |
| `TextureId` | String | toolbar icon |
| `ToolTip` | String | hover text |

---

### TrussPart

Inherits all Part properties plus:

| Property | Type | Notes |
|---|---|---|
| `Style` | Enum | `Custom \| ChatBlue \| RobloxSquare \| RobloxRound \| ChatGreen \| ChatRed \| CornerButton` |

> Note: TrussPart has no `Shape` or `FormFactor` property.

---

### Vector3Value

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Name` | String | |
| `Parent` | Object | |
| `Value` | Vector3 | |

---

### VehicleSeat

Inherits most Part properties plus:

| Property | Type | Notes |
|---|---|---|
| `Disabled` | Bool | |
| `HeadsUpDisplay` | Bool | show speedometer HUD |
| `MaxSpeed` | Number | studs/sec |
| `Steer` | Number | read-only steer input |
| `Throttle` | Number | read-only throttle input |
| `Torque` | Number | engine torque |
| `TurnSpeed` | Number | |

> Note: VehicleSeat has no `Shape` or `FormFactor`.

---

### WedgePart

Inherits all Part properties. No additional properties.

---

### Weld

| Property | Type | Notes |
|---|---|---|
| `Archivable` | Bool | |
| `ClassName` | String | can't change |
| `Enabled` | Bool | |
| `Name` | String | |
| `Parent` | Object | |
| `Part0` | Object | first part |
| `Part1` | Object | second part |

---

## Common Property Patterns

### Changing a Part's appearance

```
-- BrickColor
Block Type SetObjectProperty ... Inputs Object 2 game.Workspace.Part Property 0 BrickColor Value 0 Bright red Outputs

-- Transparency (0.5 = half transparent, hex 0.1F4)
Block Type SetObjectProperty ... Inputs Object 2 game.Workspace.Part Property 0 Transparency Value 0 0.1F4 Outputs

-- Material
Block Type SetObjectProperty ... Inputs Object 2 game.Workspace.Part Property 0 Material Value 0 Neon Outputs
```

### Physics control

```
-- Anchor (freeze in place)
Block Type SetObjectProperty ... Inputs Object 2 game.Workspace.Part Property 0 Anchored Value 0 true Outputs

-- Disable collision
Block Type SetObjectProperty ... Inputs Object 2 game.Workspace.Part Property 0 CanCollide Value 0 false Outputs
```

### Humanoid stats

```
-- Set WalkSpeed (hex 1E = 30)
Block Type SetObjectProperty ... Inputs Object 1 humanoid Property 0 WalkSpeed Value 0 1E Outputs

-- Set Health to max
Block Type GetObjectProperty ... Inputs Object 1 humanoid Property 0 MaxHealth Outputs Value maxhp
Block Type SetObjectProperty ... Inputs Object 1 humanoid Property 0 Health Value 1 maxhp Outputs
```

### GUI

```
-- Show/hide
Block Type SetObjectProperty ... Inputs Object 2 game.StarterGui.ScreenGui.Frame Property 0 Visible Value 0 true Outputs

-- Change label text
Block Type SetObjectProperty ... Inputs Object 2 game.StarterGui.ScreenGui.TextLabel Property 0 Text Value 0 Hello! Outputs
```
