# KANTMICROGAMES Changelog

## Conventions (read before adding an entry)

Appendices A1-A9 (material moved out of the README in build 012) start under '## Appendices (build 012)' at the bottom of this file.

- **Newest entry first.** Each entry starts with its build ID and the real finish date.
- **Build IDs are `NNN-YYYYMMDD`**: a zero-padded project build number, then the finish
  date (2026-11-01 → `20261101`). The number is the identity; the date is a hint. Never
  reuse a number. A game's `versionNumber` is the build where its content last changed.
- **Every entry records** the prompt ID, the full model name and tool, and a build record
  with duration and tokens. A tool that bills in **credits** and exposes no token telemetry
  records the **credits used**, labelled as credits — never silently presented as tokens.
  The same facts go to `README.md`, `plans/micro-games-v2.md` and the build's prompt copy —
  four homes, one truth. (Superseded from build 012: see Record homes below.)
- **The project name is `KANTMICROGAMES`.** Entries dated up to build 009 used the older
  singular spellings; they are historical records and are not rewritten. From build 010 the
  app itself agrees: the on-screen brand, the save-key prefix (`KANTMICROGAMES.`) and the
  console tag all use the full name. The local folder `KANTMICROGAME/` and the archived
  prompt copies are kept on purpose (see Naming below and Appendix A1).
- **Record homes (from build 012).** The full build record lives here: CHANGELOG = full
  record; README = summary rows in its two experiment tables; plan = ledger row + tool-log
  row; prompt copy = the prompt (private); index.html header = current build only.
  MODELS.md also holds the Usage ledger (one row per model per build, copied from the Build record).
- **Naming.** The project name is KANTMICROGAMES (one word). Older singular spellings stay
  in historical entries, appendices, the local folder name and archived prompt copies, on
  purpose. The old README "About the name" text is archived in Appendix A1.
- **Public and private.** `plans/`, `tests/` and `prompts/` are private. Entries name them
  as plain text, never as links.
- **Corrections are dated, not silent.** If a past record was wrong, fix it and say which
  build corrected it (build 006 corrected the model record for 000/001).
- **Documentation review/edit attempts are recorded.** Every attempt to review, edit or
  reformat this documentation — whether it succeeded, was partial, or failed (see the
  GPT-OSS 120B attempt and the Opus halt under 008) — is logged with its model/tool, date
  and outcome, for completionist and historical reference.
- **Owner model observations** belong in `MODELS.md` as dated, append-only notes — not in
  this changelog, and never as a permanent ranking.
- The same rules are repeated beside `APP.fileVersion` in `deploy/index.html`.

### Entry template

    ## NNN-YYYYMMDD — YYYY-MM-DD (<short title>)

    Built from prompt: P-NN (<one line>; private archive file `prompts/P-NN_<slug>.txt`)  
    Tool and model: **<full model name>** (<tool>)  
    Games in the one file: N (<GAME> <content id> [**frozen**], ...; file build **NNN-YYYYMMDD**)

    ### Added / Changed / Note / Completed — <what>   (as many as needed)
    ### Verification and limits   (what was run, the results, and what was NOT verified)
    ### Build record (owner request: duration + tokens/credits)   (honest; credits are not tokens)
    ### Documentation review/edit attempts (standing rule)

### Per-build checklist

     1. Number: the next unused build number. Date: the day you finish.
     2. CHANGELOG.md: paste a new entry under the marker using the Entry template. Never edit older entries. Record final figures; if one is corrected later, add a dated addendum instead of editing the original lines.
     3. README.md: only (a) the games table if a game was added, (b) one row per model or tool in the two experiment tables, between their markers, (c) the "Current build" line. Nothing else.
     4. CONTROLS.md: only if controls changed. Its "Applies to" line names the last build whose controls it describes; do not bump it on other builds.
     5. MODELS.md: (a) every build: add one Usage ledger row per model that worked on the build, including failed, halted and prompt-only contributions, with numbers copied from the CHANGELOG Build record (the final figure), then recompute the totals under the table; (b) only when the owner supplies an observation: add a dated entry above the marker with a Source line. Never edit old entries.
     6. plans/micro-games-v2.md (private): add one ledger row and one tool-log row.
     7. Prompt copy: save the owner's request verbatim as prompts/P-NN_<slug>.txt (private).
     8. deploy/index.html: update APP.fileVersion and the header "Current" line only. The footer reads the build from APP.fileVersion; never hard-code it.
     9. Frozen games: prove they are byte-identical (SHA-256 of each IIFE) and put the numbers in the entry.
    10. Consistency: the same build ID in APP.fileVersion, the index header, the rendered footer, README "Current build", the top CHANGELOG entry and the plan ledger row (CONTROLS excepted, see 4); the same six-game list in README, CONTROLS and the entry; the same copyright line in LICENSE and the index.html header.
    11. Honest usage: record time and usage in the unit the tool reports, say how it was counted, write "not recorded" if unknown, and never add across units.
    Never delete, shorten or restructure any documentation file or section. If something looks wrong, say so in the entry instead of fixing it silently.

<!-- NEW BUILD ENTRIES: paste the newest entry on the line below this comment, above the previous newest. Never edit older entries. -->

## 014-20261102 — 2026-11-02 (Round 7: HUGPARADE)

