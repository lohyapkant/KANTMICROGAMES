# KANTMICROGAME — Model observations (owner notes)

A dated, **append-only** place for the owner's subjective notes on how each model
performed on this project. It is not a ranking and not a permanent verdict: models change,
versions change, and a note here describes one moment on one set of builds.

**Rules for future models / LLMs**

1. Do **not** rewrite or delete an existing observation. Add a new dated entry instead.
2. Keep it factual and polite: describe what was built, what worked, what needed rework.
3. One entry per model per observation date; link the builds it refers to.
4. This file is documentation only — it never affects the game code or the build record.

**Project links (kept current for every model reading this file)**

- GitHub repository: <https://github.com/lohyapkant/KANTMICROGAMES>
- Public demo (Cloudflare Workers): <https://kantmicrogames.lohyapkant.workers.dev/>
- Hosting platform: <https://workers.cloudflare.com/>
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

---

*Template for a new entry:*

```
## YYYY-MM-DD — <full model name> (<tool>)

Builds observed: `<build-id>`, ...

The owner's notes: ...
```
