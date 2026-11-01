# KANTMICROGAMES Changelog

## Conventions (read before adding an entry)

- **Newest entry first.** Each entry starts with its build ID and the real finish date.
- **Build IDs are `NNN-YYYYMMDD`**: a zero-padded project build number, then the finish
  date (2026-11-01 → `20261101`). The number is the identity; the date is a hint. Never
  reuse a number. A game's `versionNumber` is the build where its content last changed.
- **Every entry records** the prompt ID, the full model name and tool, and a build record
  with duration and tokens. A tool that bills in **credits** and exposes no token telemetry
  records the **credits used**, labelled as credits — never silently presented as tokens.
  The same facts go to `README.md`, `plans/micro-games-v2.md` and the build's prompt copy —
  four homes, one truth.
- **The project name is `KANTMICROGAMES`.** Entries dated up to build 009 used the older
  singular spellings; they are historical records and are not rewritten. From build 010 the
  app itself agrees: the on-screen brand, the save-key prefix (`KANTMICROGAMES.`) and the
  console tag all use the full name. The local folder `KANTMICROGAME/` and the archived
  prompt copies are kept on purpose (see "About the name" in `README.md`).
- **Corrections are dated, not silent.** If a past record was wrong, fix it and say which
  build corrected it (build 006 corrected the model record for 000/001).
- **Documentation review/edit attempts are recorded.** Every attempt to review, edit or
  reformat this documentation — whether it succeeded, was partial, or failed (see the
  GPT-OSS 120B attempt and the Opus halt under 008) — is logged with its model/tool, date
  and outcome, for completionist and historical reference.
- **Owner model observations** belong in `MODELS.md` as dated, append-only notes — not in
  this changelog, and never as a permanent ranking.
- The same rules are repeated beside `APP.fileVersion` in `deploy/index.html`.

## 010-20261101 — 2026-11-01 (SLIMEHOP + KANTMICROGAMES rename)

