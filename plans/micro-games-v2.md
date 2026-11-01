# Plan: KANTMICROGAME — HTML5 Micro Games (v2 — the one-file pivot)

Today: 2026-11-01. Status: build **009-20261101** done — the shelf and all four games
(PANDASNACK, BOOPEEK, DUCKLINE, SPROUTUP) live together in ONE file. Build 009 is the
**responsive shell** build: the shell now fits phones, tablets, foldables and desktops
with no page scroll during play, input-aware pads and hints, and safe-area padding; no
game content changed. Build 008 was the documentation cleanup (links, `deploy/` move,
MIT license). Round 5 (a fifth module) is next.

Build IDs are `NNN-YYYYMMDD` (build number first, finish date second). A game's module
content number is the build in which its content last changed. PANDASNACK is **frozen** at
007-20261101, BOOPEEK is **frozen** at 006-20261101, DUCKLINE is **frozen** at 005-20261101,
and SPROUTUP is live at 007-20261101. Builds 008 and 009 changed no module content.

Supersedes micro-games.md (v1), kept as history: v1 described one file per game in
separate folders; the owner changed their mind after round 1 — see prompt P-02.

**Project links (keep current — same links live in README, CHANGELOG, MODELS.md, the
prompt copies and the `deploy/index.html` footer):**

- GitHub repository: <https://github.com/lohyapkant/KANTMICROGAMES>
- Public demo (Cloudflare Workers): <https://kantmicrogames.lohyapkant.workers.dev/>
- Hosting platform: <https://workers.cloudflare.com/>
- License: MIT (see `LICENSE`; legal name of the original creator: **Loh Yap Kant**)

## Objective

One single HTML file, `KANTMICROGAME/deploy/index.html`, contains the arcade shelf AND every
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
| 7 | Short play | A run lasts about 20 to 120 seconds, with instant restart in one tap or key press, from any state. |

## Project layout

