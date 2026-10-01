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
- **Combat.** Infantry, ranged units and cavalry, plus watch towers that shoot arrows. A counter system decides who beats whom.
- **Ranged warfare.** Archers, skirmishers and composite archers fire real arrows and javelins. Shots arc through the air and follow their target. They can miss at long range, and a building in the way blocks them. Archers step back from melee attackers while they reload.
- **Cavalry.** Scout cavalry, horsemen and heavy cavalry are fast and see far. They charge: an attack begun 3 or more tiles away hits 50% harder. Riders take straighter, smoother paths and take up more room than foot soldiers.
- **Formations.** Line, Square and Wedge. Group moves keep the shape, with infantry in front, ranged units behind and riders at the tip of a wedge.
- **AI opponent.** It runs its own economy, builds houses, barracks, an archery range, a stable and towers, advances through the ages and defends its base. It trains a mixed army weighted to counter yours. It attacks in waves: the army gathers in formation, then the infantry go in with the archers behind them while the riders swing round a flank.
- **Fog of war.** Unexplored areas are black, and areas you've explored but can't currently see are dimmed.
- **Minimap.** Click on it to move the camera, or right-click to send orders.
- **A\* pathfinding** on a 64×64 tile grid, with 8-direction movement and no corner-cutting.
- **Procedural pixel art.** Units are drawn from ASCII sprite maps, with idle, walk, attack and death animations. Trees, mines, buildings and terrain use seeded noise.
- **Synthesized sound.** Chopping, mining, combat, the building-complete bell and the age-up fanfare are all generated with the Web Audio API.
- **Classic interface.** A resource bar at the top, and a bottom panel with the minimap, info panel, command grid and tooltips.
- **Save slots.** Five independent save slots and three rotating autosaves, stored in your browser's `localStorage`. Each slot shows a screenshot, level, completion, play time, difficulty, resources, location and when it was saved. You can load, overwrite, delete, rename, copy, export and import saves, and damaged saves can be restored from a backup.
- **Upgrades.** Eleven technologies researched at the Storage Pit, Town Center, Barracks, Archery Range and Stable.
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
| Quick save to your current slot | `Ctrl` + `S` (`Cmd` + `S` on a Mac) |
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

| Unit | Trained at | Cost | HP | Attack | Range | Notes | Requires |
|---|---|---|---|---|---|---|---|
| Villager | Town Center | 50 food | 25 | 3 | melee | Gathers and builds | — |
| Clubman | Barracks | 50 food | 45 | 7 | melee | Infantry | — |
| Axeman | Barracks | 55 food, 20 gold | 55 | 10 | melee | Heavy infantry | Tool Age |
| Archer | Archery Range | 40 food, 25 wood | 35 | 5 | 6 tiles | Fires every 1.5 s. Strong against villagers and infantry, weak in melee | Tool Age |
| Skirmisher | Archery Range | 45 food, 35 wood | 40 | 4 | 5 tiles | Javelins. +50% against archers | Tool Age |
| Composite Archer | Archery Range | 50 food, 40 wood, 25 gold | 45 | 8 | 7 tiles | Tougher, harder-hitting archer | Bronze Age |
| Scout Cavalry | Stable | 80 food | 65 | 6 | melee | Very fast, 12-tile vision | Bronze Age |
| Horseman | Stable | 100 food, 40 gold | 90 | 12 | melee | Fast. +25% against ranged units, 1 armour | Bronze Age |
| Heavy Cavalry | Stable | 120 food, 70 gold | 140 | 18 | melee | Tank. +50% against infantry, 2 armour | Bronze Age and Horse Breeding |

### Buildings

| Building | Cost | Size | Purpose | Requires |
|---|---|---|---|---|
| House | 30 wood | 1×1 | +4 population | — |
| Farm | 60 wood | 2×2 | 250 food, worked by one villager | — |
| Storage Pit | 120 wood | 2×2 | Drop-off point for wood, gold and stone | — |
| Barracks | 125 wood | 2×2 | Trains infantry | — |
| Archery Range | 175 wood | 2×2 | Trains ranged units, researches archery upgrades. 400 HP | Tool Age |
| Stable | 200 wood, 100 food | 2×2 | Trains cavalry, researches cavalry upgrades. 500 HP | Bronze Age |
| Town Center | 300 wood | 2×2 | Trains villagers, accepts all resources, advances ages, +4 population | — |
| Watch Tower | 150 stone | 1×1 | Shoots arrows at enemies within about 6 tiles. +50% against light cavalry | Tool Age |

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
| Fletching | Archery Range | 100 food, 50 wood | Ranged units +1 attack and +1 range | Tool Age |
| Bodkin Arrow | Archery Range | 150 food, 60 gold | Ranged units +2 attack | Bronze Age, Fletching |
| Composite Bow | Archery Range | 150 wood, 80 gold | Ranged units reload 20% faster | Bronze Age |
| Horse Breeding | Stable | 150 food, 100 wood | Cavalry +20 hit points. Unlocks Heavy Cavalry | Bronze Age |
| Steel Horseshoes | Stable | 100 food, 50 gold | Cavalry move 15% faster | Bronze Age |
| Cavalry Armour | Stable | 120 food, 80 gold | Cavalry +2 armour (each hit they take deals 2 less) | Bronze Age |

