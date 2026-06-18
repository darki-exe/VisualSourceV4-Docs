# INPUT Blocks

Input blocks detect player interaction: keyboard, mouse, GUI elements, and device-specific input. Some blocks are restricted to **Local Scripts** since they listen for client-side input.

---

## `ClickDetectorInteraction`
**Visual Name:** Click Detector Interaction
**Description:** Runs connected blocks when a clickdetector is interacted with in a specific way.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `ClickDetector = {` | Object |
| `InteractionType = {` | Choice |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Player = {` | Player |

---

## `GUILeftMouseButtonClick`
**Visual Name:** GUI Left Click
**Description:** Runs connected blocks when a button is left clicked.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUIButton = {` | Object |

**Outputs:** *(none)*

---

## `GUILeftMouseButtonDown`
**Visual Name:** GUI Left Mouse Down
**Description:** Runs connected blocks when the left mouse is pressed down over a button.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUIButton = {` | Object |

**Outputs:** *(none)*

---

## `GUILeftMouseButtonUp`
**Visual Name:** GUI Left Mouse Up
**Description:** Runs connected blocks when the left mouse stops pressing a button.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUIButton = {` | Object |

**Outputs:** *(none)*

---

## `GUIMouseEnter`
**Visual Name:** GUI Mouse Enter
**Description:** Runs connected blocks when the mouse goes over a GUI.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUI = {` | Object |

**Outputs:** *(none)*

---

## `GUIMouseLeave`
**Visual Name:** GUI Mouse Leave
**Description:** Runs connected blocks when the mouse leaves a GUI.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUI = {` | Object |

**Outputs:** *(none)*

---

## `GUIMouseMoved`
**Visual Name:** GUI Mouse Moved
**Description:** Runs connected blocks when the mouse moves while inside a GUI.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUI = {` | Object |

**Outputs:** *(none)*

---

## `GUIMouseWheelBackward`
**Visual Name:** GUI Mouse Wheel Down
**Description:** Runs connected blocks when the mouse wheel is moved backward while over a GUI.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUI = {` | Object |

**Outputs:** *(none)*

---

## `GUIMouseWheelForward`
**Visual Name:** GUI Mouse Wheel Up
**Description:** Runs connected blocks when the mouse wheel is moved upward while over a GUI.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUI = {` | Object |

**Outputs:** *(none)*

---

## `GUIRightMouseButtonClick`
**Visual Name:** GUI Right Click
**Description:** Runs connected blocks when a button is right clicked.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUIButton = {` | Object |

**Outputs:** *(none)*

---

## `GUIRightMouseButtonDown`
**Visual Name:** GUI Right Mouse Down
**Description:** Runs connected blocks when the right mouse is pressed down over a button.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUIButton = {` | Object |

**Outputs:** *(none)*

---

## `GUIRightMouseButtonUp`
**Visual Name:** GUI Right Mouse Up
**Description:** Runs connected blocks when the right mouse stops pressing a button.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `GUIButton = {` | Object |

**Outputs:** *(none)*

---

## `GetMousePosition2D`
**Visual Name:** Get Mouse Position 2D
**Description:** (Yields) Returns the position of a players mouse on their screen.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `X = {` | Number |

---

## `GetMousePosition2DLocal`
**Visual Name:** Get Mouse Position 2D
**Description:** Returns the position of a players mouse on their screen.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `X = {` | Number |

---

## `GetMousePosition3D`
**Visual Name:** Get Mouse Position 3D
**Description:** (Yields) Returns the position in the world that a players mouse is pointing to.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Position = {` | Vector3 |

---

## `GetMousePosition3DLocal`
**Visual Name:** Get Mouse Position 3D
**Description:** Returns the position in the world that a players mouse is pointing to.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Position = {` | Vector3 |

---

## `GetMouseTargetPart`
**Visual Name:** Get Mouse Target Part
**Description:** (Yields) Returns the part that a players mouse is pointing at.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TargetPart = {` | BasePart |

---

## `GetMouseTargetPartLocal`
**Visual Name:** Get Mouse Target Part
**Description:** Returns the part that a players mouse is pointing at.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `TargetPart = {` | BasePart |

---

## `GetMouseTargetSurface`
**Visual Name:** Get Mouse Target Surface
**Description:** (Yields) Returns the surface the mouse is pointing at. This can either be Front, Back, Left, Right, Top, or Bottom
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Surface = {` | String |

---

## `GetMouseTargetSurfaceLocal`
**Visual Name:** Get Mouse Target Surface
**Description:** Returns the surface the mouse is pointing at. This can either be Front, Back, Left, Right, Top, or Bottom
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Surface = {` | String |

---

## `HandlesMouseButtonDown`
**Visual Name:** Handles Mouse Down
**Description:** Runs connected blocks when the left mouse is pressed down over a Handles instance. The Handles must be a descendant of a PlayerGui.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Handles = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Handle = {` | String |

---

## `HandlesMouseButtonUp`
**Visual Name:** Handles Mouse Up
**Description:** Runs connected blocks when the left mouse is released over a Handles instance. The Handles must be a descendant of a PlayerGui.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Handles = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Handle = {` | String |

---

## `HandlesMouseDrag`
**Visual Name:** Handles Mouse Drag
**Description:** Runs connected blocks when the mouse drags a Handles instance. The Handles must be a descendant of a PlayerGui.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Handles = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Handle = {` | String |

---

## `HandlesMouseEnter`
**Visual Name:** Handles Mouse Enter
**Description:** Runs connected blocks when the mouse hovers over a Handles instance. The Handles must be a descendant of a PlayerGui.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Handles = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Handle = {` | String |

---

## `HandlesMouseLeave`
**Visual Name:** Handles Mouse Leave
**Description:** Runs connected blocks when the mouse leaves a Handles instance. The Handles must be a descendant of a PlayerGui.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Handles = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Handle = {` | String |

---

## `InputBegan`
**Visual Name:** Input Began
**Description:** Runs when any input begins.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Type = {` | String |

---

## `InputChanged`
**Visual Name:** Input Changed
**Description:** Runs when an input that doesn't start or end is changed. (Ex. Mouse movement, controller thumbstick movement)
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Type = {` | String |

---

## `InputEnded`
**Visual Name:** Input Ended
**Description:** Runs when any input ends.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Type = {` | String |

---

## `JumpRequest`
**Visual Name:** User Jump Request
**Description:** Runs connected blocks when the user attempts to jump.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `KeyDown`
**Visual Name:** Key Down
**Description:** Fires when the specified player starts pressing a key. For key names, see https://developer.roblox.com/en-us/api-reference/enum/KeyCode
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `Key = {` | String |

**Outputs:** *(none)*

---

## `KeyDownLocal`
**Visual Name:** Key Down
**Description:** Fires when the specified player starts pressing a key. For key names, see https://developer.roblox.com/en-us/api-reference/enum/KeyCode
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Key = {` | String |

**Outputs:** *(none)*

---

## `KeyUp`
**Visual Name:** Key Up
**Description:** Fires when the specified player stops pressing a key. For key names, see https://developer.roblox.com/en-us/api-reference/enum/KeyCode
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `Key = {` | String |

**Outputs:** *(none)*

---

## `KeyUpLocal`
**Visual Name:** Key Up
**Description:** Fires when the specified player stops pressing a key. For key names, see https://developer.roblox.com/en-us/api-reference/enum/KeyCode
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Key = {` | String |

**Outputs:** *(none)*

---

## `LeftMouseDown`
**Visual Name:** Left Mouse Down
**Description:** Runs connected blocks when the left mouse button starts being pressed.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:** *(none)*

---

## `LeftMouseDownLocal`
**Visual Name:** Left Mouse Down
**Description:** 
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `LeftMouseUp`
**Visual Name:** Left Mouse Up
**Description:** Runs connected blocks when the left mouse button stops being pressed.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:** *(none)*

---

## `LeftMouseUpLocal`
**Visual Name:** Left Mouse Up
**Description:** 
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `RightMouseDown`
**Visual Name:** Right Mouse Down
**Description:** Runs connected blocks when the right mouse button starts being pressed.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:** *(none)*

---

## `RightMouseDownLocal`
**Visual Name:** Right Mouse Down
**Description:** 
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `RightMouseUp`
**Visual Name:** Right Mouse Up
**Description:** Runs connected blocks when the right mouse button stops being pressed.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:** *(none)*

---

## `RightMouseUpLocal`
**Visual Name:** Right Mouse Up
**Description:** 
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `SetMouseBehavior`
**Visual Name:** Set Mouse Behavior
**Description:** Changes how the players mouse behaves.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Mode = {` | Choice |

**Outputs:** *(none)*

---

## `SetMouseTargetFilterLocal`
**Visual Name:** Set Mouse Target Filter
**Description:** Sets an object to be ignored when calculating the 3D mouse position and mouse target.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |

**Outputs:** *(none)*

---

## `TextBoxFocusLost`
**Visual Name:** Text Box Focus Lost
**Description:** Runs connected blocks when a text box is no longer focused on.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `TextBox = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `EnterPressed = {` | Bool |

---

## `TextBoxFocused`
**Visual Name:** Text Box Focused
**Description:** Runs connected blocks when a text box is focused on.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `TextBox = {` | Object |

**Outputs:** *(none)*

---
