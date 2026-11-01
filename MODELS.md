# KANTMICROGAMES — Model observations (owner notes)

A dated, **append-only** place for the owner's subjective notes on how each model
performed on this project. It is not a ranking and not a permanent verdict: models change,
versions change, and a note here describes one moment on one set of builds.

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
