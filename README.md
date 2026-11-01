# KANTMICROGAMES

Tiny, cute, pixel-art HTML5 micro games — **all inside ONE single HTML file**. The
arcade shelf and every game live together in `deploy/index.html`: open it, pick a game,
play a minute, smile. Fully offline by double-clicking; the rest of the folder is only
documentation. The file lives inside `deploy/` for
[Cloudflare Workers](https://workers.cloudflare.com/) deployment. (After round 1 the
owner pivoted from one-folder-per-game to this one-file architecture — see
`plans/micro-games-v2.md`.)

### About the name

The project is **KANTMICROGAMES** (plural) — the GitHub repository
`lohyapkant/KANTMICROGAMES`, the worker `kantmicrogames` and the public address
`kantmicrogames.lohyapkant.workers.dev` all use that name. Four older spellings are kept
deliberately and are not typos:

| Kept as-is | Why |
|---|---|
| Folder `KANTMICROGAME/` (singular) | The actual local folder the project is developed in; renaming it would break the owner's paths and any clone instructions. |
| Save-key prefix `KANTMICROGAME.` (and the console tag `KANTMICROGAME module error`) | Players' saved best scores and preferences already live under it (`KANTMICROGAME.<GAME>.best`, `KANTMICROGAME.ui.*`); changing it would orphan that data, and the console tag stays greppable across builds. |
| On-screen brand **KANT MICRO** | The short display name in the page title and header, chosen to fit a 100 px-wide toy console. |
| Prompt copies `P-00` … `P-08` | Archived verbatim; their singular name is a historical record and is not rewritten. |

Everything written from build 009 onward uses **KANTMICROGAMES**.

**Current state:** build `009-20261101` — the one-file app with **four** playable games
and a shell that fits phones, tablets, foldables and desktops:

| Game | Module content | One-line pitch |
|---|---|---|
| **PANDASNACK** | `007-20261101` (frozen) | Munch bamboo, dodge wasps, keep three hearts. (Live score HUD added in 007). |
| **BOOPEEK** | `006-20261101` (frozen) | Pip the lantern mouse chases Boo, a peek-a-boo nightcap ghost. |
| **DUCKLINE** | `005-20261101` (frozen) | Mama mallard gathers three ducklings and leads them home. |
| **SPROUTUP** | `007-20261101` | Sproutlet the baby seedling gathers raindrops to bloom in the sun. |

Build `009-20261101` is the **responsive-shell build**: the shelf and game screen were
rebuilt for every screen from 280 × 653 to 3440 × 1440 — no horizontal overflow, no page
scroll during play, whole-number stage scaling, safe-area padding, input-aware pads and
hints, a persisted pads/left-hand preference, a pause on tab hide, and keyboard shortcuts
that no longer leak into a game. **No game module content changed** — the four IIFEs are
byte-identical to build 008 (proved by SHA-256 in `tests/results/frozen-modules.json`).
Build `007-20261101` was the Round 4 build (SPROUTUP added, BOOPEEK frozen, PANDASNACK HUD
added and refrozen); build 008 was the documentation cleanup. See
[`CONTROLS.md`](CONTROLS.md) for everything about input.

## Models used thus far

Per the owner's standing request, the model, effort, duration and token count are
recorded in the CHANGELOG, the plan, the README and the prompt copies. When a tool bills
in **credits** and exposes no token telemetry, the credits used are recorded instead and
labelled as credits — never presented as tokens. The same applies to
**documentation review/edit attempts**: successful, partial or failed ones are logged with
model, date and outcome (e.g. the GPT-OSS 120B failure and the subsequent Opus/Qwen passes
under build 008, and the Qwen3.8-Flash documentation pass under build 009).

