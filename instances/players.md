# Players

The Players service contains a `Player` instance for each connected user. Player instances are created automatically when someone joins and removed when they leave.

**Path:** `game.Players`

---

## Service Properties

| Property | Type | Default | Notes |
|---|---|---|---|
| `ClassName` | String | `"Players"` | Read-only |
| `Name` | String | `"Players"` | |
| `Parent` | Object | `game` | |
| `CharacterAutoLoads` | Bool | `true` | Whether characters spawn automatically |
| `Archivable` | Bool | `true` | |

---

## Player Instance Properties

When a player joins, a `Player` object is added to `game.Players` with these properties:

| Property | Type | Notes |
|---|---|---|
| `Name` | String | The player's username |
| `UserId` | Number | Unique numeric identifier |
| `Character` | Object | Reference to the character `Model` in Workspace |
| `Team` | Object | Reference to a `Team` instance (if applicable) |
| `TeamColor` | BrickColor | The color of the player's team |
| `Neutral` | Bool | Whether the player is on no team |

---

## LocalPlayer

In **Local Scripts**, `game.Players.LocalPlayer` always refers to the client's own player instance:

```
Object 2 game.Players.LocalPlayer
```

> This path only works in Local Scripts. In Server Scripts, `LocalPlayer` is `nil`.

---

## Common Patterns

### Get all players
Use the `GetPlayersOnTeam` block or `GetChildren` on `game.Players`.

### React to players joining
Use the `PlayerAdded` event block — it fires with the `Player` output whenever someone connects.

### React to players leaving
Use the `PlayerRemoving` event block.

### Disable automatic character loading
```
Block Type SetObjectProperty ...
  Inputs:
    Object   2  game.Players
    Property 0  CharacterAutoLoads
    Value    0  false
```

Then spawn characters manually using the `LoadCharacter` block.

---

## Example: Get Player's Character

```
Block Type PlayerAdded Name Player Added1 ...
  Outputs: Player player

Block Type GetObjectProperty Name Get Character1 ...
  Inputs:
    Object   1  player
    Property 0  Character
  Outputs: Value char
```
