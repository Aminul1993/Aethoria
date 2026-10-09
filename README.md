# Aethoria

A small real-time strategy game *Aethoria*, written as **one HTML file** with plain JavaScript and the Canvas 2D API. It has no dependencies, no build step and no image files. All sprites, terrain, icons and sound effects are generated in code when the page loads.

> Gather resources, grow your town, advance through the ages, and destroy every enemy building.

**[Play the live demo](https://aminul1993.github.io/Aethoria/)**

---

## Quick start

Download `index.html` and open it in any modern browser. You can double-click the file, or drag it into a browser window. You don't need to install anything, run a server or build anything.

The only network request is for the **Cinzel** and **Rajdhani** fonts from Google Fonts. If you're offline, the game still runs and uses fallback fonts.

---

## Features

- **Economy.** Villagers gather wood, food (berries, deer and farms), gold and stone, and carry it back to a Town Center or Storage Pit. Fishing boats bring in fish.
- **Ships and crossing water.** Build a Dock on deep water beside the shore. It launches fishing boats and transport ships. Send land units anywhere, even to another island, and they find their own way across. They walk to the shore (your Dock if one is near), a free transport comes for them, they board, cross and land on the far shore, then carry on with their order. A transport holds 10 slots: 1 for each villager or foot soldier, 2 for a rider, and a siege engine's population (3 to 5). Big groups get several ships, which sail as a convoy and land side by side. Ships steer clear of each other and of the shore. Moored at your Dock, they're repaired. A transport sunk with units aboard loses them all. Build a Storage Pit on an island you work, or every load sails home. The AI builds docks, fishes, takes islands and invades by sea.
- **Naval combat.** The Dock builds five warships: galleys, war galleys, fire ships, ballista ships and cannon ships. Each works down its own target list. War galleys pierce armour, fire ships set the water alight, ballista ships hunt war galleys and cannon ships, and cannon ships shell docks, towers and castles from the sea. Ships turn at their own rate, and sink with wreckage left floating. **Patrol** sends warships back and forth. Right-click one of your ships to escort it. Seven Dock upgrades include Elite War Galley. The AI builds the fleet that best counters yours and sends it to hunt, escort, guard its fishing boats, blockade your Dock or patrol. Battles are deterministic: a save plays out exactly as the live game would have.
- **Procedural maps.** 17 map types (Classic, Plains, Forest, Desert, Island, Mountain, Highlands, Badlands, Riverlands, Archipelago, Canyon, Frozen Tundra, Volcanic, Oasis, Jungle, Continental and Mixed Biomes) in four sizes from 48×48 to 128×128 tiles, with three resource levels. A seed, which can be any word or number, makes the whole world: the same seed always gives the same map. The New Game screen previews the map, picks random seeds, copies a shareable map code and keeps favourites. Terrain comes from layered noise: rivers run downhill from the high ground to the sea or the map's edge with fords to cross them, basins fill into lakes, and mountains, hills, forests, deserts, snow, marsh and lava take their share of each map type. Both towns start the same distance from the centre with the same starting resources. Gold, stone, deer and berries are shared out in matching pairs, and every map is checked so the towns can always reach each other and every resource. Landmarks hold extra resources and are announced when you discover them.
- **Construction.** Several villagers can build the same site together, and each building shows its progress.
- **Three ages.** Advance from the Stone Age to the Tool Age and then the Bronze Age to unlock stronger units and buildings.
- **Combat.** Infantry, ranged units and cavalry, plus towers and castles that shoot arrows. A counter system decides who beats whom.
- **Ranged warfare.** Archers, skirmishers and composite archers fire real arrows and javelins. Shots arc through the air and follow their target. They can miss at long range, and a building in the way blocks them. Archers step back from melee attackers while they reload.
- **Cavalry.** Scout cavalry, horsemen and heavy cavalry are fast and see far. They charge: an attack begun 3 or more tiles away hits 50% harder. Riders take straighter, smoother paths and take up more room than foot soldiers.
- **Fortifications.** Palisades, timber, stone and curtain walls that you drag across the map and that join up by themselves into corners, T-junctions and crossings. Lay a heavier wall over a lighter one to rebuild it in place. Gates open for your units and stay shut to the enemy, and you can lock them. A Gatehouse also shoots and holds a garrison. Boiling oil set on a wall pours on enemies who attack beside it. Moats, dug in lines or rings or wrapped round your walls automatically, slow foot soldiers to half speed (a reinforced moat to a quarter) and stop riders and siege engines. Drawbridges carry your army across, lowering for your units and rising when the enemy comes or when they're hit. Hidden spike, fire and pit traps spring on the first enemy to step on them. Guard Towers upgrade one at a time to Watch and Fortified Towers. From there a tower becomes a Ballista Tower, or grows into a 2×2 Keep. A Keep grows into a 3×3 Castle or rises into an Imperial Keep, and either of those grows into a 4×4 Citadel. Bastions hurl boulders and anchor your walls. Towers, gatehouses, bastions, keeps, castles and citadels can be garrisoned; archers inside add arrows. The Castle fires 4-arrow volleys and the Citadel 6. Both train three elite units and project territory that heals your units, makes them fight harder and speeds production. A town the enemy can't walk into takes less damage. Units walled off from their target break through the wall or gate in the way. Villagers repair damaged buildings, and a horn sounds when enemies come near your town. Every defence is data: a new one is one entry (see Code map).
- **Siege.** The Siege Workshop builds five engines: battering rams, stone throwers, trebuchets, ballistas and cannons. It also researches six siege upgrades. Every engine has a role and a target list. Rams breach gates, then walls, towers and castles. Stone throwers lob boulders at walls, towers and castles, then at packed infantry. Trebuchets hurl huge boulders 18 tiles at any structure. Ballistas pick off siege engines, riders and ships. Cannons batter fortifications and engines with flat shots. Siege hits gates ×3, walls ×2.5, towers ×2, castles ×1.75, other engines ×1.5 and soldiers only ×0.75. Every engine but the ram must set up before it fires and pack up before it moves; how long each takes is its own. Engines take 3 to 5 population. Arrows barely scratch them; infantry and cavalry break them, and fire burns rams badly. A new engine is just two data entries (see Code map).
- **Orders.** Move, Attack, Attack-Move, Patrol and Guard, from buttons or the `A` (attack-move), `P` (patrol) and `G` (guard) hotkeys. Attack-move marches on a point and fights every enemy met on the way, then carries on, across the water by ferry if need be. Patrol works for every unit, villagers and boats included: soldiers and warships fight what comes into sight, while villagers and unarmed boats turn away from danger. Guard covers a spot, a building or one of your units (escort). One order framework runs them for land units and ships alike.
- **Formations.** Line, Square and Wedge. Group moves keep the shape, with infantry in front, ranged units and siege engines behind and riders at the tip of a wedge.
- **AI opponent.** It runs its own economy, builds houses, barracks, an archery range, a stable, a siege workshop and towers, advances through the ages and defends its base. Where there's sea it builds a Dock and fishing boats. When the sea stands between you, it builds transports and lands its army on your shore. It builds warships to escort its crossings and guard its fishing boats. Once you sail warships it matches your fleet with the ships that counter it best, and gives the fleet priority over new soldiers until it does. It hunts your ships when they come near or when it outnumbers you, and blockades your Dock with three or more. When its island runs out of gold or stone, it ships villagers to other islands and builds a storage pit there. It fortifies by a plan, one step at a time: a palisade round its town once it has 10 villagers, with a gate in each side, rebuilt as a timber wall in the Tool Age once it has a barracks. In the Bronze Age it digs a moat one tile outside the wall with a drawbridge in front of each gate, then puts gatehouses in place of its gates and adds a Keep, a Bastion on a corner, an Imperial Keep, a Castle and finally a Citadel. It grows keeps, castles and citadels out of its towers where there's room, and builds them outright (the castle on the side facing you) where there isn't. It keeps towers on its corners and upgrades them. It repairs every kind of damaged fortification, ahead of laying more wall or moat, sends raided villagers into its towers until the danger passes, and keeps its army just inside the gate that faces you between attacks. It trains a mixed army weighted to counter yours, plus rams and stone throwers (more stone throwers if you build towers), and researches siege upgrades. It attacks in waves: the army gathers in formation, then the siege engines go for the target with two infantry escorts each, the other infantry and the archers attack-move on it, fighting whatever meets them on the way, and the riders swing round a flank to hit archers, stone throwers and villagers. Against raiders at home its army attack-moves too. A border scout patrols round its towers and castle, and a rider patrols the gate facing you. An army with siege goes for your defences first. If you've built 3 or more towers, the AI saves up for the Bronze Age and holds its attacks until it has siege, for up to 4 minutes.
- **Fog of war.** Unexplored areas are black, and areas you've explored but can't currently see are dimmed.
- **Minimap.** Click or tap it to look around, double-click or double-tap to zoom in on that spot, and right-click or long-press to send your selected units there.
- **Zoom.** The camera zooms from 0.5× to 3× with smooth, animated steps, and the spot under the cursor or between your fingers stays put. There are four tactical layers: Close, Medium, Far and Strategic. At Strategic zoom units become team-coloured icons. Your last zoom is remembered between visits.
- **A\* pathfinding** on the tile grid (48×48 to 128×128), with 8-direction movement and no corner-cutting. Units wade through fords and walk round mountains and deep water. Ships use their own water graph, and a hybrid router joins the two for any trip that has to cross water.
- **Painted graphics.** Every picture is painted in code when the page loads, with gradients, soft shadows and light from the north-west. People are posed figures (six-frame walk, breathing idle, a strike or a drawn bow) in their side's colours; riders sit horses with a gait and barding; siege engines set up, loose and pack away. Buildings have thatch, timber, plaster and dressed stone, with banners in their owner's colours. The ground is painted from seeded noise: blended grass, earth and sand, lit hills, craggy ranges with snow on the peaks, coasts with foam lines and deepening water, and lava with glowing veins, with tufts, flowers, pebbles and reeds drawn over it.
- **Atmosphere.** Soft-edged fog of war, cloud shadows drifting over the land, warm light, a vignette and film grain, glints moving on the water, chimney smoke and birds. Settings can turn the atmosphere off.
- **Synthesized sound.** Chopping, mining, combat, the building-complete bell and the age-up fanfare are all generated with the Web Audio API.
- **Interface.** A gold-on-dark resource bar at the top (with the idle villager count, score and age), a mission card, and a bottom panel with the minimap, info panel, command grid and tooltips. Hovering a unit, building or resource names it; selections are marked with gold rings and corner brackets.
- **Save slots.** Five independent save slots and three rotating autosaves, stored in your browser's `localStorage`. Each slot shows a screenshot, level, completion, play time, difficulty, resources, location and when it was saved. You can load, overwrite, delete, rename, copy, export and import saves, and damaged saves can be restored from a backup.
- **Upgrades.** Eleven technologies researched at the Storage Pit, Town Center, Barracks, Archery Range and Stable.
- **Missions, score and achievements.** A mission tracker guides you through a 12-step campaign. You earn points for your economy, army and conquests, and there's a persistent high score, an XP rank and 15 achievements.
- **Three difficulty levels** (Easy, Normal, Hard) that change the enemy's income, army size and attack timing.
- **Settings.** Master, effects and music volume, difficulty, three interface themes (Gold and ember, Midnight, High contrast), the atmosphere, automatic interface fitting and UI scale, scroll speed, edge scrolling, swapped mouse buttons, touch controls, one-finger drag, pinch zoom, zoom and gesture sensitivity, touch feedback, reduced motion, colour-blind-friendly team colours and longer on-screen messages. Settings are remembered between visits.
- **Touch screens.** The game is fully playable on phones, tablets and touch laptops. Pinch to zoom, use two fingers to scroll, long-press for a command menu, and tap with three fingers for the strategic overview. Touch mode switches on automatically and makes every control at least 48×48 px. Hover tooltips become tap-to-view details and long-press information cards. On a phone held sideways, the minimap and commands move to a side column. The interface scales to the screen, and the battlefield renders at the screen's pixel density.
- **Generative music.** A quiet ambient score is played by the Web Audio API alongside the sound effects.

---

## Controls

| Action | Input |
|---|---|
| Select a unit, building or resource | Left click |
| Box-select units | Left drag |
| Select all units of one type on screen | Double click |
| Move / gather / attack / help build / drop off | Right click |
| Repair your damaged building (villagers), or garrison a tower or castle (others) | Right click the building |
| Send units across water | Right click anywhere on the other shore: they walk to the shore and board a transport by themselves |
| Board a particular transport | Select land units, right click your transport |
| Put a transport's cargo ashore | Right click the land with the transport selected, or press **Unload** |
| Fish | Select fishing boats, right click a shoal of fish |
| Attack with warships | Right click an enemy ship or Dock (or whatever else is on the ship's target list) |
| Escort one of your ships | Select warships, right click the ship to escort |
| Attack-move | Select units, press `A` (or **Attack-Move**), then left click where to go. Right click or `Esc` cancels |
| Patrol | Select units, press `P` (or **Patrol**), then left click the far end of the patrol |
| Guard a spot, a building or a unit (escort) | Select units, press `G` (or **Guard**), then left click what to guard |
| Attack, or move, by button | **Attack** then left click an enemy (open ground: attack-move there); **Move** then left click a place |
| Place a building | Choose it in the command panel, then left click (right click cancels). Walls, gates, towers, castles, moats and traps are on the three **Defences** pages (tabs switch between them) |
| Lay a wall or moat | Choose it, then drag from where it starts to where it ends (or click both ends). **Moat ring**: drag corner to corner |
| Moat round your walls | Select wall and gate segments, then **Moat around** |
| Scroll the camera | `W` `A` `S` `D`, arrow keys, screen edges, or drag with the middle mouse button (with units selected, `A` gives attack-move: scroll left with the arrow key) |
| Zoom in and out at the cursor | Mouse wheel |
| Fine zoom | `Ctrl` + mouse wheel (a trackpad pinch works too) |
| Zoom in / out | `+` / `−`, or the zoom buttons in the bottom-right corner |
| Reset the zoom to 1× | `Home` |
| Strategic overview (press again to return) | `Z` |
| Step through the zoom levels | Click the zoom level between − and + |
| Look around with the minimap | Left click or drag on the minimap |
| Zoom in on an area | Double click on the minimap |
| Give orders on the minimap | Right click on the minimap |
| Find an idle villager (press again for the next one) | `.` or the **Idle** button |
| Jump to your Town Center | `Space` or the **Home** button |
| Cancel, deselect, or open the menu | `Esc` |
| Pause / resume | `P` with nothing selected (with units selected, `P` is patrol), or `Pause` |
| Quick save to your current slot | `Ctrl` + `S` (`Cmd` + `S` on a Mac) |
| Mute / unmute | `M` |

### Touch controls

| Action | Gesture |
|---|---|
| Select a unit, building or resource | Tap |
| Give an order to the selected units (move, gather, attack, build, drop off, farm, repair, garrison, cross water, board, unload, fish) | Tap the ground, resource, enemy, building site, your own building or your transport |
| Select all units of one type on screen | Double tap a unit |
| Box-select units | Drag one finger |
| Command menu, with an information card for whatever is under your finger | Long-press the map |
| Scroll the camera | Drag with two fingers |
| Zoom | Pinch: spread two fingers to zoom in and bring them together to zoom out |
| Strategic overview (again to zoom back in where you tapped) | Tap with three fingers |
| Look around with the minimap | Tap or drag on the minimap |
| Zoom in on an area | Double tap on the minimap |
| Send the selected units somewhere | Long-press on the minimap |
| Read a command's information card without using it | Long-press a command button |
| See what a resource is for | Tap its counter in the top bar |
| Place a building | Choose it in the command panel, then tap the map. **Cancel build** stops placing |
| Lay a wall or moat | Choose it, tap where it starts, then tap where it ends (**Moat ring**: tap two opposite corners) |
| Clear the selection | **Deselect** button (top right) |

Four or more fingers are ignored. A gesture never steps down to fewer fingers: after a pinch, a finger left on the screen does nothing until you lift it. If you'd rather scroll with one finger, set **Settings → Touch & zoom → One-finger drag** to *Scrolls the map*. A **Box select** button then appears for drawing a selection box.

### Zoom levels

| Layer | Zoom | What you see |
|---|---|---|
| Close | 1.5× – 3× (button: 2×) | Units in detail |
| Medium | 0.87× – 1.5× (button: 1×) | Standard play |
| Far | 0.62× – 0.87× (button: 0.75×) | Army management. Shadows and idle animations are left out |
| Strategic | 0.5× – 0.62× (button: 0.5×) | Map overview. Units become icons: ● villager, ■ infantry, ▲ ranged, ◆ cavalry, ▬ siege |

### Touch & zoom settings

| Setting | Default | Effect |
|---|---|---|
| Touch controls (mobile mode) | Automatic | Turns on for phones and tablets and after your first touch. *Always on* and *Off* override it |
| One-finger drag | Draws a selection box | Or *Scrolls the map* |
| Enable pinch zoom | On | Off: two fingers only scroll |
| Zoom sensitivity | 100% | How far a pinch, a wheel step or a key press zooms (50–200%) |
| Gesture sensitivity | 100% | Higher values react to shorter drags and shorter long-presses (50–200%) |
| Touch feedback | On | A ripple where your finger lands, and a short vibration on orders |
| Fit the interface to this screen automatically | On | Scales the interface from the screen size: a little smaller on phones, 10% larger on touch tablets, larger on big monitors |
| UI scale | 100% | Your own scale on top of the automatic fit (80–140%) |

---

## Gameplay reference

### Starting conditions
- 1 Town Center, 3 villagers, **200 wood** and **200 food**.
- On the Classic map your Town Center is in the top-left and the enemy's is in the bottom-right. On the other map types the two towns face each other across the centre, in a direction drawn from the seed.
- On generated maps each town starts with the same resources nearby, laid out the same way: 6 berry bushes, 4 deer, two woods of 14 and 10 trees, 4 gold and 3 stone.

### Maps

**New Game** sets up the map as well as the difficulty, slot and name. A preview shows the whole map in its key colours (green grass and forest, yellow desert, blue water, light blue fords, grey mountains, brown hills, white snow), with gold, stone and food as dots, the landmarks as stars and both towns as red markers (**1** is yours). Underneath it are the map's land and water shares and its resource counts.

- **Seed.** Any word or number up to 24 characters. Letters are upper-cased and spaces become dashes. A number of up to 9 digits is used as it is, and anything else is hashed into one. The same seed, type, size and resources always make exactly the same map. **Random** picks a fresh seed, such as `4817305` or `IRON-HOLD-42`. New Game opens on a fresh random seed, with the map type, size and resources you last played. **Play again** on the end screen keeps the same map.
- **Map code.** **Copy code** copies a code such as `IRON-HOLD-42/mountain/large/high` (seed / type / size / resources). Paste one into the seed box to set all four. The pause menu shows the current map and can copy its code too.
- **Favourites.** **☆ Favourite** stars the current settings, up to 20 maps. Click a favourite to bring it back, and ✕ removes it. Favourites are kept when you reset progress.
- **Size.** Small 48×48, Medium 64×64 (the default), Large 96×96, Huge 128×128 tiles.
- **Resources.** Sparse, Normal or Rich: about 0.65×, 1× or 1.45× the scattered gold, stone, deer and berries, with fewer or more trees. The starting resources are the same at every level.
- **Players.** Two: you and one AI.
- **Restart** in the pause menu replays the same map.

| Map type | What to expect |
|---|---|
| Classic | The original valley: towns in opposite corners, forests and mines between. The seed shapes the forests and mines |
| Plains | Open grassland with scattered woods, a river and a few lakes. Extra food |
| Forest | About 70% grass, 25% dense forest and 5% water. Short sight lines and choke points. Extra wood |
| Desert | About 75% sand, 15% rocky ground and outcrops and 10% oases. Little wood, plenty of gold |
| Island | About 60% water. Each town has its own island, joined only by shallow fords |
| Mountain | About 40% mountains, 40% hills and 20% valleys. Narrow passes and plenty of stone |
| Highlands | Rolling hills, craggy peaks, glens and lochs |
| Badlands | Red rock, dry washes and mesas. Barren ground with rich veins |
| Riverlands | Many rivers with fords, marsh and meadow |
| Archipelago | A scatter of islands in a wide sea. No ford joins the homelands: you need a Dock and transport ships to cross |
| Canyon | Sheer rock walls and winding canyon floors. Every route is a choke point |
| Frozen Tundra | Snowfields and frozen moor with pine woods and cold lakes |
| Volcanic | Ash plains, black peaks and lava flows. Rich in stone and gold, poor in wood |
| Oasis | Deep desert with many green oases, each ringed with palms and date bushes |
| Jungle | Rainforest, swamps and rivers. Wood everywhere |
| Continental | One great landmass ringed by sea, with a mountain spine and rivers |
| Mixed Biomes | Snow where the climate is cold, desert where it's hot, and green land in between |

**Terrain**

| Terrain | Effect |
|---|---|
| Mountains, deep water, lava, ancient ruins | Impassable |
| Hills | Walking is 20% slower. Ranged units and siege engines that shoot (not rams) on a hill shoot 1 tile further, and your units on a hill see 1 tile further |
| Shallows (fords) | Walking is 40% slower. Nothing can be built on them |
| Marsh | Walking is 25% slower. Nothing can be built on it |
| Snow | Walking is 10% slower |
| Forest floor | Walking is 15% slower (the trees themselves block the way) |
| Grass, earth, sand, rocky ground, ash, tundra and jungle | Open ground |

With nothing selected, the info panel names the ground under the mouse. On a touch screen, long-press the ground instead.

**How maps are made.** Layered value noise gives each map elevation, moisture and climate. The map type decides how much of the map becomes water (the lowest ground), mountains and hills (the highest), and forest, sand, snow, rock and marsh (by moisture and climate). Island, Archipelago and Continental maps raise land round the towns and sink the rest, and canyons are cut by winding floors. Every tile drains to the sea or the map's edge along the lowest way out, so rivers run downhill from the high ground, widen as they go, get a ford about every 12 tiles and spread into lakes where they cross a basin. Lava runs straight downhill and pools where the ground traps it.

**Fairness.** The towns stand the same distance from the centre, on cleared, buildable ground, with identical starting resources. The other gold, stone, deer, berry bushes, oases and fish come in pairs, one on each town's side at about the same distance from it. Landmarks sit on contested ground, about as far from both towns. When a map is made, the generator checks that the towns can walk to each other, opening a ford, a pass or a gap in the trees if needed. On Archipelago it checks instead that both homelands lie on the same sea with room for a Dock within 16 tiles of each town. It also checks that every mine, bush and herd can be reached on foot from a town, or from the shore of an island a ship can reach.

**Fish.** Shoals of 3 swim in deep water within 3 tiles of a shore, on any sea the towns touch. There are more of them on maps with more water.

**Landmarks.** Every map type except Classic has 1 to 4, by map size, plus up to two oases on Desert and Oasis maps. Each one is announced and marked on the minimap the first time you see it.

| Landmark | What's there |
|---|---|
| Ancient Ruins | Fallen walls, with gold and stone |
| Stone Circle | Standing stones, with stone to quarry |
| Lost Castle | Ruined walls round gold and stone |
| Mountain Fortress | A walled hilltop, with stone and gold. Archers on the hill shoot further |
| Sacred Forest | Ancient trees holding 200 wood each |
| Gold Valley | A hill-ringed valley with 5 gold mines |
| Oasis | Fresh water, palms and dates (Desert and Oasis maps) |

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
| Battering Ram | Siege Workshop | 200 wood, 50 stone | 350 | 60 | melee | Breach. 4 population, 8 armour, slow. Batters every 3 s: gates, then walls, towers and castles. Never attacks units. Fire deals it double damage | Bronze Age |
| Stone Thrower | Siege Workshop | 150 wood, 100 stone | 120 | 120 | 2–12 tiles | Artillery. 3 population, 2 armour. Sets up in 3 s, packs in 2 s, then throws every 8 s. Boulders fly over buildings and splash. Walls, towers and castles, then the most packed infantry | Bronze Age |
| Trebuchet | Siege Workshop | 250 wood, 150 stone, 100 gold | 180 | 220 | 4–18 tiles | Long-range artillery. 5 population, 3 armour, the slowest unit. Sets up in 5 s, packs in 4 s, then hurls every 12 s. Bigger boulders, wider splash. Gates, walls, towers and castles, then any building | Bronze Age and Counterweight Systems |
| Ballista | Siege Workshop | 180 wood, 50 stone, 60 gold | 140 | 80 | 1–13 tiles | Precision. 3 population, 4 armour. Sets up in 2 s, packs in 1 s, then shoots a bolt every 4 s. The bolt hits one target, flat, so it needs a clear line. Siege engines, riders, ships and towers; never foot soldiers | Bronze Age |
| Cannon | Siege Workshop | 150 wood, 50 stone, 150 gold | 160 | 140 | 2–12 tiles | Bombard. 4 population, 4 armour, slow. Sets up and packs in 3 s, then fires every 6 s. Flat cannonballs (it needs a clear line) with a small burst. Gates, walls, towers, castles and siege engines | Bronze Age and Engineering II |
| Royal Guard | Castle | 80 food, 60 gold | 95 | 13 | melee | Elite infantry, 2 armour. +50% against cavalry | Bronze Age |
| Elite Archer | Castle | 60 food, 50 wood, 45 gold | 55 | 9 | 8 tiles | Elite archer, fires every 1.3 s, 10-tile vision | Bronze Age |
| Champion Cavalry | Castle | 140 food, 110 gold | 180 | 20 | melee | Elite rider, 3 armour. +40% against infantry. Charges | Bronze Age |
| Fishing Boat | Dock | 60 wood | 40 | — | — | Catches fish, 15 food a trip, and brings it to the Dock. Every warship deals it ×1.5 | — |
| Transport Ship | Dock | 125 wood | 150 | — | — | Carries 10 slots of units across water. 2 armour, fast | — |
| Galley | Dock | 130 wood, 25 gold | 260 | 28 | 8 tiles | Light warship: 3 armour, 3 population, sees 9. An arrow every 2.5 s (11.2 a second), ×1.5 against fishing boats and transports | Tool Age |
| War Galley | Dock | 180 wood, 80 gold | 380 | 42 | 10 tiles | Mainline warship: 6 armour, 4 population, sees 11. A heavy arrow every 2.2 s (19.1 a second) that pierces up to 15 armour. ×1.3 against galleys, ×1.5 against transports | Bronze Age |
| Fire Ship | Dock | 120 wood, 70 gold | 220 | 20 | 3 tiles | Fast: 2 armour, 3 population. A pot of burning pitch every 2 s that splashes a tile and sets the water alight (5 s, 6 damage a second). ×1.25 against warships. Goes for packed groups | Bronze Age |
| Ballista Ship | Dock | 170 wood, 110 gold | 450 | 95 | 1–13 tiles | 4 armour, 5 population. A heavy bolt every 7 s (big hits, low damage a second): ×1.75 against war galleys, ×2.5 against cannon ships, ×1.5 against ballista ships | Bronze Age |
| Cannon Ship | Dock | 250 wood, 250 gold | 800 | 130 | 2–13 tiles | Slow: 6 armour, 6 population. A cannonball every 7 s with a small burst: ×2 against docks, towers, walls and gates, ×1.75 against castles, ×1.25 against ballista and cannon ships | Bronze Age, Engineering II |

Riders take 2 slots on a transport, a siege engine as many as its population (ballista and stone thrower 3, ram and cannon 4, trebuchet 5), everyone else 1. Ships sail deep water and shallows (fords too) and never go ashore.

### Buildings

| Building | Cost | Size | Purpose | Requires |
|---|---|---|---|---|
| House | 30 wood | 1×1 | +4 population | — |
| Farm | 60 wood | 2×2 | 250 food, worked by one villager | — |
| Storage Pit | 120 wood | 2×2 | Drop-off point for wood, gold and stone | — |
| Barracks | 125 wood | 2×2 | Trains infantry | — |
| Archery Range | 175 wood | 2×2 | Trains ranged units, researches archery upgrades. 400 HP | Tool Age |
| Stable | 200 wood, 100 food | 2×2 | Trains cavalry, researches cavalry upgrades. 500 HP | Bronze Age |
| Siege Workshop | 250 wood, 150 stone | 2×2 | Builds battering rams, stone throwers, ballistas, trebuchets and cannons, researches siege upgrades. 800 HP, 2 armour | Bronze Age, a Barracks and a Stable |
| Town Center | 300 wood | 2×2 | Trains villagers, accepts all resources, advances ages, researches Domestication and Masonry, +4 population | — |
| Guard Tower | 125 wood, 50 stone | 1×1 | Shoots arrows 8 tiles, sees 10. +50% against archers and light cavalry. 500 HP, 1 armour. Garrisons 3. Upgrades along the tower line below | Tool Age |
| Keep | 300 stone, 150 wood, 75 gold | 2×2 | 2-arrow volleys 12 tiles, sees 13. Garrisons 10 (archers add arrows, villagers shelter). Claims territory 7 tiles round. 3000 HP, 6 armour. Grows into a Castle or an Imperial Keep | Bronze Age, Masonry |
| Bastion | 300 stone, 150 wood, 100 gold | 2×2 | Hurls boulders 13 tiles (40 damage, splash, every 5 s), sees 14. Walls join it. Garrisons 8. Claims territory 6 tiles round. 4000 HP, 12 armour | Bronze Age, Masonry |
| Palisade | 3 wood a segment | 1×1 | Sharpened stakes. Blocks units (not arrows). 150 HP, 1 armour, burns 2.5 times as fast | — |
| Wooden Wall | 5 wood a segment | 1×1 | Blocks units (not arrows). 200 HP, 1 armour, burns twice as fast. Can be laid over a palisade | Tool Age |
| Stone Wall | 10 stone a segment | 1×1 | Blocks units (not arrows). 750 HP, 4 armour. Can be laid over a palisade or wooden wall | Bronze Age, Masonry |
| Curtain Wall | 20 stone a segment | 1×1 | A tall, buttressed wall. 1400 HP, 8 armour. Can be laid over any lighter wall | Bronze Age, Masonry |
| Wooden Gate | 50 wood | 1×1 | Opens for your units, shut to the enemy; can be locked. 300 HP, 1 armour | Tool Age |
| Stone Gate | 50 stone | 1×1 | As the wooden gate. 900 HP, 4 armour | Bronze Age, Masonry |
| Gatehouse | 200 stone, 100 wood | 1×1 | A gate between two towers: opens for your units, shoots 2 arrows 8 tiles, garrisons 5 (archers add arrows). Placed on a wall, over a gate or on its own. 2500 HP, 10 armour | Bronze Age, Masonry |
| Boiling Oil | 50 stone, 50 gold | 1×1 | Placed on a timber, stone or curtain wall segment. When enemies attack within 2 tiles of it: 30 damage to each, the ground alight 4 s, half speed 3 s; ready again 8 s later. Destroyed, the wall it stood on is left. 500 HP, 4 armour | Bronze Age, Masonry |
| Moat | 5 stone a segment | 1×1 | A water-filled ditch, dug in 3 s. Can't be damaged. Foot units wade it at half speed; riders and siege engines can't cross it (engines and archers shoot over it). Fill it in with **Fill in** | Bronze Age |
| Reinforced Moat | 5 stone a segment | 1×1 | A deeper, stone-lined moat, dug anywhere or over a moat. Foot units wade it at a quarter speed; riders and siege engines can't cross it. Can't be damaged | Bronze Age, Masonry |
| Drawbridge | 120 wood, 30 stone | 1×1 | Placed on your moat. Lowers for your units (anyone can cross while it's down), rises when an enemy is within 3 tiles or when it's hit (stays up 8 s), can be locked up. Destroyed, the moat stays. 1200 HP, 3 armour | Bronze Age, a Moat |
| Spike Trap | 20 wood | 1×1 | Hidden from the enemy, and walked over. The first enemy to step on it takes 50 damage, and it's spent | Tool Age |
| Fire Trap | 30 wood, 20 gold | 1×1 | Hidden. 30 damage, and the ground burns for 5 s | Bronze Age |
| Pit Trap | 40 wood | 1×1 | Hidden. 20 damage, and the enemy is stuck for 5 s | Tool Age |
| Castle | 500 stone, 250 wood, 150 gold | 3×3 | 4-arrow volleys 15 tiles, sees 15. Trains elite units. Garrisons 20 (riders too). Claims territory 11 tiles round. 6000 HP, 6 armour. Grows into a Citadel | Bronze Age, Masonry |
| Citadel | 1000 stone, 500 wood, 500 gold | 4×4 | 6-arrow volleys 18 tiles, sees 20. Trains elite units. Garrisons 30 (riders too). Claims territory 15 tiles round. Siege engines deal it only 60%. 9000 HP, 18 armour | Bronze Age, Masonry, a Castle |
| Dock | 150 wood | 2×2 | Built on deep water beside the shore. Builds fishing boats, transport ships and the five warships, researches seven naval upgrades, takes in fish, repairs ships moored beside it (3 HP a second). Units cross from it. 600 HP | Deep water on the map |

The tower line, upgraded at each tower (select it and use an upgrade button). Guard → Watch → Fortified Tower, which then becomes a Ballista Tower or grows into a Keep. A Keep grows into a Castle or rises into an Imperial Keep, and a Castle or an Imperial Keep grows into a Citadel. Growing needs free, buildable ground around it for the bigger footprint. The upgrade button says so when there's no room, and if something is built there before it finishes, the cost is refunded. A grown building keeps its damage and its garrison. A Keep or Castle you build outright continues along the same line.

| Tier | Upgrade cost | Attack | Range | Sight | HP | Armour | Notes | Requires |
|---|---|---|---|---|---|---|---|---|
| Guard Tower | (built) | 9 | 8 | 10 | 500 | 1 | Arrows | Tool Age |
| Watch Tower | 100 stone, 50 wood | 11 | 10 | 12 | 850 | 2 | | Tool Age |
| Fortified Tower | 150 stone, 100 gold | 14 | 11 | 13 | 1500 | 3 | Reloads in 1.8 s | Bronze Age |
| Ballista Tower (from Fortified) | 200 stone, 150 gold, 100 wood | 22 | 11 | 13 | 1500 | 3 | Heavy bolts: ×1.5 against siege engines, ×1.3 against cavalry | Bronze Age |
| Keep (from Fortified) | 150 stone, 75 wood, 40 gold | 12 × 2 arrows | 12 | 13 | 3000 | 6 | Grows to 2×2. Garrisons 10, territory 7 | Bronze Age, Masonry |
| Castle (from Keep) | 200 stone, 100 wood, 75 gold | 8 × 4 arrows | 15 | 15 | 6000 | 6 | Grows to 3×3. Everything a castle does | Bronze Age, Masonry |
| Imperial Keep (from Keep) | 300 stone, 150 wood, 100 gold | 15 × 3 arrows | 14 | 15 | 5000 | 9 | Stays 2×2. Garrisons 15, territory 9 | Bronze Age, Masonry |
| Citadel (from Castle or Imperial Keep) | 500 stone, 250 wood, 250 gold | 12 × 6 arrows | 18 | 20 | 9000 | 18 | Grows to 4×4. Everything a citadel does | Bronze Age, Masonry |

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
| Engineering I | Siege Workshop | 150 wood, 100 gold | Siege engines deal 10% more damage | Bronze Age |
| Engineering II | Siege Workshop | 250 wood, 200 gold | Siege engines deal a further 20% more damage. Unlocks the Cannon | Bronze Age, Engineering I |
| Reinforced Frames | Siege Workshop | 200 wood, 100 stone | Siege engines +25% hit points | Bronze Age |
| Counterweight Systems | Siege Workshop | 150 wood, 150 gold | Stone throwers +15% range (12 → 13.8 tiles). Unlocks the Trebuchet | Bronze Age |
| Improved Ammunition | Siege Workshop | 150 stone, 100 gold | Stone throwers splash 20% wider (36 → 43 px) | Bronze Age |
| Masonry | Town Center | 150 food, 100 stone | Unlocks stone walls, stone gates and the Castle | Bronze Age |
| Fletched Arrows | Dock | 100 wood, 50 gold | Galleys and war galleys deal 10% more damage | Tool Age |
| Reinforced Hulls | Dock | 120 wood, 120 gold | Ships +20% hit points | Tool Age |
| Improved Rudders | Dock | 100 wood, 75 gold | Ships sail 15% faster | Tool Age |
| Sea Navigation | Dock | 150 gold | Ships see 20% further | Tool Age |
| Armoured Decks | Dock | 100 wood, 150 gold | Ships +2 armour | Bronze Age |
| Naval Engineering | Dock | 200 wood, 250 gold | Warships shoot 15% further | Bronze Age |
| Elite War Galley | Dock | 300 gold | War galleys: 380 → 500 hit points, 42 → 55 attack (afloat and new) | Bronze Age |
| Fire Projectiles | Siege Workshop | 200 wood, 150 gold | Burning boulders set the ground alight for 4 s: 5 damage a second to enemy units and buildings in it, through armour (rams take double) | Bronze Age, Improved Ammunition |

### Counters

Each hit is multiplied by the attacker's damage type (its class: melee, ranged, cavalry, siege, ship or tower) against the target. A unit is looked up by its type, then its role (`warship`, `transport`, `fishing`), then its class (infantry, ranged, cavalry, siege, ship). A building is looked up by its armour class: one of four fortification classes that come from a structure's role. Gates and drawbridges are the **gate** class. Walls are the **wall** class. Towers and keeps are the **fort** class. Castles are the **castle** class. Fortifications count as buildings unless the attacker has its own bonus against their class or against forts (defences in general). On top of that, each fortification class resists some attackers (see Fortifications). Castle territory and walled towns then adjust it (see Fortifications), and finally the target's flat armour is subtracted, less whatever the projectile pierces (a war galley's heavy arrows pierce 15). A hit always deals at least 1.

| Attacker | Strong against |
|---|---|
| Archers (all ranged units) | Villagers ×1.5, infantry ×1.25. Only ×0.5 against buildings, ×0.4 against siege engines and ×0.75 against ships, and half damage at point-blank range |
| Skirmisher | Archers and other ranged units ×1.5 |
| Infantry | Cavalry ×1.25, siege engines ×2.5 |
| Cavalry | Ranged units ×1.15 (Horseman ×1.25), siege engines ×1.25, buildings ×0.75 |
| Heavy Cavalry | Infantry ×1.5 |
| Towers and Castle | Archers and other ranged units ×1.5, light cavalry (scouts, horsemen) ×1.5. Only ×0.4 against siege engines, except the Ballista Tower's bolts (×1.5) |
| Royal Guard | Cavalry ×1.5 |
| Champion Cavalry | Infantry ×1.4 |
| Siege engines (all of them) | Gates ×3, walls ×2.5, towers and keeps ×2, castles ×1.75, other buildings and other siege engines ×1.5, ships ×1. Any other unit only ×0.75 |
| Warships (all of them) | Fishing boats ×1.5, transports ×1.25 |
| Galley | Fishing boats and transports ×1.5 |
| War Galley | Galleys ×1.3, transports ×1.5 |
| Fire Ship | Every warship ×1.25; the burning water hurts every ship in it |
| Ballista Ship | War galleys ×1.75, cannon ships ×2.5, ballista ships ×1.5 |
| Cannon Ship | Docks, towers, walls and gates ×2, castles ×1.75, ballista and cannon ships ×1.25 |
| Battering Ram | Can't attack units. Rams battering the same building: 2 → ×1.1, 3–4 → ×1.2, 5 or more → ×1.35 |
| Stone Thrower, Trebuchet, Cannon | Splash by distance from the impact: 100% within a quarter of the radius, 75% to half, 50% to three quarters, 25% to the edge. The radius is 36 px for a boulder, 48 px for a trebuchet's and 22 px for a cannonball. Each victim takes the siege multiplier for its class (×0.75 for soldiers) |

### Orders
Every order is one engine order for land units and ships alike; how a unit moves (on land, over water, or across it by ferry) is up to the unit.
- **Buttons and hotkeys.** With soldiers, siege engines or ships selected, the command panel offers **Move**, **Attack**, **Attack-Move**, **Patrol** and **Guard**. Each shows when any selected unit can take it: unarmed boats get Move and Patrol only. Press one (or `A`, `P` or `G`), then click (tap) the map. Villagers keep their build menu, but the hotkeys work for them too. **Attack** on an enemy is a direct attack; on open ground it attacks-moves there.
- **Attack-move.** The unit marches on the point. Several times a second it looks over everything in its sight for an enemy it can fight. When it finds one it breaks off, fights it (chasing no further than 4 tiles past its sight), then picks up its route again. Once at the point, it stops: moving, enemy found, engaging, target dead, back on the route, destination reached.
  - **What it fights first.** Siege engines and warships follow their own target lists. Other units follow their class's preference: archers take on riders, then foot soldiers, then archers; foot soldiers go for siege engines, then riders, foot soldiers and archers; riders go for archers, siege engines and villagers. Then any enemy unit; with no unit about, an enemy building within easy reach (walls only when they bar the way).
  - **On the way.** A wall across the route is breached and the march goes on. A siege engine sets up to fire, then packs up to move on. A group keeps its formation, at the pace of its slowest member. Sent across the water, the unit walks to a ship, crosses, lands and carries on attack-moving.
  - **Who can.** Every unit with a weapon can attack-move, villagers included. A plain Move walks past enemies without stopping.
- **Patrol.** Any unit, from villagers to warships, goes back and forth between where it is and the point picked, for ever. The AI's routes can have up to 8 waypoints. Soldiers, siege engines and warships take on enemies that come into sight, then return to the round. Villagers, fishing boats and transports turn about, heading for the waypoint furthest from an enemy that can hurt them when it comes within its reach plus 3 tiles. A leg across the water goes by ferry. A siege engine packs up between waypoints and sets up to fight.
- **Guard.** Pick a spot, a building or one of your units. On a spot or a building, the units stay by it and take on whatever comes within their range plus 3 tiles of it, then go back. On one of your units they escort it: they keep close and never chase more than 8 tiles from it. Pick an enemy and it is attacked.
- **The panel** shows what each unit is doing: attack-moving, patrolling, guarding a spot or a building, escorting, and "(engaging)" while it has broken off to fight.

### Ranged combat, cavalry, siege and formations
- **Projectiles.** Arrows and javelins fly in an arc and follow their target. The chance to hit is 97% up to half range and falls to about 65% at maximum range. It's 10% lower against a moving target. A miss lands harmlessly beside the target, unless it's a boulder that still comes down on the building it was thrown at. Buildings between the shooter and the target block the shot, so the shooter moves until it has a clear line. Ballista bolts and cannonballs fly flat like arrows; boulders fly over everything.
- **Kiting.** While reloading, a ranged unit steps back from melee attackers that come within about 2 tiles, then stops to shoot again. Rams can't hurt units, so archers don't back away from them.
- **Charge.** Cavalry that start an attack on a unit from 3 or more tiles away move 35% faster until the first hit, and that hit deals 50% more damage.
- **Rams.** A battering ram only attacks buildings. Ordered to attack a unit, it rolls to where that unit stands instead. An idle ram looks up to 7 tiles away for its next fortification: gates first (drawbridges too), then walls, towers and castles. It doesn't pick other buildings by itself, but you can send it at any building. In the AI's army, rams stay out of fights with units. The stats panel shows a ram's teamwork bonus while it batters with others.
- **Setting up.** Every engine but the ram must deploy before it fires and pack up before it moves. It goes packed → deploying → deployed → packing → packed. A stone thrower takes 3 s to set up and 2 s to pack, a trebuchet 5 s and 4 s, a ballista 2 s and 1 s, a cannon 3 s and 3 s. Packed, an engine can move but not fire; deployed, it can fire but not move, and nothing can push it aside. It deploys and packs by itself when it's given orders, or you can use the **Deploy** and **Pack up** buttons; a bar under it shows the progress. Each has a minimum range it can't hit inside: 1 tile for a ballista, 2 for a stone thrower or cannon, 4 for a trebuchet. Packed, it backs away from a target that close and gives up if it's cornered; deployed, it switches to another target.
- **Targets.** Each engine works down its own list, by itself, within its range. Ram: gate → wall → tower → castle. Stone thrower: wall → tower → castle → foot soldiers (the most packed group first). Trebuchet: gate → wall → tower → castle → any other building. Ballista: siege engine → rider → ship → tower. Cannon: gate → wall → tower → castle → siege engine. You can order an engine against any building if its list has one, but only against units of a class on its list. Ordered at any other unit, it moves to where that unit stands instead.
- **Boulders.** Boulders fly high, so buildings in the way don't block them, and they don't follow their target. A boulder lands where the target stood when it was thrown, then rolls on a little. Every enemy unit near the impact is hurt (see Counters), and the building it was aimed at takes the full blow. A cannonball bursts too, over a smaller area.
- **Fire.** With Fire Projectiles, boulders set the ground alight for 4 seconds. Enemy units and buildings in the flames take 5 damage a second, through armour, and rams take double.
- **Formations.** With soldiers selected, the command panel offers Line (best for archers), Square (infantry) and Wedge (cavalry). Choosing one re-forms the group facing the enemy. Siege engines take the back rank. Group moves then keep the shape at the pace of the slowest member. Choose it again to march loosely.
- **Vision.** Rams see 5 tiles, villagers and infantry 6, skirmishers 7, archers 8, composite archers 9, elite archers 10, scouts, stone throwers, trebuchets and cannons 12, ballistas 13; fire ships 8, galleys 9, war galleys 11, ballista and cannon ships 12 (Sea Navigation: +20%). Buildings see 7, except walls (0), gates (2), towers (10 to 12 by tier) and the Castle (15). Units on your own castle territory see 2 tiles further.

### Naval combat
- **Warships.** The Dock builds galleys (Tool Age), and war galleys, fire ships, ballista ships and cannon ships (Bronze Age; the cannon ship also needs Engineering II). Every fighting ship has the role *warship*; boats are *fishing* and *transport*. Each warship works down its own target list. Galley and war galley: warship → transport → fishing boat → dock. Fire ship: warship → transport → fishing boat, the most packed group first. Ballista ship: war galley → cannon ship → ballista ship → any warship → transport → fishing boat → dock. Cannon ship: dock → castle → tower → cannon ship → ballista ship → any warship. A warship can only be ordered at what its list names; ordered at anything else, it sails there instead. None attacks land units.
- **At sea.** An idle warship takes on the first enemy on its list that comes into sight (8 to 12 tiles) on its own water, and chases it. Ships turn at their own rate (a galley comes about in about 0.6 s, a cannon ship takes twice as long) and slow down while turning. Ships under way glide past each other; ships at rest keep apart. A sunk ship plays its sinking and leaves wreckage afloat for a few seconds; a transport takes its cargo down with it. Your Dock repairs ships moored beside it, 3 HP a second.
- **Orders.** Right-click (tap) an enemy ship or Dock to attack it, or one of your own ships to escort it. Warships take every other order too (see Orders): attack-move across the sea, patrol a lane, guard a harbour.
- **Shots.** Heavy arrows fly flat and fast, pierce armour and leave a trail and a splash. Pots of burning pitch splash a tile and set the water alight (any ship in it burns, through armour). Ballista bolts hit one ship hard. Cannonballs burst over a small area. Flat shots need a clear line past buildings.
- **The AI's fleet.** It builds warships to escort its crossings and guard its fishing boats. Once you sail warships it matches your fleet, ship for ship (up to 6). It chooses what trades best against your ships for its cost: its damage against them, after counters, armour and piercing, against theirs against it, per cost squared. Then it waits for room for that ship. Its missions follow each ship's `aiOrders`:
  - it hunts your ships when they come within 14 tiles of its docks, boats or transports, or anywhere on its water once it outnumbers your warships;
  - it escorts its loaded transports and guards the fishing boat furthest out;
  - with 3 warships or more, up to half of them blockade your nearest Dock: they hold station off it, sink whatever comes and goes, then shell the Dock;
  - the rest patrol from its Dock towards you.
- **The AI's priorities at sea.** While its fleet is short of yours it trains no new soldiers or siege, keeps fewer soldiers to leave room for ships, and builds a second Dock if the first is busy. It researches Fletched Arrows and Armoured Decks with 2 warships, Reinforced Hulls and Naval Engineering with 3, and Elite War Galley with 2 war galleys.

### Fortifications
- **Defences pages.** The villagers' **Defences** button opens three pages, with tabs between them: **Walls & Gates** (palisade, timber, stone and curtain walls, gates, the gatehouse, boiling oil), **Towers & Castles** (guard tower, keep, bastion, castle, citadel) and **Moats & Traps** (moat, moat ring, reinforced moat, drawbridge, the three traps). Each lists the structures whose data names that page.
- **Walls.** Choose a wall on the Walls & Gates page, then drag from one end of the line to the other, or click (tap) both ends. The line runs in steps, so every segment touches the next, and the cost of the segments that fit shows as you drag. Segments join their neighbours, your gates, towers and castle, drawing ends, straights, corners, T-junctions and crossings. Villagers build a line one segment after another by themselves. Walls stop every unit, cavalry included, but not arrows: archers shoot over them. You can demolish your own walls and gates (no refund). The Palisade (Stone Age, 3 wood) is the quickest and weakest wall; the Curtain Wall (Masonry) the strongest. Lay a heavier wall over your lighter one to rebuild it in place: a timber wall over a palisade, a stone wall over either, a curtain wall over any of them.
- **Gates.** A gate opens for your units and stays shut to the enemy, which pathfinding knows: your units route through your gates, the enemy's go round or break in. Place a gate on your own wall to replace that segment. A gate turns to match the wall it sits in, swings open while your units are near, and can be locked against everyone. A **Gatehouse** (Masonry) is a gate between two squat towers: it works like any gate, can go on a wall, over a lighter gate or on its own, shoots 2 arrows 8 tiles and holds 5 (each archer adds an arrow).
- **Boiling oil.** A cauldron (Masonry) placed on a timber, stone or curtain wall segment, which it replaces in the line. When an enemy attacks anything within 2 tiles of it, it pours: 30 damage to every enemy land unit there (armour doesn't help), the ground burns for 4 s and they move at half speed for 3 s. It's ready again 8 s later. If it's destroyed, the wall segment it stood on comes back as damaged as it was. It doesn't count as a town building.
- **Breaching.** A unit whose path can't bring it within reach of its target attacks the enemy wall, gate or building in the way, then goes back to its target once through.
- **Moats.** Choose **Moat** on the Defences page and drag a line, like a wall, or **Moat ring** and drag from corner to corner for a rectangle. Or select some of your walls and gates and press **Moat around**: it lays moat on every free tile just outside them, diagonals included, and on a closed ring of walls only on the outside. Villagers dig it (3 s a segment), and segments join into straights, corners, crossings and ends. A moat can't be damaged or attacked. Foot soldiers and villagers, yours and the enemy's, wade it at half speed. Riders and siege engines can't enter it and path round it, but engines and archers shoot over it. A ram facing a moat goes for its drawbridge instead. Fill your own moat in with **Fill in**. A **Reinforced Moat** (Masonry), dug anywhere or over your moat, is wider and deeper: foot units wade it at a quarter speed.
- **Drawbridges.** Place one on a segment of your moat (it needs a finished moat first) to make a crossing for your riders and siege. It lowers while your units are within 1.6 tiles and no enemy is within 3, and then anyone can cross. It rises when an enemy comes close, stays up for 8 s after it's hit, and can be raised and locked. Rams target drawbridges first along with gates. If one is destroyed, the moat underneath is left.
- **Traps.** Spike (50 damage), Fire (30, and the ground burns 5 s) and Pit (20, and the victim can't move for 5 s) traps, built on the Moats & Traps page. The enemy never sees them: they aren't drawn for it, can't be targeted and don't show on the minimap. You see yours faintly. Units walk over them, and the first enemy land unit to step on one springs it (armour doesn't help), and it's spent. They don't count as town buildings.
- **Keeps.** A heavy stone stronghold (2×2): 2-arrow volleys 12 tiles, 13-tile sight, 3000 HP, 6 armour, room for 10 inside, and territory 7 tiles round. Build one outright on the Towers & Castles page, or grow a Fortified Tower into one. A keep grows into a castle, or rises into an **Imperial Keep**: still 2×2, 5000 HP, armour 9, 3-arrow volleys 14 tiles, sight 15, room for 15 and territory 9. An Imperial Keep grows into a Citadel.
- **Bastions.** An angled artillery platform (2×2, Masonry): it hurls boulders 13 tiles that hurt everyone near where they land, sees 14, holds 8, claims 6 tiles round, and your walls join onto it. 4000 HP, armour 12.
- **Citadels.** The end-game fortress (4×4): 9000 HP, armour 18, 6-arrow volleys 18 tiles, the longest sight (20) and the biggest garrison (30, riders too), territory 15 tiles round, and it trains the castle's elite units. Siege engines deal it only 60% of what they'd deal a castle. Build one outright once you have a Castle, or grow a Castle or an Imperial Keep into one.
- **Armour classes.** A fortification's role decides its armour class. Gates and drawbridges (**gate**) and walls and moats (**wall**) take ×0.6 from infantry, villagers and cavalry. Forts (towers, keeps, bastions, boiling oil, traps) take ×0.6 from archers and ×0.85 from infantry and cavalry. Castles and citadels take ×0.6 from archers and villagers, and ×0.7 from infantry and cavalry. Siege engines hit each class by the siege multipliers (see Counters).
- **Siege priority.** The roles' order is gate, wall, fort (towers, keeps, bastions), castle (castles, citadels): each role's `siegePriority`, sorted into `SIEGE_ORDER`; a siege engine's target list can name a role or `defences` for all four. Rams batter gates first, then walls, forts and castles. Other engines follow their own lists (see Ranged combat, cavalry, siege and formations).
- **Garrison.** Right-click (tap) your tower, keep or castle with units selected to send them inside: up to 3 in a tower, 5 in a gatehouse, 8 in a bastion, 10 in a keep or 15 in an Imperial Keep (foot soldiers, archers and villagers), or 20 in a castle and 30 in a citadel (riders too); never siege engines or ships. Units inside are off the map, safe, still count towards population and heal 1 HP a second. Anyone inside raises the building's attack by 15% and its armour by 2. Each archer inside adds an arrow to a tower's, gatehouse's or keep's volley (a bastion's boulders don't change); in a castle or citadel every two add an arrow, and each also speeds its reload by 5% and adds 3% damage. **Ungarrison** brings everyone out, and a falling building lets its garrison out alive.
- **Castle volleys.** A castle fires 4 arrows at once (a citadel 6) at the nearest enemies: all of them at a lone target, or one each spread over several. It shoots soldiers before villagers.
- **Territory.** Each citadel claims the ground within 15 tiles, each castle within 11, each Imperial Keep 9, keep 7 and bastion 6 (shown with a dashed border). On your own territory your units heal 1.5 HP a second, hit 10% harder, take 15% less damage and see 2 tiles further, your buildings there take 15% less damage, and production there is 25% faster. Where both sides' territory overlaps, it's contested and nobody gains.
- **Walled town.** If no enemy unit can walk from the enemy's buildings to your Town Center, because walls, gates, buildings and resources close every way in, your buildings take 10% less damage. A moat alone doesn't count: foot soldiers can wade it. A message tells you when your town becomes walled or is breached.
- **Repair.** Villagers right-click (tap) your damaged building to repair it, paying half its cost for a full repair. They repair at half its building speed, or a third for a castle or citadel (the castle role). A drawbridge can be mended from inside its gate. Moats never need it.
- **Alarm.** When enemies come near your town (within a building's sight, or 10% beyond a tower's), a horn sounds and a message appears, at most every 25 seconds.

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
- Population is capped at **50**. Most units take 1; siege engines take 3 (stone thrower, ballista), 4 (ram, cannon) or 5 (trebuchet).
- Resource amounts: tree 100, berry bush 150, deer 120, fish 225, gold mine 400, stone mine 350. Hunting deer is 30% faster than picking berries, and fishing 15% faster.
- You **win** when every enemy building is destroyed and **lose** when all of yours are gone. Walls and gates don't count, and destroying one is worth only 2 points.

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
| `aethoria.settings.v1` | Your settings, including the last camera zoom |
| `aethoria.maps.v1` | Your favourite maps and the last map you started |

Each save is one JSON record. It holds the slot name, save time, play time, player level, completion percentage, difficulty, age, score, resources, location on the map, a small screenshot and the game version, plus the whole game: the map (seed, type, size, resources, the generator version, the terrain of every tile, both starting positions and the landmarks with whether you've found them), every unit, building, resource (fish included), order, path, training and research queue, every ship's cargo, heading and crossing (its stage, shores, berths and convoy, and each passenger's order for the far shore), orders (attack-moves, patrol routes and the waypoint each heads for, guards and escorts, the AI's blockades and hunts, and for a unit that broke off to fight, its target, the order it goes back to and where it broke off), projectile, siege engine's deployment, patch of burning ground, wall, gate and whether it's locked, what a structure was built over (the wall under boiling oil or a gatehouse, the moat under a drawbridge), boiling oil's cooldown, hidden traps, tower tier and upgrade (an Imperial Keep too), the units inside every tower, gatehouse, bastion, keep, castle and citadel, units slowed by oil or stuck in a pit, the fog of war, the AI's state, camera, selection, score, statistics and missions. It also stores the simulation's dice (the seeded generator behind every shot's accuracy and the AI's choices) and when the periodic sweeps next run. Positions, hit points, timers and projectiles are kept at full precision, so a battle loaded from a save carries on exactly as it would have. The same save played twice ends the same way. It also stores your camera preferences (`zoomLevel`, `uiScale`, `pinchSensitivity`, `touchMode`), and loading the save restores them. A checksum covers the entire record.

- **Save slots.** The five slots are independent, and nothing writes to one without you asking. **Save Game** in the pause menu opens the save screen. Pick a slot, confirm if it already holds a save, and you get a confirmation message. `Ctrl` + `S` and **Quick Save** save straight to the slot your game belongs to. **Save & Quit** saves there too.
- **Autosaves.** The game autosaves every 30 seconds of play. It also autosaves after age-ups, missions, achievements, upgrades, resource milestones, completed or lost buildings and the fall of the enemy Town Center, and when you pause, switch away or close the page. Autosaves rotate through three slots (1 → 2 → 3 → 1), so the two older copies are always intact. They never overwrite a manual slot. An unchanged game isn't written again, and routine autosaves are spaced at least 8 seconds apart. The indicator in the top bar shows *Autosaving…*, *Saved ✓* or *Save failed*.
- **New game.** Choose the map (see [Maps](#maps)), a difficulty, a slot (the first empty one is picked for you) and a name. You can also start a new game from any empty slot's **New Game** button. Each save card shows the map type, size and seed.
- **Saves from before map seeds** load on the Classic 64×64 map they were played on. Because a save stores the terrain itself, a map always loads as it was saved, even if a later version generates maps differently.
- **Continue and load.** **Continue** on the title screen and **Load Game** in the pause menu open the save screen. It lists every slot and autosave with its details and marks the most recent one. A save is never loaded automatically. You always pick it.
- **Managing saves.** **Saved Games** (on the title screen or in Settings) opens the same screen. From there you can load, overwrite, delete, rename, copy (to another slot, including from an autosave), export and import saves.
- **Backups.** Before a slot is overwritten, its current save is copied to a backup. The new save is written, read back and checked. The backup is then removed, or put back if anything failed.
- **Damaged saves.** Every save is fully validated when it's listed, loaded and written. A damaged slot is marked with *Save Slot 2 appears corrupted*. If a backup survived (for example, when the page closed in the middle of a save), you're offered *Restore from backup?*. Otherwise you can delete the save or save over it. The game never crashes on bad data, and invalid settings fall back to defaults field by field.
- **Finished games.** Winning or losing doesn't delete any save, so earlier saves of that campaign can still be loaded. Your score, XP, achievements and statistics are recorded when the game ends.
- **Export and import.** **Export** downloads a slot or autosave as a `.json` file. **Import** reads a `.json` file, validates it, and then puts it in the slot you chose, after you confirm if that slot is in use. Saves exported by Aethoria 1.1 can be imported too.
- **Upgrading from 1.1.** On the first start, your old single save (`aethoria.save.v1`, or its backup if that's the only good copy) is moved into the first free slot.
- **Reset progress.** This button is on the title screen and in Settings, and asks you to confirm first. It deletes every slot, autosave and backup, and your profile. Your settings and favourite maps are kept.
- If the browser blocks storage (for example, in some private modes), the game still runs, warns you, and keeps progress only until you close the tab.

---

## Code structure

Everything is in `index.html`. The script is split into labeled sections:

The script is a single `<script type="module">`, so nothing is added to `window`. The only exception is the optional `?debug` URL flag, which exposes `window.__aethoria` for testing.

| Section | Responsibility |
|---|---|
| `helpers` | DOM shortcut, canvas factory, `mulberry32` seeded RNG, 2D hash noise, `cyrb53` checksum, bit and nibble packing |
| `config` | `CONFIG` (timings, storage keys, limits) and the `DIFFICULTY` table |
| `persistence` | `StorageManager` (guarded `localStorage` access, settings, profile), `SaveSlotManager` (`createSlot`, `saveToSlot`, `loadFromSlot`, `deleteSlot`, `copySlot`, `renameSlot`, `getSlotInfo`, `listSlots`, `exportSlot`, `importSlot`, plus `autoSave`, `restoreFromBackup` and `parse` for validation), `Settings`, `Profile` |
| `audio` | `AudioManager` (master, effects and music buses), the generative `MusicPlayer` and the `SFX` table |
| `game data` / `progression tables` | Unit, building, upgrade and age definitions (upgrades apply by class, type, `types`, role or every ship), the counter table (`COUNTERS`, whose `siege` row is the siege damage model), projectile kinds (`PROJ_TYPES`), formations, score values, achievements, missions. Siege engines are data: a `UNITTYPES` entry with `cls: 'siege'`, `siegeRole`, `targets`, `speed`, `damage`, `attackCooldown`, `deploy` with `deployTime` / `teardownTime`, and `projectileType` (a `PROJ_TYPES` key). `siegeData` reads them into the engine's terms at start-up, adds each one to the Siege Workshop (or `at`), and names and describes any that leave that out. A picture is optional (`UNIT_ART` with a `draw` function; otherwise the generic `drawEngine`). So a new engine is one `UNITTYPES` entry and one `PROJ_TYPES` entry. Warships are data the same way: `naval: true`, `role`, attack stats (`attack`, `range`, `attackCooldown`, `speed`, `vision`, `turnRate`), `proj`, `sprite` (a `SPRITES` key), `targets` and `aiOrders`; `unitData` reads them in and adds them to the Dock. Projectile kinds may be written in the same terms (`speed` in tiles a second, `arc`, `splashRadius`, `armorPen`, `impactEffect`, `trailEffect`), and `projData` reads them in |
| `pixel sprites` / `icons` | Code-drawn sprites for units, buildings, resources and HUD icons. `SPRITES` describes pictures in a sprite sheet's layout (frame size, 16 headings, idle / move / attack / sink animations). A `sheet` image is sliced by heading row and frame column; with none, `drawShipModel` draws each frame from the entry's `model` (hull, oars, braced sails, crew), and `shipFrame` keeps the frames it has drawn |
| `game state` | The `state` object, tile blocking (`block`: resources, buildings, walls, and gates by owner), the tile-to-building grid `occ`, castle territory `infl`, fog grids, entity registry `ENT` |
| `terrain` | Terrain types (`TT`, `TERRAIN`: name, colours, blocking, speed, buildable), `setMapSize` (reallocates every grid), `blockTerrain`, `renderTerrain` (the painted ground and the minimap base) and `terrainAt` |
| `map generation` | Map settings (`MAP_SIZES`, `DENSITY`, `MAP_TYPES`, `LANDMARKS`, `START_KIT`), seeds (`cleanSeed`, `seedNum`, `randomSeed`), seeded fractal noise (`makeNoise`) and `generateWorld(settings)`, a pure function that returns the terrain, resources, starts and landmarks. `applyWorld` builds that into the game. A new map type is one `MAP_TYPES` entry; a new landmark is a `LANDMARKS` entry and a builder in `generateWorld` |
| `pathfinding` | A\* with a binary-heap open list on the tile grid (each side walks through its own gates). With `naval`, the same search runs on the water graph (open water only, no corner-cutting). Plus `nearestFree`, `nearestSail` and `landNear` fallbacks. Land and water regions (`regionsOf`, kept in `NAV`) say at once whether a trip needs a ship |
| `naval` | The hybrid router and ferry service (`Ferry`). `request` turns any order across water into a crossing. `tick` gives waiting units a ship (one already loading there with room, else a free transport: moored at a Dock, then idle, then nearest). `sail` runs a transport's trip (pickup → load → sail → unload), with convoys and spread-out landing berths. `landing` picks the landing tiles. `orderBoard` and `unloadAt` handle the manual commands, `separateShips` keeps ships at rest apart (ships under way pass), `repairShips` mends them at docks. Every decision uses tiles and the unit list in order, so it's deterministic |
| `orders` / `unit update` | Command state machine for units: `move`, `gather`, `deposit`, `build`, `repair`, `garrison`, `guard` (a spot, a building, or a unit: escort), `attack` (with `ret`, the order to go back to, and a leash), `attackmove`, `patrol`, `ferry`, `hunt`, `blockade`. `ORDERS` is the data behind the order buttons and hotkeys: who takes each, what a click means, and the order it gives (`orderAttackMove`, `orderPatrol`, `orderGuard`, `groupOrder` for formations). `ordersOf` gives a unit's orders in the order model's terms (`ATTACK_MOVE` with its destination, `PATROL` with `pointA`, `pointB` and `currentTarget`, and so on). `pickByClass` and `TARGET_PREFS` choose a fight for units without a target list; `flee` turns unarmed patrollers away from danger. `pickTarget` works down any unit's `targets`: siege engines and warships alike, measured from the unit or from what it escorts, and a ship only picks what it can reach on its own water. `engage` and `attackFrom` break off an order to fight and come back to it. A ship's heading turns at its `turnRate` in `followPath`. Includes ranged combat (range, line of sight, kiting), cavalry charges, siege (`siegeTarget` works down an engine's `targets`, `canHit` and `targetKind` filter what it may attack, `ramGroup`, the deploy state machine `setDeploy` / `deployState` / `deployTimes`, minimum range), breaching walls (`walledOff`), the counter system (`dmgMult`, `hitDamage`, `fortFactor`) and soldier collision |
| `buildings, training & research` | Training queues (`TRAINS`), upgrade effects (`TECHS`), tower upgrades and tower / castle volleys |
| `fortifications` | Data-driven: a new defence is data only. Every defensive structure is a `BLDTYPES` entry with a `role`, and `ROLES` says what the role means: armour class (`ROLE_ARMOR`), `siegePriority` (sorted into `SIEGE_ORDER`), `repairable` and the repair rate and cost, `joins` (whether it draws joined pieces) and its join group, AI planning (`plan`: `ring`, `corner`, `front`), whether it counts as a town building, and the picture a new structure borrows until it has its own (`art`). A structure's own data adds `fire` (volleys), `garrison` (plus `riders`), `territory`, `resist` (by attacker class), `lay: 'line'`, `over` / `overOnly` (placed on another structure, replacing it; with `restoresUnder` that structure comes back when it falls), `wade` (a moat's speed), `walkable`, `hidden`, `town: false`, `trigger` (when an enemy steps on it or attacks nearby: damage, burning ground, a slow, a hold, a cooldown, spent once sprung; run by `triggers`), `indestructible`, `layer: 'ground'`, `spriteSet`, `art` and `menu` (its page in `DEF_PAGES`). `fortifyData` fills in each entry's `id`, `armorClass`, `upgrades` and a default sprite set at start-up. Sprite sets are `SPRITES` entries of kind `line` (16 joined pieces, also named `straight`, `corner`, `tee`, `crossroads` and `endcap`), `gate`, `moat` or `bridge`, built per side into `SSPR`; `setPiece` picks one. The tower line is `TOWER_TIERS` (built by `tierData`): a row grows out of the row before it unless `after` names another (or several), and `becomes` turns the building into another type, growing it into free ground (`growSpot`). A plain row is a tier of any building on its line (a Keep's Imperial Keep), and a plain row with `becomes` gets its grow step added right after it. `nextTiers`, `tierLock`, `queueTowerTier` and `completeTowerTier` read only this table, so a new tier is one row (at the end), and a tier without its own picture borrows its parent's (`tierSprite`). Also: volleys (`fireOf`, `defenseOf`, `volley`), garrisons (`enterGarrison`, `ejectGarrison`), lines, rings and joins (`wallLine`, `ringTiles`, `placeWallLine`, `wallMask`, `joinOf`), moat round walls (`moatAround`), gates and drawbridges (`updGates`, `setGateLock`), territory (`computeInfluence`, `ownGround`), walled towns (`computeWalled`) and the alarm (`checkWarning`) |
| `projectiles` | `Rng`, the seeded dice behind every roll the simulation makes (saved with the game). The `Projectiles` manager: `fire`, `update` (flight, target tracking, hits and misses, armour piercing, `IMPACT_FX` where it lands), `burst` (splash damage for any `PROJ_TYPES` kind with `splash`, the rolling boulder and fire), `burn` (burning ground) and `draw` (arcs, shadows, tumbling boulders and `TRAIL_FX`) |
| `formations` | `formationSlots` and `formationMove` for Line, Square and Wedge |
| `AI` | Economy balancing (gatherer quotas per age, `aiQuota`), the navy (`aiNavy`: a Dock, fishing boats and transports; `aiCamp`: storage pits on islands it works; `aiOverseas`: landed soldiers fight on; seaborne invasions straight from `aiMuster`; the fleet: `aiFleet`, `aiShipChoice` (the best trade against your ships per cost squared), `aiFleetOrders` (missions from each ship's `aiOrders`), `blockadeStation`, `seaward`), border patrols (`AI_PATROLS`, `aiRoute`, `aiPatrols`), build order, age-ups, upgrades, an army mix that counters yours, siege engines by role (`aiSiege` fills `AI_SIEGE_MIX`: 2 breach, then 1 of each other role, plus artillery against many towers), fortification by plan (`AI_FORT_PLAN`, worked one step at a time by `aiFortify` and `aiFortStep` from each step's role: wall-role lines round the ring by `aiRingStep`, with `aiExits` keeping a gate where its way out crosses it, moats by `aiMoatStep`, gates by `aiGateStep`, forts on the ring's corners and castles facing you, and anything the tower line reaches grown by `aiGrow`; plus `aiRing`, `aiTower`, `aiUpgradeTowers`, `aiRepair`, `aiShelter`, `aiRally`), defence, and attack waves that gather in formation, escort their siege, attack-move on the target and flank with cavalry |
| `camera` | The `cam` object: position, `zoomCurrent` easing toward `zoomTarget`, the anchor that keeps the zoomed-on spot in place, clamping, tactical layers and the strategic overview |
| `fog` / `rendering` / `minimap` | Visibility. One world transform (zoom × pixel density) with view culling, a pooled Y-sorted draw queue, simplified drawing at Far zoom and icons at Strategic zoom. The fog is drawn as merged runs in device pixels, and the minimap fog as one image |
| `HUD` / `command panel` | Resource bar, selection info, context-sensitive command buttons |
| `progression` | Score, milestones, achievements, missions and debounced save requests |
| `serializer` | `GameSerializer.serialize` / `validate` / `restore`, which convert between the live world and plain JSON. Whatever moves or counts down in a fight is saved at full precision, with the units' running timers, the dice and the sweep clocks, so a loaded battle resumes exactly |
| `game controller` / `UI` | New game, load, pause, restart and quit; the overlay stack, confirm / prompt / choice dialog, the New Game screen with its map preview (`drawPreview`), map codes (`shareCode`, `parseShare`) and favourites (`MapPrefs`), save-slot screen, settings, records and end screen |
| `input` | Mouse (wheel zoom, middle-button scroll), the touch gesture recogniser (tap, double tap, long-press, drag, pinch, three-finger overview), the long-press command menu and information cards, keyboard and minimap handlers, smart mobile mode, and the lifecycle autosave hooks |
| `main loop` | `requestAnimationFrame` loop with a timestep capped at 50 ms. If a high-density canvas keeps drawing slowly (software rendering), it drops to 1× pixel density for the rest of the session |

### Built with
- HTML5 Canvas 2D
- Web Audio API
- Plain JavaScript (ES2015+, strict mode)

---

## Browser support

Works in any current version of Chrome, Edge, Firefox or Safari, with a mouse and keyboard or with touch. The interface scaling uses CSS `zoom`, which needs Firefox 126 or later. Over the game, pinches and `Ctrl` + wheel zoom the map, not the page, so the browser's own page zoom is blocked while you play. Use **UI scale** to make the interface larger.

---

## Known limitations
- There's one AI opponent, so every map has two players. Maps go up to 128×128 tiles. Larger maps would need a faster pathfinder and a tiled ground canvas. The AI doesn't seek out hills, landmarks or fords on purpose.
- Warships fight only ships, and the cannon ship also docks, towers and castles: no ship attacks land units. Land units hit ships only from the shore (archers, towers, castles and ballistas), or soldiers when a ship is beside them. Units waiting at the shore for a ship don't fight back unless re-ordered. Boarding and landing take no time. Fishing boats and transports keep their side-view pictures; warships are drawn in 16 headings. The simulation is deterministic from a save and a sequence of frame times, but live play runs on real frame times, so two live games never match.
- Of the upgrades, the AI researches only Fletching, Horse Breeding, Masonry, Engineering I and II, Counterweight Systems, Reinforced Frames and five of the Dock's (not Improved Rudders or Sea Navigation). Its fleet is capped at 6 warships and, like its army, shares the 50 population. Its waves send every siege engine at the wave's target, so a ballista shoots a town center if your army has no engines or riders for it. Its fortifications follow its plan only: it never builds stone or curtain walls, stone gates, boiling oil, reinforced moats or traps, and builds one of each fort and castle.
- The game has three ages, so the Keep, Imperial Keep, Bastion and Citadel (late-age buildings in some designs) come in the Bronze Age with Masonry. Boiling oil and traps hurt land units only, and their damage ignores armour. Moats can only be crossed at a drawbridge or on foot: pontoon bridges and engineers aren't in yet. Like a gate, a drawbridge changes only the routes planned after it moves, so a unit already crossing finishes.
- The AI gets a passive trickle of resources on top of what it gathers, scaled by difficulty. It reaches the Bronze Age, and so its siege and castle, late (often after 10–15 minutes, its castle after 20 or more), and its villagers don't avoid your towers when they go looking for resources.
- Territory and the walled-town check are worked out from the buildings, so a save doesn't need to store them. There's no morale or "security" beyond the combat bonuses described above.
- Saves live in one browser. Use export and import to move them to another browser or device.
- The projectile manager also supports fire arrows, which no unit uses yet.
- Touch gestures were tested with simulated touch events and phone-sized screens, not on physical devices.
- Orders aren't queued: a new order replaces the current one (an attack-move or patrol remembers itself while its unit fights). There's no multiplayer, so there's nothing to recover across players.

## Ideas for contributions
- More defences, each one data entry: a `BLDTYPES` entry with a `role` and a `menu` page (joins, armour class, siege priority, repairs, the AI's planning and, until it has art of its own, its picture follow from `ROLES`), plus `lay: 'line'` if it's wall-like, a `trigger` if it springs, a `SPRITES` set or `art` for its look; a stronger tower or keep is one `TOWER_TIERS` row at the end; one `AI_FORT_PLAN` step has the AI build it. A siege tower that climbs walls, or murder holes that need a unit underneath, would need new behaviour.
- More siege engines (mangonels, siege towers, bombards): one `UNITTYPES` entry with `cls: 'siege'`, a `siegeRole`, its `targets` and stats, and one `PROJ_TYPES` entry for its `projectileType`. It is built at the Siege Workshop, picks its targets, deploys, fires, saves and shows up in the AI's mix with no other change. Add a `UNIT_ART` entry with a `draw` function for a picture of its own. A siege tower that carries troops onto walls would need new behaviour.
- More players per map. `generateWorld` already places starts and shares resources out in pairs, so it would need to work in sets of N instead.
- More warships: one `UNITTYPES` entry with `naval: true`, a `role`, attack stats, a `proj`, a `sprite`, `targets` and `aiOrders`. It is built at the Dock, picks its targets, fights, saves, sinks and joins the AI's fleet with no other change. Give it a new picture with a `SPRITES` entry: a `model`, or a `sheet` image. Ships that fight land units or carry troops into battle would need new behaviour.
- A map editor that saves a seed's terrain with your changes (saves already store terrain per tile)
- Queued orders (shift-click a chain of orders), and more AI patrol routes (between its docks, along its walls), each one more `AI_PATROLS` row

---

## Disclaimer

This is a non-commercial project. All art and sound are generated in code.