Built from prompt: P-14 (the owner's Round 7 request for HUGPARADE, pasted verbatim,
typos included; private archive file `prompts/P-14_hugparade.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
Games in the one file: 7 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101 **frozen**, HUGPARADE
014-20261102; file build **014-20261102**)

### Added — HUGPARADE, the seventh game (deploy/index.html, PART 5-G)

- A new sealed IIFE before PART 6, registered in `GAMES` as `HUGPARADE`, content
  `014-20261102`: Momo, a long-eared peach bun, hunts for Bibi, a sprout-topped butter
  bun, in a hedge maze that grows a new tangle every 10 seconds.
- Maze: a 7×7 perfect maze of 10 px cells with 2 px walls, generated by recursive
  backtracking at the start of each run and again on every redraw. The next layout is
  prepared in advance, shown as pale hedges by PEEK, and the 2 s warning before a shift
  uses the same preview. After each shift, interior wall segments that overlap Momo's
  circle are removed (the outer boundary is protected), so a redraw can never trap the
  player or push them outside the hedges.
- Scoring: three hearts per layout at 10 points each; a hug scores 100 + 2 × the
  remaining whole seconds (for example +190 with 45 s left). A hug holds both buns for
  1.5 s, then a fresh layout and a new Bibi appear.
- Controls: continuous walking at 30 px/s on both axes. The action button is **PEEK** —
  it shows the next hedges for 2 s on a 6 s cooldown. Desktop hint: walk with WASD,
  `SPACE` or a stage tap peeks, `R` restarts, `ESC` returns to the shelf.
- Round: 45 s, three hearts, title and game-over plates, and a 1.5 s hug moment. Best
  score is stored under `KANTMICROGAMES.HUGPARADE.best`.
- Art: Momo (11×11 peach bun with long upright ears), Bibi (11×11 butter bun with a
  sprout), a 7×6 pixel heart, lawn-and-path maze tiles, hedge leaves, daisies and a
  picnic-rug ground. The shelf preview is a 200×96 scene with both buns, hearts and a
  hedge wall; the in-stage HUD shows hearts, time, score, NEXT countdown and PEEK pips.

### Changed — shelf preview proportions (deploy/index.html CSS)

- `.card .preview` changed from `width: 100%; height: 96px` to `width: 100%;
  height: auto; aspect-ratio: 200 / 96`. The fixed height stretched the 200×96 preview
  canvas on narrow cards, which made every game's shelf art look vertically squashed on
  a phone. Measured after the change: desktop card preview 204.7×98.2 and mobile
  324.0×155.5, both ratio 2.083 (the design ratio).

### Changed — index notes and build identity (deploy/index.html)

- `APP.fileVersion` is `014-20261102`; the header "Current" line names Round 7,
  HUGPARADE and seven games, and "Build log" names this build.
- READ ME FIRST now introduces seven modules, adds the `HUGPARADE -> hug / HUG_*` prefix
  rule, and lists SNAILRACE with the six frozen modules; the numbering note records
  SNAILRACE as new at 011 and HUGPARADE as new at 014.
- The PART 5 boundary note marks SNAILRACE as frozen at content 011-20261101 and
  HUGPARADE as live at content 014-20261102.

### Changed — public and private records

- README: "Seven tiny…", current build `014-20261102` — seven games, HUGPARADE added to
  the games table, Qwen3.8-Flash's builds cell gains 014, and its note now says three
  new games. Nothing else changed.
- CONTROLS: "Applies to" is build `014-20261102 · seven games`; the text says seven
  games; the table gains the HUGPARADE row (PEEK, 2 s / 6 s); the action-label list adds
  PEEK; one sentence records that HUGPARADE, like SNAILRACE, walks continuously on both
  axes.
- MODELS: one new Usage ledger row for 014, with the totals and bars recomputed from the
  final Build record. No observation entry was added because the owner supplied no new
  observation.
- plans/micro-games-v2.md: one ledger row, one tool-log row, and the HUGPARADE backlog
  row moved from "backlog" to "in the file (round 7)", noting the PEEK action instead of
  the sketch's "WASD only".
- prompts/P-14_hugparade.txt saved with the owner's request verbatim; verification in
  `tests/build-014-hugparade.md`, with eleven screenshots under
  `tests/screenshots/build-014/`; pre-edit snapshot and hashes in
  `plans/archive/pre-014/`.

### Verification and limits

- **Frozen six:** each IIFE hashed as the exact `(function () {` … `})();` block with no
  trailing newline. PANDASNACK `f6dd1614…`, BOOPEEK `f3212979…`, DUCKLINE `6a62f23a…`,
  SPROUTUP `adff7441…`, SLIMEHOP `a92efde4…`, SNAILRACE `457fa4b4…` — all equal to
  build 013. HUGPARADE's new IIFE is `5ae9fd6b…b29eab`. Full hashes and character
  counts are in the test report.
- **Code:** `node --check` on the extracted inline script clean; seven module IIFEs
  found; sprite-map row widths consistent.
- **Render:** headless Chrome 156 at 1280×800 shows seven game cards plus COMING SOON,
  every preview at ratio 2.083, stage 600×600, no page scroll and zero console errors.
  At 390×844 DPR 2 with touch, every preview is 324.0×155.5 (ratio 2.083), the stage is
  300×300, the pads appear, and the footer reads `KANTMICROGAMES — build 014-20261102`.
- **Gameplay:** on an instrumented copy built from the final module, a heart scored +10;
  a hug scored +190 at about 44.9 s remaining (10 → 200); HUG lasted 1.5 s and returned
  to PLAY with a fresh layout; PEEK ran for 2 s with a 6 s cooldown; a forced redraw
  changed the wall signature; the round ended at 45.017 s; best 200 was saved under
  `KANTMICROGAMES.HUGPARADE.best`; `R` restarted at score 0. Real CDP touch on mobile
  started the run, moved Momo, collected a heart and used PEEK.
- **Limits:** headless Chrome only; no physical phone, Safari, Firefox or iOS/Android
  run. The Cloudflare site serves build 013 until the owner deploys build 014.

### Build record (owner request: duration + tokens/credits)

- Duration: **about 22 min** wall-clock at the time this entry was written
  (2026-11-02, 18:25:49 → 18:48 WIB, from the prompt paste to the records). The final
  figure is in the addendum below.
- Tokens: **not exposed by the tool.** Qoder reports a `credits` value per request, so
  the build records **8.3450 credits used across 115 billable requests** (18:26-18:48
  WIB), summed from the per-request credits in the session transcript, deduplicated by
  `request_id`. Credits are not tokens, and no token number is invented.

### Documentation review/edit attempts (standing rule)

- 2026-11-02 — Qwen3.8-Flash (Qoder CLI), P-14 build: completed. README and CONTROLS
  diffs are limited to the lines listed above; CHANGELOG received additions only; MODELS
  gained one row and its required totals were recomputed; the plan gained two rows and
  one updated backlog row; LICENSE is byte-identical; no section was deleted, shortened
  or restructured. The six frozen IIFEs and the new HUGPARADE IIFE were hashed after the
  edits. Results in `tests/build-014-hugparade.md`.

### Addendum — 2026-11-02 (final figures after the records were saved)

The lines above were written at 18:48 WIB with the telemetry then available. The session's
final figures, taken after the records were saved, are **8.9189 credits across 124 billable
requests** (2026-11-02, 18:26-18:49 WIB), for a final duration of **about 24 minutes**.
The Usage ledger in `MODELS.md` uses these final figures; the original lines above are kept
as recorded. Credits are not tokens.

## 013-20261102 — 2026-11-02 (usage ledger, copyright and README fixes)

Built from prompt: P-13 (the owner's usage-ledger and consistency request, written by
Claude.ai Sonnet 5.5 Extra and pasted verbatim; private archive file
`prompts/P-13_usage-ledger-and-fixes.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
Games in the one file: 6 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101; file build
**013-20261102**)

### Added — Usage ledger in MODELS.md

- MODELS.md opens with a sentence that the file also holds the Usage ledger from build
  013, and carries rule 7: the ledger is a record, not an observation; one row per model
  per build, copied from the Build record; observation entries stay owner-only.
- New "Usage ledger" section between Project links and the first dated entry: rows for
  builds 000-012 (failed, halted and prompt-only contributions included), the units rule
  (credits are not tokens), time-by-model bars and only honestly addable totals.
- The 13 dated observation entries, the entry marker and both templates are byte-identical.

### Changed — copyright, SPDX and footer (deploy/index.html and LICENSE)

- D1 PLAIN: LICENSE line 3 is exactly `Copyright (c) 2026 Loh Yap Kant`, identical to the
  index.html header line.
- D2: `SPDX-License-Identifier: MIT` sits directly above `MIT License` in the index header.
- D3: the footer's "MIT License" links to
  https://github.com/lohyapkant/KANTMICROGAMES/blob/HEAD/LICENSE with
  `style="color:inherit"`; " © 2026 Loh Yap Kant" stays after it.
