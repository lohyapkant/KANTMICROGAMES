# KANTMICROGAMES — Model observations (owner notes)

A dated, **append-only** place for the owner's subjective notes on how each model
performed on this project. It is not a ranking and not a permanent verdict: models change,
versions change, and a note here describes one moment on one set of builds.

From build 013 this file also holds the Usage ledger: a record of what each model used on
each build. It is a record, not an opinion.

**Rules for future models / LLMs**

1. Do **not** rewrite or delete an existing observation. Add a new dated entry instead.
2. Keep it factual and polite: describe what was built, what worked, what needed rework.
3. One entry per model per observation date; link the builds it refers to.
4. This file is documentation only — it never affects the game code or the build record.
5. From build 012 every entry starts with a Source line: either 'Owner's words (verbatim)'
   or 'Recorded by <model> from the owner's feedback'. Earlier entries predate this and are
   kept as written.
6. When one model delivers several builds, write one entry per build and name the build in
   the heading.
7. The Usage ledger is a record, not an observation. Add one row per model per build, every
   build, copied from the CHANGELOG Build record. Observation entries stay owner-only.
8. Model names are written exactly as the tool shows them; effort is recorded separately (in the ledger's Role cell). Earlier entries merge the two and are kept as written.

**Project links (kept current for every model reading this file)**

- GitHub repository: <https://github.com/lohyapkant/KANTMICROGAMES>
- Public demo (Cloudflare Workers): <https://kantmicrogames.lohyapkant.workers.dev/>
- Hosting platform: <https://workers.cloudflare.com/>
- Project name: **KANTMICROGAMES** (repository, worker and public address). The app, the
  save keys (`KANTMICROGAMES.<GAME>.best`, `KANTMICROGAMES.ui.*`) and the console tag use
  that name from build 010; the local folder is `KANTMICROGAME/` and the archived prompt
  copies keep their original spellings. For both, see Naming in `CHANGELOG.md` →
  Conventions.
- License: MIT (see `LICENSE` and the header comment in `deploy/index.html`). Legal name of
  the original creator: **Loh Yap Kant**, with help from the models observed below.

## How this project is paid for

This project is built on free and trial plans on purpose, to see what a person with no budget can do.
- **Qoder CLI** runs on Qoder's first-sign-in offer: a free 14-day Pro trial with 300 credits. Unused trial credits are cleared when the trial ends. Model selection is set to Auto; the ledger records the model name the tool reports.
- **Claude.ai chat** (used to write some of the prompts) runs on a plan with a usage window that the owner describes as about 5 hours. Its usage is read by the owner from Claude's usage page, in percent of the window, not tokens.
- Earlier builds used OpenCode's free models and Antigravity.
- **Update, 2026-11-03:** the Qoder trial credits are used up (plan meter 300/300; the trial itself ends 2026-11-15 at 15:24:49 GMT+7). Build 017 was finished on OpenCode with DeepSeek V4.1 Flash Free, and builds 018 onward run on OpenCode's free models unless noted.
When a quota runs out the work pauses and resumes with whatever is available (see CHANGELOG.md → Conventions → Continuity when a free tier runs out).

## Usage meters explained

What each tool's own meter shows, in plain words. Filled from each tool's documentation
where a page could be opened (2026-11-03); anything that could not be confirmed from a
page says "to confirm" or "not confirmed".

| Tool | What the meter shows | Unit | Resets or expires | Where to look | Source |
|---|---|---|---|---|---|
| Qoder CLI | credits spent per request; heavier models and longer work spend more | credits | the 14-day Pro trial (300 credits from first sign-in) ends on its date and unused credits are cleared; list price is about US$0.01 per credit | Qoder usage page | https://docs.qoder.com/account/pricing |
| Claude.ai chat | how much of the usage window is used | percent of the window, not tokens | the window resets (owner: about 5 hours); exact rules to confirm | Claude's usage page, read by the owner | to confirm |
| OpenCode | the Console tracks usage with budget controls, credits can be added to a workspace, and open-source model access comes through Go subscriptions (US$10 / US$40 / US$20 per member per month) | credits; US$ per month | how added credits expire is not stated on the page read; subscriptions are monthly | the OpenCode Console, Usage and Billing pages | https://opencode.ai/v2/docs/console/ |
| Antigravity | the free Individual plan (US$0/month) works on basic weekly rate limits; Google AI Pro and Ultra add higher rate limits and a flexible AI credit pool; organizations use Google Cloud with consumption-based API pricing | weekly rate limits; credits | rate limits reset weekly; credit-pool rules are on the plans docs | the Antigravity pricing page and its plans docs | https://antigravity.google/pricing |

## Usage ledger

What each model used on each build. This is a record, not an opinion, and not a ranking.

- One row per model per build. Failed, halted and prompt-only contributions get a row too.
- Numbers are copied from the build's Build record in CHANGELOG.md. If a figure was corrected later, the final one is used.
- **Tokens and credits are different units.** Credits are a tool's billing unit (here Qoder CLI), not tokens and not money. Token figures were counted in different ways (see "How counted"), so they are never added together.
- "—" means not recorded. "~" means approximate.

<!-- ADD NEW LEDGER ROWS DIRECTLY AFTER THE LAST ROW OF THE TABLE BELOW (no blank lines inside the table), then recompute the totals under it. -->
| Build | Model · tool | Role | Time | Usage | How counted |
|---|---|---|---|---|---|
| 000 | DeepSeek V4.1 Flash Free · OpenCode | built | — | — | not recorded |
| 001 | DeepSeek V4.1 Flash Free · OpenCode | built | — | — | not recorded |
| 002 | GLM-5.3 Flash Free · OpenCode | built | — | — | not recorded |
| 003 | GLM-5.3 Flash Free · OpenCode | built | ~45 min | ~27,000 tokens | approximate; method not stated |
| 004 | Flint 40B Free · OpenCode | built | ~25 min | ~20,000 tokens | approximate; method not stated |
| 005 | DeepSeek V4.1 Flash Free · OpenCode | built | ~115 min active | ~2.37 M tokens | measured: input + output + reasoning; ≈28.4 M cached reads not counted |
| 006 | DeepSeek V4.1 Flash Free · OpenCode, then Gemini 3.8 Flash · Antigravity | started, then completed | ~30 min | ~1.5 M tokens | "processed"; one shared figure, cannot be split |
| 007 | Gemini 3.8 Flash · Antigravity | built | ~25 min | ~48,000 tokens | approximate; method not stated |
| 008 | GPT-OSS 120B Medium · Antigravity | attempted, abandoned | — | — | not recorded |
| 008 | Claude Opus 4.6 Thinking · Antigravity | built, halted mid-round | ~20 min | ~60,000 tokens | approximate; method not stated |
| 008 | Qwen3.8-Flash · Qoder CLI | recovery pass | ~15 min | ~30,000 tokens | estimate |
| 009 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 009 | Qwen3.8-Flash · Qoder CLI | built | ~30 min | 19.7809 credits | measured: Qoder per-request credits, 157 requests |
| 010 | Qwen3.8-Flash · Qoder CLI | built | ~30 min | 9.0583 credits | measured: 186 requests |
| 011 | Qwen3.8-Flash · Qoder CLI | built | ~30 min | 8.2768 credits | measured: 115 requests |
| 012 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 012 | Qwen3.8-Flash · Qoder CLI | built | ~20 min | 5.9094 credits | measured: 112 requests (4.4968 at build end; final total from the CHANGELOG addendum) |
| 013 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 013 | Qwen3.8-Flash · Qoder CLI | built | ~22 min | 4.5351 credits | measured: 104 requests |
| 014 | Qwen3.8-Flash · Qoder CLI | built | ~24 min | 8.9189 credits | measured: 124 requests (final figures from the CHANGELOG addendum) |
| 015 | Qwen3.8-Flash · Qoder CLI | built | ~17 min | 7.8667 credits | measured: 147 requests (final figures from the CHANGELOG addendum) |
| 016 | Qwen3.8-Flash · Qoder CLI | built | ~18 min | 10.2413 credits | measured: 198 requests (final figures from the CHANGELOG addendum) |
| 017 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 017 | Qwen3.8-Flash · Qoder CLI | built | ~99 min (1 h 38 min 49 s wall; 1 h 13 min 18 s active) | 52.7558 credits at 17:49; 300.8933 session credits at exit | measured: 104 billable requests at 17:49; Qoder exit report: plan 300/300, session 300.8933, 398 tool calls; the two meters are not added together |
| 017 | DeepSeek V4.1 Flash Free · OpenCode | finished build 017 after the Qoder trial ended | ~25 min | 165,312 tokens processed | measured: 116,561 input + 23,506 output + 25,245 reasoning; 11.82 M cached reads not counted; 107 assistant turns |
| 018 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 018 | DeepSeek V4.1 Flash Free · OpenCode | built | ~35 min | — | not visible to the model; owner notes blank, no meter reading supplied |
| 019 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 019 | DeepSeek V4.1 Flash Free · OpenCode | built | ~30 min | — | not visible to the model; owner notes blank, no meter reading supplied |
| 020 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 020 | DeepSeek V4.1 Flash Free · OpenCode | built | ~15 min | — | not visible to the model; owner notes blank, no meter reading supplied |
| 021 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 021 | DeepSeek V4.1 Flash Free · OpenCode | built | ~10 min | 162,156 tokens processed | measured: 105,696 input + 28,262 output + 28,198 reasoning; 8.61 M cached reads not counted; OpenCode stats delta (see CHANGELOG build record) |
| 022 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 022 | Gemini 3.8 Flash · Google Antigravity | started build 022 (steps 0-4) and halted when it ran out of tokens | ~35 min | — | not recorded — time only |
| 022 | DeepSeek V4.1 Flash Free · OpenCode | finished build 022 (steps 5-6) after the Gemini halt, in two runs (the first stopped during the docs check) | ~38 min | 361,981 tokens processed | measured: 309,861 input + 32,999 output + 19,121 reasoning; 7,112,192 cache reads not counted; 69 steps; 68 tool calls; OpenCode stats delta, final reading after the swap and the docs check (see CHANGELOG build record) |
| 023 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt | — | — | not recorded |
| 023 | DeepSeek V4.1 Flash Free · OpenCode | built | ~17 min | 187,025 tokens processed | measured: 109,671 input + 36,437 output + 40,917 reasoning; 7,591,808 cache reads not counted; 67 steps; 68 tool calls; OpenCode stats delta, final reading after the swap and the live regression (see CHANGELOG build record) |
| 024 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt (effort Extra) | — | — | not recorded |
| 024 | DeepSeek V4.1 Flash Free · OpenCode | built (effort High) | ~33 min | 301,245 tokens processed | measured: 177,793 input + 52,299 output + 71,153 reasoning; 16,589,568 cache reads not counted; 164 steps; 170 tool calls; OpenCode stats delta, final reading after the swap and the live regression (see CHANGELOG build record) |
| 025 | Claude.ai Sonnet 5.5 Extra · Claude.ai chat | wrote the prompt (effort Extra) | — | — | not recorded |
| 025 | DeepSeek V4.1 Flash Free · OpenCode | built (effort High) | ~13 min | 241,367 tokens processed | measured: 183,163 input + 35,981 output + 22,223 reasoning; 8,790,144 cache reads not counted; 81 steps; 103 tool calls; OpenCode stats delta, final reading after the swap and the live regression (see CHANGELOG build record) |

### Totals that can honestly be added
- **Credits, Qoder CLI, per-request transcript, builds 009-016:** 74.5874 credits over 1,143 billable requests.
- **Build 017, two readings, never added:** the transcript snapshot taken at 17:49 shows 52.7558 credits over 104 requests (incomplete: the session ran on afterwards). Qoder's own exit report shows session 300.8933 credits, 398 tool calls and the plan at 300/300 credits.
- **Unreconciled:** the transcript total for builds 009-016 plus the exit-report figure for build 017 is more than the 300-credit plan, and why is not known. Do not total these readings. The authoritative figure is Qoder's usage history, read by the owner.
- **Approximate list-price value:** the plan meter reads 300 of 300 trial credits used, which is about US$3.00 at about US$0.01 per credit. An estimate, not a bill: the trial is free. Check https://docs.qoder.com/account/pricing before relying on it. Never converted for tokens and never added across tools.
- **Iterations recorded (from build 017):** 4 over 1 build.
- **Iterations recorded (build 018):** 1 repair cycle pair (a 280 px control clash, fixed by stacking the corner pair under 360 px and using 4 px page padding).
- **Tokens, OpenCode readings (input + output + reasoning; cache reads not counted), builds 005, 017, 021, 023, 024 and 025:** about 3.47 M tokens in total (005 is approximate at about 2.37 M; 017 is 165,312; 021 is 203,831 at the final reading; 023 is 187,025; 024 is 301,245 at the final reading after the swap and the live regression; 025 is 241,367 at the final reading after the swap and the live regression). Builds 018, 019 and 020 have no token reading. Other token figures count different things and are never added to these.
- **Build 021 usage note:** the ledger row for build 021 shows the reading taken when the records were written (162,156 tokens); the build's usage after the final swap is 203,831 tokens. The row is a record and is not edited.
- **Build 022 token reading:** 361,981 tokens (input 309,861 + output 32,999 + reasoning 19,121; 7,112,192 cache reads not counted; 69 steps; 68 tool calls; cost $0.00), from the OpenCode final reading after the swap and the docs check. An earlier post-swap reading of 249,131 was taken before the OpenCode run stopped and resumed; the ledger uses 361,981. Gemini 3.8 Flash's share of build 022 has no reading. The bullet above listed builds 005, 017 and 021 when this note was written; build 023 extended it.
- **Time by model, approximate.** Builds 000-002 and the GPT-OSS attempt have no time recorded, so DeepSeek and GLM are undercounted. One block = 10 minutes, rounded half up.

| Model | Minutes | At a glance |
|---|---|---|
| Qwen3.8-Flash | ~305 | ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ |
| DeepSeek V4.1 Flash Free | ~331 | ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ |
| Gemini 3.8 Flash | ~60 | ▇▇▇▇▇▇ |
| GLM-5.3 Flash Free | ~45 | ▇▇▇▇▇ |
| Flint 40B Free | ~25 | ▇▇▇ |
| Claude Opus 4.6 Thinking | ~20 | ▇▇ |
| Shared session (build 006: DeepSeek + Gemini) | ~30 | ▇▇▇ |

Total recorded: about 816 minutes (about 13 h 36 min) over 23 of 26 builds.
(Totals were recomputed after the build-025 row was added and the earlier correction applied; the CHANGELOG Build records remain the source of truth.)

## 2026-11-07 — DeepSeek V4.1 Flash Free (OpenCode) — build 021

Source: Owner's words (verbatim)

Builds observed: `021-20261107`.

The owner's notes: after trying build 021, the owner said, verbatim:

> "I am quite happy with the settings button at the first initial page and the color matches the tone of the kantmicrogames"

This is a dated owner note about one build on one day, not a model-written summary.

## 2026-11-07 — Claude.ai Sonnet 5.5 Extra (Anthropic, chat) — prompt author, builds 017 to 021

Source: Owner's words (verbatim)

Builds observed: `017-20261103`, `018-20261104`, `019-20261106`, `020-20261106`, `021-20261107`.

The owner's notes: the owner said, verbatim:

> "I am happy with the way Claude Ai Sonnet 5.5 Extra has been providing the prompt to assist in the continued development."

The prompts for these five builds were written by Claude.ai Sonnet 5.5 Extra and pasted into the executing tools by the owner. This is a dated owner note, not a ranking.

---

## 2026-11-01 — DeepSeek V4.1 Flash Free (OpenCode)

Builds observed: `000-20261031`, `001-20261031`, `005-20261101`, `006-20261101`.

The owner's notes: the strongest results on this project so far. Pixel art was a
particular highlight — characters read clearly at 100×100, with distinct silhouettes,
expressive faces and a consistent cute style (the panda, Pip the lantern mouse, Boo the
nightcap ghost, the mallard family). Coding was also strong: the one-file structure stayed
readable, the module boundaries held, and the builds passed syntax, sprite-map and
headless smoke checks. The owner described the output as "amazing" for both art and code.

## 2026-11-01 — GLM-5.3 Flash Free (OpenCode)

Builds observed: `002-20261031`, `003-20261031`.

The owner's notes: at the time of this observation, a noticeably weaker fit for this
project. The one-file pivot and the first BOOPEEK module worked mechanically, but BOOPEEK
reused the PANDASNACK stage interface and mover instead of getting its own look, so it
needed a full art and gameplay rework in `005-20261101`. This is a snapshot of that date,
not a claim about later GLM versions.

## 2026-11-01 — Flint 40B Free (OpenCode)

Builds observed: `004-20261101`.

The owner's notes: at the time of this observation, also a weaker fit. DUCKLINE was added
as a working module but without its own 100×100 pixel art — it leaned on the shared
interface, so the pond and duck family had to be rebuilt in `005-20261101`. As above, this
records one dated experience and may not reflect future versions.

## 2026-11-01 — Gemini 3.8 Flash (Antigravity)

Builds observed: `006-20261101`, `007-20261101`.

The owner's notes: picked up cleanly from DeepSeek after token limits were reached.
Successfully cleaned up code, fixed the BooPeek lower floor traversal bug allowing Pip
to walk down through the translucent score panel to poke Boo, and refactored and reviewed
the README and CHANGELOG records cleanly. In Round 4 (`007-20261101`), delivered SPROUTUP
with cute pixel art, frozen BOOPEEK, and added live in-stage HUD score tracking to
PANDASNACK before refreezing it, strictly adhering to all architectural and documentation rules.

## 2026-11-01 — GPT-OSS 120B Medium (OpenAI, via Antigravity)

Builds observed: `008-20261101` (attempted, not completed).

The owner's notes: attempted for build 008 (documentation cleanup — adding links, MIT
license, and recording the `deploy/` folder move). The model deleted sections of the
README, CHANGELOG, and other files instead of following the existing templates and
guidance inside those files. The owner described the output as "really bad" for this task —
the model removed content rather than appending to or editing it as instructed. The attempt
was abandoned and the work was completed by a different model. This is a snapshot of one
session on 2026-11-01 and may not reflect later versions or different task types.

