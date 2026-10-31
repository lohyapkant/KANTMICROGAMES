# KANTMICROGAME

Tiny, cute, pixel-art HTML5 micro games — **all inside ONE single HTML file**. The
arcade shelf and every game live together in `index.html`: open it, pick a game, play a
minute, smile. Fully offline by double-clicking; the rest of the folder is only
documentation. (After round 1 the owner pivoted from one-folder-per-game to this
one-file architecture — see `plans/micro-games-v2.md`.)

**Current state:** build 20261031-003 — the one-file app with **PANDASNACK** (module
content: 20261031-001) and **BOOPEEK** (module content: 20261031-003) playable from the
shelf.

## Models used thus far

All builds so far were made with the same model, **GLM-5.3 Flash Free** (full name:
GLM-5.3 Flash Free), through the **OpenCode** tool. Per the owner's standing request, the
model, effort, duration and token count are recorded in the CHANGELOG, the plan, the
README and the prompt copies.

| Build | Full model name | Effort | Duration | Tokens |
|---|---|---|---:|---:|
| 20261031-000 | GLM-5.3 Flash Free (OpenCode) | Round 0 scaffold | not recorded | not recorded |
| 20261031-001 | GLM-5.3 Flash Free (OpenCode) | Round 1 — PANDASNACK module + docs | not recorded | not recorded |
| 20261031-002 | GLM-5.3 Flash Free (OpenCode) | Round 1.5 — one-file pivot rewrite | not recorded | not recorded |
| 20261031-003 | GLM-5.3 Flash Free (OpenCode) | Round 2 — BOOPEEK module + wiring + docs + verification | **~45 min** | **~27,000** |

Build 20261031-003 is the first whose effort, duration and token count were recorded; the
earlier builds predate that recording.

## How to open and play

- Double-click `index.html`. The shelf shows the game cards today — **PANDASNACK** and
  **BOOPEEK** — with their pixel previews, concept lines and best scores, plus a dashed
  COMING SOON slot.
- Click a card to open the game in the same page (no navigation, no iframes, no folders).
  `ESC` or the ⌂ SHELF button always brings you home.
- Tip: open `index.html#game=PANDASNACK` or `index.html#game=BOOPEEK` to land straight in a
  game.
- PANDASNACK controls: `W A S D` (+arrow keys) move, `SPACE`/tap to dash, `R` restarts
  instantly; on phones: the four pads plus DASH plus RESTART. Three stings end a run.
- BOOPEEK controls: `W A S D` (+arrow keys) walk the visitor toward the cozy door, `SPACE`
  / tap the stage (or the POKE pad on phones) pops the shy ghost; `R` restarts instantly;
  on phones: the four pads plus POKE plus RESTART.

## The seven rules

| # | Rule | Meaning |
|---|---|---|
| 1 | One file | The shelf and every game live inside the one `index.html`; a new game is one new module and adds zero files. |
| 2 | Offline | Works with the internet off: no web fonts, no CDN, no downloaded media. |
| 3 | Tiny stage | A `100 x 100` design-pixel canvas shared by all games, scaled up in whole numbers so pixels stay crisp. |
| 4 | Pixel art | Everything inside the stage is drawn as pixels — chubby shapes, big eyes, 2-6 frame animations, pastel palette. Emoji only outside the stage. |
| 5 | Simple controls | `W A S D` (+arrows) and a shared action button; shared chunky touch pads on phones. |
| 6 | One concept | One screen, one verb, one rule short enough to say in one sentence. |
| 7 | Short play | A run lasts about 30 to 120 seconds and restarts in one press from any state. |

## The micro games

- **PANDASNACK** (module content: 20261031-001): a chubby panda scurries on a tiny pastel
  meadow, munching the two bamboo shoots that are always around (+1 each) while wasps drift
  past; a sting costs one heart with 1.6 s of shy flashing, and three stings end the run.
  Dash (0.7 s at 1.75× speed, 2.2 s cooldown) is the save-me button; difficulty climbs by
  table.