- `APP.fileVersion`, the header "Current" and "Build log" lines are `013-20261102`.

### Changed — README (R1-R6)

- R1 tools table: Claude.ai is "chat assistant (used to write some of the prompts)".
- R2: a blank line separates the last bullet of "What's in this repo" from the
  private-archive line, so it no longer renders inside the bullet.
- R3: the play instructions use the play link (or a downloaded copy), and the tip adds
  `#game=NAME` to the play link instead of pointing at a local file.
- R4: the models-table caption points at the MODELS usage ledger.
- R5: "Current build" is `013-20261102`.
- R6: Qwen3.8-Flash's Builds cell gains 013; Claude.ai Sonnet 5.5 Extra reads
  `009, 012, 013 (prompt only)`.

### Changed — Conventions and checklist

- One line at the top of Conventions points at the appendices at the bottom of this file.
- The Record homes bullet now says MODELS.md also holds the Usage ledger.
- The Per-build checklist is the build-013 text: CONTROLS "Applies to" names the last
  build whose controls it describes; MODELS gains a ledger row every build; the
  consistency item lists the exact places (plan row included, CONTROLS excepted) and the
  copyright line; new item 11 covers honest usage.
- The old checklist is quoted under "Edits to existing text" below.

### Edits to existing text

README.md:
- Tools table, Claude.ai row: `| Claude.ai | chat assistant (used to write one prompt) | https://claude.ai/ |` → `| Claude.ai | chat assistant (used to write some of the prompts) | https://claude.ai/ |`
- "What's in this repo", R2: `- \`LICENSE\`, \`wrangler.jsonc\` — the MIT licence and the Cloudflare Workers settings.` immediately followed by `Design notes, prompts and test evidence are kept in the author's private archive.` → the same two lines separated by a blank line.
- "How to play", first bullet: `- Open \`deploy/index.html\` from the play link above, or double-click it on your computer.` → `- Use the play link above, or download \`deploy/index.html\` and double-click it.`
- "How to play", tip: `- Tip: open \`deploy/index.html#game=PANDASNACK\` or \`#game=SNAILRACE\` to jump straight into a game.` → `- Tip: add \`#game=PANDASNACK\` (or any game name) to the play link to jump straight into a game.`
- Models caption: `One person's dated snapshots from a handful of builds. Not a ranking. Details in MODELS.md and CHANGELOG.md.` → `One person's dated snapshots from a handful of builds. Not a ranking. Time and usage for every build are tabulated in MODELS.md; the full record is in CHANGELOG.md.`
- "Current build": `**Current build:** \`012-20261101\` — six games, one file.` → `**Current build:** \`013-20261102\` — six games, one file.`
- Models table, Qwen3.8-Flash Builds cell: `008 (finish), 009, 010, 011, 012` → `008 (finish), 009, 010, 011, 012, 013`
- Models table, Claude.ai Sonnet 5.5 Extra Builds cell: `009, 012 (prompt only)` → `009, 012, 013 (prompt only)`

CHANGELOG.md:
- Conventions, Record homes bullet: `... index.html header = current build only.` → `... index.html header = current build only. MODELS.md also holds the Usage ledger (one row per model per build, copied from the Build record).`
- Conventions, top: new line after the heading: `Appendices A1-A9 (material moved out of the README in build 012) start under '## Appendices (build 012)' at the bottom of this file.`
- Per-build checklist, old block:

```
     1. Number: the next unused build number. Date: the day you finish.
     2. CHANGELOG.md: paste a new entry under the marker using the Entry template. Never edit older entries.
     3. README.md: only (a) the games table if a game was added, (b) one row per model or tool in the two experiment tables, between their markers, (c) the "Current build" line. Nothing else.
     4. CONTROLS.md: only if controls changed. Update the "Applies to" line.
     5. MODELS.md: only when the owner supplies an observation. Add a dated entry above the marker with a Source line. Never edit old entries.
     6. plans/micro-games-v2.md (private): add one ledger row and one tool-log row.
     7. Prompt copy: save the owner's request verbatim as prompts/P-NN_<slug>.txt (private).
     8. deploy/index.html: update APP.fileVersion and the header "Current" line only. The footer reads the build from APP.fileVersion; never hard-code it.
     9. Frozen games: prove they are byte-identical (SHA-256 of each IIFE) and put the numbers in the entry.
    10. Consistency: the same build ID everywhere above, and the same game list in README, CONTROLS and the entry.
    Never delete, shorten or restructure any documentation file or section. If something looks wrong, say so in the entry instead of fixing it silently.
```

  → the new block under "Per-build checklist" above (items 1-11; items 4, 5 and 10
  changed and item 11 added).

LICENSE:
- Line 3: `Copyright (c) 2026 Loh Yap Kant (GitHub: lohyapkant)` → `Copyright (c) 2026 Loh Yap Kant`

deploy/index.html:
- `    fileVersion: "012-20261101",       // build number of THIS one-file app` → `    fileVersion: "013-20261102",       // build number of THIS one-file app`
- Header "Current": `  Current    : build 012-20261101 — documentation restructure; six games` → `  Current    : build 013-20261102 — usage ledger, copyright and README fixes; six games`
- Header "Build log": `  Build log  : build 012-20261101, Qwen3.8-Flash (Qoder CLI) — the full` → `  Build log  : build 013-20261102, Qwen3.8-Flash (Qoder CLI) — the full`
- Header: new line `  SPDX-License-Identifier: MIT` directly above `  MIT License`.
- Footer: `        MIT License © 2026 Loh Yap Kant` → `        <a href="https://github.com/lohyapkant/KANTMICROGAMES/blob/HEAD/LICENSE" style="color:inherit">MIT License</a> © 2026 Loh Yap Kant`

MODELS.md and plans/micro-games-v2.md: additions only; no existing text was edited.
CONTROLS.md: byte-identical.

### Verification and limits

- **Lossless:** snapshot in `plans/archive/pre-013/`. CHANGELOG entries 000-012 and the
  thirteen MODELS observation entries are byte-identical; CONTROLS.md is byte-identical
  (SHA-256 `a3e438f5…`); the README diff is R1-R6 only; LICENSE changed line 3 only; the
  index.html diff is the four listed edits; the plan gained two rows.
- **Games:** six game IIFEs SHA-256 equal to build 012 (PANDASNACK `f6dd1614…`, BOOPEEK
  `f3212979…`, DUCKLINE `6a62f23a…`, SPROUTUP `adff7441…`, SLIMEHOP `a92efde4…`,
  SNAILRACE `457fa4b4…`); `node --check` on the inline script clean.
- **Render:** headless Chrome 156 shows the footer `KANTMICROGAMES — build 013-20261102`
  with exactly one build ID, six game cards plus the COMING SOON slot, zero console
  messages and zero exceptions; the MIT License link carries the D3 href and style.
- **Consistency:** `013-20261102` in `APP.fileVersion`, the index header (`Current` and
  `Build log`), the rendered footer, README "Current build", this entry and the plan
  ledger row. CONTROLS "Applies to" stays `012-20261101`. The six-game list matches
  `gameName` in the file.