## 2026-11-01 — Claude Opus 4.6 Thinking (Anthropic, via Antigravity)

Builds observed: `008-20261101`.

The owner's notes: picked up from the failed GPT-OSS 120B attempt. Successfully completed
the documentation cleanup build: added GitHub and public-site links to all documentation
homes, documented the `deploy/` folder move for Cloudflare Workers, added the MIT license
header to `index.html`, added educational model links, and recorded the GPT-OSS attempt
factually. Followed all existing file templates, conventions and guidance without deleting
or restructuring existing content.

## 2026-11-01 — Qwen3.8-Flash (Qoder CLI)

Builds observed: `008-20261101` (completion pass).

The owner's notes: picked up after Claude Opus 4.6 Thinking halted mid-round with most of
the documentation cleanup done but uncommitted. This model audited every P-08 requirement
against the actual files, found the gaps (the project links claimed for `MODELS.md` were
never added; the model home-page links were missing from the CHANGELOG and the prompt copy;
`plans/micro-games-v2.md` had no project links) and completed them. Added the model's own
build record per the owner's standing request. Existing content was preserved throughout —
append and edit-in-place only, following each file's template.

## 2026-11-01 — Claude.ai Sonnet 5.5 Extra (Anthropic, chat) — prompt author

Builds observed: `009-20261101` (authored the P-09 prompt; did not edit the repository).