### Counters

Each hit is multiplied by the attacker's bonus against the target's class, then the target's armour is subtracted. A hit always deals at least 1.

| Attacker | Strong against |
|---|---|
| Archers (all ranged units) | Villagers ×1.5, infantry ×1.25. Only ×0.5 against buildings, and half damage at point-blank range |
| Skirmisher | Archers and other ranged units ×1.5 |
| Infantry | Cavalry ×1.25 |
| Cavalry | Ranged units ×1.15 (Horseman ×1.25), buildings ×0.75 |
| Heavy Cavalry | Infantry ×1.5 |
| Watch Tower | Light cavalry (scouts, horsemen) ×1.5 |

### Ranged combat, cavalry and formations
- **Projectiles.** Arrows and javelins fly in an arc and follow their target. The chance to hit is 97% up to half range and falls to about 65% at maximum range. It's 10% lower against a moving target. A miss lands harmlessly beside the target. Buildings between the shooter and the target block the shot, so the shooter moves until it has a clear line.
- **Kiting.** While reloading, a ranged unit steps back from melee attackers that come within about 2 tiles, then stops to shoot again.
- **Charge.** Cavalry that start an attack on a unit from 3 or more tiles away move 35% faster until the first hit, and that hit deals 50% more damage.
- **Formations.** With soldiers selected, the command panel offers Line (best for archers), Square (infantry) and Wedge (cavalry). Choosing one re-forms the group facing the enemy. Group moves then keep the shape at the pace of the slowest member. Choose it again to march loosely.
- **Vision.** Villagers and infantry see 6 tiles, skirmishers 7, archers 8, composite archers 9 and scouts 12.

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
| `aethoria.slot.1` … `aethoria.slot.5` | The five manual save slots |
| `aethoria.autosave.1` … `aethoria.autosave.3` | The three rotating autosaves |
| `aethoria.backup.slot.1` … `aethoria.backup.slot.5` | A slot's previous save, kept only while that slot is being overwritten |
| `aethoria.save.quarantine` | The last save that failed validation, kept only so it isn't lost silently |
| `aethoria.profile.v1` | High score, XP and rank, achievements and lifetime statistics |
| `aethoria.settings.v1` | Your settings |

Each save is one JSON record. It holds the slot name, save time, play time, player level, completion percentage, difficulty, age, score, resources, location on the map, a small screenshot and the game version, plus the whole game: every unit, building, resource, order, path, training and research queue, projectile, the fog of war, the AI's state, camera, selection, score, statistics and missions. A checksum covers the entire record.