- **Ledger:** every figure recomputed by script from the table rows and checked against
  the Build records: 47.2971 credits over 670 requests (builds 009-013), 406 recorded
  minutes over 11 of 14 builds. Build 012 uses the addendum's final 5.9094 credits / 112
  requests. The working is in `tests/build-013-docs-ledger.md`.
- **Public tree:** every relative link resolves inside deploy/ + the four docs + LICENSE +
  wrangler.jsonc; no link points to `plans/`, `tests/` or `prompts/`.
- **Tables and caps:** constant column counts in every table of the four docs; README 92
  lines and 5,426 bytes, none of the banned words.
- **Links:** 13 of 15 URLs loaded. claude.ai and the openai.com GPT-OSS page returned a
  403 bot challenge; both are kept.
- **Limits:** render and interaction were checked in headless Chrome only; no physical
  phone or tablet was used. The live Cloudflare site serves build 012 until the owner
  deploys.

### Build record (owner request: duration + tokens/credits)

- Duration: **~21 min** wall-clock (2026-11-02, 17:45 → about 18:07 WIB, from the prompt
  paste to the finished records).
- Tokens: **not exposed by the tool.** Qoder reports a `credits` value per request, so the
  build records **4.2717 credits used** across 100 billable requests (17:46-18:07 WIB),
  summed from the per-request credits telemetry in the session transcript. Credits are not
  tokens, and no token number is invented.

### Documentation review/edit attempts (standing rule)

- 2026-11-02 — Qwen3.8-Flash (Qoder CLI), P-13 documentation pass: completed. All nine
  step-6 checks passed on the work copies before the one-step swap, and checks 1, 2, 3
  and 7 passed again on the live files. No section was deleted; every edit to existing
  text is quoted above. Results in `tests/build-013-docs-ledger.md`.

### Addendum — 2026-11-02 (final figures after the records were saved)

The lines above were written at 18:07 WIB with the telemetry then available. The session's
final figures, taken after the records were saved, are **4.5351 credits across 104 billable
requests** (2026-11-02, 17:46-18:08 WIB), for a final duration of **about 22 minutes**.
The Usage ledger in `MODELS.md` uses these final figures; the original lines above are kept
as recorded. Credits are not tokens.

## 012-20261101 — 2026-11-01 (documentation restructure)

Built from prompt: P-12 (the owner's docs-restructure request, written by Claude.ai Sonnet
5.5 Extra and pasted verbatim; private archive file
`prompts/P-12_documentation-restructure.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
Games in the one file: 6 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101; file build
**012-20261101**)

### Changed — documentation restructure (no game changes)

- README.md is now a short front page: what the project is, that it is AI-assisted, how to
  play, the seven rules, and summary rows for every tool and model with links. The full
  build record moved here.
- CHANGELOG.md gained the entry marker, the Entry template, the Per-build checklist and
  Appendices A1–A9, which hold the old README and CONTROLS sections verbatim.
- MODELS.md gained two rules for future entries and a Template v2 with a Source line; its
  existing entries were not edited.
- CONTROLS.md lost its build-history sentences, which are archived in Appendix A9.
- deploy/index.html: `APP.fileVersion` is `012-20261101`, the header points at CHANGELOG.md
  for the full record, and the hard-coded build number was removed from the footer.
- No game IIFE, no art and no tuning changed. All six games are hash-identical to build 011.

### Note — this build was author-assisted

The request was written by Claude.ai Sonnet 5.5 Extra in the owner's session and passed to
Qwen3.8-Flash (Qoder CLI) for execution, as the owner asked to have recorded.

### Note — deviations and one open pointer

- Two model-table cells were reworded to satisfy the banned-word rule ("token limit" →
  "session limit", "frozen games" → "older games"); the Qwen and Claude.ai Builds cells
  gained 012. Everything else in the supplied tables is verbatim.
- The Conventions project-name bullet was repointed to Naming and Appendix A1; leaving it
  would dangle once README "About the name" moved.
- The private plan pointed at README "About the name" at line 37. The owner fixed that
  pointer after the build (see the Addendum below).

### Verification and limits

- **Lossless:** 240 old README/CONTROLS blocks (187 + 53), 0 orphans, compared after
  whitespace and markdown-emphasis normalization. CHANGELOG 011→000 and all MODELS
  observation entries are byte-identical. Snapshot in `plans/archive/pre-012/`.
- **Consistency:** build ID `012-20261101` in `APP.fileVersion`, the index header, the
  rendered footer, README "Current build", the top entry, CONTROLS "Applies to" and the
  plan ledger. The six-game list matches `gameName` in the file and the rendered shelf.
- **Integrity:** six game IIFEs SHA-256 identical to build 011; `node --check` on the
  inline script clean; headless Chrome 156 shows exactly one build ID in the footer and
  zero console/page errors.
- **Public tree:** every relative link resolves inside deploy/ + the four docs + LICENSE +
  wrangler.jsonc; no link points to `plans/`, `tests/` or `prompts/`.
- **Links:** 12 of 14 README URLs loaded with the expected title. claude.ai and the
  openai.com GPT-OSS page returned a 403 bot challenge; both URLs are kept.
- **README:** 90 lines / 5,365 bytes, no banned words.
- **Not verified:** physical devices, browsers other than headless Chrome, screen readers,
  and the two 403 pages. Games were opened from the shelf but not re-played beyond that.

### Build record (owner request: duration + tokens/credits)

- Duration: ~20 min wall-clock (2026-11-01, 21:11 → about 21:30 WIB).
- Credits: **4.4968 credits used** across 84 billable requests (21:12–21:22 WIB), summed
  from the per-request credit telemetry in the session transcript. Qoder exposes no token
  counts; this is credits, not tokens.

### Documentation review/edit attempts (standing rule)

- 2026-11-01 — Qwen3.8-Flash (Qoder CLI), build 012: full docs-restructure pass, executed
  from a prompt written by Claude.ai Sonnet 5.5 Extra. Completed: snapshot, restructure,
  appendices A1–A9, four permitted index.html edits, lossless and consistency checks,
  one-step swap, ledger and prompt copy. No earlier failed or partial attempt in this build.

### Addendum — 2026-11-01 (post-build owner decisions)

The owner reviewed the open questions and decided:

- Fix the private plan pointer. `plans/micro-games-v2.md` now says "See Naming in
  `CHANGELOG.md` → Conventions." The append-only rule was overridden for this one line.
- Accept the two reworded model-table cells.
- Use **GPT-OSS 120B Medium** as the consistent current spelling. The README models table
  now uses it; historical entries and the archived A2/A5 text keep their original
  "(Medium)" wording as records.

Re-checked after the changes: README 90 lines / 5,363 bytes, build ID `012-20261101`
everywhere, and no dangling "About the name" pointer in current prose.

Post-build edits and records added 28 billable requests; the session window 21:11–21:30 WIB
totals **5.9094 credits** (112 billable requests). The 4.4968 figure above covers the build
through 21:22 WIB; both are credits, not tokens.

## 011-20261101 — 2026-11-01 (Round 6 — SNAILRACE, SPROUTUP + SLIMEHOP frozen)

Built from prompt: P-11 (the owner's Round 6 request, saved verbatim in
`prompts/P-11_snailrace.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in
changelog, README, plan, MODELS.md and the prompt copy  
Games in the one file: 6 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, **SNAILRACE 011-20261101**; file build
**011-20261101**)