The owner's notes: this build's prompt was written by Claude.ai Sonnet 5.5 Extra and
pasted unaltered. It is unusually specific for this project: it states the editing
boundaries (frozen IIFEs, no contract changes, stage stays 100×100), fixes the three owner
decisions (zoom allowed, pads auto with overrides, whole-number scaling with a documented
fallback), lists thirteen measured baseline findings and seven ordered steps, and defines
the verification matrix, assertions, screenshots, deliverables and definition of done. In
practice this kept the work inside the shell and made the build auditable. Its only
mismatch was the build number — it says 008, but 008 had already been used — which was
handled as a documented deviation rather than by editing the prompt. This is a snapshot of
one prompt on one date.

## 2026-11-01 — Qwen3.8-Flash (Qoder CLI) — responsive shell build

Builds observed: `009-20261101` (full build; see also the completion pass entry above).

The owner's notes: implemented all seven steps of P-09 in the shared shell only. The four
game IIFEs were left byte-identical (proved by SHA-256 of the PART 5 region). Built a
Playwright matrix over 24 viewports × 4 games, inspected 120 screenshots, and fixed two
layout issues that the DOM metrics alone did not catch (the stage stayed small because its
measurement box was content-sized; the pads sat at the screen edges in landscape). The
resulting suite runs 1,409 assertions with zero failures, and the build added `CONTROLS.md`,
a test report, a real-device checklist and the build's records. Honest limits recorded in
the report: headless Chrome only, no physical device or other browser, and the token count
is unknown because the tool surfaced no telemetry.

