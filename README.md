# Lost In Space — PICO-8 Game

A complete arcade game built in **PICO-8** using **Lua**. *Lost In Space* is a Flappy-Bird-style side-scroller: the player flaps to stay airborne, dodges obstacles, manages a health bar, and collects pickups while the score climbs. The cartridge includes hand-made sprites, a tile map, sound effects, and music.

---

## Gameplay

- Tap to **flap** upward; **gravity** constantly pulls the player down.
- Navigate through scrolling **pipe** obstacles without colliding.
- Survive on a **health** system — running out ends the run.
- Grab **pickups** scattered through the level.
- Rack up **score** the longer you last.

The game runs through three states — **start → game → game over** — driven by a simple state machine.

---

## Technical Design

The cartridge is organized around PICO-8's standard game loop (`_init`, `_update`, `_draw`), with each subsystem split into its own init/update/draw routines:

| System | Functions |
|--------|-----------|
| Game loop | `_init`, `_update`, `_draw` |
| State machine | `update_start` / `draw_start`, `update_game` / `draw_game`, `update_game_over` / `draw_game_over` |
| Obstacles | `init_pipes`, `update_pipes`, `draw_pipes` |
| Collision | `collide` (player vs. pipes / bounds) |
| Health | `init_health`, `update_health`, `draw_health` |
| Pickups | `init_pickups`, `update_pickups`, `draw_pickups` |
| Score | `u_score` |

Tunable parameters (flap strength, gravity) are exposed at the top of `_init` for easy balancing. Audio is handled through PICO-8's `sfx`/`music` channels, with `__gfx__`, `__map__`, `__sfx__`, and `__music__` data embedded in the cartridge.

---

## Repository Contents

```
.
├── Lost_In_Space_Nurlan_Abdullayev.p8   # PICO-8 cartridge (Lua + gfx + map + sfx + music)
├── Game Devolepment (A) Project Proposal ... .docx   # Project proposal
└── README.md
```

---

## How to Play

You'll need [PICO-8](https://www.lexaloffle.com/pico-8.php) (a fantasy console).

```bash
git clone https://github.com/nurlan-abdullazada/Game_Devolepment.git
```

1. Launch PICO-8.
2. Load the cartridge:
   ```
   load Lost_In_Space_Nurlan_Abdullayev.p8
   ```
3. Run it:
   ```
   run
   ```

Press the action button to flap and start playing.

---

## Author

[Nurlan Abdullazada](https://github.com/nurlan-abdullazada)