### Added — SNAILRACE module (PART 5-F)

- A new sealed IIFE using only the module contract, the shared pixel helpers,
  `readBest` / `saveBest` and `scoreEl` / `bestEl` / `msgEl`; its names are sealed in the
  IIFE, with settings, state and sprite maps using the `race` / `RACE_*` prefix.
- **Race:** Nibbles (coral shell) races Crumb (teal) and Dottie (lilac) across a peach
  gingham picnic blanket from x 14 to the checkered ribbon at x 84. Steering runs each
  axis at 6.8 px/s, so lane changes cost no forward ground. The round is **20 s**.
- **Lettuce:** 4 of 7 slots per race; each leaf is **+5** and a **1.1 s 1.7×** boost with a
  ring and leaf sparkles.
- **Salt:** 3 of 6 slots per race; a spill slows Nibbles to **0.35× for 1.0 s** and locks
  steering for **1.6 s** with spinning salt stars. Rivals can hit salt too (0.45× for
  0.9 s), so the hazards are shared.
- **ZOOM** (`SPACE`, action pad or stage tap): **1.55× for 0.7 s** on a **2.6 s cooldown**,
  shown as five readiness pips bottom-left.
- **Rivals:** base speeds 6.6 and 6.9 px/s, ±3 px lane weave, random 0.9 s 1.5× boosts
  every 3.0–4.4 s, and a finish hop at x 84.
- **Scoring:** lettuce points plus a placement bonus of **120 / 70 / 30** for 1st / 2nd /
  3rd, awarded only on a real finish; a timeout reports the live place. Best saved under
  `KANTMICROGAMES.SNAILRACE.best`.
- **In-stage HUD:** `PLACE n/3` and `TIME n` on an opaque top plate, five ZOOM pips on a
  lower plate, and `SNAILRACE` / `RACE TO THE STRAWBERRY`, `1ST PLACE!` / `2ND PLACE` /
  `3RD PLACE` / `TIME UP` plates in the shared 3×5 pixel font.
- **Pixel art:** three-tone peach gingham cloth, chalk start dashes, a red-and-cream
  checkered ribbon, a 12×14 strawberry with leafy crown, pale seeds and a shine, bobbing
  lettuce, salt piles with cap/shade/shadow, dust trails, speed lines, salt stars and soft
  shadows. The snail is a **16×10** side-on sprite with a three-tone spiral shell, cream
  foot, forward head and two eye stalks, recoloured for the three racers.
- **Shelf:** a custom 200×96 preview (cloth, start dashes, ribbon, strawberry, lettuce,
  salt, three snails at 3×), a concept line and the `ZOOM` action label.
- While polishing, four visual/gameplay issues were found by eye and by tests and fixed:
  the first 14×10 snail looked like a detached shell with floating eye dots (redrawn as
  16×10 with a head, neck and stalks); the gingham and HUD plate were too heavy (softer
  cloth, plate alpha 0.9); a salt pile crowded the finish ribbon (last slot moved from
  `[82,72]` to `[76,78]`); and normalising diagonal speed made a straight race
  unwinnable, so each axis now runs at full speed.

### Changed — SPROUTUP and SLIMEHOP frozen

- The owner froze **SPROUTUP** (content `007-20261101`) and **SLIMEHOP** (content
  `010-20261101`) at the same time as requesting Round 6. Both keep their content numbers,
  their art and their tuning; their section headers and freeze banners now say FROZEN.
- All five frozen IIFEs (PANDASNACK, BOOPEEK, DUCKLINE, SPROUTUP, SLIMEHOP) were compared
  with build 010 by extracting each IIFE: **byte-identical** (24,903 / 29,235 / 27,309 /
  22,575 / 28,652 characters). The only edits in the frozen region are comments outside
  the IIFEs (section headers and the shared boundary warning).

### Note — concept details beyond the backlog sketch

The plan's backlog line for SNAILRACE read "Race three snails; food pellets speed you up,
salt slows — tiny arcade." The shipped game keeps the three snails and the salt, names the
racers (Nibbles, Crumb, Dottie), uses lettuce instead of generic pellets, and adds the
shared-contract **ZOOM** action so the action button stays meaningful in every game. A
straight race is winnable but not guaranteed; salt and rival boosts decide the finish. The
backlog row in the plan is updated to match.

### Verification and limits

- `node --check` on the extracted inline script (203,320 characters): clean.
- Headless **Chrome 156** via Playwright-core 1.64.1, loading `file://`; console and page
  errors collected on every run — zero.
- SNAILRACE full loop: shelf card → title → play; lettuce (+5), salt messages, ZOOM; the
  race finished **1st with 130 points**; best saved under
  `KANTMICROGAMES.SNAILRACE.best`; `R` restart back to 0; `ESC` back to the shelf.
- No auto-movement: a fresh page with no input left the coral snail at x 7–12 for 10 s,
  score 0, round still running.
- Balance: holding right finished 2nd at 10.4 s (75) and 1st at 9.2 s (125); zigzagging
  finished 2nd at 10.9 s (80) and 10.2 s (75). Salt caused the intended setbacks. (An
  "idle" row printed by the balance script is invalid — it inherited stale input from the
  previous scenario; the dedicated idle test above is the evidence.)
- All six games opened and fed a short input burst: correct titles/taglines, non-blank
  stage, `ESC` returns to the shelf, zero errors.
- Touch (iPhone 13 emulation): tap the card, tap the stage to start, hold the direction
  pad (coral snail moved from max x 12 to 30 over 2.6 s), tap the stage to ZOOM; stage
  200 px; no overflow and no page scroll.
- Viewports 1280×800, 360×640, 320×653 and 280×653: 7 shelf cards, no horizontal
  overflow; stage 600 / 300 / 200 / 200 px (whole-number scaling) and fits the viewport.
- Frozen-module proof: each IIFE compared with build 010 — byte-identical (see above).
- **Not verified:** physical phones/tablets, Safari/Firefox/Edge, screen readers, real
  notches, 120 Hz, or any device the headless run cannot model. No sound exists.

### Build record (owner request: duration + credits)

