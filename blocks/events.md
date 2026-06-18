# EVENTS Blocks

Event blocks fire **asynchronously** when something happens in-game. They are always root blocks — they sit at the top of a block chain and trigger automatically when their condition is met.

---

## `ActivateTool`
**Visual Name:** Activate Tool
**Description:** Activates a tool
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Tool = {` | Object |

**Outputs:** *(none)*

---

## `AncestryChanged`
**Visual Name:** Ancestry Changed
**Description:** Runs connected blocks when the parent of the object or one of its ancestors changes.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Child = {` | Instance |

---

## `AnyPropertyChanged`
**Visual Name:** Any Property Changed
**Description:** Runs connected blocks when any property of an object is changed.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Property = {` | String |

---

## `BindToClose`
**Visual Name:** Bind To Close
**Description:** Runs code prior to the server shutting down.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `BindableFire2`
**Visual Name:** Fire Bindable Event
**Description:** Sends a message to another script. Parameters are optional and can be used to send extra data with the event.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `BindableEvent = {` | Object |
| `Parameters = {` | Tuple |

**Outputs:** *(none)*

---

## `BindableFunctionInvoke`
**Visual Name:** Invoke Bindable Function
**Description:** (Yields) Sends a message to another script. Parameters are optional and can be used to send extra data with the event.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `BindableFunction = {` | Object |
| `Parameters = {` | Tuple |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Output = {` | — |

---

## `BindableFunctionOnInvoke`
**Visual Name:** Receive Bindable Function
**Description:** Receive a message from another script. Parameters are optional and can be used to send extra data to the function. Requires a return block to function.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `BindableFunction = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Parameters = {` | — |

---

## `BindableRecieve2`
**Visual Name:** Receive Bindable Event
**Description:** Receive a message from another script. Parameters are optional and can be used to send extra data with the event.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `BindableEvent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Parameters = {` | — |

---

## `BodyPositionReachedTarget`
**Visual Name:** Body Position Reached Target
**Description:** Runs connected blocks when a specific body position reaches the desired position within .1 studs. Once fired this event will not fire again until Position is updated.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `BodyPosition = {` | Object |

**Outputs:** *(none)*

---

## `CharacterAdded`
**Visual Name:** Character Added
**Description:** Runs connected blocks when the character of a specified player is spawned.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Character = {` | Model |

---

## `Chatted`
**Visual Name:** Chatted
**Description:** Runs connected blocks when a player chats. Be warned, the filtered result may be different than what appears in chat.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Message = {` | String |

---

## `ChattedSpecificMessage`
**Visual Name:** Chatted Specific Message
**Description:** Runs connected blocks when a player says a specific thing.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `Message = {` | String |

**Outputs:** *(none)*

---

## `ChildAdded`
**Visual Name:** Child Added
**Description:** Runs connected blocks when a child is added to an object.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Child = {` | Instance |

---

## `ChildRemoved`
**Visual Name:** Child Removed
**Description:** Runs connected blocks when a child is removed from an object.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Child = {` | Instance |

---

## `DescendantAdded`
**Visual Name:** Descendant Added
**Description:** Runs connected blocks when a descendant is added to an object.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Descendant = {` | Instance |

---

## `DescendantRemoved`
**Visual Name:** Descendant Removed
**Description:** Runs connected blocks when a descendant is removed from an object.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Descendant = {` | Instance |

---

## `DialogChoiceSelected`
**Visual Name:** Dialog Choice Selected
**Description:** Runs connected blocks when a dialogchoice of a dialog is selected.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Dialog = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Player = {` | Player |

---

## `DisconnectEvent`
**Visual Name:** Disconnect Event
**Description:** Disconnects an event. Use the "EventConnection" output of any event block with this.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `EventConnection = {` | EventConnection |

**Outputs:** *(none)*

---

## `ExplosionHit`
**Visual Name:** Explosion Hit
**Description:** Runs connected blocks when an explosion hits a part.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Explosion = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Part = {` | BasePart |

---

## `Heartbeat`
**Visual Name:** Post Simulation
**Description:** Runs the connected blocks every frame after the physics simulation.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `DeltaTime = {` | Number |

---

## `HumanoidDied`
**Visual Name:** Humanoid Died
**Description:** Runs connected blocks when a humanoid dies.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:** *(none)*

---

## `HumanoidFreeFalling`
**Visual Name:** Humanoid Free Falling
**Description:** Runs connected blocks when a humanoid starts or stops free falling.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Active = {` | Bool |

---

## `HumanoidJumping`
**Visual Name:** Humanoid Jumping
**Description:** Runs connected blocks when a humanoid starts or stops jumping.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Active = {` | Bool |

---

## `HumanoidMoveToFinished`
**Visual Name:** Humanoid Move To Finished
**Description:** Runs connected blocks when a humanoid moveto finishes.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `ReachedTarget = {` | Bool |

---

## `HumanoidRunning`
**Visual Name:** Humanoid Running
**Description:** Runs connected blocks when the speed at which a humanoid is running changes.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Speed = {` | Number |

---

## `HumanoidSeated`
**Visual Name:** Humanoid Seated
**Description:** Runs connected blocks when a humanoid either sits in a seat or gets up.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Active = {` | Bool |

---

## `HumanoidStateChanged`
**Visual Name:** Humanoid State Changed
**Description:** Runs connected blocks when a humanoid changes state.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Humanoid = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `PreviousState = {` | String |

---

## `IsConnected`
**Visual Name:** Is Connected
**Description:** Check if an event is connected. Use the "EventConnection" output of any event block with this.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `EventConnection = {` | EventConnection |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `PartTouchEnded`
**Visual Name:** Part Touch Ended
**Description:** Runs connected blocks when a specified part stops touching another part.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `otherPart = {` | BasePart |

---

## `PartTouched`
**Visual Name:** Part Touched
**Description:** Runs connected blocks when a specified part is touched by another part.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Part = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `otherPart = {` | BasePart |

---

## `PlayerAdded`
**Visual Name:** Player Added
**Description:** Runs connected blocks when a player joins the game.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Player = {` | Player |

---

## `PlayerRemoving`
**Visual Name:** Player Removing
**Description:** Runs connected blocks when a player leaves the game.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Player = {` | Player |

---

## `PreSimulation`
**Visual Name:** Pre Simulation
**Description:** Runs code every frame before the physics simulation. DeltaTime is the time in seconds since the last frame.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `deltaTime = {` | Number |

---

## `PropertyChanged`
**Visual Name:** Property Changed
**Description:** Runs connected blocks when a specific property of an object is changed.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |
| `Property = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `NewValue = {` | Any |

---

## `RemoteFireAllClients2`
**Visual Name:** Fire Remote to All Clients
**Description:** Sends a message to all clients. Parameters are optional and can be used to send extra data with the event. Strings are filtered when sent from the client to server!
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `RemoteEvent = {` | Object |
| `Parameters = {` | Tuple |

**Outputs:** *(none)*

---

## `RemoteFireClient2`
**Visual Name:** Fire Remote Event
**Description:** Sends a message to a client. Parameters are optional and can be used to send extra data with the event. Strings are filtered when sent from the client to server!
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `RemoteEvent = {` | Object |
| `Player = {` | Object |
| `Parameters = {` | Tuple |

**Outputs:** *(none)*

---

## `RemoteFireServer2`
**Visual Name:** Fire Remote Event
**Description:** Sends a message to the server. Parameters are optional and can be used to send extra data with the event. Strings are filtered when sent from the client to server!
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `RemoteEvent = {` | Object |
| `Parameters = {` | Tuple |

**Outputs:** *(none)*

---

## `RemoteFunctionInvokeClient`
**Visual Name:** Invoke Remote Function
**Description:** (Yields) Calls a function on the client. Parameters are optional and can be used to send extra data with the event. Strings are filtered when sent from the client to server!
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `RemoteFunction = {` | Object |
| `Player = {` | Object |
| `Parameters = {` | Tuple |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Output = {` | — |

---

## `RemoteFunctionInvokeServer`
**Visual Name:** Invoke Remote Function
**Description:** (Yields) Calls a function on the server. Parameters are optional and can be used to send extra data with the event. Strings are filtered when sent from the client to server!
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `RemoteFunction = {` | Object |
| `Parameters = {` | Tuple |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Output = {` | — |

---

## `RemoteFunctionOnInvokeClient`
**Visual Name:** Receive Remote Function
**Description:** Receives a message from a server. Parameters are optional and can be used to send extra data to the server. Requires a return block to function.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `RemoteFunction = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Parameters = {` | — |

---

## `RemoteFunctionOnInvokeServer`
**Visual Name:** Receive Remote Function
**Description:** Receives a message from a client. Parameters are optional and can be used to send extra data to the client. Requires a return block to function.
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `RemoteFunction = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Parameters = {` | — |

---

## `RemoteRecieveClient2`
**Visual Name:** Receive Remote Event
**Description:** Receives a message from the server. Parameters are optional and can be used to send extra data with the event. Strings are filtered when sent from the client to server!
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `RemoteEvent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Parameters = {` | — |

---

## `RemoteRecieveServer2`
**Visual Name:** Receive Remote Event
**Description:** Receives a message from a client. Parameters are optional and can be used to send extra data with the event. Strings are filtered when sent from the client to server!
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `RemoteEvent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TUPLE_Parameters = {` | — |

---

## `RenderStepped`
**Visual Name:** Pre Render
**Description:** Runs code every frame before rendering. DeltaTime is the time in seconds since the last frame.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `deltaTime = {` | Number |

---

## `ToolActivated`
**Visual Name:** Tool Activated
**Description:** Runs connected blocks when the player clicks while holding the specified tool if the enabled property of the tool is true.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Tool = {` | Object |

**Outputs:** *(none)*

---

## `ToolDeactivated`
**Visual Name:** Tool Deactivated
**Description:** Runs connected blocks when the player stops clicking while holding the specified tool if the enabled property of the tool is true.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Tool = {` | Object |

**Outputs:** *(none)*

---

## `ToolEquipped`
**Visual Name:** Tool Equipped
**Description:** Runs connected blocks when the specified tool is equipped.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Tool = {` | Object |

**Outputs:** *(none)*

---

## `ToolUnequipped`
**Visual Name:** Tool Unequipped
**Description:** Runs connected blocks when the specified tool is unequipped.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Tool = {` | Object |

**Outputs:** *(none)*

---