- **BOOPEEK** (module content: 20261031-003): a shy ghost (BOO) peeks from a cozy door; the
  visitor walks up with WASD and pokes with SPACE / tap / the POKE pad; each poke scores
  +1 and pops warm star sparkles; victory is poking him 10 times.

## How the one file is organized

The file holds: an app runtime (screen swap, `#game=NAME` hash routing, shared keyboard and
pads, one fixed-step loop), a once-defined pixel helper layer (`paintPixels`,
`paintRoundBlob`, `paintEyes`, 3×5 pixel font, `paintPixelText`), and one self-contained
game module per game. Best scores save to `KANTMICROGAME.<GAME>.best`, so scores survive
re-factors.

## Where things go next

| Build | Status | Deliverable |
|---|---|---|
| 000–001 | done | Round 0 scaffold + round 1 PANDASNACK (folder era, then preserved here). |
| 002 | done | The one-file pivot: everything lives in `index.html`; `games/` removed. |
| 003 | done | Round 2 BOOPEEK: the second module (shy ghost poke) inside the one-file app. |

**Next:** Round 3 — a third module from the backlog (DUCKLINE, SPROUTUP, SLIMEHOP, SNAILRACE,
HUGPARADE or CATNAPCATCH, at the owner's pick).

## What is not built yet

Sound, sharing between games, score sending, main-game embedding, a variant generator —
none of these exist. Nothing outside `KANTMICROGAME/` is touched, and no git commands are
run on the owner's repo (they upload/merge to GitHub themselves).

## Files in this folder

- `index.html` — the one-file app (shelf + games), build 20261031-003.
- `README.md` — this guide.
- `CHANGELOG.md` — build history with tool/model per build.
- `plans/micro-games.md`, `plans/micro-games-v2.md` — plan v1 (history) and v2 (current).
- `prompts/P-00_round-0_project-kickoff.txt` — round 0 prompt copy.
- `prompts/P-01_round-1_pandasnack.txt` — round 1 prompt copy.
- `prompts/P-02_round_1-5_one-file-pivot.txt` — the one-file pivot prompt copy.
- `prompts/P-03_round_2_boopeek.txt` — round 2 (BOOPEEK) prompt copy.

## Prompt history

The `prompts` folder holds the prompt copies used to build this project, one per build,
the same way our other KANT projects keep them.

## Appendix — technical details

- **Module contract:** each game module provides `id, name, tagline, concept, actionLabel,
  hint, versionNumber, previewPaint` plus `start(), stop(), restart(), update(dt), paint(ctx),
  onDir(dir, pressed), onAction(), onStageTap(), onAnyKey()`. The runtime opens/closes
  games, feeds events, ticks and paints only the open module, and keeps instant restart
  (`R`) and `ESC`-to-shelf working for every game.
- **Stage and controls spec:** exactly `100 x 100` design pixels; whole-number integer
  scaling only; `image-rendering: pixelated`; refit on resize and rotation. Fixed-step
  update (60 steps/second) with capped catch-up, inside each module. All stage colors
  referenced by name from the game's own palette. `W A S D` + arrows move; `Space`/action
  pad is the action (dash in PANDASNACK, poke in BOOPEEK); `R` restarts instantly; stage
  tap = module's choice (dash in PANDASNACK, poke in BOOPEEK); `ESC` or ⌂ SHELF exits home.
- **PANDASNACK settings and difficulty (module content 20261031-001):** stroll speed,
  dash strength/length and cooldown, starting hearts, protection seconds, sting radii,
  bamboo counts and spacing, wasp spawn curve and bands unlocked by score.
- **BOOPEEK settings (module content 20261031-003):** poke reach (10 design px), victory
  target (10 pokes), wiggle seconds, mover speed, cozy door placement; no difficulty table
  (short cozy run by design).