| Build | Full model name | Effort | Duration | Tokens / credits |
|---|---|---|---:|---:|
| 000-20261031 | DeepSeek V4.1 Flash Free (OpenCode) | Round 0 scaffold (corrected in 006) | not recorded | not recorded |
| 001-20261031 | DeepSeek V4.1 Flash Free (OpenCode) | Round 1 — PANDASNACK module + docs (corrected in 006) | not recorded | not recorded |
| 002-20261031 | GLM-5.3 Flash Free (OpenCode) | Round 1.5 — one-file pivot rewrite | not recorded | not recorded |
| 003-20261031 | GLM-5.3 Flash Free (OpenCode) | Round 2 — BOOPEEK module + wiring + docs + verification | ~45 min | ~27,000 |
| 004-20261101 | Flint 40B Free (OpenCode) | Round 3 — DUCKLINE module add | ~25 min | ~20,000 |
| 005-20261101 | DeepSeek V4.1 Flash Free (OpenCode) | Pre-Round-4 cleanup: docs rewrite, BOOPEEK + DUCKLINE re-skin, module independence, runtime hardening | ~1 h 55 min active | ~2.37 M processed |
| 006-20261101 | DeepSeek V4.1 Flash Free (OpenCode) / Gemini 3.8 Flash (Antigravity) | Final special review: numbering, 000/001 record fix, DuckLine freeze, BooPeek variability, MODELS.md | ~30 min | ~1.5 M processed |
| 007-20261101 | Gemini 3.8 Flash (Antigravity) | Round 4 — SPROUTUP module, BOOPEEK freeze, PANDASNACK in-stage live HUD score tracking & refreeze | ~25 min | ~48,000 |
| **008-20261101** | **Claude Opus 4.6 Thinking (Antigravity) / Qwen3.8-Flash (Qoder CLI)** | **Documentation cleanup: GitHub/public-site/model links, `deploy/` move documented, MIT license in index.html, GPT-OSS 120B attempt recorded; recovery pass closed the remaining gaps** | **~20 min + ~15 min** | **~60,000 + ~30,000 est.** |
| **009-20261101** | **Qwen3.8-Flash (Qoder CLI)** — prompt authored by **Claude.ai Sonnet 5.5 Extra** | **Responsive shell: shelf, no-scroll game screen, measured stage fit, input-aware pads/hints, keyboard hygiene, lifecycle pause, sliding direction cluster, accessibility polish; 24-viewport verification; new CONTROLS.md and tests** | **~30 min wall-clock** | **19.7809 credits used** (157 billable requests; tokens not exposed by Qoder) |

Notes on the `-005` record: duration is **active** working time measured across the two
sittings that produced this build (2026-10-31 21:06 → 2026-11-01 09:18, owner breaks
excluded; wall-clock was ~12 h). Tokens come from the session's full telemetry —
≈1.96 M input + ≈0.31 M generated output + ≈0.11 M reasoning, plus ≈28.4 M cached input
reads — so the figure is not comparable with the rough estimates used for `-003`/`-004`.
Earlier builds predate token/duration recording.

Notes on the `-006` record: started with DeepSeek V4.1 Flash Free (OpenCode), which hit
its session token limit after drafting the changes; reviewed, verified and completed by
Gemini 3.8 Flash (Antigravity). Tokens and duration reflect the combined session.

Notes on the `-008` record: documentation-only build. GPT-OSS 120B (Medium) was attempted
first for this build but deleted sections of files instead of following the templates and
guidance; the owner switched to Claude Opus 4.6 Thinking (Antigravity) to complete the
work. Opus halted mid-round; a recovery pass by Qwen3.8-Flash (Qoder CLI) verified every
P-08 requirement against the files and closed the remaining gaps (MODELS.md and plan
project links, model links in the changelog and prompt copy). The GPT-OSS attempt is
recorded in `MODELS.md` and the prompt copy for historical completeness.

Notes on the `-009` record: the **prompt was authored by Claude.ai Sonnet 5.5 Extra** and
pasted by the owner with the request that its authorship be recorded. It was executed by
**Qwen3.8-Flash (Qoder CLI)**. Duration is wall-clock from the prompt paste to the finished
records (2026-11-01, 16:14 → about 16:45 WIB, ≈30 min). Qoder does not report token
counts, so the build records **19.7809 credits used** instead, summed from the per-request
`credits` telemetry in the session transcript (157 billable requests, 16:14–16:40 WIB).
Earlier builds used tools that reported tokens; the two units are not comparable and are
labelled separately. The build number is **009**, not the 008 in the prompt title: 008 had
already been used by the documentation cleanup, and build numbers are never reused. The
prompt copy is saved unaltered in `P-09_responsive-shell.txt`. The frozen game modules were
verified unchanged by SHA-256; only the shared shell, the documentation and the new
`tests/` folder changed.

## How to open and play

