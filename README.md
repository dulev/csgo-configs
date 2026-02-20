# CS2 Configs

Personal CS2 (Counter-Strike 2) autoexec and practice configs.

## Installation

Place cfg files in:

```
<Steam Library>/steamapps/common/Counter-Strike Global Offensive/game/csgo/cfg/
```

Note: The game folder is still called "Counter-Strike Global Offensive" even though the game is CS2. The key difference from CS:GO is the extra `game/` directory in the path.

## Launch Options

Set these in Steam > CS2 > Properties > Launch Options:

```
-novid -console +exec autoexec.cfg
```

| Option | What it does |
|--------|-------------|
| `-novid` | Skips the intro video on startup |
| `-console` | Enables the developer console (toggle with `~` in-game) |
| `+exec autoexec.cfg` | Executes the autoexec on launch (CS2 doesn't always auto-run it) |

### Removed CS:GO launch options

These no longer do anything useful in CS2:

| Option | Why removed |
|--------|-----------|
| `-threads N` | CS2's Source 2 engine manages threads automatically |
| `-high` | Can cause instability; CS2 manages process priority itself |
| `-nojoy` | Joystick support is off by default in CS2 |
| `-tickrate 128` | CS2 uses sub-tick; tickrate is not configurable |
| `-d3d9ex` | CS2 uses DX11/Vulkan, not DX9 |

## Files

- **autoexec.cfg** - Main config: keybinds, settings, buy binds
- **practice.cfg** - Practice/workshop config: infinite money, grenades, sv_cheats

## CS:GO to CS2 Migration Notes

Key changes from the original CS:GO config:

- **Grenade binds** now use `slot6`-`slot10` instead of `use weapon_*`
- **Network commands** (`cl_interp`, `cl_cmdrate`, `cl_updaterate`, `cl_forcepreload`) are all removed -- server handles netcode
- **net_graph** replaced by `cq_netgraph`
- **r_cleardecals** no longer works on official/competitive servers
- **m_rawinput** forced on by default, command removed
- **Jumpthrow alias** may not work reliably on official servers due to sub-tick enforcement
- **Buy binds** require exact weapon name matching your loadout -- silent fail if mismatched
- **Damage display** developer trick blocked on official servers (`sv_max_allowed_developer 0`)
