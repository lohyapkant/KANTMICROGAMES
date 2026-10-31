# Plan: KANTMICROGAME — HTML5 Micro Games (v2 — the one-file pivot)

Today: 2026-10-31. Status: build 20261031-003 done — the shelf and PANDASNACK + BOOPEEK
now live together in ONE file (the one-file pivot of round 1.5, round 2 shipped BOOPEEK).
Round 3 (a third module) is next.

Supersedes micro-games.md (v1), kept as history: v1 described one file per game in
separate folders; the owner changed their mind after round 1 — see prompt P-02.

## Objective

One single HTML file, `KANTMICROGAME/index.html`, contains the arcade shelf AND every
micro game. Tiny, cute, pixel-art games; round-by-round builds like our other KANT
projects; fully offline by double-clicking. The folder beside the file holds only
documentation (README, CHANGELOG, plans, prompts) — no code files, no game folders.

Long-term: some of these micro games may live inside one bigger game later — but we are
NOT building any sharing, engine, SDK or embedding support now.

## What counts as a micro game — the seven rules

| # | Rule | Meaning |
|---|---|---|
| 1 | One file | The shelf and every game live inside the one `index.html`. A new game adds zero files: it is one new module inside the file. |
| 2 | Offline | Double-click works with the internet off; no web fonts, no CDN, no images loaded from disk or web. |
| 3 | Tiny stage | The game world is a small fixed canvas of `100 x 100` design pixels (default); the page around it may be bigger. One stage canvas is shared by every game. |
| 4 | Pixel art | All art drawn as pixels on the stage grid: chubby rounded shapes, big eyes, 2-6 frame squishy animations, pastel palette. Emoji only OUTSIDE the stage. |
| 5 | Simple controls | `W A S D` always works (plus arrows), `Space` is the shared action button; phones get the shared chunky pads around the stage. |
| 6 | One concept | One screen, one verb, one rule a child can restate in one sentence. |
| 7 | Short play | A run lasts about 30 to 120 seconds, with instant restart in one tap or key press, from any state. |

## Project layout

```
KANTMICROGAME/
  index.html            <- EVERYTHING: shelf screen + game screen + all game modules
  README.md             <- project guide + a short manual per game
  CHANGELOG.md          <- one entry per finished build (builds, not rounds)
  plans/micro-games.md       <- v1 plan, kept for history
  plans/micro-games-v2.md    <- this plan (later pivots add v3, v4 …)
  prompts/P-XX_*.txt    <- one prompt copy per build, per KANTPLANEINVASION convention
```

Nothing else in the project folder; no other workspace folder is touched. The owner
uploads/merges changes to GitHub themselves.

## How the one file is organized

| Part of the file | Holding |
|---|---|
| `<style>` | The two screens' looks: shelf chrome + game chrome, shared design tokens |
| `<section id="shelfScreen">` | The arcade shelf the player sees first |
| `<section id="gameScreen" hidden>` | One shared stage canvas, one shared pad deck, shared chips — used by whichever game is open |
| PART 0 — app + storage | File version, save keys (`KANTMICROGAME.<GAME>.best`), read/save helpers |
| PART 1 — shared helpers | `paintPixels` (with scale + flip), `paintRoundBlob`, `paintEyes`, the 3×5 pixel font, `paintPixelText` — defined ONCE here, used by mascot, previews and games |
| PART 2–3 — shelf | Mascot animation, card builder, coming-soon slot |
| PART 4 — runtime | `GAMES` registry, screen swap, shared keyboard + pad routing, hash routing (`#game=NAME`), stage scaling, the one loop |
| PART 5 — game modules | One self-contained IIFE per game: its own `SETTINGS`, palette, maps, state — registered into `GAMES` |
| PART 6 — boot | Stamp version, build shelf, wake mascot, follow hash, start loop |

### The module contract (how a game plugs in)

Each game module provides: `id, name, tagline, concept, actionLabel, hint,
versionNumber, previewPaint` plus `start(), stop(), restart(), update(dt), paint(ctx),
onDir(dir, pressed), onAction(), onStageTap(), onAnyKey()`. The runtime opens/closes
games, feeds events, ticks and paints only the open module, and keeps instant restart
(`R`) and `ESC`-to-shelf working for every game for free.

### How a game behaves inside the file

- The game's `SETTINGS` keeps its own `versionNumber` (its content build number); the
  FILE has its own build number in the footer. A inside-file refactor of a game that
  keeps content identical leaves the game's number alone (PANDASNACK stays -001).
