# Soundscape

Soundscape is a RetroStudio-specific service that manages the audio environment and ambient sound effects for the game.

**Path:** `game.Soundscape`

---

## Properties

| Property | Type | Default | Notes |
|---|---|---|---|
| `ClassName` | String | `"SoundService"` | Read-only |
| `Name` | String | `"Soundscape"` | |
| `Parent` | Object | `game` | |
| `AmbientReverb` | Enum | `NoReverb` | Echo/reverb effect for all sounds |
| `DistanceFactor` | Number | `3.33` | How sound volume changes with distance |
| `DopplerScale` | Number | `1` | Intensity of the Doppler pitch shift effect |
| `RolloffScale` | Number | `1` | How quickly sound fades with distance |
| `Archivable` | Bool | `true` | |

---

## AmbientReverb Options

### No Effect
| Value | Description |
|---|---|
| `NoReverb` | No echo — default outdoor sound |

### Indoor Environments
| Value | Description |
|---|---|
| `GenericReverb` | Generic indoor echo |
| `PaddedCell` | Very dampened, minimal echo |
| `Room` | Small room echo |
| `Bathroom` | Reflective tile surfaces |
| `LivingRoom` | Carpeted room with furniture |
| `StoneRoom` | Small stone chamber |
| `Auditorium` | Large indoor venue |
| `ConcertHall` | Very large performance space |
| `Hangar` | Massive industrial building |
| `CarpettedHallway` | Long hallway with carpet |
| `Hallway` | Standard corridor echo |
| `StoneCorridor` | Stone hallway with more echo |
| `Arena` | Large sports arena |
| `Cave` | Natural cave reverb |

### Outdoor Environments
| Value | Description |
|---|---|
| `Alley` | Narrow space between buildings |
| `Forest` | Trees dampening sound |
| `City` | Urban outdoor environment |
| `Mountains` | High altitude outdoor |
| `Quarry` | Open pit with rock walls |
| `Plain` | Flat open area |
| `ParkingLot` | Flat pavement outdoors |

### Special Environments
| Value | Description |
|---|---|
| `SewerPipe` | Cylindrical enclosed space |
| `UnderWater` | Muffled underwater audio |

---

## Example: Set Cave Reverb

```
Block Type SetObjectProperty ...
  Inputs:
    Object   2  game.Soundscape
    Property 0  AmbientReverb
    Value    0  Cave
```

---

## Audio Physics Properties

| Property | Effect |
|---|---|
| `DistanceFactor` | Higher = sounds fade faster over distance |
| `DopplerScale` | Higher = more extreme pitch shift for moving sounds |
| `RolloffScale` | Higher = faster volume rolloff with distance |

> **Performance Tip:** Complex reverbs like `ConcertHall` or `Cave` use more CPU than `NoReverb`. Consider simpler options for better performance on lower-end devices.
