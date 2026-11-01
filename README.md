# KANTMICROGAME

Tiny, cute, pixel-art HTML5 micro games — **all inside ONE single HTML file**. The
arcade shelf and every game live together in `index.html`: open it, pick a game, play a
minute, smile. Fully offline by double-clicking; the rest of the folder is only
documentation. (After round 1 the owner pivoted from one-folder-per-game to this
one-file architecture — see `plans/micro-games-v2.md`.)

**Current state:** build `20261031-005` — the one-file app with **three** playable games:

| Game | Module content | One-line pitch |
|---|---|---|
| **PANDASNACK** | `20261031-001` (frozen) | Munch bamboo, dodge wasps, keep three hearts. |
| **BOOPEEK** | `20261031-005` | Pip the lantern mouse pokes Boo, a shy nightcap ghost. |
| **DUCKLINE** | `20261031-005` | Mama mallard gathers three ducklings and leads them home. |

Build `20261031-005` is the **pre-Round-4 cleanup build**: documentation rewritten,
BOOPEEK and DUCKLINE re-skinned with their own pixel art, and the three game modules
verified to be independent of each other. PANDASNACK was deliberately left untouched.

## Models used thus far

Per the owner's standing request, the model, effort, duration and token count are
recorded in the CHANGELOG, the plan, the README and the prompt copies.

| Build | Full model name | Effort | Duration | Tokens |
|---|---|---|---:|---:|
| 20261031-000 | GLM-5.3 Flash Free (OpenCode) | Round 0 scaffold | not recorded | not recorded |
| 20261031-001 | GLM-5.3 Flash Free (OpenCode) | Round 1 — PANDASNACK module + docs | not recorded | not recorded |
| 20261031-002 | GLM-5.3 Flash Free (OpenCode) | Round 1.5 — one-file pivot rewrite | not recorded | not recorded |
| 20261031-003 | GLM-5.3 Flash Free (OpenCode) | Round 2 — BOOPEEK module + wiring + docs + verification | ~45 min | ~27,000 |
| 20261031-004 | Flint 40B Free (OpenCode) | Round 3 — DUCKLINE module add | ~25 min | ~20,000 |
| **20261031-005** | **DeepSeek V4.1 Flash Free (OpenCode)** | **Pre-Round-4 cleanup: docs rewrite, BOOPEEK + DUCKLINE re-skin, module independence, runtime hardening** | **~1 h 55 min active** | **~2.37 M processed** |

Notes on the `-005` record: duration is **active** working time measured across the two
sittings that produced this build (2026-10-31 21:06 → 2026-11-01 09:18, owner breaks
excluded; wall-clock was ~12 h). Tokens come from the session's full telemetry —
≈1.96 M input + ≈0.31 M generated output + ≈0.11 M reasoning, plus ≈28.4 M cached input
reads — so the figure is not comparable with the rough estimates used for `-003`/`-004`.
Earlier builds predate token/duration recording.

## How to open and play

- Double-click `index.html`. The shelf shows one card per game — PANDASNACK, BOOPEEK and
  DUCKLINE — with a code-drawn pixel preview, a concept line and the best score, plus a
  dashed COMING SOON slot.
- Click a card to open the game in the same page (no navigation, no iframes, no folders).
  `ESC` or the ⌂ SHELF button always brings you home.
- Tip: open `index.html#game=PANDASNACK`, `#game=BOOPEEK` or `#game=DUCKLINE` to land
  straight in a game.
- Every game: `W A S D` (+ arrow keys) move, `SPACE` or the action pad acts, `R` restarts
  instantly. On phones/tablets the four pads + action pad + RESTART appear automatically.
  A stage tap acts too.

| Game | Move | Action (`SPACE` / pad / tap) | Goal |
|---|---|---|---|
| PANDASNACK | scurry | **DASH** (0.7 s at 1.75×, 2.2 s cooldown) | survive: 3 stings end the run |
| BOOPEEK | tiptoe | **POKE** (reach 20 px, 0.1 s cooldown) | 10 pokes in 20 s, then keep going for a high score |
| DUCKLINE | swim | **GO** = quack boost (0.55 s at 1.7×, 2 s cooldown) | collect 3 ducklings and reach the far bank in 22 s |

