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
-console +exec autoexec
```

| Option | What it does |
|--------|-------------|
| `-console` | Enables the developer console (toggle with `~` in-game) |
| `+exec autoexec` | Executes the autoexec on launch. CS2 should auto-run it too; running it twice is harmless for this config |

To check it loaded, run `exec autoexec` in the console and look for `AUTOEXEC END` with no `Unknown command` lines.

### Removed CS:GO launch options

These no longer do anything useful in CS2:

| Option | Why removed |
|--------|-----------|
| `-threads N` | CS2's Source 2 engine manages threads automatically |
| `-high` | Can cause instability; CS2 manages process priority itself |
| `-nojoy` | Joystick support is off by default in CS2 |
| `-tickrate 128` | CS2 uses sub-tick; tickrate is not configurable |
| `-d3d9ex` | CS2 uses DX11/Vulkan, not DX9 |
| `-novid` | CS2 has no intro video |

## Files

- **autoexec.cfg** - Main config: keybinds, settings, buy binds
- **practice.cfg** - Practice/workshop config: infinite money, grenades, sv_cheats

## CS:GO to CS2 Migration Notes

Key changes from the original CS:GO config:

- **Grenade binds** now use `slot6`-`slot10` instead of `use weapon_*`
- **Network commands** (`cl_interp`, `cl_cmdrate`, `cl_updaterate`, `cl_forcepreload`) are all removed -- server handles netcode
- **net_graph** replaced by `cl_hud_telemetry_serverrecvmargin_graph_show` (`cq_netgraph` was also removed)
- **Numpad keys renamed**: `kp_ins`/`kp_end`/`kp_downarrow`/`kp_pgdn`/`kp_leftarrow`/`kp_rightarrow`/`kp_home`/`kp_uparrow`/`kp_pgup` are now `kp_0`-`kp_9`
- **Walk** is `+sprint` (was `+speed`)
- **Bomb drop** uses a `+dropc4`/`-dropc4` alias with `slot3; slot5` since `use weapon_*` no longer works
- **Q toggle** swaps an alias instead of rebinding `q`, so CS2 doesn't save a changed bind to its vcfg
- **Removed settings** with no CS2 equivalent: `cl_bob*`, `cl_viewmodel_shift_*`, `cl_disablefreezecam`, `cl_showhelp`, `cl_autowepswitch`, `cl_join_advertise`, `playgamesound`; `voice_scale` is now `snd_voipvolume`; `snd_mixahead 0.1` dropped (adds ~100 ms audio delay in CS2)
- **Radar zoom** clamped to CS2's `cl_radar_scale` range of 0.25-1.0
- **r_cleardecals** no longer works on official/competitive servers
- **m_rawinput** forced on by default, command removed
- **Jumpthrow alias** may not work reliably on official servers due to sub-tick enforcement
- **Buy binds** require exact weapon name matching your loadout -- silent fail if mismatched, so binds chain both variants (`m4a1; m4a1_silencer`, `fiveseven; tec9; cz75a`, `deagle; revolver`, `mp7; mp5sd`)
- **Damage display** developer trick blocked on official servers (`sv_max_allowed_developer 0`)