## 2026-11-01 — Qwen3.8-Flash (Qoder CLI) — credit record for build 009

Builds observed: `009-20261101` (record addendum; no code change).

The owner's notes: this tool does not report token counts. Its session transcript carries a
`credits` value for every API request instead, so the record for build 009 was updated to
**19.7809 credits used** across 157 billable requests (2026-11-01, 16:14–16:40 WIB), summed
from that per-request telemetry. The unit is credits, not tokens, and is labelled as such
everywhere it appears (README, CHANGELOG, plan tool log and `P-09` prompt copy). By
coincidence, this is also the first build whose documentation pass audited the project name
and standardised it on **KANTMICROGAMES**. Credits are a snapshot of one billing meter on
one date, not a ranking of the model.

## 2026-11-01 — Qwen3.8-Flash (Qoder CLI) — Round 5, SLIMEHOP

Builds observed: `010-20261101` (full build).

The owner's notes: delivered Round 5 in one sitting. SLIMEHOP shipped as a fifth sealed
IIFE — a 3×3 lily-pad pond with one-hop movement, the WET → MOSS → BLOOM pad states, a
stomp with cooldown and snail stun, a snail that eats flowers, an in-stage pixel HUD and a
custom shelf preview. The art went through several screenshot-driven revisions: the slime
initially touched the pad above it, the moss and flower floated a pixel or two off the pad,
the title plate ghosted the pads behind it, and bloom sparkles landed on the slime's face —
all fixed after inspecting 6× crops rather than trusting the code. The model also renamed
the on-screen brand, save prefix and console tag to **KANTMICROGAMES** on the owner's
instruction (the page is fresh, so no migration was needed), kept the four frozen modules
byte-identical apart from their unused `saveKey` labels, proved that by diff, and recorded a
documented deviation from the backlog's floating-pad concept. Verification covered all five
games, four viewports and touch emulation in headless Chrome. Honest limits are recorded in
the changelog: no physical devices, no other browsers, and Qoder exposes credits but not
tokens. This is a snapshot of one build on one date.