Built from prompt: P-10 (the owner's Round 5 request, saved verbatim in
`prompts/P-10_slimehop.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in
changelog, README, plan, MODELS.md and the prompt copy  
Games in the one file: 5 (PANDASNACK module content 007-20261101 **frozen**, BOOPEEK
006-20261101 **frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101,
**SLIMEHOP 010-20261101**; file build **010-20261101**)

### Added — SLIMEHOP module (PART 5-E)

- A new sealed IIFE using only the module contract, the shared pixel helpers,
  `readBest` / `saveBest` and `scoreEl` / `bestEl` / `msgEl`; private names use the
  `slime` / `SLIME_*` prefix.
- **Pond:** a 3×3 set of nine lily pads at x `[26, 50, 74]`, y `[38, 59, 80]`, with the slime
  starting on the middle pad. Every direction press is exactly one 0.24 s hop (11 px arc);
  hopping into the edge is a harmless squash.
- **Bloom states:** each landing steps the pad **WET → MOSS → BLOOM** and scores **+10**
  per step. Landing or stomping the ninth bloom wins instantly with **+100**; the round
  otherwise ends at **30 s**.
- **STOMP** (`SPACE`, action pad or stage tap): blooms the pad underfoot for +10 on a
  **1.2 s cooldown**, shown as five readiness pips bottom-left, and stuns the snail within
  30 px for **1.8 s** (cancel-safe: a stunned snail returns to the pad it left).
- **Snail saboteur:** wanders when no flowers exist, otherwise crawls toward a bloomed pad
  (0.7 s per crawl) and eats it back to WET. Its move delay eases from 3.2 s to 1.5 s as
  the round ticks.
- **In-stage HUD:** `BLOOM n/9` and `TIME n` on the top plate, plus `SLIMEHOP`,
  `BLOOM EVERY PAD` and `POND IN BLOOM!` / `THE POND WENT STILL` overlay plates, all drawn
  with the shared 3×5 pixel font. The shared font gained a `/` glyph so `1/9` renders.
- **Pixel art:** three-tone rolling water with drifting glints, soft fireflies and framing
  reeds; plump lily pads with a light top edge, dark under-rim and a wedge notch; a wet
  glint, a moss tuft and an 11×8 pink-and-gold bloom with a green stem for the three pad
  states; a 14×12 spring slime with a stretch hop, squash landing, blink, blush and a stomp
  glow; a shaded-spiral snail with a cream foot, sleepy eyes, wobble and stun stars; pink
  petals spilling out to the sides of a bloom.
- **Shelf:** a custom 200×96 preview (slime, moss, bloom and snail on their pads between
  reeds), a concept line and the `STOMP` action label.
- While polishing the art and effects, four issues were found by eye in 6× screenshots and
  fixed: the slime touched the pad above it (rows moved to 38/59/80), the moss and flower
  floated a pixel or two above their pad (offsets tightened), the title sign ghosted the
  top pads and snail (opaque plates), and bloom sparkles landed on the slime's face (sprayed
  to the pad's sides instead).

### Changed — on-screen brand, save keys and console tag

- `APP.name`, the `<h1>`, the document title, the footer (`KANTMICROGAMES — build
  010-20261101`), `APP.savePrefix` (`KANTMICROGAMES.`) and the console tag
  (`KANTMICROGAMES module error:`) now use the full project name. UI preferences live under
  `KANTMICROGAMES.ui.pads` / `KANTMICROGAMES.ui.hand` and bests under
  `KANTMICROGAMES.<GAME>.best`.
- **Owner's rationale, recorded:** the page is fresh and nobody else has this build, so no
  saved scores or preferences exist under the old prefix and there is nothing to migrate —
  this was the safe moment to rename. The four frozen modules changed only their unused
  `saveKey` label strings; historical documentation, `tests/` evidence and prompt copies
  `P-00` … `P-09` keep their original spellings as records.

### Note — concept changed from the backlog sketch

The plan's backlog line for SLIMEHOP read "a bouncing slime must only land on lily pads
that float apart over time". The shipped game keeps the slime, the hopping and the pond but
makes the pads a static 3×3 board and moves the timing pressure into the **stomp cooldown**,
the **snail's crawl** and the **30 s clock**, so the verb stays one sentence: *bloom every
pad before the sleepy snail eats the flowers.* The backlog row in the plan is updated to
match. If the owner prefers the original floating-pad timing idea, that is a new round.

### Verification and limits

- `node --check` on the extracted inline script: clean. Headless **Chrome 156** via
  Playwright-core 1.64.1, loading `file://`.
- SLIMEHOP loop: title → play, five hops plus a stomp (score 40), snail movement, round
  ending at 30 s with the time-out message, best saved under `KANTMICROGAMES.SLIMEHOP.best`,
  `R` restart back to 0, `ESC` back to the shelf. Zero console and page errors.
- All five games opened and fed a short input burst: correct titles/taglines, non-blank
  stage, no console errors, `ESC` returns to the shelf.
- Touch: iPhone 13 emulation — tap the stage to start, tap the direction pad to hop (+10),
  tap the stage to stomp (+10). Pads fit and the page does not scroll.
- Viewports 1280 × 800, 360 × 640, 320 × 653 and 280 × 653: no horizontal overflow; the
  stage sizes 600 px, 300 px and 200 px (whole-number 2×–6×) and fits the viewport.
- Frozen-module proof: each of PANDASNACK, BOOPEEK, DUCKLINE and SPROUTUP compared with
  build 009 with the `saveKey` label normalised — identical line for line.
- **Not verified:** physical phones/tablets, Safari/Firefox/Edge, screen readers, real
  notches, 120 Hz, or any device the headless run cannot model. No sound exists.

### Build record (owner request: duration + tokens/credits)

- Duration: **~30 min** wall-clock, one sitting (2026-11-01, 18:59 → about
  19:30 WIB, from the owner's request to the finished records). Wall-clock, not a
  stopwatch on active editing.
- Tokens: **not exposed by the tool.** As in build 009, Qoder reports a `credits` value per
  request instead of token counts, so this build records **9.0583 credits used** across
  186 billable requests (18:59–19:26 WIB), summed from the per-request `credits`
  telemetry in the session transcript. Labelled as credits, never presented as tokens, and
  no token number is invented.

### Documentation review/edit attempts (standing rule)

- One documentation pass by **Qwen3.8-Flash (Qoder CLI)** during this build, covering
  README, CHANGELOG, MODELS.md, CONTROLS.md, the plan and the new prompt copy. Edits were
  append-only or in place following each file's template; no content was deleted and no
  documentation attempt failed in this round.

## 009-20261101 — 2026-11-01 (responsive shell)

Built from prompt: P-09 (responsive shell — phones, tablets, foldables, desktops); the
prompt was **authored by Claude.ai Sonnet 5.5 Extra** and is saved unaltered in
`prompts/P-09_responsive-shell.txt`  
Tool and model: **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in
changelog, README, plan, MODELS.md and the prompt copy  
Games in the one file: 4 (PANDASNACK module content 007-20261101 **frozen**, BOOPEEK module
content 006-20261101 **frozen**, DUCKLINE module content 005-20261101 **frozen**, SPROUTUP
module content 007-20261101; file build **009-20261101** — **no game code changes**; the
four IIFEs are byte-identical to build 008 by SHA-256)

### Note — build number deviation

The prompt title says **build 008**, but build 008 had already been used by the
documentation cleanup (P-08). Build numbers are never reused, so this build is
**009-20261101** in `APP.fileVersion`, the footer and every record. The prompt text itself
was not altered; the deviation is documented in the prompt copy, README and MODELS.md.

### Changed — shelf (F1, F2, F3)

- The shelf is capped at a 760 px column and its grid uses
  `minmax(min(228px, 100%), 1fr)`: one card column on the narrowest phones, two around
  600–932 px, three above. No horizontal overflow from 280 px to 3440 px.
- Cards are real buttons opened on `click`, so mouse, tap, `ENTER`/`SPACE` and assistive
  tech all work; a drag that scrolls the shelf no longer launches a game.
- Ghost-click guard: the tap that leaves a game cannot open a card that appears under the
  finger; `openGame` is idempotent.
- Visible `:focus-visible` rings; hover lift only under `(hover: hover)`.
- Two persisted preferences under the how-to chips: `PADS · AUTO/SHOW/HIDE` and
  `DIR PAD · LEFT/RIGHT` (`KANTMICROGAME.ui.pads`, `KANTMICROGAME.ui.hand`).

### Changed — game screen layout (F4, F5, F9, F10, F11, D1, D3)

- The game screen is a no-scroll app shell: `100dvh` with a `100vh` fallback,
  `overscroll-behavior: none`, `touch-action: none` on stage and pads, footer hidden while
  playing.
- `fitStage()` now measures the real stage box after the header and controls are laid out,
  in both the portrait and landscape layouts, and picks the larger stage. Whole-number
  2×–6× while it fits; fractional only below 200 px (280×653 → 155 px, 568×320 → 187 px).
- Portrait: stage on top, one controls row below. Landscape: direction cluster and action
  column beside the stage, arena capped at 960 px so the pads stay near a 600 px stage on
  large screens; `DIR PAD · RIGHT` mirrors both layouts.
- Header compacted to one row (⌂ SHELF, title, SCORE, BEST); tagline hidden on short
  screens. Every visible control is at least 48 × 48 px and 8 px from its neighbours.
- Safe-area variables `--sai-t/-r/-b/-l` are used for page and top-bar padding, with
  extra clearance near edges. Page zoom is allowed; double-tap zoom is suppressed with
  `touch-action` on the chrome.

### Changed — input, keyboard, lifecycle, pads (F6, F7, F8, F12)

- Input mode comes from real use (`pointerType`, keydown), never from a user-agent check:
  touch/pen shows the pads, keyboard/mouse hides them, and hints, shelf chips, the action
  label and `RESTART · R` switch live. Frozen `hint` strings are displayed, not edited.
- Ctrl/Cmd/Alt shortcuts pass through untouched; Tab, CapsLock, modifiers and F1–F12 never
  count as "any key"; keys are ignored while a form field has focus.
- `visibilitychange` (hidden), `pagehide` and `blur` release every direction and pause with
  a `PAUSED` overlay; the first input only resumes (swallowed) and the frame clock resets.
- The direction cluster is one sliding touch surface with per-`pointerId` tracking, a dead
  centre, release on up/cancel/lost capture, and working multi-touch with the action pad.

### Changed — accessibility polish (F13)

- Focus-visible styles, `#msg` as `role="status" aria-live="polite"`, rem chrome text,
  reduced-motion press/pulse handling, `100vh` fallbacks before `100dvh`.

### Added — documentation and evidence

- `CONTROLS.md` — one controls table for all four games, keyboard/mouse/touch/assistive
  notes, preferences and persistence, pause, layout rules, and why the pads use
  `tabindex="-1"`.
- `tests/responsive-shell-report.md` — environment, 24-viewport matrix, pass/fail per
  assertion, screenshot reference, frozen-module proof, what could not be verified,
  browser caveats and a change list by file section.
- `tests/real-device-checklist.md` — the hands-on checklist for the owner.
- `tests/screenshots/` — three contact sheets covering 120 screenshots (24 viewports ×
  shelf + 4 games) and eight full-size samples.
- `tests/results/` — final verification JSON and the frozen-module SHA-256 proof.
- `prompts/P-09_responsive-shell.txt` — the prompt copy, with the owner's prompt verbatim.

### Documentation review/edit attempts (standing rule)

- One documentation pass by **Qwen3.8-Flash (Qoder CLI)** on 2026-11-01: README,
  CHANGELOG, MODELS.md, plan, `CONTROLS.md`, the test report, the real-device checklist and
  this prompt copy. No content was deleted; edits were append-only or in place following
  each file's template. No failed documentation attempt in this round.
- A second pass by **Qwen3.8-Flash (Qoder CLI)** on 2026-11-01, after the build was
  finished: owner-requested naming audit plus the credit record (see the addendum below).
  Titles and current prose were corrected to **KANTMICROGAMES**; historical entries,
  prompt copies, the folder name, the save-key prefix and the on-screen brand were left
  unchanged on purpose. No content was deleted.

### Verification and limits

- 1,409 automated assertions, **0 failures**, 0 console errors and 0 page errors, across
  24 viewports × 4 games plus 41 interaction checks (drag/tap, ghost click, tab order,
  shortcuts, slide, multi-touch, pointercancel, pagehide, pause/resume, mode switching,
  preference persistence, mid-run resize/rotate, simulated portrait and landscape notches,
  stage swipe, per-game key map).
- 120 screenshots inspected on contact sheets; two layout problems were found by eye and
  fixed (small stage from a content-sized measurement box; pads at the screen edges in
  landscape).
- Frozen modules proved unchanged with SHA-256 of the whole PART 5 region and of each of
  the four modules.
- **Not verified:** physical iOS/Android devices, Safari/Firefox/Edge, real notches and
  home indicators, real pinch zoom, screen readers, foldable postures, more than two
  pointers, 120 Hz and low-end performance. The report lists these gaps explicitly.

### Build record (owner request: duration + tokens/credits)

- Duration taken to build this round: **~30 min wall-clock** (2026-11-01, 16:14 → about
  16:45 WIB, from prompt paste to finished records; no idle gaps observed).
- Tokens used in this round: **not exposed by the tool.** Qoder reports a `credits` figure
  per request instead of token counts, so the build records **19.7809 credits used** (157
  billable requests, 16:14–16:40 WIB), summed from the session's per-request credit
  telemetry. The unit is credits, not tokens; the owner asked for it to be recorded this
  way rather than left blank, and no token number is invented.

### Addendum — 2026-11-01 (post-build: naming audit and credit record)

Owner request after 009 was signed off: check the project name across the files, and record
credits in place of the unavailable token count.

- **Naming.** The project is **KANTMICROGAMES**, as used by the GitHub repository, the
  worker `name` in `wrangler.jsonc` and the public address. Current titles and prose in
  `README.md`, `CHANGELOG.md`, `MODELS.md`, `CONTROLS.md`, `plans/micro-games-v2.md` and
  the `deploy/index.html` header now use that spelling. Kept unchanged on purpose: the
  local folder `KANTMICROGAME/`, the save-key prefix `KANTMICROGAME.`, the on-screen brand
  `KANT MICRO`, and the archived prompt copies `P-00` … `P-08`. All four exceptions are
  explained in "About the name" in `README.md`.
- **Credits.** Build 009's record now states **19.7809 credits used** instead of "unknown";
  the token field stays explicitly unavailable. The same figure is carried in `README.md`,
  `MODELS.md`, `plans/micro-games-v2.md` (tool log) and `prompts/P-09_responsive-shell.txt`.
- **Creator name.** `LICENSE` said "Copyright (c) 2026 lohyapkant" (the GitHub handle) while
  the README, changelog and the `index.html` MIT header name **Loh Yap Kant**. The licence
  line now reads "Copyright (c) 2026 Loh Yap Kant (GitHub: lohyapkant)", so the legal name
  and the handle both appear and nothing is lost.
- No game code changed in this addendum; the four IIFEs remain byte-identical.

## 008-20261101 — 2026-11-01 (documentation cleanup)

Built from prompt: P-08 (documentation cleanup — links, `deploy/` move, MIT license, model links, GPT-OSS attempt recorded)  
Tool and model: **Claude Opus 4.6 Thinking (Antigravity)**, completed by **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 4 (PANDASNACK module content 007-20261101 **frozen**, BOOPEEK module content 006-20261101 **frozen**, DUCKLINE module content 005-20261101 **frozen**, SPROUTUP module content 007-20261101; file build 007-20261101 — **no game code changes**)

### Added — project links

- Added **GitHub repository** and **public demo site** links to README, CHANGELOG, prompt
  file, MODELS.md and the `deploy/index.html` footer:
  - GitHub: <https://github.com/lohyapkant/KANTMICROGAMES>
  - Public demo: <https://kantmicrogames.lohyapkant.workers.dev/>
  - Hosting: [Cloudflare Workers](https://workers.cloudflare.com/)
- Added a "Models used in this project" table in README with home-page links for every AI
  model used (DeepSeek, GLM/ChatGLM, Flint/Zyphra, Gemini/Google, GPT/OpenAI,
  Claude/Anthropic) for educational reference. The same links, kept here so every model has
  them in one place:
  - DeepSeek: <https://www.deepseek.com/>
  - ChatGLM: <https://chatglm.cn/>
  - Zyphra (Flint): <https://www.zyphra.com/>
  - Google (Gemini): <https://gemini.google.com/>
  - OpenAI (GPT): <https://openai.com/>
  - Anthropic (Claude): <https://www.anthropic.com/>
  - Qwen: <https://qwen.ai/>

### Added — MIT license in index.html

- Added the full MIT license text as an HTML comment at the top of `deploy/index.html`,
  crediting **Loh Yap Kant** as the original creator.
- Added a License section in README linking to the `LICENSE` file.

### Changed — `deploy/` folder documented

- Documented that `index.html` was moved from the project root into `deploy/` to satisfy
  Cloudflare Workers deployment requirements (`wrangler.jsonc` sets `assets.directory` to
  `"./deploy"`). All file references in README and this changelog updated accordingly.

### Changed — GPT-OSS 120B (Medium) attempt recorded

- The owner first attempted this documentation cleanup with **GPT-OSS 120B (Medium)**
  via Antigravity. The model deleted sections of files instead of following the existing
  templates and guidance. The owner switched to **Claude Opus 4.6 Thinking (Antigravity)**
  to complete the work. The GPT-OSS attempt is recorded in `MODELS.md` and the prompt
  copy (`P-08`) for historical and educational completeness.

### Documentation

- Updated README (build 008 row in models table, links section, model links table, license
  section, file list updated for `deploy/` and `wrangler.jsonc`, build history row).
- Updated `plans/micro-games-v2.md` (build ledger row 008, tool/model log row 008).
- Added `MODELS.md` entries for GPT-OSS 120B (Medium) and Claude Opus 4.6 Thinking.
- Created `prompts/P-08_documentation-cleanup.txt`.

### Completed — recovery pass (dated correction, not silent)

- Claude Opus 4.6 Thinking halted mid-round with most of the work done but uncommitted. A
  recovery pass by **Qwen3.8-Flash (Qoder CLI)** on 2026-11-01 verified every P-08
  requirement against the actual files and closed the gaps:
  - Project links were claimed for `MODELS.md` but missing there — added (plus the MIT
    license and legal-name note, so every documentation home carries the links).
  - Project links added to `plans/micro-games-v2.md` for cross-file consistency.
  - Model home-page links added to this changelog entry and to the `P-08` prompt copy
    (previously only in README).
  - Qwen3.8-Flash recorded as a model used on this project (README model link table,
    `MODELS.md`, tool logs).
- No content deleted; all edits follow the existing templates in each file.

### Added — documentation-attempt history rule

- On the owner's instruction (2026-11-01, Qwen3.8-Flash/Qoder CLI), the records now
  include every attempt to review, edit or reformat the documentation — successful,
  partial or failed — with model/tool, date and outcome. Written into this changelog's
  conventions, the README record-keeping section, and the `P-08` prompt copy.

### Build record (owner request: duration + tokens)

- Claude Opus 4.6 Thinking (Antigravity): duration **~20 min**, tokens **~60,000**.
- Qwen3.8-Flash (Qoder CLI), recovery pass: duration **~15 min**, tokens **~30,000**
  (rough estimate; no session telemetry surfaced by the tool).

## 007-20261101 — 2026-11-01 (Round 4 — SPROUTUP)

Built from prompt: P-07 (Round 4 — SPROUTUP module, BOOPEEK freeze, PANDASNACK in-stage live HUD score tracking & refreeze)  
Tool and model: **Gemini 3.8 Flash (Antigravity)** — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 4 (PANDASNACK module content 007-20261101 **frozen**, BOOPEEK module content 006-20261101 **frozen**, DUCKLINE module content 005-20261101 **frozen**, SPROUTUP module content 007-20261101; file build 007-20261101)

### Added — SPROUTUP module (Round 4, content 007-20261101)

- Added the fourth micro game to the one-file app: **SPROUTUP** — Sproutlet the baby
  seedling weaves through a gentle summer rain shower to drink dewdrops and reach for warm
  sunbeams.
- Gameplay loop: 24 s round timer, target 15 drops. Clear dewdrops grant +1 drop with water
  splash ripples; rare golden sun drops grant +3 drops with radiant star sparkles; drifting
  fuzzy thistle burrs cause a brief flinch and -1 drop. Reaching 15 unlocks the Bloom ready
  state with golden sunbeams; winning crowns Sproutlet with a glorious 5-petal rose-pink flower
  crown.
- Verb: **WASD weave** + **REACH** action button (`SPACE`, REACH pad, or stage tap) for a swift
  upward leaf flutter burst (1.85× move speed for 0.5 s, 2.0 s cooldown).
- Pixel art: Sproutlet chubby seedling with waddling walk, sway frames, blinking eyes with white
  highlights, sip mouth, water and sun drop sprites, thistle burr, blooming flower crown, soft
  pastel misty sky with diagonal rain glints, and mossy loam soil base.
- Shelf card added: 200×96 code-drawn preview scene with Sproutlet leaping toward a golden sun
  drop and sparkling dewdrops over a mossy soil base.
- Scoring: persistent best score saved to `KANTMICROGAME.SPROUTUP.best`.

### Changed — PANDASNACK live score HUD & refreeze (content 007-20261101)

- Temporarily unfroze PANDASNACK by owner request to add in-stage live score HUD tracking
  inside the 100×100 stage:
  - Added bottom translucent plate `drawPandaPlate(stageCtx, 82, 15)` matching DuckLine and
    BooPeek.
  - Draws `"BAMBOO "` + score and `"BEST "` + storedBest during play in 3×5 pixel font.
- Refroze PANDASNACK at content version `007-20261101` with an updated code banner in PART 5.

### Changed — BOOPEEK frozen (content 006-20261101)

- Marked BOOPEEK as **FROZEN** at content version `006-20261101` per owner request, with a
  FROZEN banner in the code and matching documentation.

### Documentation

- Updated README (four-game table, models table through 007, SPROUTUP manual section,
  technical appendix), plan v2 (status, deliverable table, backlog row), and created
  `prompts/P-07_round-4_sproutup.txt`.

### Verification

- Script syntax OK; all sprite maps verified for row length consistency; zero external URLs.
- Headless smoke run green for all four games (1500 frames of full gameplay simulation).

### Build record (owner request: duration + tokens)

- Duration taken to build this round: **~25 min**.
- Tokens used in this round: **~48,000**.

## 006-20261101 — 2026-11-01 (final special review)

Built from prompt: P-06 (final special review before Round 4 — numbering, record correction, DuckLine freeze, BooPeek variability)  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode) / Gemini 3.8 Flash (Antigravity)** — recorded per the owner's standing request in changelog, README, plan and prompt copies (DeepSeek drafted the refactor and hit token limits; Gemini 3.8 Flash reviewed, verified and completed documentation)  
Games in the one file: 3 (PANDASNACK module content 001-20261031 **frozen**, BOOPEEK module content 006-20261101, DUCKLINE module content 005-20261101 **frozen**; file build 006-20261101)

### Changed — build numbering (retroactive)

- Adopted **`NNN-YYYYMMDD`** (build number first, finish date second) as the project-wide
  build ID, replacing the old `YYYYMMDD-NNN` order. Sorting the IDs alphabetically now
  sorts them by build.
- Renamed every earlier build in the code, README, CHANGELOG, both plans and all prompt
  copies. Builds `004` and `005` were also corrected from `20261031` to their true finish
  date `20261101`.
- Module content numbers follow the same rule: PANDASNACK `001-20261031`, DUCKLINE
  `005-20261101`, BOOPEEK `006-20261101`.
- Added a "BUILD NUMBERING AND RECORD-KEEPING" comment beside `APP.fileVersion`, a
  README section and this conventions block so future models keep the method.

### Changed — model record correction

- Builds `000-20261031` and `001-20261031` were recorded as GLM-5.3 Flash Free. The owner
  confirmed they were built with **DeepSeek V4.1 Flash Free**; the README, CHANGELOG, plan
  tool log and the P-00/P-01 prompt copies now say so, and name build 006 as the
  correction.

### Changed — BOOPEEK peek-a-boo (content 006-20261101)

- Boo no longer sits in one cupboard spot. He now hides around **five spots** — cupboard
  mouth, window sill, behind the plant, over the rug, behind the book — and pops out one
  at a time.
- Each peek has a **0.26 s warning sparkle**, a visible window of **1.15–1.80 s**, and a
  hidden gap of **0.30–0.60 s**. Poking him while visible scores +1, plays the hop and
  ring, then he poofs away (0.16 s) and relocates.
- The next spot is preferred within **55 px**, so the chase stays fair on a 100 px stage.
  Poking empty air does nothing.
- Extended Pip's vertical floor traversal from `y: 54–62` to `y: 50–81`, allowing the player
  to walk freely down through the translucent score plate to reach and poke Boo when hiding
  over the rug or behind the book.
- Updated the title line to "POKE HIM WHEN HE POPS OUT", the chrome message, the shelf
  concept line and the preview text to match the new loop.

### Changed — DUCKLINE frozen

- Added a **FROZEN** banner to the DUCKLINE module (content 005-20261101) and a matching
  note in README, plan and backlog: the pond and duck family are approved as-is and must
  not be restyled, rebalanced or refactored without the owner asking.

### Documentation

- Added `MODELS.md`: dated, append-only owner observations on model performance, with
  rules for future models and a template.
- Updated README (numbering section, model table through 006, BooPeek manual, DuckLine
  freeze, file list), plan v2 (status, ledger, tool log, backlog) and added prompt copy
  `prompts/P-06_final-special-review.txt`.

### Verification

- Script syntax OK; 27 pixel sprite maps with zero width mismatches; no external URLs.
- Comment-stripped cross-reference audit: each of the three modules is clean of the other
  modules' names, palettes and element handles.
- Headless smoke run green for all three games, including the new peek-a-boo cycle
  (hidden → tell → peek → poke → relocate) and the frozen games' regression checks.
- Stage output rendered to PNG and inspected by eye for BooPeek (title, play, over) and
  DuckLine (title, play, over) plus both shelf cards.

### Build record (owner request: duration + tokens)

- Duration taken to build this review: **~30 min** (DeepSeek refactor + Gemini verification and docs completion).
- Tokens used in this change: **~1.5 M tokens processed** (DeepSeek session reached token limit; finalized in Antigravity).

## 005-20261101 — 2026-11-01 (pre-Round-4 cleanup)

Built from prompt: P-05 (special in-between cleanup before Round 4 — docs, art, module independence)  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode)** — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 3 (PANDASNACK module content 001-20261031 **unchanged/frozen**, BOOPEEK module content 005-20261101, DUCKLINE module content 005-20261101; file build 005-20261101)

### Changed — BOOPEEK re-skin (content 005-20261101)

- Replaced the reused panda-mover look with **Pip**, a cream lantern mouse with pink inner ears, a red scarf and a glowing lantern, and replaced the old door ghost with **Boo**, a soft white sheet ghost in a candy-teal nightcap with a pom, blush and a little tongue.
- Rebuilt the stage as a midnight nursery: striped plum wallpaper, moonlit window with a crescent moon and stars, string lights, framed heart, wall clock, a lived-in cupboard with a jar on a tiny shelf, potted plant, braided rug, toy ball and book.
- Gameplay polish: round limit 15 s → **20 s**, move speed 22 → 30 px/s, poke reach 10 → 20 px (forgiving on a 100 px stage), poke cooldown 0.10 s, ghost bob/blink/happy hop, poke rings and star sparkles. Reaching the goal of 10 no longer ends the round, so scores can exceed 10 and the best-score chase continues.

### Changed — DUCKLINE re-skin (content 005-20261101)

- Rebuilt the stage as a sunny top-down pond: drifting water bands with glints, lily pads, lotus flowers, cattails, a tiny frog, flowered banks and a patrolling dragonfly.
- New cast: a **mallard mother** (green head, white neck ring, cream body, brown chest, orange bill/feet) and **three ducklings**, each with a different silly accessory (red bow, leaf hat, single tuft).
- Gameplay polish: ducklings now scatter around the pond and fall into a **trail-following waddling line** once collected; round limit 12 s → **22 s**; swim speed 26 px/s; GO is a **quack boost** (1.7× for 0.55 s, 2 s cooldown) with a feather gauge; elliptical wakes and a foam splash. Score = ducklings × 10 + time bonus at the far bank.

### Changed — module independence and runtime hardening

- Added a "READ ME FIRST" boundary block at the top of the script and a boundary warning above PART 5: one sealed IIFE per game, only the module contract + PART 1 pixel helpers + `readBest`/`saveBest` + `scoreEl`/`bestEl`/`msgEl` may be shared, and private names must stay prefixed per game.
- Renamed every BOOPEEK private (`peek*`, `boo*`, `pip*`, `BOO_*`, `PIP_*`) and DUCKLINE private (`duck*`, `mama*`, `DUCK_*`) so no name can collide with PANDASNACK. Both new modules paint through the passed `ctx` only.
- Added a **FROZEN** banner to PANDASNACK (content 001-20261031): its art, numbers and legacy `stageCtx` painting are deliberately untouched.
- Runtime: opening a game, returning to the shelf and window `blur` now release every held direction through the contract (`releaseAllDirs` / `clearPadVisuals`), so input cannot leak between games; the shared frame loop wraps each module tick in `try/catch` and reports once instead of killing the loop.
- File build raised to `005-20261101` (app stamp and footer); PANDASNACK keeps `001-20261031`.

### Documentation

- Rewrote `README.md`: all three games documented (concept, controls, art highlights), models table extended through `-005`, module-boundary warning, build history, technical appendix.
- Added prompt copy `prompts/P-05_cleanup_before-round-4.txt`; updated `plans/micro-games-v2.md` (status, ledger, tool/model log, backlog).
- Marked build `004-20261101` as superseded for the file build and for BOOPEEK/DUCKLINE art.

### Verification

- Script syntax check OK; 27 pixel sprite maps checked with zero width mismatches; no external URLs.
- Line-level cross-reference audit after stripping comments: each of the three modules is clean of the other modules' names, palettes and element handles.
- Headless smoke run over all three games: PANDASNACK route/play/dash/restart/ESC, BOOPEEK scoring past 10 and timeout, DUCKLINE duckling collection and far-bank win, plus shelf reopen for each — all pass.

### Build record (owner request: duration + tokens)

- Duration taken to build this cleanup: **about 1 h 55 min of active work**, across two sittings (2026-10-31 21:06 → 2026-11-01 09:18; owner breaks excluded, ~12 h wall-clock).
- Tokens used in this change: **≈2.37 M processed** — ≈1.96 M input + ≈0.31 M output + ≈0.11 M reasoning, plus ≈28.4 M cached input reads. Counted from the session's full telemetry, so this figure is not comparable with the rough estimates recorded for `-003` and `-004`.

## 004-20261101 — 2026-11-01 (superseded by -005 for the file build and for BOOPEEK/DUCKLINE art)

Built from prompt: P-04 (Round 3 — DUCKLINE module add, the duck-family micro game)  
Tool and model: Flint 40B Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 3 (PANDASNACK module content 001-20261031, BOOPEEK module content 003-20261031, DUCKLINE module content 004-20261101; file build 003-20261031)

### Added

- Added the DUCKLINE module as the third game inside the one-file app (module content 004-20261101): a mother duck crosses the pastel pond with three ducklings in a waddling line behind her (WASD lead-a-chain), timer-limited round (12 s), victory at the far shore.

### Documentation

- Added prompt copy: prompts/P-04_round_3_duckline.txt.
- Updated the project README (round 3 status), the current plan (v2 backlog row for DUCKLINE).

### Build record (owner request: duration + tokens)

- Duration taken to build this round: about 25 minutes (DUCKLINE module add, prompt and plan updates, verification).
- Tokens used in this change: approximately 20,000 (DUCKLINE module add, prompt and plan updates, verification).

## 003-20261031 — 2026-10-31

Built from prompt: P-03 (Round 2 — BOOPEEK, the poke-the-ghost micro game)  
Tool and model: GLM-5.3-Flash Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 2 (PANDASNACK module content 001-20261031, BOOPEEK module content 003-20261031; file build 003-20261031)

### Added

- Added BOOPEEK as the second game module inside the one-file app: a shy ghost peeks from a cozy door on a small floor-and-wall pastel stage, the visitor (the panda mover) walks up with WASD and pokes with SPACE / the POKE pad or a stage tap; reaching the ghost within 10 design pixels scores a poke and pops six star sparkles, victory is at 10 pokes (BOO! YOU FOUND HIS HEART!), and the goal readout is drawn as "BOO LOVE n/n" in the shared pixel font.
- Wired BOOPEEK into the one-file runtime: shelf card, module registry entry, action button label (DASH → POKE per module), input routing, hash route `#game=BOOPEEK`, module-level restart/save/read.
- Updated the file version to 003-20261031 and stamped the footer accordingly; PANDASNACK's module content keeps its round 1 version number.

### Changed

- Re-verified the whole one-file app after adding the module: script syntax check OK, pixel maps consistent, no external URLs, no sentinels, no stray characters, balanced tags, full headless smoke run (route, play, poke actions via keys, restart, ESC, reopen) with zero exceptions.
- Finished the BOOPEEK module for real play during final QA: the module now paints its visitor (the walking panda) on the stage, pushes the score into the shared chrome on poke, and both crash paths on the first successful poke are closed (the score-chip pulse helper is module-scoped to PANDASNACK and was not visible inside BOOPEEK; the sparkle drawer now takes the context), and poking is action-driven (button / stage tap / pad) instead of firing on every physics step.
- BooPeek round-time limit: added a 15 second round timer (`roundTimeLimitSeconds`) that ends the round via `finishRun(false)`; the victory run (`finishRun(true)`) stays at the 10 poke target; the stage HUD now also shows the remaining time.
- BooPeek ghost polish: the ghost now wiggles and hops in place while shy after a poke (`pokeT` / `wiggleT` phases) instead of sitting static.
- BooPeek decoration: added small pastel floral dots inside the 100x100 stage, and the shelf card preview now uses a BooPeek scene painter (`paintBoopeekPreview`).

### Documentation

- Added prompt copy: prompts/P-03_round_2_boopeek.txt.
- Updated the project README (round 2 status), the current plan (v2 ledger row -003), the backlog row for BOOPEEK.

### Build record (owner request: duration + tokens)

- Duration taken to build this round: about 45 minutes (BooPeek module, wiring, docs, verification).
- Tokens used in this change: approximately 27,000 (BooPeek module, registry wiring, docs and changelog edits for build 003-20261031).

## 002-20261031 — 2026-10-31

Built from prompt: P-02 (the one-file pivot)  
Tool and model: GLM-5.3-Flash Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 1 (PANDASNACK, module content still -001)

### Added

- Added the one-file architecture: the arcade shelf and the game view are two screens that swap inside a single `index.html` — no navigation, no iframes, no game folders; the file build number steps to 002-20261031 while PANDASNACK's module content keeps its round 1 number.
- Added the module contract: every game is a self-contained IIFE with its own SETTINGS, palette and maps, registered into a GAMES registry (start/stop/restart/update/paint/onDir/onAction/onStageTap/onAnyKey), and the runtime ticks and paints only the open module through one shared loop.
- Added one shared stage canvas and one shared pad deck with global keyboard routing (WASD + arrows move, SPACE action, R instant restart, ESC back to the shelf), hash routing (`#game=PANDASNACK` lands straight in a game) and whole-number stage scaling kept as before.
- Kept the shared pixel helper layer defined once in the file (paintPixels with scale and flip, paintRoundBlob, paintEyes, the 3x5 pixel font, paintPixelText) so the mascot, card previews and game modules all share the same drawing language; best-score save keys stay unchanged so old scores survive.
- Removed the `games/` folder after folding PANDASNACK into the file; the folder now holds only documentation.
- Updated docs for the pivot: README (one-file layout plus the PANDASNACK manual section), plan v2 (micro-games-v2.md) with a history note left on plan v1, and the P-02 prompt copy. Ran the lint checks (map widths, balanced tags, zero external URLs) and an extended headless smoke test: hash routing into the shelf and game, 1,500 frames of walking, dashing and restarting, round trip back to the shelf and reopen — zero exceptions. A hands-on phone (Safari) test remains pending.

## 001-20261031 — 2026-10-31

Built from prompt: P-01  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode)** — corrected in build 006; this build was originally recorded as GLM-5.3 Flash Free, but the owner confirmed it was made with DeepSeek V4.1 Flash Free  
Games on the shelf: 1 (PANDASNACK)

