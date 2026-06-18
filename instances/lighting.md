# Lighting

The Lighting service controls the visual atmosphere of the game: time of day, ambient colors, shadows, and fog.

**Path:** `game.Lighting`

---

## Properties

### Appearance
| Property | Type | Default | Notes |
|---|---|---|---|
| `Ambient` | Color3 | `[127, 127, 127]` | Overall light color in shaded areas |
| `Brightness` | Number | `1` | Global brightness multiplier |
| `ColorShift_Bottom` | Color3 | `[0, 0, 0]` | Color tint applied to bottom surfaces |
| `ColorShift_Top` | Color3 | `[0, 0, 0]` | Color tint applied to top surfaces |
| `GlobalShadows` | Bool | `true` | Enable/disable shadows |
| `OutdoorAmbient` | Color3 | `[28, 128, 1]` | Light color in outdoor lit areas |

### Time & Position
| Property | Type | Default | Notes |
|---|---|---|---|
| `ClockTime` | Number | `14` | Time of day as a 24-hour hour value (0–24) |
| `GeographicLatitude` | Number | `41.73` | Latitude used to calculate sun angle |

### Fog
| Property | Type | Notes |
|---|---|---|
| `FogColor` | Color3 | Color of the fog |
| `FogStart` | Number | Distance (studs) at which fog begins |
| `FogEnd` | Number | Distance (studs) at which fog is fully opaque |

### Data
| Property | Type | Notes |
|---|---|---|
| `ClassName` | String | `"Lighting"` (read-only) |
| `Name` | String | `"Lighting"` |
| `Parent` | Object | `game` |

---

## ClockTime Values

| Value | Time of Day |
|---|---|
| `0` | Midnight |
| `6` | 6:00 AM (sunrise) |
| `12` | Noon |
| `14` | 2:00 PM |
| `18` | 6:00 PM (sunset) |
| `24` | Midnight (same as 0) |

---

## Fog Configuration

To add realistic fog, configure these three properties together:

- **FogStart** — fog begins at this distance; objects closer appear unaffected
- **FogEnd** — objects at this distance (or further) are completely hidden
- **FogColor** — the color of the fog (usually gray or white)

A `FogEnd` of `100000` (default) effectively disables fog since it's far beyond rendering distance.

---

## Example: Set Time to Sunset

```
Block Type SetObjectProperty ...
  Inputs:
    Object   2  game.Lighting
    Property 0  ClockTime
    Value    0  12          -- hex 18 = decimal 24? No: 12 hex = 18 decimal
```

> Remember: `ClockTime` inputs use hex. `12` hex = 18 decimal = 6:00 PM.

---

## Example: Add Gray Fog

```
-- FogColor = gray (192, 192, 192)
Block Type SetObjectProperty ...
  Inputs:
    Object   2  game.Lighting
    Property 0  FogColor
    Value    0  C0,C0,C0

-- FogStart = 100 studs
Block Type SetObjectProperty ...
  Inputs:
    Object   2  game.Lighting
    Property 0  FogStart
    Value    0  64          -- hex 64 = 100

-- FogEnd = 500 studs
Block Type SetObjectProperty ...
  Inputs:
    Object   2  game.Lighting
    Property 0  FogEnd
    Value    0  1F4         -- hex 1F4 = 500
```

---

## Sky Objects

You can parent a `Sky` object to `game.Lighting` to customize the skybox. Create one using the `CreateObject` block with `ClassName = "Sky"` and `Parent = game.Lighting`.