## 2026-11-01 — Owner observation — SLIMEHOP (build 010) and the Round 6 brief

Builds observed: `010-20261101`, `011-20261101`.

The owner's notes: after playing SLIMEHOP, the owner asked for this assessment to be kept
for historical reference, verbatim:

> "This looks very very very good - thank you. Please note that i am impressed with the
> gameplay, pixel art, design of the SlimeHop game in one pass thanks to your model in a
> single session. Have this recorded for historical reference in the model file for
> documentation. Please proceed to freeze Sproutup and Slimehop. And please proceed with
> SNAILRACE for Round 6, and still following the same required concept for pixel art,
> simple and fun and quirky and colourful pixel art for the game design and shelf art
> work, and intended for the 100x100 play area with scoring and time as needed - dependent
> on your game design for this project. Please continue to document in detail for
> reference in readme file, prompt file, changelog file, and continue to test as needed
> within the rules of the intended design. Please also track the time taken, and the token
> or credit used as usual for records and record keeping."

The owner froze **SPROUTUP** and **SLIMEHOP** in the same message; both keep their content
numbers (`007-20261101`, `010-20261101`) and their IIFEs are byte-identical to build 010.
This is a dated owner note, not a model-written summary.

## 2026-11-01 — Qwen3.8-Flash (Qoder CLI) — Round 6, SNAILRACE

