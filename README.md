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
- **Save and continue.** The game saves itself to your browser's `localStorage` every 30 seconds and at key moments. **Continue Game** on the title screen resumes exactly where you left off. You can also save by hand, load your last save, export a save to a file, import one, and reset all progress.
- **Upgrades.** Five technologies researched at the Storage Pit, Town Center and Barracks.
- **Missions, score and achievements.** A mission tracker guides you through a 12-step campaign. You earn points for your economy, army and conquests, and there's a persistent high score, an XP rank and 15 achievements.
- **Three difficulty levels** (Easy, Normal, Hard) that change the enemy's income, army size and attack timing.
- **Settings.** Master, effects and music volume, difficulty, three interface themes (Classic, Midnight, High contrast), interface size, scroll speed, edge scrolling, swapped mouse buttons, reduced motion, colour-blind-friendly team colours and longer on-screen messages. Settings are remembered between visits.
- **Touch and small screens.** You can play on phones and tablets, and the layout adapts to narrow and landscape screens.
- **Generative music.** A quiet ambient score is played by the Web Audio API alongside the sound effects.

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
| Find an idle villager (press again for the next one) | `.` or the **Idle** button |
| Jump to your Town Center | `Space` or the **Home** button |
| Cancel, deselect, or open the menu | `Esc` |
| Pause / resume | `P` |
| Quick save | `Ctrl` + `S` (`Cmd` + `S` on a Mac) |
| Mute / unmute | `M` |

### Touch controls

| Action | Gesture |
|---|---|
| Select a unit, building or resource | Tap |
| Give an order to the selected units (move, gather, attack, build, drop off, farm) | Tap the ground, resource, enemy or building site |
| Select all units of one type on screen | Double tap a unit |
| Box-select units | Long-press and then drag, or tap **Box select** and then drag |
| Scroll the camera | Drag with one or two fingers, or tap the minimap |
| Place a building | Choose it in the command panel, then tap the map. **Cancel build** stops placing |
| Clear the selection | **Deselect** button (top right) |

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

### Upgrades

| Upgrade | Researched at | Cost | Effect | Requires |
|---|---|---|---|---|
| Woodworking | Storage Pit | 100 food, 50 wood | Villagers chop wood 30% faster | — |
| Prospecting | Storage Pit | 120 food, 80 wood | Villagers mine gold and stone 30% faster | Tool Age |
| Domestication | Town Center | 150 food, 60 wood | Every farm holds 100 more food | Tool Age |
| Toolworking | Barracks | 120 food, 40 gold | Infantry deal +2 damage | Tool Age |
| Leather Armour | Barracks | 100 food, 30 gold | Infantry gain +15 hit points | Tool Age |

### Difficulty

| | Easy | Normal | Hard |
|---|---|---|---|
| Your starting wood and food | 300 / 300 | 200 / 200 | 200 / 200 |
| Enemy bonus income | ×0.35 | ×1 | ×1.8, plus extra starting resources |
| Enemy villager limit | 9 | 12 | 15 |
| Enemy attack waves | late and rare (about 80 s apart, 9+ soldiers) | about 50 s apart, 7+ soldiers | early and frequent (about 36 s apart, 6+ soldiers) |
| Score multiplier | ×0.75 | ×1 | ×1.5 |

### Score
You earn points for resources you drop off, units you train, buildings you complete, upgrades, age advances, missions, enemies you defeat and enemy buildings you raze. Destroying the enemy Town Center gives a large bonus, and a victory adds a speed bonus. Your final score is added to your XP, which raises your rank.

### Rules to know
- Villagers carry up to **10** resources at a time and gather about 1 per second.
- Population is capped at **50**.
- Resource amounts: tree 100, berry bush 150, gold mine 400, stone mine 350.
- You **win** when every enemy building is destroyed and **lose** when all of yours are gone.

---

## Saving and progress

Everything is stored in your browser's `localStorage` under keys that start with `aethoria.`:

| Key | Contents |
|---|---|
| `aethoria.save.v1` | The game in progress: every unit, building, resource, order, path, training and research queue, projectile, the fog of war, the AI's state, camera, selection, score, statistics and missions |
| `aethoria.save.v1.bak` | The previous good save, kept as a fallback |
| `aethoria.save.quarantine` | The last save that failed validation, kept only so it isn't lost silently |
| `aethoria.profile.v1` | High score, XP and rank, achievements and lifetime statistics |
| `aethoria.settings.v1` | Your settings |

