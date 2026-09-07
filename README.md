# BUBBLEDEEP 🐠✨

Sibling of CastleForge, sequel to IslandForge. One static `index.html` — no build
step, no dependencies, Canvas 2D with a real dynamic lighting engine. Deploys
anywhere that serves static files (render.com etc.).

## Play it

- Open `index.html` directly, **or** `python3 -m http.server 8644` → http://localhost:8644
- Saves to localStorage (`bubbledeep-save-v1`), autosaves constantly.

## Controls

| Input | Action |
|---|---|
| Arrows / WASD / left stick | Swim (momentum + drag — it feels floaty on purpose) |
| X / Space / south button | Grab, talk, pet, open, repair, fire |
| C / west button | Build menu |
| V / north button | Captain's Log (stats + hat picker) |
| Z / Esc / east button | Pause / cancel |
| M | Sound on/off |
| Touch | Virtual joystick + GRAB / BUILD buttons |

Gamepads via the same guarded `window.ArcadeController` shell as IslandForge.

## The game

Side-view ocean canyon, 6,400 units deep. 37 quests, one at a time, every quest
drops a glowing crate (loot or one of 6 hats). Your dive suit is the age system —
6 gear tiers, each unlocking a deeper zone (a red pressure line pushes you back
until you upgrade at the Gear Station):

1. **Snorkel Kid** — the Sunny Shallows
2. **Bubble Suit** — the Kelp Forest
3. **Brass Diver** — the Twilight Zone + Wreck Reef (build ON the pirate ship deck)
4. **Glow Suit** — the Glowing Abyss (headlamp turns on; darkness is real down here)
5. **Magma Suit** — the Boiling Vents (free geothermal volts)
6. **Ancient Armor** — the Lost City

Below it all: a crashed flying saucer. Repair it in 3 stages, press X, and ride
it up through every zone, out of the ocean, into the stars — fireworks, then it
brings you back for free play.

Friends: **Blub** the anglerfish (feed him a taco → follows you forever and
lights your way), a whale that crosses the canyon and says hellooo, pettable
fish-folk residents, a Jellyfish Disco, and a Taco Cannon.

## Notes for the next session

- Data tables at the top of the `<script>`: `ZONES`, `GEAR`, `BLD`, `GOALS`,
  `HATS`, `SAUCER_STAGES`.
- World is deterministic (seeded); saves store buildings + counters only.
- Volts are a global power pool (make vs use); short-powered buildings idle with 💤.
- The lighting pass is `drawLighting()` — darkness by depth, holes punched per
  light source, plus a colored additive glow pass.