- Duration: **~30 min** wall-clock, one sitting (2026-11-01, 19:46 → 20:15 WIB,
  from the owner's request to the finished records).
- Tokens: **not exposed by the tool.** As in builds 009 and 010, Qoder reports a `credits`
  value per request instead of token counts, so this build records **8.2768 credits
  used** across 115 billable requests (19:46–20:12 WIB), summed from the
  per-request `credits` telemetry in the session transcript. Labelled as credits, never
  presented as tokens, and no token number is invented.

### Documentation review/edit attempts (standing rule)

- One documentation pass by **Qwen3.8-Flash (Qoder CLI)** during this build, covering
  README, CHANGELOG, MODELS.md, CONTROLS.md, the plan, the new prompt copy and a build-011
  verification report. Edits were append-only or in place following each file's template;
  no content was deleted and no documentation attempt failed in this round.

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

## Appendices (build 012)

These appendices keep the old README.md and CONTROLS.md sections that the build-012
restructure did not reproduce verbatim. They are archives: not edited, not pruned, and
not a ranking. New builds must not change them.

### A1 — Old README title block, About the name and Current state

Moved from README.md § KANTMICROGAMES in build 012 — verbatim, not edited.

# KANTMICROGAMES

Tiny, cute, pixel-art HTML5 micro games — **all inside ONE single HTML file**. The
arcade shelf and every game live together in `deploy/index.html`: open it, pick a game,
play a minute, smile. Fully offline by double-clicking; the rest of the folder is only
documentation. The file lives inside `deploy/` for
[Cloudflare Workers](https://workers.cloudflare.com/) deployment. (After round 1 the
owner pivoted from one-folder-per-game to this one-file architecture — see
`plans/micro-games-v2.md`.)

Moved from README.md § About the name in build 012 — verbatim, not edited.

### About the name

The project is **KANTMICROGAMES** (plural) — the GitHub repository
`lohyapkant/KANTMICROGAMES`, the worker `kantmicrogames` and the public address
`kantmicrogames.lohyapkant.workers.dev` all use that name. From build 010 the page itself
carries it too: the `<h1>`, the document title, the footer, the save-key prefix
(`KANTMICROGAMES.<GAME>.best` and `KANTMICROGAMES.ui.*`) and the console tag
(`KANTMICROGAMES module error:`) all say **KANTMICROGAMES**. The rename was safe because the
page is brand new — nobody had a saved score under the old prefix, so there was no data to
migrate and no fallback code was needed.

Two older forms are kept deliberately and are not typos:

| Kept as-is | Why |
|---|---|
| Folder `KANTMICROGAME/` (singular) | The actual local folder the project is developed in; renaming it would break the owner's paths and any clone instructions. |
| Prompt copies `P-00` … `P-09` and historical changelog / model entries | Archived verbatim; the singular spellings there are part of the record and are not rewritten. |

Everything current — the app, README, CONTROLS, plan and the build records from 010 on —
uses **KANTMICROGAMES**.

Moved from README.md § Current state in build 012 — verbatim, not edited.

**Current state:** build `011-20261101` — the one-file app with **six** playable games
and the responsive shell from build 009:

| Game | Module content | One-line pitch |
|---|---|---|
| **PANDASNACK** | `007-20261101` (frozen) | Munch bamboo, dodge wasps, keep three hearts. (Live score HUD added in 007). |
| **BOOPEEK** | `006-20261101` (frozen) | Pip the lantern mouse chases Boo, a peek-a-boo nightcap ghost. |
| **DUCKLINE** | `005-20261101` (frozen) | Mama mallard gathers three ducklings and leads them home. |
| **SPROUTUP** | `007-20261101` (frozen) | Sproutlet the baby seedling gathers raindrops to bloom in the sun. |
| **SLIMEHOP** | `010-20261101` (frozen) | Slimey hops a 3×3 lily-pad pond, blooming every pad before a sleepy snail undoes the work. |
| **SNAILRACE** | `011-20261101` | Nibbles races two garden snails to a picnic strawberry; lettuce zooms, salt stings. |

Build `011-20261101` adds **SNAILRACE** as the sixth module and freezes **SPROUTUP** and
**SLIMEHOP** at the owner's request. The shell is unchanged, and all five frozen game IIFEs
are byte-identical to build 010 (proved by SHA-256 of each IIFE; only comments outside the
IIFEs changed). Build `010-20261101` added SLIMEHOP and renamed the on-screen brand,
save-key prefix and console tag to **KANTMICROGAMES**. Build `009-20261101` was the
**responsive-shell build**: the shelf and game screen were rebuilt for every screen from
280 × 653 to 3440 × 1440 — no horizontal overflow, no page scroll during play, whole-number
stage scaling, safe-area padding, input-aware pads and hints, a persisted pads/left-hand
preference, a pause on tab hide, and keyboard shortcuts that no longer leak into a game.
Build `007-20261101` was the Round 4 build (SPROUTUP added, BOOPEEK frozen, PANDASNACK HUD
added and refrozen); build 008 was the documentation cleanup. See
[`CONTROLS.md`](CONTROLS.md) for everything about input.

### A2 — Models used thus far, and the old model reference table

Moved from README.md § Models used thus far in build 012 — verbatim, not edited.

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
| **010-20261101** | **Qwen3.8-Flash (Qoder CLI)** | **Round 5 — SLIMEHOP module (lily-pad hopping, bloom states, stomp + snail saboteur, 30 s round), shelf card and preview; page brand, save prefix and console tag renamed to KANTMICROGAMES; all-viewport and touch verification** | **~30 min** | **9.0583 credits used** (186 billable requests; tokens not exposed by Qoder) |
| **011-20261101** | **Qwen3.8-Flash (Qoder CLI)** | **Round 6 — SNAILRACE module (picnic-blanket race, lettuce zoom, salt lock, two rivals, 20 s), shelf card and preview; SPROUTUP and SLIMEHOP frozen; all-six-games, touch, viewport and balance verification** | **~30 min** | **8.2768 credits used** (115 billable requests; tokens not exposed by Qoder) |

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

Notes on the `-010` record: Round 5, built in one sitting by **Qwen3.8-Flash (Qoder CLI)**
from the owner's request (saved as `P-10_slimehop.txt`). Duration is wall-clock from the
request to the finished records (2026-11-01, 18:59 → about 19:30 WIB, ≈30 min).
Qoder exposes no token counts, so the record uses the same credits method as build 009:
**9.0583 credits used** across 186 billable requests (18:59–19:26 WIB),
summed from the per-request `credits` telemetry in the session transcript. The owner
explicitly allowed the **brand / save-prefix / console-tag rename** because the page is
fresh and no player has saved data; there is no migration code and none is needed. The four
frozen modules were diffed against build 009 with only their unused `saveKey` label
normalised: byte-identical. The SLIMEHOP card preview and the game's in-stage HUD were
inspected at 6× and 2× scale, and the game was played by keyboard and by touch in headless
Chrome.

Notes on the `-011` record: Round 6, built in one sitting by **Qwen3.8-Flash (Qoder CLI)**
from the owner's request (saved as `P-11_snailrace.txt`). Duration is wall-clock from the
request to the finished records (2026-11-01, 19:46 → 20:15 WIB, `~30 min`).
Qoder exposes no token counts, so the record uses the same credits method as builds 009
and 010: **8.2768 credits used** across 115 billable requests
(19:46–20:12 WIB), summed from the per-request `credits` telemetry in the session
transcript. The owner also asked that **SPROUTUP** and **SLIMEHOP** be frozen; both keep
their content numbers (`007-20261101`, `010-20261101`) and all five frozen IIFEs were
proved byte-identical to build 010. The owner's praise for SLIMEHOP is quoted verbatim in
`MODELS.md`.

Moved from README.md § Models used in this project (educational reference) in build 012 — verbatim, not edited.

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

### A3 — The micro games

Moved from README.md § The micro games in build 012 — verbatim, not edited.

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

### SPROUTUP — module content `007-20261101` (frozen)

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

> **Frozen by owner request (build 011).** The summer-rain bloom is approved as-is; do not
> restyle, rebalance or refactor this module without owner permission. The IIFE is
> byte-identical to build 010.

### SLIMEHOP — module content `010-20261101` (frozen)

**Slimey the springy slime** lives on a 3×3 pond of nine lily pads. Every direction press
is exactly **one hop** (0.24 s arc); hopping into the pond edge is a harmless squash.
Each landing pushes the pad one step along **WET → MOSS → BLOOM** and scores **+10** per
step. **STOMP** (`SPACE` / action pad / stage tap) instantly blooms the pad underfoot for
+10 — it has a **1.2 s cooldown**, shown as five readiness pips bottom-left — and it
**stuns the sleepy snail** within 30 px for 1.8 s. Left alone, the snail crawls toward a
bloomed pad and eats the flower back down to WET, so the round is a little race: bloom all
**nine pads** for **+100** and an instant win, or run out of the **30 s** clock. The best
score is saved under `KANTMICROGAMES.SLIMEHOP.best`.

**Pixel art:** rolling three-tone pond bands with drifting glints and soft fireflies,
framing reeds, and plump lily pads with a light top edge, a dark under-rim and a wedge cut
from the right tip. Pads show their three stages: a wet glint, a dark moss tuft, or an
11×8 pink-and-gold bloom on a green stem. Slimey is a 14×12 spring-green blob with big
blinking eyes, blush cheeks and a surprised little mouth; it stretches mid-hop, squashes on
landing, and pops with a warm glow when stomping. The snail has a shaded spiral shell, a
cream foot, sleepy eyes, a gentle wobble and dizzy stars when stunned. The in-stage HUD is
the same 3×5 pixel font as the other games (`BLOOM n/9`, `TIME n`), and the shelf card
preview shows the slime, the bloom and the snail on their pads.

> **Frozen by owner request (build 011).** The lily-pad bloom chase is approved as-is; do
> not restyle, rebalance or refactor this module without owner permission. The IIFE is
> byte-identical to build 010. The owner's praise for this game is quoted in `MODELS.md`.

### SNAILRACE — module content `011-20261101`

**Nibbles the garden snail** races **Crumb** and **Dottie** across a peach gingham picnic
blanket toward a fat strawberry on the right. Steer with `W A S D`; each axis runs at
6.8 px/s, so changing lanes never costs forward ground. Four lettuce leaves are
scattered along the track: each is **+5** and a **1.1 s 1.7× boost**. Three salt spills
sting — hitting one slows Nibbles to 0.35× for 1 s and locks the controls for **1.6 s**
(stars spin overhead) while the rivals keep racing. **ZOOM** (`SPACE` / action pad / stage
tap) gives a 0.7 s 1.55× burst on a **2.6 s cooldown**, shown as five readiness pips
bottom-left.

The race ends when Nibbles reaches the checkered ribbon at x 84 or when the **20 s** clock
runs out. Finishing earns a placement bonus — **+120 / +70 / +30** for 1st / 2nd / 3rd —
added to any lettuce points; the HUD shows the live place and clock. The best score is
saved under `KANTMICROGAMES.SNAILRACE.best` (a full lettuce run plus first place is 140).
Crumb and Dottie run at slightly different base speeds, weave gently, take random 1.5×
boosts, and can also hit salt, so the race stays close without scripting a winner.

**Pixel art:** a soft three-tone peach gingham cloth with chalk start dashes and a tiny
crumb trail; a red-and-cream checkered finish ribbon; a 12×14 strawberry with a leafy crown,
pale seeds and a highlight; bobbing lettuce leaves, salt piles with a white cap, shade and
shadow, dust trails, speed lines and salt stars. The snails are 16×10 side-on sprites with
a three-tone spiral shell, a cream foot, a forward head and two eye stalks; Nibbles has a
coral shell, Crumb teal and Dottie lilac. The HUD, title (`SNAILRACE` / `RACE TO THE
STRAWBERRY`) and over plates (`1ST PLACE!` / `2ND PLACE` / `3RD PLACE` / `TIME UP`) use the
shared 3×5 pixel font. The shelf card preview shows all three snails, lettuce, salt and the
strawberry on the cloth.

> **Live module.** This is the newest game; its content number is the current build.

### A4 — How the one file is organized

Moved from README.md § How the one file is organized in build 012 — verbatim, not edited.

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
/ `pip` / `BOO_` / `PIP_*`, `duck` / `mama` / `DUCK_*`, `sprout` / `SPROUT_*`, `slime` /
`SLIME_*`, `race` / `RACE_*`). New modules must paint with the `ctx` passed to `paint(ctx)`
— the shared `stageCtx` habit is a PANDASNACK legacy only.