Builds observed: `011-20261101` (full build).

The owner's notes: delivered Round 6 in one sitting after the SLIMEHOP praise above.
SNAILRACE shipped as a sixth sealed IIFE: three garden snails race across a peach gingham
picnic blanket to a strawberry, with lettuce giving points and a boost, salt locking the
controls, a ZOOM action on a cooldown, two auto-running rivals and a 20 s clock. The art
went through several screenshot-driven revisions: the first 14×10 snail read as a shell
with a detached foot and floating eyes (redrawn as 16×10 with a head, neck and eyestalks),
the gingham and HUD plate were too heavy (softened cloth, plate alpha 0.9), a salt pile
crowded the finish ribbon (moved), and normalising diagonal speed made a straight race
unwinnable (per-axis full speed fixed it; "hold right + zoom" then won twice). The model
froze SPROUTUP and SLIMEHOP on request, kept all five frozen IIFEs byte-identical to build
010, and recorded the proof. Verification covered six games, four viewports, touch
emulation, a no-auto-movement test and balance runs in headless Chrome. Honest limits are
in the changelog: no physical devices, no other browsers, and Qoder exposes credits but not
tokens. This is a snapshot of one build on one date.

---

## 2026-11-02 — Owner observation — HUGPARADE (builds 014 and 015), Qwen3.8-Flash (Qoder CLI)

Source: Owner's words (verbatim, from prompt P-15)

Builds observed: `014-20261102`, `015-20261102`.

The owner's notes: the first HUGPARADE build is impressive work for Qwen and Qoder, but
it shipped with logic problems and needed correction before the next game. The owner's
words:

> "Finally, please record my observation that the first round HUGPARADE creation is
> amazing for the Qoder Qwen model, but has logic problems for the initial build, and
> needs correction."

The owner also described the problems in the same message (abridged, wording kept):