- **Play online:** <https://kantmicrogames.lohyapkant.workers.dev/> (hosted on
  [Cloudflare Workers](https://workers.cloudflare.com/)).
- **Source code:** <https://github.com/lohyapkant/KANTMICROGAMES>
- **Play offline:** double-click `deploy/index.html`. The shelf shows one card per game — PANDASNACK, BOOPEEK,
  DUCKLINE and SPROUTUP — with a code-drawn pixel preview, a concept line and the best score,
  plus a dashed COMING SOON slot.
- Click a card to open the game in the same page (no navigation, no iframes, no folders).
  `ESC` or the ⌂ SHELF button always brings you home.
- Tip: open `deploy/index.html#game=PANDASNACK`, `#game=BOOPEEK`, `#game=DUCKLINE` or `#game=SPROUTUP`
  to land straight in a game.
- Every game: `W A S D` (+ arrow keys) move, `SPACE` or the action pad acts, `R` restarts
  instantly. On phones/tablets the four pads + action pad + RESTART appear automatically.
  A stage tap acts too.
- **On touch devices** the pads follow your last input. `PADS · AUTO / SHOW / HIDE` and
  `DIR PAD · LEFT / RIGHT` sit under the shelf chips and are remembered between visits.
  A drag on a shelf card scrolls instead of opening it; a tap opens it.
- **While playing** the page does not scroll: the stage scales by whole numbers (2×–6×)
  to fit, controls stay at least 48 px, and notches/home-indicator areas are avoided.
  Switching tabs or apps pauses the run with a `PAUSED` plate; the first input only
  resumes. Page zoom is allowed. Full details: [`CONTROLS.md`](CONTROLS.md).

| Game | Move | Action (`SPACE` / pad / tap) | Goal |
|---|---|---|---|
| PANDASNACK | scurry | **DASH** (0.7 s at 1.75×, 2.2 s cooldown) | survive: 3 stings end the run |
| BOOPEEK | tiptoe | **POKE** (reach 20 px, 0.1 s cooldown) | poke Boo while he peeks — 10 in 20 s, then beat your score |
| DUCKLINE | swim | **GO** = quack boost (0.55 s at 1.7×, 2 s cooldown) | collect 3 ducklings and reach the far bank in 22 s |
| SPROUTUP | weave | **REACH** = leap burst (0.5 s at 1.85×, 2 s cooldown) | gather 15 drops in 24 s to bloom into a sunny flower |

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

### PANDASNACK — module content `007-20261101` (frozen)

A chubby panda scurries on a tiny pastel meadow, munching the two bamboo shoots that are
always around (+1 each) while wasps drift past. A sting costs one heart with 1.6 s of shy
flashing; three stings end the run. Dash is the save-me button, and difficulty climbs
through a four-band table (1→4 wasps, speeds 13→26).

**Pixel art:** blob-composed panda with lean-and-waddle walking, random blinks, a happy
munch mouth, dust puffs, droopy ears and a rolling tear at game over; two-frame flapping
wasps; swaying bamboo; sparkle bursts; dot-flowers on a cached two-tone checker meadow;
shared 3×5 pixel font for all stage text; lower translucent score plate added in `007`
matching DuckLine and BooPeek.

> **Frozen by owner request.** Temporarily unfrozen in build 007 to add live in-stage HUD
> score tracking matching the other micro games, then refrozen. See code banner in PART 5.

### BOOPEEK — module content `006-20261101` (frozen)

**Pip the lantern mouse** plays **peek-a-boo** with **Boo**, a shy ghost in a candy-teal
nightcap, in a midnight nursery. Boo hides around five spots — the cupboard mouth, the
window sill, behind the plant, over the rug and behind the book — and pops out one at a
time with a warning sparkle. Poke him **while he is visible**: +1, a warm ring, star
sparkles and a happy hop, then he vanishes and reappears somewhere nearby. Poking empty
air does nothing, so the round is a little chase with a timing beat instead of a walk to
one fixed spot. The round lasts **20 s**; reaching the goal of **10** pokes does **not**
end the round, so a good run scores above 10 and the best score is the real target.

**Pixel art (re-skinned in `-005`, re-staged in `-006`):** striped plum wallpaper, a
moonlit window with a crescent moon, string lights, a framed heart, a wall clock, a
lived-in cupboard where Boo hides (with a jar on a tiny shelf), a potted plant, a braided
rug, a toy ball and a book. Pip is a cream mouse with pink inner ears, a red scarf and a
glowing lantern that pools warm light on the floor; Boo is a soft white sheet ghost with a
nightcap, pom, blush and a little tongue, who bobs, blinks and hops when poked.

> **Frozen by owner request (build 007).** BooPeek's five-spot peek-a-boo chase and art
> are approved as-is; do not restyle, rebalance or refactor without owner permission.

### DUCKLINE — module content `005-20261101` (frozen)

**Mama mallard** swims across a sunny top-down pond with **three ducklings** scattered on
the water — one in a red bow, one with a leaf on its head, one with a single feather tuft.
Swim near a duckling to collect it; collected ducklings fall into a waddling line behind
Mama along her actual path. Reach the far bank within **22 s**. Score = ducklings × 10
plus a time bonus at the shore, so hurry and still gather the family.

**Pixel art:** drifting water bands with glints, lily pads, lotus flowers, cattails, a tiny
frog, flowers on both grassy banks and a dragonfly that patrols the top of the pond. Mama
has a green head, white neck ring, cream body, brown chest and orange bill/feet; the
ducklings are fluffy yellow with orange bills and blush. Swimming leaves elliptical wakes;
the GO boost shows a foam splash and a feather gauge top-left.

> **Frozen by owner request (build 006).** The pond and the duck family are approved as-is;
> do not restyle, rebalance or refactor this module unless the owner asks. See the code
> banner in PART 5.

### SPROUTUP — module content `007-20261101`

**Sproutlet the seedling** weaves through a gentle summer rain shower to drink dewdrops
and catch warm sunbeams before the sun settles. Gather **15 drops in 24 s** to bloom!
Clear dewdrops grant +1 drop with water ripples and splash glints; glowing golden sun
drops grant +3 drops with radiant star bursts; fuzzy thistle burrs drift in the breeze
and cause a brief flinch and -1 drop. Press REACH (`SPACE` / action pad / tap) for a swift
upward leaf flutter leap (1.85× speed, 2 s cooldown).

**Pixel art:** Sproutlet is a chubby mint seedling with two fluttery leaves that bob and
sway, rosy pink cheeks, blinking dark eyes with white shine, and root feet that step as it
walks; sips drops with an open mouth; when goal is reached or round won, Sproutlet blooms
with a glorious 5-petal rose-pink flower crown with a golden center while warm morning
sunbeams stream down from above. Garden has a soft pastel sky with diagonal rain glints,
mossy loam ground, and tiny clover sprouts.

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
| 006 | done | Final special review: new `NNN-YYYYMMDD` build numbering, model-record correction for 000/001, DUCKLINE frozen, BOOPEEK turned into a peek-a-boo chase. |
| 007 | done | Round 4: SPROUTUP module added (summer rain, Sproutlet, dewdrops, sunbeams, victory bloom), BOOPEEK frozen, PANDASNACK in-stage live HUD score tracking added & refrozen. |
| 008 | done | Documentation cleanup: GitHub/public-site links added to all docs and index footer, `deploy/` move documented, MIT license header added to `index.html`, model links for educational reference, GPT-OSS 120B (Medium) attempt recorded. Started by Claude Opus 4.6 Thinking, gaps closed by a Qwen3.8-Flash recovery pass. |
| 009 | done | Responsive shell (prompt by Claude.ai Sonnet 5.5 Extra, built by Qwen3.8-Flash): shelf and game screen fit 280–3440 px, no scroll during play, measured whole-number stage fit, safe areas, input-aware pads/hints + persisted preferences, keyboard shortcut hygiene, pause on hide/blur, sliding direction cluster, focus/live-region/reduced-motion polish. Game modules unchanged. |
| 010+ | next | Round 5 — a fifth module from the backlog (SLIMEHOP, SNAILRACE, HUGPARADE or CATNAPCATCH, at the owner's pick). |

## Build numbering and record-keeping

Build IDs are **`NNN-YYYYMMDD`** — for example `007-20261101`.

- `NNN` is the project-wide build number, zero-padded and only ever increasing. It is the
  identity of the build; never reuse a number.
- `YYYYMMDD` is the date the build was **finished** (2026-11-01 → `20261101`). It is a
  human hint, so alphabetical order still equals build order.
- A game's `versionNumber` is the build in which that game's content last changed. A pure
  refactor that leaves a game's art and numbers identical does **not** bump it — DUCKLINE
  is frozen at `005-20261101`, BOOPEEK is frozen at `006-20261101`, PANDASNACK was updated
  for live HUD score tracking and refrozen at `007-20261101`, and SPROUTUP is live at
  `007-20261101`. Builds 008 and 009 changed no game content, so no module number moved.
- Build 006 renamed the earlier builds from the old `YYYYMMDD-NNN` form to this one
  (`20261031-003` → `003-20261031`), and corrected builds 004/005 to their true finish
  date (2026-11-01).
- Every finished build records **model, effort, duration and tokens** in four homes: this
  README, `CHANGELOG.md`, the plan's tool log and the build's prompt copy. The same rule is
  written in a comment beside `APP.fileVersion` in `deploy/index.html` so a future model sees it.
- **Documentation review/edit attempts are part of the record.** Every attempt to review,
  edit or reformat the docs — successful, partial or failed — is logged with model/tool,
  date and outcome, so readers can see what was attempted as well as what was done.

The owner's subjective notes on how each model performed live in `MODELS.md`, as dated,
append-only observations — never as a permanent ranking.

## What is not built yet

Sound, sharing between games, score sending, main-game embedding, a variant generator —
none of these exist. Nothing outside `KANTMICROGAME/` is touched, and no git commands are
run on the owner's repo (they upload/merge to GitHub themselves).

## Files in this folder

- `deploy/index.html` — the one-file app (shelf + four games), build `009-20261101`.
  Moved from the project root into `deploy/` for Cloudflare Workers deployment (see
  `wrangler.jsonc`).
- `wrangler.jsonc` — Cloudflare Workers configuration pointing to the `deploy/` directory.
- `README.md` — this guide.
- `CONTROLS.md` — the controls and device behaviour guide (keyboard, mouse, touch, pads,
  preferences, pause, accessibility).
- `CHANGELOG.md` — build history with tool/model per build.
- `MODELS.md` — dated owner observations on model strengths (append-only).
- `LICENSE` — MIT licence (© Loh Yap Kant).
- `plans/micro-games.md`, `plans/micro-games-v2.md` — plan v1 (history) and v2 (current).
- `tests/` — build 009 evidence: the responsive-shell test report, the real-device
  checklist, three contact sheets (120 screenshots), eight full-size samples, and the
  machine-readable results (verification JSON, frozen-module hashes). Documentation and
  screenshots only — no app code.
- `prompts/` — one prompt copy per build:
  - `P-00_round-0_project-kickoff.txt`
  - `P-01_round-1_pandasnack.txt`
  - `P-02_round_1-5_one-file-pivot.txt`
  - `P-03_round_2_boopeek.txt`
  - `P-04_round_3_duckline.txt`
  - `P-05_cleanup_before-round-4.txt`
  - `P-06_final-special-review.txt`
  - `P-07_round-4_sproutup.txt`
  - `P-08_documentation-cleanup.txt`
  - `P-09_responsive-shell.txt` (prompt authored by Claude.ai Sonnet 5.5 Extra, saved
    verbatim; executed by Qwen3.8-Flash / Qoder CLI)

## Prompt history

The `prompts` folder holds the prompt copies used to build this project, one per build,
the same way our other KANT projects keep them.

## Links

| What | URL |
|---|---|
| **GitHub repository** | <https://github.com/lohyapkant/KANTMICROGAMES> |
| **Play online** | <https://kantmicrogames.lohyapkant.workers.dev/> |
| **Hosting** | [Cloudflare Workers](https://workers.cloudflare.com/) |

### Models used in this project (educational reference)

This project is built entirely by prompting different AI coding models as a public-domain
educational experiment. Links to each model's home page are provided for reference:

| Model | Home page |
|---|---|
| DeepSeek V4.1 Flash Free | <https://www.deepseek.com/> |
| GLM-5.3 Flash Free (ChatGLM) | <https://chatglm.cn/> |
| Flint 40B Free (Zyphra) | <https://www.zyphra.com/> |
| Gemini 3.8 Flash (Google) | <https://gemini.google.com/> |
| GPT-OSS 120B Medium (OpenAI) | <https://openai.com/> |
| Claude Opus 4.6 Thinking (Anthropic) | <https://www.anthropic.com/> |
| Claude.ai Sonnet 5.5 Extra (Anthropic) — authored the P-09 prompt | <https://www.anthropic.com/> |
| Qwen3.8-Flash (Qwen) | <https://qwen.ai/> |

## License

This project is released under the **MIT License** — see [`LICENSE`](LICENSE).

Copyright © 2026 **Loh Yap Kant**.

## Appendix — technical details

- **Module contract:** each game module provides `id, name, tagline, concept, actionLabel,
  hint, versionNumber, previewPaint` plus `start(), stop(), restart(), update(dt), paint(ctx),
  onDir(dir, pressed), onAction(), onStageTap(), onAnyKey()`. The runtime opens/closes
  games, feeds events, ticks and paints only the open module, and keeps instant restart
  (`R`) and `ESC`-to-shelf working for every game.
- **Stage and controls spec:** exactly `100 x 100` design pixels; scaled by whole numbers
  `2×`–`6×` while it fits, fractional only below 200 px so the page never scrolls during
  play; `image-rendering: pixelated`; re-measured on resize, rotation, fold and
  `visualViewport` changes. Fixed-step update (60 steps/second) with capped catch-up,
  inside each module. All stage colors referenced by name from the game's own palette.
  `W A S D` + arrows move; `Space`/action pad is the action (dash / poke / quack boost /
  reach); `R` restarts instantly; stage tap = the module's action; `ESC` or ⌂ SHELF exits
  home. Full input details: [`CONTROLS.md`](CONTROLS.md).
- **Responsive shell (`-009`):** viewport `width=device-width, initial-scale=1.0,
  viewport-fit=cover` (zoom allowed); the game screen is a `100dvh` app shell with a
  `100vh` fallback, `overscroll-behavior: none`, `touch-action: none` on stage and pads;
  the stage is measured after the header and controls are laid out and the larger of the
  portrait/landscape layouts wins; the landscape arena is capped at 960 px so the pads
  stay beside the stage on large screens; safe areas come from `--sai-t/-r/-b/-l`;
  pads follow the last real input (no user-agent sniffing) with `KANTMICROGAME.ui.pads`
  (auto/show/hide) and `KANTMICROGAME.ui.hand` (left/right) persisted; hidden tabs,
  `pagehide` and `blur` pause the run and release inputs, and the resuming input is
  swallowed. Verification and limits: `tests/responsive-shell-report.md`.
- **Input hygiene (`-005`, extended in `-009`):** opening a game, returning to the shelf,
  losing window focus, hiding the tab, `pagehide` and `pointercancel` all release every
  held direction through the module contract, so a key or thumb held during a screen swap
  cannot leak into the next game. Browser shortcuts (`Ctrl`/`Cmd`/`Alt`) are never
  consumed; Tab, modifiers and F1–F12 never count as "any key". The shared loop wraps each
  module tick in `try/catch`, so one broken game can never kill the shelf or the others.
- **PANDASNACK settings and difficulty (module content `007-20261101`, frozen):** stroll
  speed, dash strength/length and cooldown, starting hearts, protection seconds, sting
  radii, bamboo counts and spacing, wasp spawn curve and bands unlocked by score; lower
  translucent score plate added in `007` with live score tracking.
- **BOOPEEK settings (module content `006-20261101`, frozen):** move speed 30 px/s, poke reach
  20 px, goal 10 pokes, poke cooldown 0.10 s, round 20 s, start `(26,56)`, Pip walks the
  floor band y 50–81 (freely traversing through the lower translucent score plate to reach
  Boo anywhere on the floor). Peek-a-boo: five hiding spots `(78,46) (16,40) (5,52) (40,72)
  (66,74)`, a 0.26 s warning sparkle, 1.15–1.80 s visible, 0.30–0.60 s hidden, a 0.16 s
  poof after a hit, and the next spot is preferred within 55 px so the chase stays fair.
  Save key `KANTMICROGAME.BOOPEEK.best`; no difficulty table (short cozy run by design).
- **DUCKLINE settings (module content `005-20261101`, frozen):** swim speed 26 px/s, boost 1.7×
  for 0.55 s with a 2 s cooldown, collect radius 8 px, 3 ducklings, line spacing 8 px,
  round 22 s, start `(8,50)`, shore at x 84; save key `KANTMICROGAME.DUCKLINE.best`.
- **SPROUTUP settings (module content `007-20261101`):** move speed 30 px/s, reach 1.85×
  for 0.50 s with a 2.0 s cooldown, collect radius 8 px, burr hit radius 6 px, goal 15
  drops, round 24 s, start `(44,60)`, soil at y 74; save key `KANTMICROGAME.SPROUTUP.best`.
