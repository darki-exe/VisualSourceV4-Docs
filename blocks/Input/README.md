# Input

Input blocks detect **player interaction** — keyboard presses, mouse clicks, mouse movement, GUI element interaction, and device-specific input. Most input blocks are Event-flagged, meaning they fire asynchronously when the interaction occurs.

> Many Input blocks are restricted to **Local Scripts** since they listen for client-side signals. Always check the **Context** field before using an Input block in a Server Script.

---

## Documented Blocks

| Block | Visual Name | Description |
|---|---|---|
| [`GUILeftMouseButtonClick`](GUILeftMouseButtonClick.md) | GUI Left Click | Fires when a GuiButton is left-clicked |

---

## Input Categories

### GUI Interaction
Events tied to specific `GuiButton` or `GuiObject` instances:
- `GUILeftMouseButtonClick` — left click on a button
- `GUILeftMouseButtonDown` / `GUILeftMouseButtonUp` — press/release
- `GUIRightMouseButtonClick` — right click
- `GUIMouseEnter` / `GUIMouseLeave` — hover in/out
- `GUIMouseMoved` — mouse moves over a GUI
- `GUIMouseWheelForward` / `GUIMouseWheelBackward` — scroll wheel

### Keyboard
- `KeyDown` / `KeyUp` — key pressed/released (server-side via `ContextActionService` or deprecated input)
- `KeyDownLocal` / `KeyUpLocal` — client-side keyboard input
- `InputBegan` / `InputChanged` / `InputEnded` — `UserInputService` events (all input types)

### Mouse (Raw)
- `LeftMouseDown` / `LeftMouseUp` — global left mouse button
- `RightMouseDown` / `RightMouseUp` — global right mouse button
- `GetMousePosition2D` / `GetMousePosition3D` — current mouse position

### Click Detectors
- `ClickDetectorInteraction` — fires when a `ClickDetector` in a 3D part is clicked or hovered

### TextBox
- `TextBoxFocused` / `TextBoxFocusLost` — TextBox gains or loses focus

---

## Context Notes

- **Local Only blocks:** `KeyDownLocal`, `KeyUpLocal`, `LeftMouseDownLocal`, raw mouse position blocks — these depend on `UserInputService` or `Mouse`, which only exist on the client.
- **All Scripts blocks:** GUI blocks like `GUILeftMouseButtonClick` technically work in both server and local contexts, but GUI interaction is always a client event — these blocks are most effective in Local Scripts.