- **When it saves.** When a game starts, then every 30 seconds of play. It also saves after age-ups, missions, achievements, upgrades, resource milestones, completed or lost buildings and the fall of the enemy Town Center. It saves when you pause, when the window loses focus or is hidden, and when the page closes. Bursts of events are combined into one write. The indicator in the top bar shows *Autosaving…*, *Saved ✓* or *Save failed*.
- **Continue.** The title screen shows **Continue Game**, with a summary, only when a valid save exists. Choosing it restores the whole session.
- **Protection.** Every record carries a checksum and a schema version, and is fully validated before it's loaded, and again before it's written. If the latest save is damaged, the backup is restored and you see *Save recovered*. If both copies are damaged, they're removed, you get a message, and the game starts clean. It never crashes. Invalid settings fall back to defaults field by field.
- **Finished games.** When you win or lose, the game in progress is removed from storage, because a finished game can't be continued. Your score, XP, achievements and statistics are kept.
- **Export and import.** In the pause menu or Settings, **Export Save** downloads a `.json` file. **Import Save** (on the title screen or in Settings) validates a file before it replaces your current save.
- **Reset progress.** This button is on the title screen and in Settings, and asks you to confirm first. It deletes the saved game, the backup and your profile. Your settings are kept.
- If the browser blocks storage (for example, in some private modes), the game still runs, warns you, and keeps progress only until you close the tab.

---

## Code structure

Everything is in `Aethoria.html`. The script is split into labeled sections:

The script is a single `<script type="module">`, so nothing is added to `window`. The only exception is the optional `?debug` URL flag, which exposes `window.__aethoria` for testing.

| Section | Responsibility |
|---|---|
| `helpers` | DOM shortcut, canvas factory, `mulberry32` seeded RNG, 2D hash noise, `cyrb53` checksum, bit packing |
| `config` | `CONFIG` (timings, storage keys, limits) and the `DIFFICULTY` table |
| `persistence` | `StorageManager` (`saveGame`, `loadGame`, `autoSave`, `saveSettings`, `loadSettings`, `validateSave`, `hasSaveData`, `resetSave`, `exportSave`, `importSave`), `Settings`, `Profile` |
| `audio` | `AudioManager` (master, effects and music buses), the generative `MusicPlayer` and the `SFX` table |
| `game data` / `progression tables` | Unit, building, upgrade and age definitions, score values, achievements, missions |
| `pixel sprites` / `icons` | Code-drawn sprites for units, buildings, resources and HUD icons |
| `game state` | The `state` object, tile blocking, fog grids, entity registry `ENT` |
| `terrain` / `map generation` | Noise-based grass and dirt, forests, mines, starting bases |
| `pathfinding` | A\* on the tile grid, plus `nearestFree` fallback |
| `orders` / `unit update` | Command state machine for units: `move`, `gather`, `deposit`, `build`, `attack` |
| `buildings update` | Training queues and tower targeting |
| `AI` | Economy balancing, build order, age-ups, defence, attack waves |
| `fog` / `rendering` / `minimap` | Visibility, Y-sorted drawing, fog overlay, minimap |
| `HUD` / `command panel` | Resource bar, selection info, context-sensitive command buttons |
| `progression` | Score, milestones, achievements, missions and debounced save requests |
| `serializer` | `GameSerializer.serialize` / `validate` / `restore`, which convert between the live world and plain JSON |
| `game controller` / `UI` | New game, continue, pause, restart and quit; the overlay stack, confirm dialog, settings, records and end screen |
| `input` | Mouse, touch, keyboard and minimap handlers, and the lifecycle autosave hooks |
| `main loop` | `requestAnimationFrame` loop with a timestep capped at 50 ms |

### Built with
- HTML5 Canvas 2D
- Web Audio API
- Plain JavaScript (ES2015+, strict mode)

---

## Browser support

Works in any current version of Chrome, Edge, Firefox or Safari, with a mouse and keyboard or with touch. The interface-size setting uses CSS `zoom`, which needs Firefox 126 or later.

---

## Known limitations
- There's one map layout and one AI opponent. The AI doesn't research upgrades.
- The AI gets a passive trickle of resources on top of what it gathers, scaled by difficulty.
- There's one save slot per browser. Use export and import to keep more.
- There are no ranged units, walls or zoom.

## Ideas for contributions
- Ranged units such as archers, and a stable
- Random map seeds and more map layouts
- Several save slots
- Unit formations and attack-move
- Pinch-to-zoom on touch screens

---

## Disclaimer

This is a non-commercial project. All art and sound are generated in code.
