# Aethoria

A small real-time strategy game *Aethoria*, written as **one HTML file** with plain JavaScript and the Canvas 2D API. It has no dependencies, no build step and no image files. All sprites, terrain, icons and sound effects are generated in code when the page loads.

> Gather resources, grow your town, advance through the ages, and destroy every enemy building.

**[Play the live demo](https://aethoria.makemysitelive.com/)**

---

## Quick start

Download `Aethoria.html` and open it in any modern browser. You can double-click the file, or drag it into a browser window. You don't need to install anything, run a server or build anything.

The only network request is for the **Cinzel** and **Spectral** fonts from Google Fonts. If you're offline, the game still runs and uses fallback serif fonts.

---

## Features

- **Economy.** Villagers gather wood, food (berries and farms), gold and stone, and carry it back to a Town Center or Storage Pit.
- **Construction.** Several villagers can build the same site together, and each building shows its progress.
- **Three ages.** Advance from the Stone Age to the Tool Age and then the Bronze Age to unlock stronger units and buildings.
- **Combat.** Melee infantry, and watch towers that shoot arrows.
- **AI opponent.** It runs its own economy, builds houses, barracks and towers, advances through the ages, defends its base, and sends attack waves.
- **Fog of war.** Unexplored areas are black, and areas you've explored but can't currently see are dimmed.
- **Minimap.** Click on it to move the camera, or right-click to send orders.
- **A\* pathfinding** on a 64×64 tile grid, with 8-direction movement and no corner-cutting.
- **Procedural pixel art.** Units are drawn from ASCII sprite maps. Trees, mines, buildings and terrain use seeded noise.
- **Synthesized sound.** Chopping, mining, combat, the building-complete bell and the age-up fanfare are all generated with the Web Audio API.
- **Classic interface.** A resource bar at the top, and a bottom panel with the minimap, info panel, command grid and tooltips.

---

## Controls

| Action | Input |
|---|---|
| Select a unit, building or resource | Left click |
| Box-select units | Left drag |
| Select all units of one type on screen | Double click |
| Move / gather / attack / help build / drop off | Right click |
| Place a building | Choose it in the command panel, then left click (right click cancels) |
| Scroll the camera | `W` `A` `S` `D`, arrow keys, screen edges, or mouse wheel |
| Look around with the minimap | Left click or drag on the minimap |
| Give orders on the minimap | Right click on the minimap |
| Find an idle villager | `.` or the **Idle Villager** button |
| Jump to your Town Center | `Space` |
| Cancel, deselect, or open the menu | `Esc` |

---

## Gameplay reference

### Starting conditions
- 1 Town Center, 3 villagers, **200 wood** and **200 food**.
- Your Town Center is in the top-left of the map and the enemy's is in the bottom-right.

### Units

| Unit | Trained at | Cost | HP | Attack | Requires |
|---|---|---|---|---|---|
| Villager | Town Center | 50 food | 25 | 3 | — |
| Clubman | Barracks | 50 food | 45 | 7 | — |
| Axeman | Barracks | 55 food, 20 gold | 55 | 10 | Tool Age |

### Buildings

| Building | Cost | Size | Purpose | Requires |
|---|---|---|---|---|
| House | 30 wood | 1×1 | +4 population | — |
| Farm | 60 wood | 2×2 | 250 food, worked by one villager | — |
| Storage Pit | 120 wood | 2×2 | Drop-off point for wood, gold and stone | — |
| Barracks | 125 wood | 2×2 | Trains infantry | — |
| Town Center | 300 wood | 2×2 | Trains villagers, accepts all resources, advances ages, +4 population | — |
| Watch Tower | 150 stone | 1×1 | Shoots arrows at enemies within about 6 tiles | Tool Age |

### Ages

| Advance to | Cost | Time |
|---|---|---|
| Tool Age | 500 food | 40 s |
| Bronze Age | 800 food | 60 s |

### Rules to know
- Villagers carry up to **10** resources at a time and gather about 1 per second.
- Population is capped at **50**.
- Resource amounts: tree 100, berry bush 150, gold mine 400, stone mine 350.
- You **win** when every enemy building is destroyed and **lose** when all of yours are gone.

---

## Code structure

Everything is in `Aethoria.html`. The script is split into labeled sections:

| Section | Responsibility |
|---|---|
| `helpers` | DOM shortcut, canvas factory, `mulberry32` seeded RNG, 2D hash noise |
| `audio` | Tiny Web Audio synth (`tone`, `nz`) and the `SFX` table |
| `constants` | Map size, unit, building and age definitions, player colours |
| `pixel sprites` / `icons` | Code-drawn sprites for units, buildings, resources and HUD icons |
| `game state` | The `state` object, tile blocking, fog grids, entity registry `ENT` |
| `terrain` / `map generation` | Noise-based grass and dirt, forests, mines, starting bases |
| `pathfinding` | A\* on the tile grid, plus `nearestFree` fallback |
| `orders` / `unit update` | Command state machine for units: `move`, `gather`, `deposit`, `build`, `attack` |
| `buildings update` | Training queues and tower targeting |
| `AI` | Economy balancing, build order, age-ups, defence, attack waves |
| `fog` / `rendering` / `minimap` | Visibility, Y-sorted drawing, fog overlay, minimap |
| `HUD` / `command panel` | Resource bar, selection info, context-sensitive command buttons |
| `input` | Mouse, keyboard, minimap and overlay handlers |
| `main loop` | `requestAnimationFrame` loop with a timestep capped at 50 ms |

### Built with
- HTML5 Canvas 2D
- Web Audio API
- Plain JavaScript (ES2015+, strict mode)

---

## Browser support

Works in any current version of Chrome, Edge, Firefox or Safari. You need a mouse (it uses right click) and a keyboard. Touch controls aren't supported.

---

## Known limitations
- There's one map layout, one AI opponent and one difficulty level.
- The AI gets a small passive trickle of resources on top of what it gathers.
- There's no save/load; **Restart** reloads the page.
- There are no ranged units, walls or technologies beyond the age advances.

## Ideas for contributions
- Ranged units such as archers, and a stable
- Difficulty settings and random map seeds
- Save and load through `localStorage`
- Touch controls
- Unit formations and attack-move

---

## Disclaimer

This is a non-commercial project. All art and sound are generated in code.

## License

Add a license of your choice, for example [MIT](https://opensource.org/licenses/MIT).