## The seven rules

| # | Rule | Meaning |
|---|---|---|
| 1 | One file | The shelf and every game live inside the one `index.html`; a new game is one new module and adds zero files. |
| 2 | Offline | Works with the internet off: no web fonts, no CDN, no downloaded media. |
| 3 | Tiny stage | A `100 x 100` design-pixel canvas shared by all games, scaled up in whole numbers so pixels stay crisp. |
| 4 | Pixel art | Everything inside the stage is drawn as pixels — chubby shapes, big eyes, 2-6 frame animations, pastel palette. Emoji only outside the stage. |
| 5 | Simple controls | `W A S D` (+arrows) and a shared action button; shared chunky touch pads on phones. |
| 6 | One concept | One screen, one verb, one rule short enough to say in one sentence. |
| 7 | Short play | A run lasts about 20 to 120 seconds and restarts in one press from any state. |

## The micro games

### PANDASNACK — module content `20261031-001` (frozen)

A chubby panda scurries on a tiny pastel meadow, munching the two bamboo shoots that are
always around (+1 each) while wasps drift past. A sting costs one heart with 1.6 s of shy
flashing; three stings end the run. Dash is the save-me button, and difficulty climbs
through a four-band table (1→4 wasps, speeds 13→26).

**Pixel art:** blob-composed panda with lean-and-waddle walking, random blinks, a happy
munch mouth, dust puffs, droopy ears and a rolling tear at game over; two-frame flapping
wasps; swaying bamboo; sparkle bursts; dot-flowers on a cached two-tone checker meadow;
shared 3×5 pixel font for all stage text.

> **Frozen by owner request.** This module's art, numbers and behaviour must not change
> in later rounds unless the owner asks. See the code banner in PART 5.

### BOOPEEK — module content `20261031-005`

**Pip the lantern mouse** tiptoes through a midnight nursery to poke **Boo**, a shy ghost
in a candy-teal nightcap. Walk close and poke: each poke is +1 and pops a warm ring and
star sparkles. The round lasts **20 s**; reaching the goal of **10** pokes does **not**
end the round, so a good run scores above 10 and the best score is the real target.

**Pixel art (re-skinned in `-005`):** striped plum wallpaper, a moonlit window with a
crescent moon, string lights, a framed heart, a wall clock, a lived-in cupboard where Boo
hides (with a jar on a tiny shelf), a potted plant, a braided rug, a toy ball and a book.
Pip is a cream mouse with pink inner ears, a red scarf and a glowing lantern that lights
the floor around them; Boo is a soft white sheet ghost with a nightcap, pom, blush and a
little tongue, who bobs, blinks and does a happy hop when poked.

### DUCKLINE — module content `20261031-005`

**Mama mallard** swims across a sunny top-down pond with **three ducklings** scattered on
the water — one in a red bow, one with a leaf on its head, one with a single feather tuft.
Swim near a duckling to collect it; collected ducklings fall into a waddling line behind
Mama along her actual path. Reach the far bank within **22 s**. Score = ducklings × 10
plus a time bonus at the shore, so hurry and still gather the family.

**Pixel art (re-skinned in `-005`):** drifting water bands with glints, lily pads, lotus
flowers, cattails, a tiny frog, flowers on both grassy banks and a dragonfly that patrols
the top of the pond. Mama has a green head, white neck ring, cream body, brown chest and
orange bill/feet; the ducklings are fluffy yellow with orange bills and blush. Swimming
leaves elliptical wakes; the GO boost shows a foam splash and a feather gauge top-left.

## How the one file is organized

The file holds four layers:

1. **App runtime** — screen swap, `#game=NAME` hash routing, shared keyboard and pads, one
   fixed-step loop, best-score storage.
2. **Pixel helper layer (PART 1)** — `paintPixels`, `paintRoundBlob`, `paintEyes`, the 3×5
   pixel font and `paintPixelText`, defined once and shared.
