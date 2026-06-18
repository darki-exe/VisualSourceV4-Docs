# MISC Blocks

Miscellaneous blocks provide utilities such as debug output, JSON encoding/decoding, time functions, group/badge checks, and plugin tools.

---

## `AddDebrisItem`
**Visual Name:** Add Item To Debris
**Description:** Adds an item to debris removing it after the inputted time
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Object = {` | Object |
| `Time = {` | Number |

**Outputs:** *(none)*

---

## `AddPluginButton`
**Visual Name:** Add Button
**Description:** Add a button to a toolbar. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `ToolbarName = {` | String |
| `ID = {` | String |
| `ToolTip = {` | String |
| `Icon = {` | String |

**Outputs:** *(none)*

---

## `AddPluginToolbar`
**Visual Name:** Add Toolbar
**Description:** Add a toolbar to the studio UI. This will automatically be deleted when the plugin that created it is deactivated. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Name = {` | String |

**Outputs:** *(none)*

---

## `AddToStudioSelection`
**Visual Name:** Add to Selection
**Description:** Adds an array of instances to the studio selection. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Instances = {` | Table |

**Outputs:** *(none)*

---

## `AddUserToChatChannel`
**Visual Name:** Add User To Chat Channel
**Description:** Allows a user to talk and listen to a channel. The "TextSource" output is a TextSource object, look on the Roblox Creator Hub for more information.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Channel = {` | Object |
| `UserId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TextSource = {` | TextSource |

---

## `Assert`
**Visual Name:** Assert
**Description:** Errors if the value to assert is equal to false or nil
**Context:** All Scripts

**Inputs:**
| Name | Type |
|---|---|
| `Value = {` | Any |
| `ErrorMessage = {` | String |

**Outputs:** *(none)*

---

## `CreateChatChannel`
**Visual Name:** Create Chat Channel
**Description:** Creates a channel that chat messages can be sent to and received from.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Channel = {` | TextChannel |

---

## `DumpMemory`
**Visual Name:** Dump Memory
**Description:** Prints the scripts entire memory table. Useful for advanced debugging.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `Error`
**Visual Name:** Error
**Description:** Halts execution and throws an error with the specified message
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Text = {` | String |

**Outputs:** *(none)*

---

## `GetDefaultChannel`
**Visual Name:** Get Default Channel
**Description:** Outputs the default text chat channel. This can be used to recieve messages sent using the default chat bar. Messages cannot be sent to this channel.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Channel = {` | TextChannel |

---

## `GetGameBadges`
**Visual Name:** Get Game Badges
**Description:** Returns a table with all of the current game's badges.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Badges = {` | Table |

---

## `GetGameInfo`
**Visual Name:** Get Game Info
**Description:** Returns a table with the current game's info
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `GameInfo = {` | Table |

---

## `GetGamepasses`
**Visual Name:** Get Gamepasses
**Description:** Returns a table with the current game's gamepasses
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Gamepasses = {` | Table |

---

## `GetRankInGroup`
**Visual Name:** Get Rank In Group
**Description:** (Yields) Returns the rank the user holds in a group.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `GroupId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Number |

---

## `GetRobloxVersion`
**Visual Name:** Get Roblox Version
**Description:** Returns the time era of this place.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Number |

---

## `GetServerTimeNow`
**Visual Name:** Get Server Time Now
**Description:** Returns the server epoch time in seconds.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Number |

---

## `GetStudioSelection`
**Visual Name:** Get Selection
**Description:** Returns a table of everything selected in studio. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Selection = {` | Table |

---

## `GetStudioTheme`
**Visual Name:** Get Studio Theme
**Description:** Detect what studio theme is being used. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Design = {` | String |

---

## `GetTestStatus`
**Visual Name:** Get Test Status
**Description:** Returns a string telling if the user is playtesting or not. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Status = {` | String |

---

## `GetUserThumbnail`
**Visual Name:** Get User Thumbnail
**Description:** Gets an image ID that can be used to show a players avatar. This will only be the players Retrostudio avatar if they are currently in the place.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `UserId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `ImageId = {` | String |

---

## `InsertModel`
**Visual Name:** Insert Model
**Description:** (Yields) Loads the model from its retrostudio id The success output returns true or false based on whether or not it successfully loads. If success is true and LoadedModel is nil then there was no model at that id. Loading blocks may only be used 5 + (5 * number of players) times per minute.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `ID = {` | Number |
| `Parent = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Success = {` | Bool |

---

## `InsertRetrostudioAvatar`
**Visual Name:** Insert RetroStudio Avatar
**Description:** (Yields) Inserts a player's RetroStudio Avatar.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `ID = {` | Number |
| `CFrame = {` | CFrame |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Model = {` | Model |

---

## `IsClient`
**Visual Name:** Is Client
**Description:** Returns a bool based on whether or not this script is running on the server.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Bool |

---

## `IsFriendsWith`
**Visual Name:** Is Friends With
**Description:** (Yields) Returns a bool based on if a player is friends with another player.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `UserId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `IsGameLoaded`
**Visual Name:** Is Game Loaded
**Description:** Returns a bool based on whether or not the game has loaded.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Bool |

---

## `IsGuest`
**Visual Name:** Is Guest
**Description:** Returns a bool based on if a player is a guest or not.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Bool |

---

## `IsInGroup`
**Visual Name:** Is In Group
**Description:** (Yields) Returns a bool based on if a player is in a certain group or not.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Player = {` | Object |
| `GroupId = {` | Number |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Result = {` | Bool |

---

## `IsPlayingSolo`
**Visual Name:** Is Solo
**Description:** Returns a bool based on whether or not this script is running in a solo game server.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Bool |

---

## `IsServer`
**Visual Name:** Is Server
**Description:** Returns a bool based on whether or not this script is running on the server.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Bool |

---

## `IsStudio`
**Visual Name:** Is Studio
**Description:** Returns a bool based on whether or not this script is running in studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Bool |

---

## `IsTouchscreen`
**Visual Name:** Is Touchscreen
**Description:** Detects if the game is running on a touchscreen device.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Bool |

---

## `JsonDecode`
**Visual Name:** Json Decode
**Description:** Decodes JSON to a lua table
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `JSON = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Table = {` | Table |

---

## `JsonEncode`
**Visual Name:** Json Encode
**Description:** Encodes a table to JSON
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Table = {` | Table |

**Outputs:**
| Name | Type Hint |
|---|---|
| `JSON = {` | String |

---

## `LoadInstance`
**Visual Name:** Load Instance
**Description:** (Yields) Loads the model stored to a key. Loading blocks may only be used 5 + (5 * number of players) times per minute.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Key = {` | String |
| `Parent = {` | Object |
| `Shared = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Success = {` | Bool |

---

## `LoadVariable`
**Visual Name:** Load Variable
**Description:** (Yields) Loads the variable stored to a key. Loading blocks may only be used 5 + (5 * number of players) times per minute.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Key = {` | String |
| `Shared = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Success = {` | Bool |

---

## `ModelInserted`
**Visual Name:** Model Inserted
**Description:** Runs the connected blocks whenever an Insert Model block executes in any server script.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `SourceScript = {` | Script |

---

## `OsClock`
**Visual Name:** Os Clock
**Description:** Returns the amount of CPU time used in seconds. This is high precision and can be used for benchmarking.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Number |

---

## `OsDate`
**Visual Name:** Os Date
**Description:** Returns date/time information based on the given time, Timezone must either be '*t' (local time) or '!*t' (UTC time | Default)
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Time = {` | Number |
| `Timezone = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `DateTable = {` | Table |

---

## `OsTime`
**Visual Name:** Os Time
**Description:** Returns the real world time in seconds.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Answer = {` | Number |

---

## `PluginButtonClicked`
**Visual Name:** Button Clicked
**Description:** Fires when a plugin button is clicked. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `ToolbarName = {` | String |
| `ID = {` | String |

**Outputs:** *(none)*

---

## `PluginButtonSetActive`
**Visual Name:** Set Button Active
**Description:** Add or remove an outline from a plugin button. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `ToolbarName = {` | String |
| `ID = {` | String |
| `State = {` | Bool |

**Outputs:** *(none)*

---

## `PluginDeactivating`
**Visual Name:** Plugin Deactivating
**Description:** Runs connected blocks when the plugin that this script is a part of is toggled off or reloaded. The plugin will wait until the code under this block finishes running to delete itself. If more than 5 seconds pass, the plugin will delete itself anyways. This is for plugins and will error outside of studio.
**Context:** All Scripts

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `Print`
**Visual Name:** Print
**Description:** Prints text to the output window.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Text = {` | String |

**Outputs:** *(none)*

---

## `ReceiveChatMessage`
**Visual Name:** Receive Chat Message
**Description:** An event that is fired when a chat message is received from the given channel The "TextChatMessage" output is a TextChatMessage object, look on the Roblox Creator Hub for more information.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:**
| Name | Type |
|---|---|
| `Channel = {` | Object |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TextChatMessage = {` | TextChatMessage |

---

## `ReloadPlace`
**Visual Name:** Reload Place
**Description:** Reloads the place (Does not work in Studio), same function as the '!reloadplace' command.
**Context:** All Scripts

**Inputs:** *(none)*

**Outputs:** *(none)*

---

## `RemoveFromStudioSelection`
**Visual Name:** Remove from Selection
**Description:** Removes an array of instances from the studio selection. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Instances = {` | Table |

**Outputs:** *(none)*

---

## `SaveInstance`
**Visual Name:** Save Instance
**Description:** (Yields) Saves a model to a key. This model can be accessed across servers with the Load Instance block if the same key is given. This block may only be used 5 + (5 * number of players) times per minute.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Model = {` | Object |
| `Key = {` | String |
| `Shared = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Success = {` | Bool |

---

## `SaveVariable`
**Visual Name:** Save Variable
**Description:** (Yields) Saves a variable to a key. This variable can be accessed across servers with the Load Variable block if the same key is given. This block may only be used 5 + (5 * number of players) times per minute.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Value = {` | Any |
| `Key = {` | String |
| `Shared = {` | Bool |

**Outputs:**
| Name | Type Hint |
|---|---|
| `Success = {` | Bool |

---

## `SendChatMessage`
**Visual Name:** Send Chat Message
**Description:** Sends a chat message to the given channel. The "TextChatMessage" output is a TextChatMessage object, look on the Roblox Creator Hub for more information.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Channel = {` | Object |
| `Message = {` | String |

**Outputs:**
| Name | Type Hint |
|---|---|
| `TextChatMessage = {` | TextChatMessage |

---

## `StudioSelectionChanged`
**Visual Name:** Selection Changed
**Description:** Runs connected blocks when something is selected or deselected in studio. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Selection = {` | Table |

---

## `TestStatusChanged`
**Visual Name:** Test Status Changed
**Description:** Runs connected blocks when a playtest starts, stops, or is paused. This is for plugins and will error outside of studio.
**Context:** All Scripts
**Flags:** `Event`

**Inputs:** *(none)*

**Outputs:**
| Name | Type Hint |
|---|---|
| `Status = {` | String |

---

## `Warn`
**Visual Name:** Warn
**Description:** Prints text to the output window but now it's orange.
**Context:** All Scripts
**Flags:** `Auto Execute`

**Inputs:**
| Name | Type |
|---|---|
| `Text = {` | String |

**Outputs:** *(none)*

---