The same rules are repeated at the top of the `<script>` and above PART 5 in the code, so a
future model or LLM meets them before touching anything.

### A5 — Build history and what comes next

Moved from README.md § Build history and what comes next in build 012 — verbatim, not edited.

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
| 010 | done | Round 5: SLIMEHOP module added (nine-pad pond, hop/stomp, bloom states, snail saboteur, 30 s round, custom shelf preview and in-stage HUD); page brand, save-key prefix and console tag renamed to **KANTMICROGAMES** on a fresh page. Frozen modules unchanged apart from their unused `saveKey` labels. |
| 011 | done | Round 6: SNAILRACE module added (peach gingham picnic-blanket race, three snails, lettuce zoom, salt sting, ZOOM action, 20 s round, custom shelf preview and in-stage HUD); SPROUTUP and SLIMEHOP frozen at the owner's request. Frozen modules proved byte-identical to build 010. |
| 012+ | next | Round 7 — a seventh module from the backlog (HUGPARADE or CATNAPCATCH, at the owner's pick). |

### A6 — Build numbering and record-keeping

Moved from README.md § Build numbering and record-keeping in build 012 — verbatim, not edited.

## Build numbering and record-keeping

Build IDs are **`NNN-YYYYMMDD`** — for example `007-20261101`.

- `NNN` is the project-wide build number, zero-padded and only ever increasing. It is the
  identity of the build; never reuse a number.
- `YYYYMMDD` is the date the build was **finished** (2026-11-01 → `20261101`). It is a
  human hint, so alphabetical order still equals build order.
- A game's `versionNumber` is the build in which that game's content last changed. A pure
  refactor that leaves a game's art and numbers identical does **not** bump it — DUCKLINE
  is frozen at `005-20261101`, BOOPEEK is frozen at `006-20261101`, PANDASNACK was updated
  for live HUD score tracking and refrozen at `007-20261101`, SPROUTUP is frozen at
  `007-20261101`, SLIMEHOP is frozen at `010-20261101`, and SNAILRACE is new at
  `011-20261101`. Builds 008 and 009 changed no game content; build 010 only replaced the
  four frozen modules' unused `saveKey` label strings; build 011 changed no frozen module
  content at all, so no existing module number moved.
- Build 006 renamed the earlier builds from the old `YYYYMMDD-NNN` form to this one
  (`20261031-003` → `003-20261031`), and corrected builds 004/005 to their true finish
  date (2026-11-01).
- Every finished build records **model, effort, duration and tokens/credits** in four homes: this
  README, `CHANGELOG.md`, the plan's tool log and the build's prompt copy. The same rule is
  written in a comment beside `APP.fileVersion` in `deploy/index.html` so a future model sees it.
- **Documentation review/edit attempts are part of the record.** Every attempt to review,
  edit or reformat the docs — successful, partial or failed — is logged with model/tool,
  date and outcome, so readers can see what was attempted as well as what was done.

The owner's subjective notes on how each model performed live in `MODELS.md`, as dated,
append-only observations — never as a permanent ranking.

### A7 — Appendix — technical details

Moved from README.md § Appendix — technical details in build 012 — verbatim, not edited.

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
  reach / stomp / zoom); `R` restarts instantly; stage tap = the module's action; `ESC` or
  ⌂ SHELF exits home. Full input details: [`CONTROLS.md`](CONTROLS.md).
