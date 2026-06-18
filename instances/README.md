# Game Hierarchy

RetroStudio uses a mid-2015 era Roblox game hierarchy. Understanding this structure is essential for referencing objects correctly in block inputs using `value_type 2` (object paths).

---

## Top-Level Structure

```
game (DataModel)
│
├── Workspace          — All 3D objects in the game world
├── Players            — Player instances (added/removed automatically)
├── Lighting           — Visual atmosphere and time of day
├── StarterGui         — UI elements cloned to players on spawn
├── StarterPack        — Tools cloned to player backpacks on spawn
├── Debris             — Service for managing temporary objects
├── Teams              — Team objects for team-based games
└── Soundscape         — Audio environment (RetroStudio-specific)
```

---

## Object Paths in VisualSource

When a block needs a reference to an instance, you can provide an object path as a `value_type 2` input:

```
Object 2 game.Workspace.Part
Object 2 game.Players.LocalPlayer
Object 2 game.Lighting
Object 2 game.Workspace.Model.HumanoidRootPart
```

Paths are dot-separated, starting from `game`.

---

## Services Reference

| Service | Path | Description |
|---|---|---|
| Workspace | `game.Workspace` | 3D game world container |
| Players | `game.Players` | Connected player instances |
| Lighting | `game.Lighting` | Atmosphere and time of day |
| StarterGui | `game.StarterGui` | UI templates |
| StarterPack | `game.StarterPack` | Tool templates |
| Debris | `game.Debris` | Temporary object management |
| Teams | `game.Teams` | Team definitions |
| Soundscape | `game.Soundscape` | Audio environment |

---

## Detailed Pages

- [Workspace](workspace.md)
- [Players](players.md)
- [Lighting](lighting.md)
- [Soundscape](soundscape.md)

---

## Mid-2015 Era Notes

RetroStudio targets the **mid-2015 Roblox engine**. Some features present in modern Roblox do not exist here:

### ✅ Available
- Basic lighting controls (Ambient, Brightness, ColorShift)
- GlobalShadows
- Fog system
- ClockTime and GeographicLatitude
- CharacterAutoLoads
- Sound service with reverb options

### ❌ Not Available
- Advanced atmosphere/volumetric effects
- Post-processing effects (Bloom, Blur, SunRays, ColorCorrection)
- Terrain Clouds object
- EnvironmentDiffuseScale / EnvironmentSpecularScale