- Saves use the same keys as always, so an old best score survives the merge.
- Any-key start and stage taps are decided by the module (`onAnyKey`, `onStageTap`).

## Stage and controls spec (unchanged in spirit from v1)

- Exactly `100 x 100` design pixels; whole-number integer scaling only;
  `image-rendering: pixelated`; refit on resize and rotation.
- Fixed-step update (60 steps/second) with capped catch-up, inside each module.
- All stage colors referenced BY NAME from the game's own `palette`.
- Difficulty if present is one table of bands unlocked by score/time (BOOPEEK has none —
  the cozy poke game keeps it simple by design).
- `W A S D` + arrows move; `Space`/action pad is the action (dash in PANDASNACK, poke in
  BOOPEEK); `R` restarts instantly; stage tap = module's choice (dash in PANDASNACK, poke in
  BOOPEEK); `ESC` or ⌂ SHELF exits home.

## Definition of done (per build)

1. All seven rules pass; no console errors during 5 minutes of play; resize/rotation refit without reload.
2. The headless smoke test still passes: shelf routes into a game by hash, the game runs walking/dashing/restarting without exceptions, ESC returns to the shelf, reopening re-runs `start()` cleanly.
3. Touch + keyboard both playable (phone check on real Safari pending and honestly noted until done).
4. README updated (its per-game manual section), CHANGELOG entry with the file build number and tool/model line, prompt copy saved, tool/model log row added, backlog row updated.
5. Shelf card shows the game with preview, concept and best score.

## Build ledger

| Build | Date | Deliverable |
|---|---|---|
| 20261031-000 | 2026-10-31 | Round 0 scaffold (v1 architecture: folder per game). DONE. |
| 20261031-001 | 2026-10-31 | Round 1: PANDASNACK shipped in `games/PANDASNACK/`. DONE. |
| 20261031-002 | 2026-10-31 | One-file pivot: shelf + game screens + shared helper layer + PANDASNACK folded in as a module; `games/` deleted; hash routing; pads/keys re-routed through the runtime. DONE. |
| 20261031-003 | 2026-10-31 | Round 2: BOOPEEK shipped as the second module (shy ghost poke) inside the one-file app; CHANGELOG/README/plan/prompt updated; smoke re-run green. DONE. |

## Tool and model log (owner request, 2026-10-31)

Standing convention in four homes: this plan, the CHANGELOG, the project README and
the build's prompt copy.

| Build | Date | Tool and model that did the building |
|---|---|---|
| 000 | 2026-10-31 | GLM-5.3-Flash Free (OpenCode) |
| 001 | 2026-10-31 | GLM-5.3-Flash Free (OpenCode) |
| 002 | 2026-10-31 | GLM-5.3-Flash Free (OpenCode) |
| 003 | 2026-10-31 | GLM-5.3-Flash Free (OpenCode) |

Rule: every future build truthfully records its model in all four homes.

## Game backlog (concepts sized for a 100×100 stage)

| Name | One sentence | Verb | Status |
|---|---|---|---|
| PANDASNACK | A chubby panda scurries to eat bamboo shoots while wasps drift past. | WASD dodge+dash | in the file (round 1) |
| DUCKLINE | A mother duck crosses a pond; collected ducklings waddle in a line behind her. | WASD lead-a-chain | backlog — round 2 candidate |
| SPROUTUP | A baby sprout climbs a rain of water drops; sun settles, it blooms — short and lovely. | WASD weave | backlog |
| SLIMEHOP | A bouncing slime must only land on lily pads that float apart over time. | WASD + Space hop timing | backlog |
| BOOPEEK | A shy ghost peeks from doors; poke it before it hides — cozy not scary. | WASD walk + Space poke | built in round 2 (module content 20261031-003) |
| SNAILRACE | Race three snails; food pellets speed you up, salt slows — tiny arcade. | WASD steer | backlog |
| HUGPARADE | Two round friends reunite across a maze that redraws itself every 10 seconds. | WASD only | backlog |
| CATNAPCATCH | Guard a sleeping cat from falling noise-makers with a paper pillow. | WASD catch | backlog |

Names are placeholders; a round may rename its game before it ships.

## What we are NOT doing now

- No game folders, no extra code files, no imports between games, no build tools.
- No iframe embedding, no postMessage API, no main-game hooks, no audio yet.
- Nothing outside `KANTMICROGAME/` is created, moved or edited; no git commands
  run on the owner's repo — they upload/merge to GitHub themselves.
