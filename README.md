# KANTMICROGAME

Tiny, cute, pixel-art HTML5 micro games — **all inside ONE single HTML file**. The
arcade shelf and every game live together in `index.html`: open it, pick a game, play a
minute, smile. Fully offline by double-clicking; the rest of the folder is only
documentation. (After round 1 the owner pivoted from one-folder-per-game to this
one-file architecture — see `plans/micro-games-v2.md`.)

**Current state:** build 20261031-002 — the one-file app with PANDASNACK playable.  
**Built with:** GLM-5.3-Flash Free (OpenCode), recorded per build in `CHANGELOG.md`,
the prompt copies and the plan's tool/model log (a standing owner request).

## How to open and play

- Double-click `index.html`. The shelf shows one game card today — **PANDASNACK** —
  with its pixel preview, concept line and best score, plus a dashed COMING SOON slot.
- Click a card to open the game in the same page (no navigation, no iframes, no folders).
  `ESC` or the ⌂ SHELF button always brings you home.
- Tip: open `index.html#game=PANDASNACK` to land straight in a game.
- PANDASNACK controls: `W A S D` (+arrow keys) move, `SPACE`/tap to dash, `R` restarts
  instantly; on phones: the four pads plus DASH plus RESTART. Three stings end a run.

## Every micro game follows the seven rules

| # | Rule | Meaning |
|---|---|---|
| 1 | One file | The shelf and every game live inside the one `index.html`; a new game is one new module and adds zero files. |
| 2 | Offline | Works with the internet off: no web fonts, no CDN, no downloaded media. |
| 3 | Tiny stage | A `100 x 100` design-pixel canvas shared by all games, scaled up in whole numbers so pixels stay crisp. |
| 4 | Pixel art | Everything inside the stage is drawn as pixels — chubby shapes, big eyes, 2-6 frame animations, pastel palette. Emoji only outside the stage. |
| 5 | Simple controls | `W A S D` (+arrows) and a shared action button; shared chunky touch pads on phones. |
| 6 | One concept | One screen, one verb, one rule short enough to say in one sentence. |
| 7 | Short play | A run lasts about 30 to 120 seconds and restarts in one press from any state. |

## How the one file is organized

```
KANTMICROGAME/
  index.html            the whole app: shelf screen + game screen + game modules
  README.md             this guide (with a manual per game, below)
  CHANGELOG.md          one entry per finished build, with tool/model per build
  plans/micro-games.md       plan v1 (folder-per-game era) — kept for history
  plans/micro-games-v2.md    the current plan (one-file pivot)
  prompts/P-00…P-02     one prompt copy per build
```

Inside the file: an app runtime (screen swap, `#game=NAME` hash routing, shared
keyboard/pads, one fixed-step loop that ticks only the open game), a once-defined
pixel helper layer (`paintPixels`, `paintRoundBlob`, `paintEyes`, 3×5 pixel font,
`paintPixelText`), and one self-contained IIFE module per game with its own `SETTINGS`,
palette and maps. Best scores save to `KANTMICROGAME.<GAME>.best`, so scores survive
re-factors. Copy this single file anywhere — even alone — and it still works.

## PANDASNACK (module content: 20261031-001)

A chubby panda scurries on a tiny pastel meadow, munching the two bamboo shoots that
are always around (+1 each) while wasps drift past: a sting costs one heart with 1.6 s
of shy flashing, and three stings end the run. Dash (0.7 s at 1.75× speed, 2.2 s
cooldown) is the save-me button. Difficulty climbs by table: 1→4 wasps, speed 13→26 as
the score grows. The run ends with droopy ears, one tear, and the best score saved.

| Name | Meaning | Value | Range |
|---|---|---:|---|
| `moveSpeedDesignPixelsPerSecond` | stroll speed | 26 | 10–60 |
| `dashSpeedMultiplier` / `dashSeconds` | dash strength/length | 1.75 / 0.7 | 1–3 / 0.3–2 |
| `dashCooldownSeconds` | dash refill | 2.2 | 1–6 |
| `startingHearts` | stings that end a run | 3 | 1–5 |
| `secondsOfProtectionAfterHit` | shy flashing | 1.6 | 0–3 |
| `pandaCenterHitRadius` / `waspHitRadius` | sting distances | 7.0 / 6.5 | 4–12 / 3–10 |
| `bambooShootsOnStage` / `bambooRespawnDelaySeconds` | shoots | 2 / 0.45 | 1–4 / 0–2 |
| `minBambooDistanceFromPanda` / `...FromBamboo` | shoot spacing | 14 / 16 | 8–40 / 10–50 |
| `firstWaspSpawnDelaySeconds` | calm start | 1.2 | 0–5 |
| `waspWaveAmplitude` / `waspWaveSeconds` | wasp bob | 2.5 / 3.0 | 0–6 / 1–8 |

Difficulty bands (unlocked by score): ≤4 → 1 wasp every 2.7 s at speed 13; ≤9 → 2
wasps / 2.0 s / 17; ≤14 → 3 / 1.6 / 21; beyond → 4 / 1.25 / 26. All 31 palette colors
are named in the module's `palette` (see the `PAL` block inside `index.html`).

## Where things go next

| Build | Status | Deliverable |
|---|---|---|
| 000–001 | done | Round 0 scaffold + round 1 PANDASNACK (folder era, then preserved here). |
| 002 | done | The one-file pivot: everything lives in `index.html`; `games/` removed. |
| 003 | next | Round 2 game: a second module with a different control verb (backlog: DUCKLINE, BOOPEEK, CATNAPCATCH…). |

## What is not built yet

Sound, sharing between games, score sending, main-game embedding, a variant generator —
none of these exist. Nothing outside `KANTMICROGAME/` is touched, and no git commands
are run on the owner's repo (they upload/merge to GitHub themselves).

## Files in this folder

- `index.html` — the one-file app (shelf + games), build 20261031-002.
- `README.md` — this guide.
- `CHANGELOG.md` — build history with tool/model per build.
- `plans/micro-games.md`, `plans/micro-games-v2.md` — plan v1 (history) and v2 (current).
- `prompts/P-00_round-0_project-kickoff.txt` — round 0 prompt copy.
- `prompts/P-01_round-1_pandasnack.txt` — round 1 prompt copy.
- `prompts/P-02_round-1-5_one-file-pivot.txt` — the one-file pivot prompt copy.

## Prompt history

The `prompts` folder holds the prompt copies used to build this project, one per build,
the same way our other KANT projects keep them.
