# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Desktop players and touch players count equally. Neither is the default design target.

- **Desktop players** use a mouse and keyboard. Many know classic age-progression strategy games (villagers, a Town Center, advancing through ages) and expect hotkeys, box selection, right-click orders and a dense command panel.
- **Touch players** use phones (portrait and landscape), tablets and touch laptops. They often arrive from the live demo link and learn the game as they play.

Both groups want to play a full match against the AI in a browser tab: gather, build, advance through the ages, defend, and destroy every enemy building. They then come back to their saves, the campaign, their score and their rank.

Contributors who read the code and extend its data tables are a secondary audience. The README addresses them, but they are not a design target for the interface.

## Product Purpose

Aethoria is a small real-time strategy game played against one AI opponent. The game, its graphics and its sound are all in one HTML file.

Success means two things, and both are confirmed:

1. **Players finish matches and come back.** The 12-step mission campaign, the persistent high score, the XP rank, the 15 achievements, the five save slots and the autosaves exist for this.
2. **It shows what one HTML file can do.** Every sprite, terrain tile, icon, sound effect and piece of music is generated in code. There is no build step and there are no dependencies.

## Positioning

Aethoria is a full classic-era strategy game in one HTML file with no image or audio files. It has an economy, three ages, a navy, siege engines, fortifications, and an AI that builds walls, ferries armies and invades by sea. It plays with touch as completely as with a mouse and keyboard. The simulation is deterministic, so a loaded save carries on exactly as the live game would have.

## Operating Context

- **Where it runs:** the live demo on GitHub Pages (https://aminul1993.github.io/Aethoria/) serves `index.html` from the repository root. Players can also download `index.html` and open it straight from disk, with no server.
- **A session:** title screen → New Game (map type, size, seed, resource level, difficulty, slot and name) → the match → the pause menu, save screen and end screen. During a match the screen has a resource bar at the top, a mission card, and a bottom panel with the minimap, the info panel and the command grid.
- **Input:** a mouse and keyboard with hotkeys, or touch gestures: tap, long-press for the command menu and information cards, two-finger scroll, pinch zoom, and a three-finger tap for the strategic overview. On a phone held sideways, the minimap and commands move to a side column.
- **Persistence:** browser `localStorage` only, under keys that start with `aethoria.`. Players move saves between browsers or devices by exporting and importing JSON files.
- **Offline:** the game runs with no network. Fonts fall back when Google Fonts can't be reached.

## Capabilities and Constraints

**Binding constraints (confirmed):**

- The whole game stays in one HTML file (`index.html`) with a single `<script type="module">`. There is no build step, no dependency and no framework.
- There are no image or audio files. All art, icons, terrain, sound effects and music are generated in code with Canvas 2D and the Web Audio API.
- Google Fonts is the only network request allowed. The game must stay fully playable offline with fallback fonts.
- The game must stay fully playable by touch. In touch mode every control is at least 48×48 px.
- The game supports current Chrome, Edge, Firefox (126 or later, because interface scaling uses CSS `zoom`) and Safari.

**Files:**

- `index.html` is the live game (version 1.3.0) and the only file future work edits.
- `index1.html` is an archive of the earlier look: beveled panels, parchment dialogs and Spectral type. It is kept for reference only. Leave it untouched.

**Capabilities:** `README.md` is the complete reference. It covers the economy, ships and ferrying, naval combat, 17 procedural map types in four sizes, construction, three ages, combat and counters, ranged units, cavalry, fortifications, siege, orders, formations, the AI, fog of war, the minimap, four zoom layers, save slots, upgrades, missions, settings, touch play and generative music.

**Terminology:**

- **Ages:** Stone Age, Tool Age, Bronze Age.
- **Key buildings:** Town Center, Storage Pit, Dock, Siege Workshop.
- **Zoom layers:** Close, Medium, Far, Strategic.
- **Difficulty levels:** Easy, Normal, Hard.
- **Interface themes:** Gold and ember, Midnight, High contrast.

**Known limits, stated openly in the README:**

- There is one AI opponent, so every map has two players.
- There is no multiplayer.
- Orders can't be queued.
- Touch gestures have been tested only with simulated touch events and phone-sized screens, not on physical devices.

## Brand Commitments

- **Name:** Aethoria. The title screen line is "A STRATEGY GAME IN THE BROWSER".
- **Non-commercial and open source:** the game is MIT licensed (© 2026 Aminul1993). The README disclaimer says all art and sound are generated in code.
- **Voice (seen in the README and the interface, not separately confirmed):** plain, direct sentences in British spelling (colour, armour, favourites, defences). Instructions say exactly what happens.

## Evidence on Hand

- `README.md` has the full feature list, the controls and the gameplay reference.
- The live demo is at https://aminul1993.github.io/Aethoria/.
- There are no screenshots, logos or image files in the repository. The game draws everything at load.
- There are no player numbers, reviews, testimonials, press coverage or download statistics. Future work must not invent any.

## Product Principles

1. **One file, made in code.** Anything new lives inside `index.html` and is generated when the page loads. Work that needs an asset file, a dependency or a build step is out of scope.
2. **Desktop and touch are equal.** A feature is done only when it works with a mouse and keyboard and with touch, on every screen from a phone held sideways to a large monitor.
3. **Worth coming back to.** Saves, the campaign, score and rank are part of the product. Never put a player's progress at risk.
4. **Honest about limits.** Describe what the game does as precisely as the README does, and state its gaps rather than hiding them.

## Accessibility & Inclusion

These features already exist and must be preserved:

- A High contrast interface theme.
- Colour-blind-friendly team colours.
- A reduced-motion setting, which also follows the system's `prefers-reduced-motion`.
- Longer on-screen messages.
- A setting that turns the atmosphere effects off.
- Touch targets of at least 48×48 px in touch mode.
- A UI scale from 80% to 140%, applied on top of automatic interface fitting.
- An option to swap the mouse buttons.

**Open decision:** no formal accessibility standard, such as a WCAG level, has been set.