3. **Shelf layer** — cards, previews and the panda mascot.
4. **Game modules (PART 5)** — one sealed IIFE per game, each registering itself in `GAMES`.

### Module boundaries — read this before editing

Each game is an IIFE with its own `SETTINGS`, palette, sprite maps, state and draw
helpers. The **only** legal handshake with the app is the module contract plus the shared
pixel helpers, `readBest` / `saveBest`, and the three chrome elements `scoreEl`, `bestEl`,
`msgEl`. Private names carry a game prefix on purpose (`panda` / `PANDA_*`, `peek` / `boo`
/ `pip` / `BOO_` / `PIP_*`, `duck` / `mama` / `DUCK_*`). New modules must paint with the
`ctx` passed to `paint(ctx)` — the shared `stageCtx` habit is a PANDASNACK legacy only.

The same rules are repeated at the top of the `<script>` and above PART 5 in the code, so a
future model or LLM meets them before touching anything.

## Build history and what comes next

| Build | Status | Deliverable |
|---|---|---|
| 000–001 | done | Round 0 scaffold + Round 1 PANDASNACK (folder era, later folded into the one file). |
| 002 | done | The one-file pivot: everything lives in `index.html`; `games/` removed. |
| 003 | done | Round 2 BOOPEEK: second module (shy ghost poke) inside the one-file app. |
| 004 | done | Round 3 DUCKLINE: third module (duck family) added. |
| 005 | done | Pre-Round-4 cleanup: docs, unique BOOPEEK/DUCKLINE art, module independence, runtime hardening. |
| 006+ | next | Round 4 — a fourth module from the backlog (SPROUTUP, SLIMEHOP, SNAILRACE, HUGPARADE or CATNAPCATCH, at the owner's pick). |

## What is not built yet

Sound, sharing between games, score sending, main-game embedding, a variant generator —
none of these exist. Nothing outside `KANTMICROGAME/` is touched, and no git commands are
run on the owner's repo (they upload/merge to GitHub themselves).

## Files in this folder

- `index.html` — the one-file app (shelf + three games), build `20261031-005`.
- `README.md` — this guide.
- `CHANGELOG.md` — build history with tool/model per build.
- `LICENSE` — project licence.
- `plans/micro-games.md`, `plans/micro-games-v2.md` — plan v1 (history) and v2 (current).
- `prompts/` — one prompt copy per build:
  - `P-00_round-0_project-kickoff.txt`
  - `P-01_round-1_pandasnack.txt`
  - `P-02_round_1-5_one-file-pivot.txt`
  - `P-03_round_2_boopeek.txt`
  - `P-04_round_3_duckline.txt`
  - `P-05_cleanup_before-round-4.txt`

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
  pad is the action (dash / poke / quack boost); `R` restarts instantly; stage tap = the
  module's action; `ESC` or ⌂ SHELF exits home.
- **Input hygiene (`-005`):** opening a game, returning to the shelf and losing window
  focus all release every held direction through the module contract, so a key or thumb
  held during a screen swap cannot leak into the next game. The shared loop wraps each
  module tick in `try/catch`, so one broken game can never kill the shelf or the others.
- **PANDASNACK settings and difficulty (module content `20261031-001`, frozen):** stroll
  speed, dash strength/length and cooldown, starting hearts, protection seconds, sting
  radii, bamboo counts and spacing, wasp spawn curve and bands unlocked by score.
- **BOOPEEK settings (module content `20261031-005`):** move speed 30 px/s, poke reach
  20 px, goal 10 pokes, poke cooldown 0.10 s, wiggle/hop 0.34 s, round 20 s, start
  `(26,56)`, ghost home `(78,46)`, Pip walks the floor band y 54–62; save key `KANTMICROGAME.BOOPEEK.best`; no difficulty
  table (short cozy run by design).
- **DUCKLINE settings (module content `20261031-005`):** swim speed 26 px/s, boost 1.7×
  for 0.55 s with a 2 s cooldown, collect radius 8 px, 3 ducklings, line spacing 8 px,
  round 22 s, start `(8,50)`, shore at x 84; save key `KANTMICROGAME.DUCKLINE.best`.