> "The path for the controlled character of the player is hard to maneuver in the game.
> Sometimes, it get stuck moving between the maze."

> "It is not made clear on what is the scoring about or what is the objective of the
> game."

> "I am not sure what is the one being kept track of - is it the hugs? Or the collection
> of the hearts? Or is the score?"

Build `014-20261102` created the game (maze, art, PEEK, shelf preview) and build
`015-20261102` corrected it: movement now runs on cell rails and cannot wedge, and the
score is hug points (1 plus one per heart held, maximum 4) stated on the title plate.
This is a dated owner note, not a model-written summary, and not a permanent verdict.

## 2026-11-03 — Qwen3.8-Flash (Qoder CLI) — build 017: shell UX, then credit exhaustion

Source: Recorded by DeepSeek V4.1 Flash Free from the owner's feedback, the CHANGELOG
addendum and the Qoder exit report.

Builds observed: `017-20261103` (steps 0–6; the swap into the live files was not reached).

The owner's notes: this session did the shell work and then ran the Qoder trial out of
credits while repeating the verification matrix. What it delivered: shelf cards aligned by
a flex column with the best line pinned to the bottom; a corner MENU button and the M key
with a paused dialog (RESUME / RESTART · R / ⌂ SHELF, focus trap, ghost-click safety);
crisp+ stage scaling; PAD SIZE S/M/L; the CHANGELOG conventions, continuity block and
checklist additions; the MODELS “How this project is paid for” and “Usage meters
explained” sections; a 20-viewport matrix with screenshots; and the `017-20261103` entry.
What it did not reach: the swap into the live files, `tests/build-017-report.md`, the P-17
prompt copy and the final-session addendum. The live files were still build 016 when the
trial ended. The work itself was substantially complete and verified; the failure was
operational (the credits ran out), not a missing design.

The owner describes the session as stuck in continuous testing, with the matrix repeated
until the 300-credit trial was completely used up. The owner's wording is “tokens”; Qoder's
meter reports **credits**, not tokens, and the record keeps that distinction. The Qoder
exit report for the session: plan **300/300 credits used**, session **300.8933 credits**,
**398 tool calls**, wall **1 h 38 min 49 s** (agent active 1 h 13 min 18 s), code changes
**+1,041 / −104** lines. This is a dated snapshot of one session, not a permanent verdict
on the model, and later Qwen versions may behave differently.

## 2026-11-03 — Claude.ai Sonnet 5.5 Extra (Anthropic, chat) — P-17 prompt author

Source: Recorded by DeepSeek V4.1 Flash Free from the owner's feedback and the saved
prompt.

Builds observed: `017-20261103` (authored the P-17 prompt; did not edit the repository).

The owner's notes: the structured prompt again did the heavy lifting for the build. It set
the boundaries (shell and docs only; all eight game IIFEs must stay hash-identical), listed
the owner decisions, measured baseline findings F1–F6, and gave seven ordered steps with
acceptance criteria. It supplied the exact text for the CHANGELOG conventions, the
continuity block, the MODELS payment and meter sections, the README sentence and the
roadmap, plus a 20-viewport verification matrix, a screenshot list, deliverables and a
definition of done. It told the model to work in `plans/archive/pre-017/work/`, keep
`PROGRESS.md` with DONE/NEXT lines, and swap into the live files in one step at the end —
which is exactly what made the hand-over possible when the credits ran out. The prompt is
saved verbatim in `prompts/P-17_shell-ux-and-process.txt` (private archive). This is a
snapshot of one prompt on one date.

## 2026-11-03 — DeepSeek V4.1 Flash Free (OpenCode) — build 017 hand-over

Source: Owner's words (verbatim) and a record of the completion pass.

Builds observed: `017-20261103` (completion pass after the Qoder trial ended).

The owner's words, verbatim: “my observation that you have saved me from a horrible
unfinished situation and that you have picked up and assisted me properly”.

What this pass did: read the CHANGELOG conventions and checklist, the 017 entry and
`plans/archive/pre-017/PROGRESS.md`; verified the work copies (all eight game IIFEs
hash-identical to build 016, `node --check` clean, docs 26/26); found and fixed one real
defect — the game title still truncated at 390–430 px because the compact top row only
applied below 380 px, so the breakpoint is now 440 px; re-ran a focused 20-viewport check
(1,184 checks, 0 fails) and retook the 12 screenshots; swapped the six work files into the
live files in one step; ran the post-swap checks (hashes, syntax, docs 26/26, live render
175 checks / 0 fails); wrote `tests/build-017-report.md` and
`prompts/P-17_shell-ux-and-process.txt`; added the final-session addendum and this MODELS
update. Qwen's part is the entry above: the shelf, MENU, crisp+ stage, PAD SIZE, the
conventions and the 20-viewport matrix; the missing part was the swap, report and prompt
copy.

