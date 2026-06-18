# ACTIONS Blocks

Action blocks perform operations on game objects, players, sounds, terrain, and services. Most are **Auto Execute** — they run inline as part of a block chain.

> **Note:** Some blocks marked *(Yields)* pause execution until the operation completes.

---

## `AbortRocketPropulsion`
**Visual Name:** Abort Rocket Propulsion
**Description:** Makes a rocket propulsion object stop following its target.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `RocketPropulsion = {` | Object |

**Outputs:** *(none)*

---

## `AddToLeaderstat`
**Visual Name:** Add to Leaderstat
**Description:** Adds to the value of a leaderstat.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `StatName = {` | String |
| `Amount = {` | Number |

**Outputs:** *(none)*

---

## `AnimationStopped`
**Visual Name:** Animation Stopped
**Description:** Runs connected blocks when an AnimationTrack stops playing. Use the Load Animation block to create an AnimationTrack.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `AnimationTrack = {` | Object |

**Outputs:** *(none)*

---

## `AssignCollisionGroup`
**Visual Name:** Assign Collision Group
**Description:** Assigns a BasePart to a specific collision group.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `BasePart = {` | Object |
| `GroupName = {` | String |

**Outputs:** *(none)*

---

## `AutowedgeCell`
**Visual Name:** Auto Wedge Cell
**Description:** Smoothen out a voxel terrain cell.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Position = {` | Vector3 |

**Outputs:** *(none)*

---

## `BanPlayer`
**Visual Name:** Ban Player
**Description:** (Yields) Bans the specified player from the game. Use the unban player block to unban a player.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:** *(none)*

---

## `BreakJoints`
**Visual Name:** Break Joints
**Description:** Removes all of a parts welds.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:** *(none)*

---

## `ChangeHumanoidState`
**Visual Name:** Change Humanoid State
**Description:** Changes a humanoids state.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |
| `State = {` | String |

**Outputs:** *(none)*

---

## `CheckIfPlayerIsBanned`
**Visual Name:** Is Player Banned
**Description:** (Yields) Returns whether the player is banned from the game.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `UserId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `CheckToolEquipped`
**Visual Name:** Check Tool Equipped
**Description:** Returns a bool based on whether or not a tool is equipped.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Tool = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `CloneObject`
**Visual Name:** Clone Object
**Description:** Clones an object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |
| `Parent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `NewObject = {` | Instance |

---

## `CollisionGroupSetCollidable`
**Visual Name:** Collision Group Set Collidable
**Description:** Changes collision status between two groups.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `GroupName1 = {` | String |
| `GroupName2 = {` | String |
| `Collidable = {` | Bool |

**Outputs:** *(none)*

---

## `ComputePath`
**Visual Name:** Compute Path
**Description:** (Yields) Uses PathfindingService to compute a path between two Vector3s.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `StartPosition = {` | Vector3 |
| `EndPosition = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `ComputedPath = {` | Table |

---

## `CreateLeaderstat`
**Visual Name:** Create Leaderstat
**Description:** Creates a leaderstat.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `StatName = {` | String |
| `InitialValue = {` | Number |

**Outputs:** *(none)*

---

## `CreateObject`
**Visual Name:** Create Object
**Description:** Creates an object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `ClassName = {` | String |
| `Parent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Object = {` | Instance |

---

## `DestroyObject`
**Visual Name:** Destroy Object
**Description:** Destroys an object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:** *(none)*

---

## `DialogChat`
**Visual Name:** Dialog Chat
**Description:** Make a part say something.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |
| `Message = {` | String |
| `Color = {` | Choice |

**Outputs:** *(none)*

---

## `EmitParticle`
**Visual Name:** Emit Particle
**Description:** Emits a certain amount of particles from a particle emitter.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `ParticleCount = {` | Number |
| `ParticleEmitter = {` | Object |

**Outputs:** *(none)*

---

## `FindFirstChild`
**Visual Name:** Find First Child
**Description:** Run the connected blocks only if the given object has a child with the given name.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |
| `ChildName = {` | String |
| `Recursive = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---

## `FindFirstChildNew`
**Visual Name:** Find First Child
**Description:** Run the connected blocks only if the given object has a child with the given name.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |
| `ChildName = {` | String |
| `Recursive = {` | Bool |
| `CanReturnNil = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---

## `FindFirstChildOfClass`
**Visual Name:** Find First Child Of Class
**Description:** Run the connected blocks only if the given object has a child with the given class, does not support super classes.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |
| `ChildClass = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---

## `FindFirstChildOfClassNew`
**Visual Name:** Find First Child Of Class
**Description:** Run the connected blocks only if the given object has a child with the given class, does not support super classes.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |
| `ChildClass = {` | String |
| `CanReturnNil = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---

## `FindFirstChildWhichIsA`
**Visual Name:** Find First Child Which Is A
**Description:** Run the connected blocks only if the given object has a child with the given super class.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |
| `ChildClass = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---

## `FindFirstChildWhichIsANew`
**Visual Name:** Find First Child Which Is A
**Description:** Run the connected blocks only if the given object has a child with the given super class.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |
| `ChildClass = {` | String |
| `CanReturnNil = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---

## `FindPartOnRay`
**Visual Name:** Find Part On Ray
**Description:** Sends out an invisible ray from a point in space with a specific direction and length, and then detects if it hits a part. If nothing is hit, the outputs will all be nil.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Origin = {` | Vector3 |
| `Direction = {` | Vector3 |
| `FilterType = {` | Choice |
| `FilterDescendantsTable = {` | Table |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Instance = {` | Instance |

---

## `FindPartsInRegion`
**Visual Name:** Find Parts in Region
**Description:** Returns a table of all parts within the given area.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CFrame = {` | CFrame |
| `Size = {` | Vector3 |
| `FilterType = {` | Choice |
| `FilterDescendantsTable = {` | Table |
| `MaxParts = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `PartsTable = {` | Table |

---

## `FireRocketPropulsion`
**Visual Name:** Fire Rocket Propulsion
**Description:** Makes a rocket propulsion object fly towards its target.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `RocketPropulsion = {` | Object |

**Outputs:** *(none)*

---

## `GetCameraPositionLocal`
**Visual Name:** Get Camera Position
**Description:** Gets the position of the camera.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Position = {` | Vector3 |

---

## `GetCell`
**Visual Name:** Get Cell
**Description:** Get what type of voxel terrain cell is at the given location.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Position = {` | Vector3 |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Material = {` | String |

---

## `GetChildren`
**Visual Name:** Get Children
**Description:** Returns a table of all of an objects children.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `ChildrenTable = {` | Table |

---

## `GetConnectedParts`
**Visual Name:** Get Connected Parts
**Description:** Returns a table of all parts connected to an object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `PartsTable = {` | Table |

---

## `GetDescendants`
**Visual Name:** Get Descendants
**Description:** Returns a table of all of an objects descendants.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `DescendantTable = {` | Table |

---

## `GetFullName`
**Visual Name:** Get Full Name
**Description:** Returns a string describing the objects's ancestry.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `FullName = {` | String |

---

## `GetHumanoidState`
**Visual Name:** Get Humanoid State
**Description:** Gets a humanoids state.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `State = {` | String |

---

## `GetJoints`
**Visual Name:** Get Joints
**Description:** Gives a list of all joints connected to a part
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Joints = {` | Table |

---

## `GetLeaderstat`
**Visual Name:** Get Leaderstat
**Description:** Gets the value of a leaderstat.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `StatName = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Value = {` | Any |

---

## `GetModelBoundingBox`
**Visual Name:** Get Model Bounding Box
**Description:** Gives the size, rotation, and position of a box containing all the parts in a model.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Model = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Position = {` | Vector3 |

---

## `GetNameFromUserIdAsync`
**Visual Name:** Get Name from User Id
**Description:** (Yields) Takes a User Id and returns a UserName
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `UserId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Username = {` | String |

---

## `GetObjectProperty`
**Visual Name:** Get Object Property
**Description:** Returns the property of an object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |
| `Property = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Value = {` | Any |

---

## `GetPartPhysicalProperties`
**Visual Name:** Get Part Physical Properties
**Description:** Gets the physical properties of a part.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | PhysicalProperties |

---

## `GetPlayerFromCharacter`
**Visual Name:** Get Player From Character
**Description:** Takes a character from workspace and returns the player object inside of the players service.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Character = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Player = {` | Player |

---

## `GetPlayersOnTeam`
**Visual Name:** Get Players On Team
**Description:** Returns a table of all players on a team.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Team = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `PlayerTable = {` | Table |

---

## `GetRandomChild`
**Visual Name:** Get Random Child
**Description:** Returns a random child of an object.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---

## `GetTouchingParts`
**Visual Name:** Get Touching Parts
**Description:** Returns a table of all parts touching an object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `PartsTable = {` | Table |

---

## `GetUserIdFromNameAsync`
**Visual Name:** Get User Id from Name
**Description:** (Yields) Takes a Username and returns a User Id
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Username = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `UserId = {` | Number |

---

## `GiveBadge`
**Visual Name:** Give Badge
**Description:** (Yields) Gives a badge to a player.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `BadgeId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `HasBadge`
**Visual Name:** Has Badge
**Description:** Returns a bool based on whether or not a player has a badge. If there is an error checking this, it will always return false.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `BadgeId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `HasBadgeFromForeignPlace`
**Visual Name:** Has Badge from Foreign Place
**Description:** Returns a bool based on whether or not a player has a badge from another place. If there is an error checking this, it will always return false.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `BadgeId = {` | Number |
| `PlaceId = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `HasGamepass`
**Visual Name:** Has Gamepass
**Description:** Returns a bool based on whether or not a player owns a gamepass
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `GamepassId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `HasGamepassFromForeignPlace`
**Visual Name:** Has Gamepass from Foreign Place
**Description:** Returns a bool based on whether or not a player owns a gamepass from a foreign place
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `GamepassId = {` | Number |
| `PlaceId = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `HumanoidMoveTo`
**Visual Name:** Humanoid Move To
**Description:** Sets the humanoid target to the specificed location. The humanoid will attempt to walk to the location. If the humanoid cannot reach it's target in 8 seconds, the MoveTo is canceled.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |
| `Target = {` | Vector3 |

**Outputs:** *(none)*

---

## `IsA`
**Visual Name:** Is A
**Description:** Returns true or false based on whether or not an object is of the given class, or a class inherited from it.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |
| `Class = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `IsAncestorOf`
**Visual Name:** Is Ancestor Of
**Description:** Returns a boolean on whether or not the given object is an ancestor of another object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Descendant = {` | Object |
| `Ancestor = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `OutputValue = {` | Bool |

---

## `IsDescendantOf`
**Visual Name:** Is Descendant Of
**Description:** Returns a boolean on whether or not the given object is a descendant of another object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Ancestor = {` | Object |
| `Descendant = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `OutputValue = {` | Bool |

---

## `IsOwner`
**Visual Name:** Is Owner
**Description:** Returns whether the player is the owner of the game, or an authorized user.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `AllowAuthorizedUsers = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `IsTouching`
**Visual Name:** Is Touching
**Description:** Returns a boolean on whether or not two provided objects are touching
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part1 = {` | Object |
| `Part2 = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `IsTouching = {` | Bool |

---

## `KickPlayer`
**Visual Name:** Kick Player
**Description:** (Yields) Kicks a player. Does not run on Retrostudio admins.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `Reason = {` | String |

**Outputs:** *(none)*

---

## `LeaderstatChanged`
**Visual Name:** Leaderstat Changed
**Description:** Fires every time a leaderstat changes.
**Context:** All Scripts
**Flags:** `Event, Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `StatName = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Value = {` | Any |

---

## `LoadAnimation`
**Visual Name:** Load Animation
**Description:** Loads an animation onto a character and returns an AnimationTrack instance that can be used with the other animation blocks. Only permitted animations can be loaded, see the animations section of the toolbox for useable animations.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |
| `Animation = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `AnimationTrack = {` | AnimationTrack |

---

## `LoadCharacter`
**Visual Name:** Load Character
**Description:** (Yields) Respawns a players character.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:** *(none)*

---

## `MakeJoints`
**Visual Name:** Make Joints
**Description:** Connects a part, or all the parts in a model, to any parts they are touching that have compatible surfaces.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:** *(none)*

---

## `MoveModelTo`
**Visual Name:** Move Model To
**Description:** Moves a model to the given position. If the model ends up inside of something, it will teleport ontop of it.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Model = {` | Object |
| `Position = {` | Vector3 |

**Outputs:** *(none)*

---

## `MutePlayer`
**Visual Name:** Mute Player
**Description:** Mutes a player
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `Mute = {` | Bool |

**Outputs:** *(none)*

---

## `PauseSound`
**Visual Name:** Pause Sound
**Description:** Pauses a sound.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Sound = {` | Object |

**Outputs:** *(none)*

---

## `PlayAnimation`
**Visual Name:** Play Animation
**Description:** Plays an AnimationTrack. Use the Load Animation block to create an AnimationTrack.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `AnimationTrack = {` | Object |
| `FadeTime = {` | Number |
| `Weight = {` | Number |
| `Speed = {` | Number |

**Outputs:** *(none)*

---

## `PlaySound`
**Visual Name:** Play Sound
**Description:** Plays a sound.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Sound = {` | Object |

**Outputs:** *(none)*

---

## `PromptDeveloperProductPurchase`
**Visual Name:** Prompt Developer Product Purchase
**Description:** Prompts a player to purchase a developer product.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `DeveloperProductId = {` | Number |

**Outputs:** *(none)*

---

## `PromptDeveloperProductPurchaseFinished`
**Visual Name:** Prompt Developer Product Purchase Finished
**Description:** Executes when a player responds to a developer product purchase prompt.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Player = {` | Player |

---

## `PromptGamepassPurchase`
**Visual Name:** Prompt Gamepass Purchase
**Description:** Prompts a player to purchase a gamepass.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `GamepassId = {` | Number |

**Outputs:** *(none)*

---

## `PromptGamepassPurchaseFinished`
**Visual Name:** Prompt Gamepass Purchase Finished
**Description:** Executes when a player responds to a gamepass purchase prompt.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Player = {` | Player |

---

## `RegisterCollisionGroup`
**Visual Name:** Register Collision Group
**Description:** Registers a collision group
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `GroupName = {` | String |
| `Unregister = {` | Bool |

**Outputs:** *(none)*

---

## `ResumeSound`
**Visual Name:** Resume Sound
**Description:** Resumes a paused sound.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Sound = {` | Object |

**Outputs:** *(none)*

---

## `SetCameraPositionLocal`
**Visual Name:** Set Camera Position
**Description:** Sets the position of the camera. For this to work, you must also set the CameraType property of the camera to scriptable!
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Position = {` | Vector3 |
| `Rotation = {` | Vector3 |

**Outputs:** *(none)*

---

## `SetCell`
**Visual Name:** Set Cell
**Description:** Set a voxel terrain cell
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Position = {` | Vector3 |
| `Material = {` | Choice |
| `Block = {` | Choice |
| `Orientation = {` | Choice |

**Outputs:** *(none)*

---

## `SetCoreGuiEnabled`
**Visual Name:** Set Core Gui Enabled (Late 2013+)
**Description:** Hide or show a core gui.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `CoreGui = {` | Choice |
| `Enabled = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | — |

---

## `SetLeaderstat`
**Visual Name:** Set Leaderstat
**Description:** Sets the value of a leaderstat.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `StatName = {` | String |
| `Value = {` | Number |

**Outputs:** *(none)*

---

## `SetModelPrimaryPartCFrameNew`
**Visual Name:** Set Model Primary Part CFrame
**Description:** Moves a model to the given position.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Model = {` | Object |
| `CFrame = {` | CFrame |

**Outputs:** *(none)*

---

## `SetMouseIconLocal`
**Visual Name:** Set Mouse Icon
**Description:** Sets the image for the mouse cursor.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Icon = {` | String |

**Outputs:** *(none)*

---

## `SetNetworkOwner`
**Visual Name:** Set Part Network Owner
**Description:** Sets the network owner of a part. If the owner is set to nil instead of a player, it will transfer ownership to the server. See https://developer.roblox.com/en-us/articles/Network-Ownership
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |
| `Player = {` | Any |

**Outputs:** *(none)*

---

## `SetObjectProperty`
**Visual Name:** Set Object Property
**Description:** Sets a property of an object.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |
| `Property = {` | String |
| `Value = {` | Any |

**Outputs:** *(none)*

---

## `SetPartPhysicalProperties`
**Visual Name:** Set Part Physical Properties
**Description:** Sets the elasticity and friction of a part.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |
| `Elasticity = {` | Number |
| `Friction = {` | Number |
| `Density = {` | Number |
| `ElasticityWeight = {` | Number |
| `FrictionWeight = {` | Number |

**Outputs:** *(none)*

---

## `StopAnimation`
**Visual Name:** Stop Animation
**Description:** Stops an AnimationTrack. Use the Load Animation block to create an AnimationTrack.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `AnimationTrack = {` | Object |
| `FadeTime = {` | Number |

**Outputs:** *(none)*

---

## `StopSound`
**Visual Name:** Stop Sound
**Description:** Stops a sound.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Sound = {` | Object |

**Outputs:** *(none)*

---

## `TakeDamage`
**Visual Name:** TakeDamage
**Description:** Deals the given amount of damage to the player if they are not protected by a forcefield. For the player you can input the player object, the character model, a part of the character, or the characters humanoid.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `Damage = {` | Number |

**Outputs:** *(none)*

---

## `TeleportPlayerToPosition`
**Visual Name:** Teleport Player To Position
**Description:** Moves a player to a point.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `Position = {` | Vector3 |
| `Rotation = {` | Vector3 |

**Outputs:** *(none)*

---

## `TeleportToPlace`
**Visual Name:** Teleport To Place
**Description:** Teleports a player to another Retrostudio place.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `PlaceId = {` | String |

**Outputs:** *(none)*

---

## `TeleportToPlaceProtected`
**Visual Name:** Teleport To Owned Place
**Description:** Teleports a player to another Retrostudio place as long the place was created by the same creator. Adds options for solo servers and forcing a new server.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `PlaceId = {` | String |
| `NewServer = {` | Bool |
| `SoloServer = {` | Bool |

**Outputs:** *(none)*

---

## `TextBoxCaptureFocus`
**Visual Name:** Focus on TextBox
**Description:** Make the user begin typing in a TextBox.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `TextBox = {` | Object |

**Outputs:** *(none)*

---

## `TextBoxReleaseFocus`
**Visual Name:** Unfocus on TextBox
**Description:** Make the user stop typing in a TextBox.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `TextBox = {` | Object |

**Outputs:** *(none)*

---

## `ToggleMobileControls`
**Visual Name:** Toggle Mobile Controls
**Description:** Hide or show the mobiole controls.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Enabled = {` | Bool |

**Outputs:** *(none)*

---

## `TweenObjectProperty`
**Visual Name:** Tween Object Property
**Description:** Smoothly transitions a property to another value over a set time.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |
| `Property = {` | String |
| `Value = {` | Any |
| `Time = {` | Number |
| `EasingStyle = {` | Choice |
| `EasingDirection = {` | Choice |
| `RepeatCount = {` | Number |
| `Reverses = {` | Bool |

**Outputs:** *(none)*

---

## `UnbanPlayerUID`
**Visual Name:** Unban Player
**Description:** (Yields) Unbans the specified player from the game.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `UserId = {` | Number |

**Outputs:** *(none)*

---

## `WaitForChild`
**Visual Name:** Wait For Child
**Description:** Wait until the given object has a child with the given name, and then run the connected blocks.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Parent = {` | Object |
| `ChildName = {` | String |
| `TimeOut = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Instance |

---
