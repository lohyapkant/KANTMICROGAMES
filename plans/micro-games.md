# Plan: KANTMICROGAME — HTML5 Micro Games (v1)

Today: 2026-10-31. Status: round 1 complete — shelf active, PANDASNACK playable.
(Historical: after this round the owner pivoted to a one-file architecture;
see micro-games-v2.md — this v1 plan stays as history.)

## Objective

Fill the `KANTMICROGAME/` folder with tiny, cute, pixel-art HTML5 games. Each game is one
single-file `index.html` that works offline by double-clicking. A selection page lists every
game so a player can pick one. Games are built round-by-round, one game (or one scaffold step)
per round, in the same style as our other KANT projects.

Long-term: some of these micro games may live inside one bigger game later — but we are NOT
building any sharing, engine, SDK or embedding support now. Every game stays fully
self-contained and standalone.

## What counts as a micro game — the seven rules

Every game must obey all seven:

| # | Rule | Meaning |
|---|---|---|
| 1 | Single file | One `index.html` per game; no other files, no imports, no network. |
| 2 | Offline | Double-click works with the internet off; no Google Fonts, no CDN, no images loaded from disk or web. |
| 3 | Tiny stage | The game world is a small fixed canvas of `100 x 100` game pixels (default). The living page around it may be bigger. |
| 4 | Pixel art | All art drawn as chunks on the stage grid. Rounded-cute shapes, big eyes, 2-6 frame squishy animations, pastel palette. Emoji are allowed only OUTSIDE the stage. |
| 5 | Simple controls | Keyboard `W A S D` always works (plus Space per game when needed). On touch, virtual buttons drawn on the page around the stage. |
| 6 | One concept | One screen, one verb, one rule a child can restate in one sentence. |
| 7 | Short play | A run lasts about 30 to 120 seconds, with instant restart in one tap or key press. |

## Project layout

```
KANTMICROGAME/
  index.html            <- the selection page (arcade shelf) — also single-file, offline
  games/
    <NAME>/index.html   <- one game per folder, NAME is short ALL-CAPS, e.g. PANDASNACK
    <NAME>/README.md    <- added when a game needs one; short by default
  plans/micro-games.md  <- this plan (new versions copy the pattern: micro-games-v2.md)
  prompts/P-XX_*.txt    <- prompt copy for every round, per KANTPLANEINVASION convention
  CHANGELOG.md          <- one entry per finished round across the whole project
```

No other workspace folder is touched by this project.

## The stage spec (details that every game follows)

- Stage canvas is exactly `stageSize x stageSize` game pixels (default `100 x 100`), declared in the game's settings table.
- The canvas element on screen is the largest whole-number scale of the stage that fits the viewport, so pixels stay crisp:
  `image-rendering: pixelated`, integer scale only, re-fit on resize and phone rotation.
- Drawing uses one tiny helper set shared by-copies inside each file (same function names, copied text): `clearStage`, `paintPixels`, `paintRoundBlob`, `paintEyes`, `paintPixelText` (`3 x 5` pixel font baked in), so stage text always looks pixel, never browser-smooth.
- UI text OUTSIDE the stage (title, score, hints) uses the system rounded font stack (`-apple-system` … `ui-rounded`), so nothing imports a web font.
- Game clock: fixed-step update (60 per second) with a capped frame catch-up, safe on slow phones.

## Controls spec

| Input | Behavior |
|---|---|
| `W A S D` | Primary move (8 directions when two keys held) on every game, no exceptions. |
| `Space` | Optional per-game action button (jump, squash, fire, peck…). |
| Touch move | A virtual d-pad panel beside the stage; big tap targets, multi-touch safe, pointer events, no double-tap zoom (`touch-action: none`). |
| Restart | Press `R` or tap the RESTART button instantly; one press from any state including win/lose. |

The visible page = a cute "toy console" chrome: title ribbon, the glowing stage in the middle,
score / best-score labels, and the control pads. This gives the small game real screen
presence without making the stage itself big.

## Per-game recipe (settings style, like KANTPLANEINVASION)

Every game starts with one `SETTINGS` object holding named values, all tuned from one place:

```
const SETTINGS = {
  gameName: "PANDASNACK",
  versionNumber: "001-20261031",       // date + increasing 3-digit count
  stageSize: 100,
  palette: { ... },                    // every color referenced by NAME, never a raw hex in draw code
  playerSettings: { ... },             // speed, size, animation frames …
  worldSettings: { ... },              // spawns, timers, difficulty curve …
};
```

Difficulty if present is one curve from a table (rows = minute/level, values = spawn rates), not special cases.

## Selection page spec

- Single-file `KANTMICROGAME/index.html`, offline, same toy-console look.
- One card per game: pixel-art mini preview (a tiny canvas painted in code — never a screenshot file), name, one-line concept, best score read from `localStorage` if the game writes it there.
- Cards are plain `<a href="games/NAME/index.html">` links — navigation only, no iframes (file:// iframes are unreliable).
- An empty "COMING SOON" slot card at the end so the shelf always has room to grow.

## Definition of done (per game round)

1. All seven micro-game rules pass.
2. No console errors during 5 minutes of play; resize and rotation refit without reload.
3. Touch + keyboard both playable on real phone (Safari) and desktop.
4. README updated: what it is, how to play with both input types, the settings table with names and allowed ranges, palette table.
5. CHANGELOG entry with version number; prompt copy saved to `prompts/`.
6. Selection page lists the game with its preview and concept line.

## Build rounds

| Round | Version | Deliverable |
|---|---|---|
| 0 | 000-20261031 | DONE — Scaffold: selection page (arcade shelf), folder layout, README, CHANGELOG, prompts folder. |
| 1 | 001-20261031 | DONE — First game, PANDASNACK, translated through the Stage spec, with its shelf card, game README and prompt copy. Hands-on phone test still pending. |
| 2 | 002-20261031 | NEXT — Second game with a DIFFERENT control verb (one move-only, one action-button). |
| 3 | 003-20261031 | Third game; then review: were the stage helpers enough? Adjust template. |
| 4+ | … | One game per round; polish round any time a shelf entry is rough. |

Each round produces exactly one finished, shippable thing. We stop, play, then plan the next round.

## Tool and model log (owner request, 2026-10-31)

The owner asked that the model behind each round be recorded as a standing
convention in four homes: this plan, the CHANGELOG, the README (project level) and
the round's prompt copy. The log itself lives here and grows one row per round.

| Round | Date | Tool and model that did the building |
|---|---|---|
| 0 | 2026-10-31 | DeepSeek V4.1 Flash Free (OpenCode) — corrected in build 006 (originally recorded as GLM-5.3 Flash Free) |
| 1 | 2026-10-31 | DeepSeek V4.1 Flash Free (OpenCode) — corrected in build 006 (originally recorded as GLM-5.3 Flash Free) |

Rule for future rounds: every CHANGELOG entry carries its "Tool and model:" line,
every prompt copy names the model that saved it, and a new row lands in this table.
If a round is finished by a different model, that model is named truthfully.

## Game backlog (concepts sized for a 100×100 stage)

| Name | One sentence | Verb | Status |
|---|---|---|---|
| PANDASNACK | A chubby panda scurries to eat bamboo shoots while wasps drift past. | WASD dodge+collect | built in round 1 |
| DUCKLINE | A mother duck crosses a pond; collected ducklings waddle in a line behind her. | WASD lead-a-chain | backlog |
| SPROUTUP | A baby sprout climbs a rain of water drops; sun settles, it blooms — short and lovely. | WASD weave | backlog |
| SLIMEHOP | A bouncing slime must only land on lily pads that float apart over time. | WASD + Space hop timing | backlog |
| BOOPEEK | A shy ghost peeks from doors; poke it before it hides — cozy not scary. | WASD walk + Space poke | backlog |
| SNAILRACE | Race three snails; food pellets speed you up, salt slows — tiny arcade. | WASD steer | backlog |
| HUGPARADE | Two round friends reunite across a maze that redraws itself every 10 seconds. | WASD only | backlog |
| CATNAPCATCH | Guard a sleeping cat from falling noise-makers with a paper pillow. | WASD catch | backlog |

Names are placeholders; a round may rename its game before it ships.

## What we are NOT doing now

- No shared engine file, no import-from-file, no package tools.
- No iframe embedding, no postMessage API, no main-game hooks.
- No multi-file assets, no audio yet (WebAudio beeps may arrive in a later round if wanted).
- Nothing outside `KANTMICROGAME/` is created, moved or edited.