Time and usage: about **25 min** wall-clock (2026-11-03, 19:05–19:30 WIB); **165,312
tokens processed** (116,561 input + 23,506 output + 25,245 reasoning); 11.82 M cached reads
not counted; 107 assistant turns, measured from the session's per-message token telemetry.
No credits were used (OpenCode free model). No git command was run; the suggested commands
in the report are suggestions only, now and always.

## 2026-11-03 — Owner observation — the viewport test matrix (from build 009)

Source: Recorded by DeepSeek V4.1 Flash Free from the owner's request and the
CHANGELOG/test reports.

Builds observed: `009-20261101` (where the matrix started), `017-20261103` (latest full
use).

The owner's notes: the owner asked when the test matrix began and wants it kept as a
highlight of self-testing and validation, because it measurably helped the quality of the
implementation. It started with **build 009** (`009-20261101`, the responsive-shell
rebuild), from **prompt P-09**, authored by **Claude.ai Sonnet 5.5 Extra** and executed by
**Qwen3.8-Flash (Qoder CLI)**. That build checked **24 viewports from 280×653 to
3440×1440**, portrait and landscape, with **1,409 automated assertions (0 failures, 0
console errors)** and **120 screenshots inspected on contact sheets**. The matrix caught
two real layout faults that DOM numbers alone had missed — a stage sized from a
content-sized measurement box, and pads pushed to the screen edges in landscape — and both
were fixed before the build shipped. Later builds reused the same approach at different
depths (builds 010 and 011 checked four viewports; builds 014-016 checked desktop and
mobile), and **build 017** brought the full matrix back: a **20-viewport focused run
(1,184 checks, 0 failures)** plus a live post-swap check (175 checks) and 12 screenshots.
That pass found the game title still truncating at 390-430 px, which led to the 440 px
breakpoint fix. The owner's point is that this self-testing and validation is a quality
highlight of the project, not just paperwork: measure every size, look at the screenshots,
and fix what the numbers miss. This is a dated owner note, not a model-written summary.

## 2026-11-06 — DeepSeek V4.1 Flash Free (OpenCode) — builds 018 and 019

Source: Owner's words (verbatim)

Builds observed: `018-20261104`, `019-20261106`.

The owner's notes: after build 019, on an iPhone 16 Pro Max in Safari (portrait), the owner played all eight games and reported, verbatim:

> "Wow - it fixed it. I played all the games and there is no vibration in the image."

Build 018 had put the controls and top bar to the owner's design; build 019 removed a layout loop that made the stage vibrate on phones. This is a dated owner note about one device on one day, not a model-written summary.

## 2026-11-09 — Gemini 3.8 Flash (Medium) (Antigravity) and DeepSeek V4.1 Flash Free (OpenCode) — build 022

Source: Owner's words (verbatim)

Builds observed: `022-20261107`.

The owner's notes: after trying build 022, which Gemini 3.8 Flash (Medium) started in Antigravity and DeepSeek V4.1 Flash Free finished in OpenCode after both ran out of free-tier quota, the owner said, verbatim:

> "Sound works, and we will keep it this way for now pending a future refinement."

This is a dated owner note about one build, not a model-written summary.

## 2026-11-10 — DeepSeek V4.1 Flash Free (OpenCode) — build 023

Source: Owner's words (verbatim)

Builds observed: `023-20261109`.

The owner's notes: after build 023, which ran in a single OpenCode run at High effort, the owner said, verbatim:

> "Single run successfully done. Thankfully."

> "So far, it looks great on the phone."

This is a dated owner note about one build, not a model-written summary.

<!-- NEW ENTRIES ABOVE THIS LINE. Never edit existing entries. -->

*Template for a new entry:*

```
## YYYY-MM-DD — <full model name> (<tool>)

Builds observed: `<build-id>`, ...

The owner's notes: ...
```

*Template v2 (from build 012) — adds the Source line:*

```
## YYYY-MM-DD — <full model name> (<tool>) — <build ID and/or short title>

Source: <Owner's words (verbatim) | Recorded by <model> from the owner's feedback>

Builds observed: `<build-id>`, ...

The owner's notes: ...
```