- **Save slots.** The five slots are independent, and nothing writes to one without you asking. **Save Game** in the pause menu opens the save screen. Pick a slot, confirm if it already holds a save, and you get a confirmation message. `Ctrl` + `S` and **Quick Save** save straight to the slot your game belongs to. **Save & Quit** saves there too.
- **Autosaves.** The game autosaves every 30 seconds of play. It also autosaves after age-ups, missions, achievements, upgrades, resource milestones, completed or lost buildings and the fall of the enemy Town Center, and when you pause, switch away or close the page. Autosaves rotate through three slots (1 → 2 → 3 → 1), so the two older copies are always intact. They never overwrite a manual slot. An unchanged game isn't written again, and routine autosaves are spaced at least 8 seconds apart. The indicator in the top bar shows *Autosaving…*, *Saved ✓* or *Save failed*.
- **New game.** Choose a difficulty, a slot (the first empty one is picked for you) and a name. You can also start a new game from any empty slot's **New Game** button.
- **Continue and load.** **Continue** on the title screen and **Load Game** in the pause menu open the save screen. It lists every slot and autosave with its details and marks the most recent one. A save is never loaded automatically. You always pick it.
- **Managing saves.** **Saved Games** (on the title screen or in Settings) opens the same screen. From there you can load, overwrite, delete, rename, copy (to another slot, including from an autosave), export and import saves.
- **Backups.** Before a slot is overwritten, its current save is copied to a backup. The new save is written, read back and checked. The backup is then removed, or put back if anything failed.
- **Damaged saves.** Every save is fully validated when it's listed, loaded and written. A damaged slot is marked with *Save Slot 2 appears corrupted*. If a backup survived (for example, when the page closed in the middle of a save), you're offered *Restore from backup?*. Otherwise you can delete the save or save over it. The game never crashes on bad data, and invalid settings fall back to defaults field by field.
- **Finished games.** Winning or losing doesn't delete any save, so earlier saves of that campaign can still be loaded. Your score, XP, achievements and statistics are recorded when the game ends.
- **Export and import.** **Export** downloads a slot or autosave as a `.json` file. **Import** reads a `.json` file, validates it, and then puts it in the slot you chose, after you confirm if that slot is in use. Saves exported by Aethoria 1.1 can be imported too.
- **Upgrading from 1.1.** On the first start, your old single save (`aethoria.save.v1`, or its backup if that's the only good copy) is moved into the first free slot.
- **Reset progress.** This button is on the title screen and in Settings, and asks you to confirm first. It deletes every slot, autosave and backup, and your profile. Your settings are kept.
- If the browser blocks storage (for example, in some private modes), the game still runs, warns you, and keeps progress only until you close the tab.

---

## Code structure

Everything is in `Aethoria.html`. The script is split into labeled sections:

The script is a single `<script type="module">`, so nothing is added to `window`. The only exception is the optional `?debug` URL flag, which exposes `window.__aethoria` for testing.

| Section | Responsibility |
|---|---|
| `helpers` | DOM shortcut, canvas factory, `mulberry32` seeded RNG, 2D hash noise, `cyrb53` checksum, bit packing |
| `config` | `CONFIG` (timings, storage keys, limits) and the `DIFFICULTY` table |
| `persistence` | `StorageManager` (guarded `localStorage` access, settings, profile), `SaveSlotManager` (`createSlot`, `saveToSlot`, `loadFromSlot`, `deleteSlot`, `copySlot`, `renameSlot`, `getSlotInfo`, `listSlots`, `exportSlot`, `importSlot`, plus `autoSave`, `restoreFromBackup` and `parse` for validation), `Settings`, `Profile` |
| `audio` | `AudioManager` (master, effects and music buses), the generative `MusicPlayer` and the `SFX` table |
| `game data` / `progression tables` | Unit, building, upgrade and age definitions, the counter table (`COUNTERS`), projectile kinds, formations, score values, achievements, missions |
| `pixel sprites` / `icons` | Code-drawn sprites for units, buildings, resources and HUD icons |
| `game state` | The `state` object, tile blocking, fog grids, entity registry `ENT` |
| `terrain` / `map generation` | Noise-based grass and dirt, forests, mines, starting bases |
| `pathfinding` | A\* on the tile grid, plus `nearestFree` fallback |
| `orders` / `unit update` | Command state machine for units: `move`, `gather`, `deposit`, `build`, `attack`. Includes ranged combat (range, line of sight, kiting), cavalry charges, the counter system (`dmgMult`, `hitDamage`) and soldier collision |
| `buildings, training & research` | Training queues (`TRAINS`), upgrade effects (`TECHS`), tower targeting |
| `projectiles` | The `Projectiles` manager: `fire`, `update` (flight, target tracking, hits and misses) and `draw` (arcs and shadows) |
| `formations` | `formationSlots` and `formationMove` for Line, Square and Wedge |
| `AI` | Economy balancing, build order, age-ups, upgrades, an army mix that counters yours, defence, and attack waves that gather in formation and flank with cavalry |
| `fog` / `rendering` / `minimap` | Visibility, Y-sorted drawing, fog overlay, minimap |
| `HUD` / `command panel` | Resource bar, selection info, context-sensitive command buttons |
| `progression` | Score, milestones, achievements, missions and debounced save requests |
| `serializer` | `GameSerializer.serialize` / `validate` / `restore`, which convert between the live world and plain JSON |
| `game controller` / `UI` | New game, load, pause, restart and quit; the overlay stack, confirm / prompt / choice dialog, save-slot screen, settings, records and end screen |
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
- There's one map layout and one AI opponent. Of the upgrades, the AI researches only Fletching and Horse Breeding.
- The AI gets a passive trickle of resources on top of what it gathers, scaled by difficulty.
- Saves live in one browser. Use export and import to move them to another browser or device.
- There are no walls, siege units or zoom. The counter table already has a siege row, and the projectile manager supports spears and fire arrows, so siege units only need data and art.

## Ideas for contributions
- A siege workshop with rams and stone throwers
- Random map seeds and more map layouts
- Attack-move and patrol orders
- Pinch-to-zoom on touch screens

---

## Disclaimer

This is a non-commercial project. All art and sound are generated in code.