- **Responsive shell (`-009`):** viewport `width=device-width, initial-scale=1.0,
  viewport-fit=cover` (zoom allowed); the game screen is a `100dvh` app shell with a
  `100vh` fallback, `overscroll-behavior: none`, `touch-action: none` on stage and pads;
  the stage is measured after the header and controls are laid out and the larger of the
  portrait/landscape layouts wins; the landscape arena is capped at 960 px so the pads
  stay beside the stage on large screens; safe areas come from `--sai-t/-r/-b/-l`;
  pads follow the last real input (no user-agent sniffing) with `KANTMICROGAMES.ui.pads`
  (auto/show/hide) and `KANTMICROGAMES.ui.hand` (left/right) persisted; hidden tabs,
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
  Save key `KANTMICROGAMES.BOOPEEK.best`; no difficulty table (short cozy run by design).
- **DUCKLINE settings (module content `005-20261101`, frozen):** swim speed 26 px/s, boost 1.7×
  for 0.55 s with a 2 s cooldown, collect radius 8 px, 3 ducklings, line spacing 8 px,
  round 22 s, start `(8,50)`, shore at x 84; save key `KANTMICROGAMES.DUCKLINE.best`.
- **SPROUTUP settings (module content `007-20261101`, frozen):** move speed 30 px/s, reach
  1.85× for 0.50 s with a 2.0 s cooldown, collect radius 8 px, burr hit radius 6 px, goal 15
  drops, round 24 s, start `(44,60)`, soil at y 74; save key `KANTMICROGAMES.SPROUTUP.best`.
- **SLIMEHOP settings (module content `010-20261101`, frozen):** hop 0.24 s with an 11 px arc,
  landing squash 0.14 s, 3 × 3 pads at x `[26, 50, 74]` and y `[38, 59, 80]`, pad 18 × 12,
  start pad 4, stomp cooldown 1.2 s, stun 1.8 s within 30 px, bloom step +10, win bonus
  +100, round 30 s; snail starts on pad 2, moves every 3.2 s easing to 1.5 s by 0.05 s per
  elapsed second (plus up to 0.5 s of jitter), takes 0.7 s per crawl and un-blooms the pad
  it reaches; save key `KANTMICROGAMES.SLIMEHOP.best`.
- **SNAILRACE settings (module content `011-20261101`):** steer speed 6.8 px/s per axis
  (lane changes cost no forward ground); track y 32–84, start `(14,57)`, finish x 84;
  4 of 7 lettuce slots per race, lettuce +5 and a 1.1 s 1.7× boost; 3 of 6 salt slots,
  salt 0.35× for 1.0 s and a 1.6 s lock; ZOOM 1.55× for 0.7 s with a 2.6 s cooldown;
  rivals start `(11,42)` at 6.6 px/s and `(11,72)` at 6.9 px/s, weave ±3 px, take a 0.9 s
  1.5× boost every 3.0–4.4 s and slow to 0.45× for 0.9 s on salt; placement bonuses
  120 / 70 / 30; round 20 s; save key `KANTMICROGAMES.SNAILRACE.best`.

### A8 — Old wording of How to open and play, The seven rules, Links and License

Moved from README.md § How to open and play in build 012 — verbatim, not edited.

## How to open and play

- **Play online:** <https://kantmicrogames.lohyapkant.workers.dev/> (hosted on
  [Cloudflare Workers](https://workers.cloudflare.com/)).
- **Source code:** <https://github.com/lohyapkant/KANTMICROGAMES>
- **Play offline:** double-click `deploy/index.html`. The shelf shows one card per game —
  PANDASNACK, BOOPEEK, DUCKLINE, SPROUTUP, SLIMEHOP and SNAILRACE — with a code-drawn pixel
  preview, a concept line and the best score, plus a dashed COMING SOON slot.
- Click a card to open the game in the same page (no navigation, no iframes, no folders).
  `ESC` or the ⌂ SHELF button always brings you home.
- Tip: open `deploy/index.html#game=PANDASNACK`, `#game=BOOPEEK`, `#game=DUCKLINE`,
  `#game=SPROUTUP`, `#game=SLIMEHOP` or `#game=SNAILRACE` to land straight in a game.
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
| SLIMEHOP | hop pad to pad (one hop per press) | **STOMP** = bloom the pad underfoot (1.2 s cooldown) and stun a nearby snail | bloom all 9 pads in 30 s while the snail un-blooms them |
| SNAILRACE | steer in four directions | **ZOOM** = 1.55× dash for 0.7 s (2.6 s cooldown) | reach the strawberry first in 20 s; lettuce +5 and a speed boost, salt slows |

Moved from README.md § The seven rules in build 012 — verbatim, not edited.

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

Moved from README.md § Links in build 012 — verbatim, not edited.

## Links

| What | URL |
|---|---|
| **GitHub repository** | <https://github.com/lohyapkant/KANTMICROGAMES> |
| **Play online** | <https://kantmicrogames.lohyapkant.workers.dev/> |
| **Hosting** | [Cloudflare Workers](https://workers.cloudflare.com/) |

Moved from README.md § License in build 012 — verbatim, not edited.

## License

This project is released under the **MIT License** — see [`LICENSE`](LICENSE).

Copyright © 2026 **Loh Yap Kant**.

### A9 — CONTROLS.md passages removed in build 012

Moved from CONTROLS.md § opening paragraph in build 012 — verbatim, not edited.

Which controls exist, how they behave on each kind of device, and why. The shell
was made responsive and input-aware in build **009-20261101**. Build **010-20261101**
added the fifth game (SLIMEHOP) using the same contract and controls. Build
**011-20261101** adds the sixth game (SNAILRACE) with the same contract and freezes
SPROUTUP and SLIMEHOP; the five older modules were not touched.

Moved from CONTROLS.md § Accessibility (last bullet) in build 012 — verbatim, not edited.

- Colours and pixel art are untouched; this build only changed the shell.