### Added

- Added the first micro game, PANDASNACK: a chubby panda scurries on a tiny 100 x 100 design-pixel pastel meadow, munches two always-available bamboo shoots (each worth +1), and dodges drifting wasps that cost one heart per sting with 1.6 seconds of shy flashing; three hearts end the run, and the difficulty climbs through a four-band table (1 to 4 wasps, speeds 13 to 26) as the score grows.
- Added a dash (SPACE, DASH pad or stage tap): a 0.7-second 1.75 times scurry with a 2.2-second cooldown shown as a rounded pixel gauge plus a tiny leaf that refills beside the three pixel hearts.
- Added the hand-drawn pixel art: blob-composed panda (lean-and-waddle walking, random blinks, happy munch mouth, dust puffs, droopy ears and a rolling tear at game over), two-frame flapping wasps, swaying bamboo shoots, sparkle bursts, dot-flowers on a cached two-tone checker background, and a shared 3 x 5 pixel font for all stage text with an optional one-pixel shadow pass.
- Added the toy-console page chrome: score/best chips with a munch pulse, a state message line, a four-pad plus DASH plus RESTART touch layout using pointer capture and touch-action none, WASD and arrow keys with instant R restart, and stage-tap dashing; the panda hides on every other beat while sting-protected.
- Wired the PANDASNACK card into the shelf page: code-drawn preview scene (panda, two bamboo shoots, two wasps), concept line, best score from the shared save key, COMING SOON blurb refreshed, shelf version raised to 001-20261031.
- Added games/PANDASNACK/README.md with controls, settings table with allowed ranges, difficulty bands and the full named palette, and saved the P-01 prompt copy.
- Ran a headless smoke test of the shipped file: the patched stub DOM ran 1,200 frames of walking, dashing and restarting with zero exceptions and a correctly auto-sized stage. A hands-on phone (Safari) play test is still pending.

## 000-20261031 — 2026-10-31

Built from prompt: P-00 (Round 0 — project scaffold)  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode)** — corrected in build 006; originally recorded as GLM-5.3 Flash Free  
Games on the shelf: 0 (one COMING SOON slot)

### Added

- Created the KANTMICROGAME project as the home for tiny, cute, pixel-art HTML5 micro games and the seven micro-game rules (single file, offline, tiny stage, pixel art, WASD touch controls, one concept, short play).
- Added the single-file offline selection page `index.html`: toy-shelf look with warmth and soft colors, a code-drawn pixel panda mascot that bobs and blinks, how-to-play chips, a card area for game links, best-score display from browser saves, a dashed COMING SOON slot that keeps the shelf open for growth, and a version footer.
- Added the project README with the seven rules, folder layout, round table and the honest "not built yet" list.
- Added the project plan `plans/micro-games.md` with the full stage spec, control spec, per-game settings recipe, selection-page spec, definition of done, round table and eight-game concept backlog.
- Saved this round's prompt copy in `prompts/P-00_round-0_project-kickoff.txt`.