```
KANTMICROGAME/
  deploy/index.html         <- EVERYTHING: shelf screen + game screen + all game modules
  wrangler.jsonc            <- Cloudflare Workers config (assets.directory: "./deploy")
  README.md                 <- project guide + a short manual per game
  CONTROLS.md               <- controls and device behaviour (keyboard/mouse/touch/pads)
  CHANGELOG.md              <- one entry per finished build (builds, not rounds)
  MODELS.md                 <- dated owner observations on model strengths (append-only)
  LICENSE                   <- MIT licence (© Loh Yap Kant)
  plans/micro-games.md      <- v1 plan, kept for history
  plans/micro-games-v2.md   <- this plan (later pivots add v3, v4 …)
  tests/                    <- build evidence: reports, real-device checklist,
                               contact sheets, verification JSON (docs only)
  prompts/P-XX_*.txt        <- one prompt copy per build, per KANTPLANEINVASION convention
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
| PART 5 — game modules | One self-contained IIFE per game: its own `SETTINGS`, palette, maps, state — registered into `GAMES`. Private names are prefixed per game (`panda`/`PANDA_*`, `peek`/`boo`/`pip`/`BOO_`/`PIP_*`, `duck`/`mama`/`DUCK_*`); a "READ ME FIRST" boundary block sits at the top of the script and above PART 5 |
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

- Exactly `100 x 100` design pixels; scaled by whole numbers `2x`–`6x` while it fits, with
  a fractional scale only below 200 px so the page never scrolls during play; measured from
  the real stage box in both the portrait and landscape layouts; `image-rendering:
  pixelated`; refit on resize, rotation, fold and `visualViewport` changes.
- Fixed-step update (60 steps/second) with capped catch-up, inside each module.
- All stage colors referenced BY NAME from the game's own `palette`.
- Difficulty if present is one table of bands unlocked by score/time (BOOPEEK has none —
  the cozy poke game keeps it simple by design).
- `W A S D` + arrows move; `Space`/action pad is the action (dash in PANDASNACK, poke in
  BOOPEEK, quack boost in DUCKLINE, reach in SPROUTUP); `R` restarts instantly; stage tap =
  the module's action; `ESC` or ⌂ SHELF exits home.
- Input hygiene: opening a game, leaving to the shelf, `blur`, `visibilitychange`,
  `pagehide` and `pointercancel` release every held direction through the module contract,
  so input never leaks between games. The shared loop catches a failing module instead of
  dying. Hiding the page pauses with a `PAUSED` plate; the resuming input is swallowed.
- Input awareness (`-009`): pads follow the last real input (touch/pen shows them,
  keyboard/mouse hides them), with persisted `PADS · AUTO/SHOW/HIDE` and
  `DIR PAD · LEFT/RIGHT` preferences; hints and shelf chips switch live. Stage and pads use
  `touch-action: none`; page zoom stays allowed.

## Definition of done (per build)

1. All seven rules pass; no console errors during 5 minutes of play; resize/rotation refit without reload.
2. The headless smoke test still passes: shelf routes into a game by hash, the game runs walking/dashing/restarting without exceptions, ESC returns to the shelf, reopening re-runs `start()` cleanly.
3. Touch + keyboard both playable (phone check on real Safari pending and honestly noted until done).
4. README updated (its per-game manual section), CHANGELOG entry with the file build number and tool/model line, prompt copy saved, tool/model log row added, backlog row updated.
5. Shelf card shows the game with preview, concept and best score.

## Build ledger

| Build | Date | Deliverable |
|---|---|---|
| 000-20261031 | 2026-10-31 | Round 0 scaffold (v1 architecture: folder per game). DONE. |
| 001-20261031 | 2026-10-31 | Round 1: PANDASNACK shipped in `games/PANDASNACK/`. DONE. |
| 002-20261031 | 2026-10-31 | One-file pivot: shelf + game screens + shared helper layer + PANDASNACK folded in as a module; `games/` deleted; hash routing; pads/keys re-routed through the runtime. DONE. |
| 003-20261031 | 2026-10-31 | Round 2: BOOPEEK shipped as the second module (shy ghost poke) inside the one-file app; CHANGELOG/README/plan/prompt updated; smoke re-run green. DONE. |
| 004-20261101 | 2026-11-01 | Round 3: DUCKLINE shipped as the third module (duck family). Later superseded for the file build and for BOOPEEK/DUCKLINE art by -005. DONE. |
| 005-20261101 | 2026-11-01 | Pre-Round-4 cleanup: README/CHANGELOG rewritten; BOOPEEK re-skinned (Pip the lantern mouse + Boo the nightcap ghost, midnight nursery); DUCKLINE re-skinned (mallard family, sunny pond, trail-following ducklings); module independence audit + boundary comments; runtime input hygiene and loop guard; all three games smoke-tested. DONE. |
| 006-20261101 | 2026-11-01 | Final special review: new `NNN-YYYYMMDD` build numbering (retro-renamed, 004/005 corrected to their finish date); model record corrected for 000/001; DUCKLINE frozen; BOOPEEK rebuilt as a five-spot peek-a-boo chase; `MODELS.md` added for dated owner observations; numbering guidance added to code, README and CHANGELOG. DONE. |
| 007-20261101 | 2026-11-01 | Round 4: SPROUTUP shipped as fourth module (summer rain, Sproutlet, dewdrops, sunbeams, victory bloom); BOOPEEK frozen; PANDASNACK in-stage live HUD score tracking added & refrozen; shelf card with custom preview added. DONE. |
| 008-20261101 | 2026-11-01 | Documentation cleanup: GitHub/public-site/model links added to all docs and index footer; `deploy/` move documented; MIT license header added to `index.html`; GPT-OSS 120B (Medium) attempt recorded. Opus halted mid-round; a Qwen3.8-Flash recovery pass verified every requirement and closed the remaining gaps. DONE. |
| 009-20261101 | 2026-11-01 | Responsive shell (prompt authored by Claude.ai Sonnet 5.5 Extra): shelf and game screen fit 280–3440 px with no horizontal overflow and no page scroll during play; measured whole-number stage fit; safe areas; input-aware pads/hints and persisted PADS/DIR PAD preferences; keyboard shortcut hygiene; pause on hide/blur/pagehide; sliding direction cluster; focus/live-region/reduced-motion polish. `CONTROLS.md` and `tests/` added; frozen modules proved byte-identical. DONE. |

## Tool and model log (owner request, 2026-10-31)

Standing convention in four homes: this plan, the CHANGELOG, the project README and
the build's prompt copy.

| Build | Date | Tool and model that did the building |
|---|---|---|
| 000 | 2026-10-31 | DeepSeek V4.1 Flash Free (OpenCode) — corrected in build 006 |
| 001 | 2026-10-31 | DeepSeek V4.1 Flash Free (OpenCode) — corrected in build 006 |
| 002 | 2026-10-31 | GLM-5.3-Flash Free (OpenCode) |
| 003 | 2026-10-31 | GLM-5.3-Flash Free (OpenCode) |
| 004 | 2026-11-01 | Flint 40B Free (OpenCode) |
| 005 | 2026-11-01 | DeepSeek V4.1 Flash Free (OpenCode) — ~1 h 55 min active, ≈2.37 M tokens processed |
| 006 | 2026-11-01 | DeepSeek V4.1 Flash Free (OpenCode) / Gemini 3.8 Flash (Antigravity) — ~30 min, ~1.5 M tokens (handoff at session limit) |
| 007 | 2026-11-01 | Gemini 3.8 Flash (Antigravity) — ~25 min, ~48,000 tokens processed |
| 008 | 2026-11-01 | Claude Opus 4.6 Thinking (Antigravity) — ~20 min, ~60,000 tokens (GPT-OSS 120B Medium attempted first, failed) / Qwen3.8-Flash (Qoder CLI) — recovery pass ~15 min, ~30,000 tokens est. (closed remaining link gaps) |
| 009 | 2026-11-01 | Qwen3.8-Flash (Qoder CLI) — ~30 min wall-clock, tokens unknown - owner to fill in. Prompt authored by Claude.ai Sonnet 5.5 Extra (saved verbatim; its title says build 008 but 008 was taken, so this build is 009). 1,409 assertions, 0 failures; 24 viewports; frozen modules byte-identical. |

Rule: every future build truthfully records its model in all four homes.

## Game backlog (concepts sized for a 100×100 stage)

| Name | One sentence | Verb | Status |
|---|---|---|---|
| PANDASNACK | A chubby panda scurries to eat bamboo shoots while wasps drift past. | WASD dodge+dash | in the file (round 1) — frozen at content 007-20261101 |
| DUCKLINE | A mother duck crosses a pond; collected ducklings waddle in a line behind her. | WASD lead-a-chain | in the file (round 3) — frozen at content 005-20261101 |
| SPROUTUP | A baby sprout climbs a rain of water drops; sun settles, it blooms — short and lovely. | WASD weave | in the file (round 4) — live at content 007-20261101 |
| SLIMEHOP | A bouncing slime must only land on lily pads that float apart over time. | WASD + Space hop timing | backlog |
| BOOPEEK | A shy ghost peeks from five spots; poke it while it is out — cozy not scary. | WASD walk + Space poke | in the file (round 2) — frozen at content 006-20261101 |
| SNAILRACE | Race three snails; food pellets speed you up, salt slows — tiny arcade. | WASD steer | backlog |
| HUGPARADE | Two round friends reunite across a maze that redraws itself every 10 seconds. | WASD only | backlog |
| CATNAPCATCH | Guard a sleeping cat from falling noise-makers with a paper pillow. | WASD catch | backlog |

Names are placeholders; a round may rename its game before it ships.

## What we are NOT doing now

- No game folders, no extra code files, no imports between games, no build tools.
- No iframe embedding, no postMessage API, no main-game hooks, no audio yet.
- Nothing outside `KANTMICROGAME/` is created, moved or edited; no git commands
  run on the owner's repo — they upload/merge to GitHub themselves.
