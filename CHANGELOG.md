# KANTMICROGAMES Changelog

## Conventions (read before adding an entry)

Appendices A1-A9, A11, A12 and A13 (material moved out of the README in builds 012 and 020 and out of CONTROLS.md in builds 018, 019 and 020) start under '## Appendices (build 012)' at the bottom of this file.

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
    ### Build record (owner request: duration + tokens/credits)
    - Duration: <minutes and how measured>
    - Usage: <value and unit as the tool reports it, how counted, number of requests>
    - Mode and owner notes: <selection mode such as Auto, plan or trial in use, meter reading at start as given by the owner>
    - Tools used: <short list of what you actually used, for example file view and edit, shell, node --check, Playwright with headless Chromium, curl>
    - Iterations: <N> rebuild loops, one line each: what looked wrong, what changed
    ### Documentation review/edit attempts (standing rule)

### Run guard (every prompt)

1. One step at a time, in order. If you finish early, stop.
2. Verification budget: one script per check, a timeout on every script, no screenshots, no browser matrix. One browser load at one viewport is enough for the footer check.
3. Repair budget: after a failed check, fix it and re-run ONLY that check. At most 2 repair cycles per problem. If it still fails, write "not fixed" in the report and move on. Never loop.
4. Checkpoint: after each step write "DONE step N / NEXT step N+1" in plans/archive/pre-020/PROGRESS.md. If a limit, error or quota message appears, finish the current edit, update PROGRESS.md and stop.
5. Work in plans/archive/pre-020/work/ and copy to the live files in ONE step at the end (STEP 7). If interrupted before that, the live files are still build 019.
6. Report what you skipped. A smaller true report beats a larger guessed one.

A prompt names one step or one small group of steps. The owner reads the usage meter between runs.

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
    11. Honest usage: record time and usage in the unit the tool reports, say how it was counted, write "not recorded" if unknown, and never add across units.
    12. Git: end your report with the suggested commands in a code block and do not run them: `git status`, `git add <the changed public files>`, `git commit -m "build NNN-YYYYMMDD: <title>" -m "<two to four bullets>"`, `git tag build-NNN`, `git push`.
    13. Meters: record what the tool's own usage meter shows at the start and the end, in its own unit, as supplied by the owner or visible to you. If you cannot see it, write "not visible to the model". Never estimate a balance. If two readings of the same usage disagree, record both, never add them, and write 'unreconciled' with what is known.
    14. Pixels: every new image, icon or badge is drawn from a pixel map. No image files, SVG or emoji as art.
    15. Stability: the stage must not change size at idle. After any change to `fitStage`, the top row or the controls, run the idle check (record the stage rectangle on every animation frame for 0.8 s at the named sizes; zero changes) before swapping files.
    Never delete, shorten or restructure any documentation file or section. If something looks wrong, say so in the entry instead of fixing it silently.

### Continuity when a free tier runs out

Free and trial tiers end without warning. Any model must be able to pick up where another stopped.
1. Before starting, ask the owner for the tool's usage meter (credits, requests or percent of a window) and record it.
2. Work in a copy (plans/archive/pre-NNN/work/), keep PROGRESS.md with DONE and NEXT lines, and swap into the live files in one step at the end.
3. Finish the step you are on. Never stop with a live file half edited. If the meter is low, do the steps in priority order and stop cleanly after a finished step.
4. A new model reads, in order: CHANGELOG.md → Conventions, the newest CHANGELOG entry, plans/archive/pre-NNN/PROGRESS.md, then the prompt copy for the build.
5. One build, one prompt, one focus. Split big requests into several builds.
6. Never carry a claim forward (credits left, tests passed) without checking it again.
7. Verification is a budget, not a goal: a small set of viewports, two repair cycles, then write 'not fixed' and move on. A test that cannot pass is a reason to stop and report, not to loop.

<!-- NEW BUILD ENTRIES: paste the newest entry on the line below this comment, above the previous newest. Never edit older entries. -->

## 020-20261106 — 2026-11-06 (Documentation repair: README, CHANGELOG, MODELS, CONTROLS, plan; no game change)

Built from prompt: P-20 (the owner's documentation-repair prompt; private archive file `prompts/P-20_docs-repair.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
Games in the one file: 8 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101 **frozen**, HUGPARADE
015-20261102 (unchanged this build), CATNAPCATCH 016-20261102 (unchanged this build);
file build **020-20261106**)

### Changed — documentation only; no game, layout or behaviour changed

- README.md: removed the unauthorised "## How the builds are checked" section (F1), archived
  verbatim in Appendix A13; the Qwen3.8-Flash Builds cell now ends `017` and the DeepSeek
  V4.1 Flash Free cell is `000, 001, 005, 006, 017, 018, 019, 020` (F2); "Current build" is
  `020-20261106`.
- MODELS.md: replaced the three F3 totals bullets with the four bullets supplied in the
  prompt (74.5874 credits / 1,143 requests for builds 009–016; build 017's two readings
  recorded and never added; an explicit "Unreconciled" bullet; the ~US$3.00 plan-meter
  estimate). Appended the 2026-11-03 payment update (F5), added the 2026-11-06 dated entry
  for builds 018 and 019 carrying the owner's iPhone report (F8), and added the build-020
  Usage ledger row.
- MODELS.md "Usage meters explained" (F4): the OpenCode and Antigravity pages cited in
  those rows were opened again on 2026-11-06. OpenCode's Console page still shows usage
  tracking, budget controls and Go / Go Plus / Go Teams at US$10 / US$40 / US$20 per member
  per month; Antigravity's pricing page still shows a US$0 Individual plan, weekly rate
  limits, a Pro/Ultra credit pool and Cloud consumption pricing. Both rows were left as
  they stand; no price or limit was changed and none was re-guessed.
- CHANGELOG.md: Conventions gained the "### Run guard (every prompt)" block and Continuity
  item 7 (F6); checklist item 13 was amended; the appendix pointer now names A13; Appendix
  A13 holds the removed README section and the removed CONTROLS sentence verbatim. Entry
  019 gained one dated addendum and nothing else (F8). Entries 000–018 are byte-identical.
- CONTROLS.md: the stale first bullet of "Known control quirks" now says the game screen
  shows no hint line (F7); the old sentence is archived in A13. "Applies to" stays at 019
  because the controls did not change.
- plans/micro-games-v2.md: one ledger row, one tool-log row and the "Roadmap v3" block
  appended; nothing above them was edited.
- deploy/index.html: `APP.fileVersion` and the header "Current" line only.
- F9: this is the documentation repair that entry 019 said "will take a later number".
  Builds 018 and 019 were the controls/top-bar and stage-stability builds.

### Verification and limits

- Old records: entries 000–018 of CHANGELOG.md are byte-identical to the pre-020 snapshot;
  entry 019 is byte-identical plus the one appended addendum; every MODELS.md dated entry
  and existing ledger row is byte-identical (diff). The removed README section and CONTROLS
  sentence are found verbatim in A13.
- Build ID: `020-20261106` in `APP.fileVersion`, the index header, the rendered footer,
  README "Current build", the top CHANGELOG entry and the plan ledger row. CONTROLS
  "Applies to" stays `019-20261106` by design.
- README: 93 lines and 5,872 bytes (caps 150 lines / 10 KB); zero whole-word,
  case-insensitive matches for IIFE, frozen, contract, credit, token, hash. Table column
  counts are constant in all five documents; every relative link resolves in the public
  tree and none points at plans/, tests/ or prompts/.
- Time totals recomputed by script from the ledger rows, with the working shown in the
  build report. No credit line is summed across the two Qoder readings.
- All eight game IIFE hashes are identical before and after (`node --check` clean): the
  eight values are the build-019 values. One browser load at one viewport found one footer
  build ID and zero console errors.
- Not verified: no screenshot matrix and no multi-viewport browser run — the Run guard
  limits this build to one load, and the layout did not change. No real iPhone or Safari
  test was run in this build (the owner's report is quoted, not re-tested). No git command
  was run.

### Edits to existing text

- `README.md` — removed, in full:
  "## How the builds are checked" and its paragraph ("Since build 009, each shell change
  is checked against a viewport test matrix … fix what the measurements do not show.").
  New text: none in the README; the removed section is archived in A13.
- `README.md` — Qwen3.8-Flash Builds cell: old `008 (finish), 009, 010, 011, 012, 013, 014,
  015, 016` → new `008 (finish), 009, 010, 011, 012, 013, 014, 015, 016, 017`. No other
  cell in that row changed.
- `README.md` — DeepSeek V4.1 Flash Free Builds cell: old `000, 001, 005, 006, 018, 019` →
  new `000, 001, 005, 006, 017, 018, 019, 020`. No other cell in that row changed.
- `README.md` — "**Current build:** `019-20261106` — eight games, one file." → "**Current
  build:** `020-20261106` — eight games, one file."
- `MODELS.md` — old bullet "**Credits, Qoder CLI, measured (builds 009-017):** 127.3432
  credits over 1,247 billable requests." replaced by "**Credits, Qoder CLI, per-request
  transcript, builds 009-016:** 74.5874 credits over 1,143 billable requests."
- `MODELS.md` — old bullet "**Approximate list-price value of the measured credits:**
  127.3432 x US$0.01 = US$1.27. An estimate, not a bill: the trial is free. Based on
  Qoder's published plan prices (about US$20 for 2,000 credits); check
  https://docs.qoder.com/account/pricing before relying on it. Never converted for tokens
  and never added across tools." replaced by "**Approximate list-price value:** the plan
  meter reads 300 of 300 trial credits used, which is about US$3.00 at about US$0.01 per
  credit. An estimate, not a bill: the trial is free. Check
  https://docs.qoder.com/account/pricing before relying on it. Never converted for tokens
  and never added across tools."
- `MODELS.md` — old bullet "**Owner's Qoder exit report for build 017:** plan **300/300
  credits used**; session **300.8933 credits**; **398 tool calls**; wall time 1 h 38 min
  49 s. This is Qoder's own meter reading, not the per-request transcript total above, and
  is not added to it (the two meters count differently)." replaced by two bullets:
  "**Build 017, two readings, never added:** the transcript snapshot taken at 17:49 shows
  52.7558 credits over 104 requests (incomplete: the session ran on afterwards). Qoder's
  own exit report shows session 300.8933 credits, 398 tool calls and the plan at 300/300
  credits." and "**Unreconciled:** the transcript total for builds 009-016 plus the
  exit-report figure for build 017 is more than the 300-credit plan, and why is not known.
  Do not total these readings. The authoritative figure is Qoder's usage history, read by
  the owner."
- `MODELS.md` — "How this project is paid for": appended "**Update, 2026-11-03:** the Qoder
  trial credits are used up (plan meter 300/300; the trial itself ends 2026-11-15 at
  15:24:49 GMT+7). Build 017 was finished on OpenCode with DeepSeek V4.1 Flash Free, and
  builds 018 onward run on OpenCode's free models unless noted."
- `MODELS.md` — Usage ledger: added the row `| 020 | DeepSeek V4.1 Flash Free · OpenCode |
  built | ~15 min | — | not visible to the model; owner notes blank, no meter reading
  supplied |`.
- `MODELS.md` — time-by-model row: old `| DeepSeek V4.1 Flash Free | ~205 |` → new
  `| DeepSeek V4.1 Flash Free | ~220 |` with 22 blocks instead of 21.
- `MODELS.md` — total: old "Total recorded: about 655 minutes (about 10 h 55 min) over 17
  of 20 builds." → new "Total recorded: about 670 minutes (about 11 h 10 min) over 18 of
  21 builds."; the parenthetical now says "after the build-020 row was added".
- `MODELS.md` — new dated entry "## 2026-11-06 — DeepSeek V4.1 Flash Free (OpenCode) —
  builds 018 and 019" added above the marker with the owner's words verbatim; no existing
  dated entry was edited.
- `CONTROLS.md` — first bullet of "Known control quirks": old "The shell writes its own
  hint line from the game's action label, so the frozen modules' original desktop hint
  strings are not shown. No game code had to change." → new "The game screen shows no hint
  line. The shelf cards and chips explain the controls, and the frozen modules' original
  desktop hint strings are not shown. No game code had to change."
- `CHANGELOG.md` — entry 019: appended "### Addendum — 2026-11-06 (owner report, recorded
  in build 020)" with the owner's iPhone 16 Pro Max / Safari / portrait report. Nothing
  above it in entry 019 changed.
- `CHANGELOG.md` — Conventions: added "### Run guard (every prompt)" with the prompt's six
  numbered rules verbatim and the closing line "A prompt names one step or one small group
  of steps. The owner reads the usage meter between runs."
- `CHANGELOG.md` — checklist item 13: old "… Never estimate a balance." → new "… Never
  estimate a balance. If two readings of the same usage disagree, record both, never add
  them, and write 'unreconciled' with what is known."
- `CHANGELOG.md` — Continuity: added item 7, "Verification is a budget, not a goal: a small
  set of viewports, two repair cycles, then write 'not fixed' and move on. A test that
  cannot pass is a reason to stop and report, not to loop."
- `CHANGELOG.md` — appendix pointer: old "Appendices A1-A9, A11 and A12 (material moved out
  of the README in build 012 and out of CONTROLS.md in builds 018 and 019) …" → new
  "Appendices A1-A9, A11, A12 and A13 (material moved out of the README in builds 012 and
  020 and out of CONTROLS.md in builds 018, 019 and 020) …".
- `deploy/index.html` — `APP.fileVersion`: old `"019-20261106"` → new `"020-20261106"`;
  header "Current" line: old `019-20261106` → new `020-20261106`. No other line changed.
- `plans/micro-games-v2.md` — one ledger row and one tool-log row appended; the
  "## Roadmap v3" block appended after the old roadmap. Nothing above them was edited.

### Build record (owner request: duration + tokens/credits)

- Duration: ~15 min wall clock (the STEP 0 snapshot was created at 14:01 and the records were finished at about 14:12 WIB; the run began a few minutes before the snapshot and its exact start was not timestamped).
- Usage: not visible to the model; the owner notes were blank and no meter reading was
  supplied. No token or credit figure is claimed. A tokens-per-second × duration figure
  was considered and rejected: it would be an estimate presented as a measurement.
- Mode and owner notes: DeepSeek V4.1 Flash Free on OpenCode's free tier. The owner's
  verbatim note after build 019 is quoted in MODELS.md and in the entry-019 addendum. The
  model/tool and meter fields were blank.
- Tools used: file view/edit, shell, `diff`/`shasum`, Python scripts for the checks,
  Node.js `--check`, one headless-Chrome CDP load for the footer.
- Iterations: 1 documentation pass. The F4 pages were re-opened once each; both confirmed
  the existing row text, so no row was changed. No layout repair cycle was needed.

### Documentation review/edit attempts (standing rule)

- No separate documentation review model was used. Every edit was checked against the
  Conventions and the per-build checklist; the removed README section and CONTROLS sentence
  were copied verbatim into Appendix A13 before the edit.

## 019-20261106 — 2026-11-06 (Stage stability and crisp sizing: no idle vibration, whole-device-pixel cap)

Built from prompt: P-19 (the owner's stage-stability and crisp-sizing prompt; private archive file `prompts/P-19_stage-stability.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
Games in the one file: 8 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101 **frozen**, HUGPARADE
015-20261102 (unchanged this build), CATNAPCATCH 016-20261102 (unchanged this build);
file build **019-20261106**)

### Fixed — the stage no longer vibrates at idle (F1)

- Removed the build-018 `.tight-top` mechanism: the conditional class toggle,
  `fitTightDone`, the `heightLimited` / `stageLimit` decision and the CSS that hid
  `#gameTagline` / `#inputHint` only when the height was the limit. Per D1 both are
  now hidden permanently on the game screen.
- `fitStage` now computes the room from `#gameScreen` (`100dvh`), the measured slim
  top row, the class-table control sizes (`--dir-size`, `--dir-gap`,
  `--action-size`), the bezel chrome, the safe areas and fixed constants. It no
  longer measures `#stageBlock` or anything inside it, so resizing the canvas cannot
  feed back into the next fit.
- Removed the `ResizeObserver` on `#stageBlock`. Re-fit happens only on `resize`,
  `orientationchange`, `visualViewport` resize, game open and restart, coalesced with
  one `requestAnimationFrame`. A size that is already current is not written.
- Baseline (build 018): IDLE SWEEP 7/33 fail — 47 stage changes and 96–225
  style/class mutations per 800 ms at 440×704, 440×720, 440×736, 440×752, 430×700,
  430×740 and 360×640. Build 019: 33/33 pass with 0 changes and 0 mutations.
  RESIZE SETTLE: 69 changes before; 1 change each at heights 744 and 800 after.

### Fixed — the 600 px cap is whole-pixel at every display scale (F2)

- `STAGE_CAP_CSS = 600`; `devicePxPerArtPx = min(floor(roomCssPx × dpr / 100),
  floor(600 × dpr / 100))`; stage CSS size = `devicePxPerArtPx × 100 / dpr`.
- Baseline (build 018): 3/8 fail — DPR 1.25 gave 7.5, 1.75 gave 10.5 and 2.25 gave
  13.5 device px per art px. Build 019: 8/8 pass — DPR 1.25 → 560, 1.75 → 571.42 and
  2.25 → 577.77 CSS px (7, 10 and 13 device px per art px); DPR 1, 1.5, 2, 2.5 and 3
  stay at 600 CSS px.
- D2 respected: whole device pixels per art pixel; no fractional or "fill" scaling was
  added. D3 respected: no new UI and no options.

### Changed — tagline and hint (D1) and image-rendering order (F4)

- `#gameTagline` and `#inputHint` are `display: none` on the game screen on every
  device. The title, SCORE, BEST, SHELF and RESTART are unchanged from build 018.
- `image-rendering: pixelated;` is now the last of the pair in every rule that had
  both declarations (four rules plus `#soonMoon`), so a browser that accepts both no
  longer lets `crisp-edges` win.

### Verification and limits

- Viewports (CSS px, DPR): 280×653 (3), 390×844 (3), 768×1024 (2), 844×390 (3),
  1280×720 (1), 1920×1080 (1). Games: PANDASNACK and CATNAPCATCH for layout.
- V1 IDLE SWEEP: 33/33 pass (0 changes, 0 mutations).
- V2 RESIZE SETTLE: pass (1 change each at heights 744 and 800, then quiet).
- V3 CAP SWEEP: 8/8 pass (see above).
- V4 stage sizes: 233.33, 333.33, 600, 266.66, 600, 600 CSS px. At 844×390 the stage
  is 266.66 with the title message present; build 018 is also 266.66 in that state.
  With an empty message the 844×390 stage is 300 CSS px, which is the F6 baseline;
  F6's 300 was measured in the empty-message state. SHELF and RESTART positions and
  sizes are unchanged from build 018; directions are left and the action right; no
  horizontal overflow and no page scroll.
- V5 play check at 390×844: a CDP touch on LEFT fired `onDir("left", true)` then
  `false`; a tap on the action button fired `onAction`; W, Space, R and Esc worked; a
  `blur` paused the run and the next key only resumed.
- V6: all eight IIFE hashes are identical to build 018 and start with the F5 values
  (PANDASNACK f6dd1614db8ca9d6, BOOPEEK f321297984175b84, DUCKLINE 6a62f23a0d747a5a,
  SPROUTUP adff7441c41aef44, SLIMEHOP a92efde40ca8618a, SNAILRACE 457fa4b4750da245,
  HUGPARADE 151deb6e718b23a6, CATNAPCATCH 26f6be1af791ee73). `node --check` clean;
  one footer build ID; zero console errors.
- V7: README is 97 lines and 6.4 KB; older CHANGELOG entries and MODELS dated entries
  and ledger rows are byte-identical (diff shows only the intended regions); the same
  build ID is in `APP.fileVersion`, the index header, the rendered footer, README, the
  top CHANGELOG entry and the plan row; table column counts are constant; relative
  links resolve.
- Stage at 440×745 @3 (PANDASNACK): 400×400 CSS px at (20, 77). Stage at 440×956 @3
  (CATNAPCATCH): 400×400 CSS px at (20, 175).
- Not verified: no real iPhone, no Safari and no real iOS hardware. The owner's phone
  is an iPhone 16 Pro Max on Safari in portrait (440 CSS px wide at 3×); that device
  and browser were **NOT** tested here. No screen reader. No git command was run.

### Edits to existing text

- `deploy/index.html`: header "Current" and "Build log" lines; `APP.fileVersion`; the
  game-screen tagline/hint CSS; `fitStage` and `stageScaleFromBox` (replacing
  `stageScaleFor`), the stage constants and element handles; the restart paths; the
  `image-rendering` order. The eight game IIFEs were not touched.
- `CONTROLS.md`: the "Applies to" line; the tagline/hint sentences in "Controls on
  the game screen" and "Layout and scaling"; one sentence added to the crisp+ bullet.
  Every removed sentence is archived verbatim in Appendix A12.
- `README.md`: "Current build" 019; 019 added to the DeepSeek V4.1 Flash Free row.
  No other README text changed.
- `MODELS.md`: one Usage ledger row for build 019 and recomputed time totals/bars. No
  dated observation was added because the owner notes were blank. No credit line was
  touched.
- `CHANGELOG.md`: this entry, checklist item 15 and Appendix A12 only; entries
  000–018 are untouched.
- `plans/micro-games-v2.md`: one ledger row and one tool-log row.
- Build 018 was the controls and top bar build; the planned docs repair is still
  pending and will take a later number.

### Build record (owner request: duration + tokens/credits)

- Duration: ~30 min wall clock (the STEP 0 snapshot was created at 09:20 and the
  final swap at 09:33 WIB; the run began a few minutes before the snapshot and its
  exact start was not timestamped).
- Usage: not visible to the model; the owner notes were blank and no meter reading was
  supplied. No token or credit figure is claimed.
- Mode and owner notes: the owner supplied the test phone (iPhone 16 Pro Max, Safari,
  portrait, 440 CSS px wide at 3×) and reported the stage vibrating and blurring on
  every game in portrait. The model/tool and meter fields were blank.
- Tools used: file view/edit, shell, Python exact-match patch scripts, Node.js
  `--check`, headless Chrome over CDP (Node WebSocket helper), `curl`, screenshots.
- Iterations: 1 implementation pass. The verification helper needed 2 repairs (a
  touch-emulation parameter and a resize-recorder race) and Chrome was restarted once
  to reset emulated DPR; no layout repair cycle was needed. The 844×390 V4 figure was
  investigated rather than changed: build 018 and build 019 both measure 266.66 with
  the title message and 300 with an empty message.

### Documentation review/edit attempts (standing rule)

- No separate documentation review model was used. The build's own documentation
  edits were checked against the Conventions and the per-build checklist; the removed
  CONTROLS sentences were copied verbatim into Appendix A12 before the edit.

### Addendum — 2026-11-06 (owner report, recorded in build 020)
- The owner played all eight games on an iPhone 16 Pro Max in Safari (portrait) after this build and reported that the vibration is gone. That is the real-device check this report lists as not done. It covers the vibration only, not every other Safari behaviour. Recorded by DeepSeek V4.1 Flash Free from the owner's message.

## 018-20261104 — 2026-11-04 (Controls and top bar: pinned SHELF/RESTART, fixed pixel labels, no menu)

Built from prompt: P-18 (the owner's controls-and-top-bar prompt; its text said "build 019"
and "currently build 018", but the repo was at build 017 with no 018 anywhere, so the owner
confirmed this run is build 018; private archive file `prompts/P-18_controls-and-top-bar.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
Games in the one file: 8 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101 **frozen**, HUGPARADE
015-20261102 (unchanged this build), CATNAPCATCH 016-20261102 (unchanged this build);
file build **018-20261104**)

### Removed — MENU and the three pad options (deploy/index.html, PART 3 + PART 4)

- The MENU button, its paused sheet (RESUME / RESTART · R / ⌂ SHELF), the M key,
  the three-bar icon and all their CSS/JS/listeners are gone. `openGame`/`openShelf`
  no longer call `closeMenu`, and the pause plate no longer checks `MENU.open`.
- The PADS (AUTO / SHOW / HIDE), DIR PAD (LEFT / RIGHT) and PAD SIZE (S / M / L)
  shelf buttons, the `#prefs` group, the `UI` object, `readUiPref` / `saveUiPref`,
  `applyUi` / `setInputMode`, the `data-pads` / `data-padsize` / `data-hand` /
  `data-input` attributes and the CSS that hid the pads in keyboard mode are gone.
  Old stored values under `KANTMICROGAMES.ui.*` are left untouched and never read.
- The shelf chip now reads "pads on every screen"; the other two chips describe the
  pad and the keyboard without a device guess.

### Added — pinned SHELF and RESTART (items 1 and 6)

- A fixed `.cornerBar` at `top: calc(var(--sai-t) + 8px); left: calc(var(--sai-l) + 8px)`
  holds two real buttons, SHELF and RESTART, with 12 px between them and the
  per-class height from the size table (48 / 48 / 52 / 56 px). They are identical on
  all eight games and do not move with the centred content column.
- Both labels are pixel-text canvases (SHELF, RESTART) with full-word `aria-label`s.
- Under 360 px wide the pair stacks vertically; that is the measured fix for the
  280 px test screen, where the side-by-side pair plus the title, SCORE and BEST did
  not fit (the title collapsed to 0 px and the row overflowed by 1 px). Stacked, the
  pair is 60 px wide and the title keeps 52 px with no overflow.
- The title, SCORE and BEST stay in the slim top row to the right of the pair; the
  tagline and hint are hidden only when the stage is height-limited, as before.

### Changed — directions left, action right, fixed sizes (items 3, 4, 5)

- Portrait: stage on top, one controls row below, directions left and action right.
- Landscape: three columns (directions, stage, action), centred with 24 px column
  gaps and capped at 1100 px, so a 1920 px screen does not push the controls to the
  edges. The stage column is centred between the controls; the group is centred.
- The direction cluster is still the plus shape with an empty centre, an 8 px gap
  between buttons, and at least 24 px from the action button in portrait.
- Sizes are fixed by the shorter side of the viewport: XS 48 / 88, SM 60 / 112,
  MD 72 / 132, LG 84 / 156; labels 2/3, 2/3, 3/4, 3/5; corner heights 48 / 48 /
  52 / 56. No user option. Every tappable is at least 48 × 48.
- The XS direction and action sizes are 48 and 88, not the prompt's 52 and 96:
  52 × 3 + 8 × 2 + 24 + 96 = 292 px cannot fit a 280 px screen. At 280 the page
  side padding also drops from 8 px to 4 px so the 272 px XS row fits exactly.

### Added — crisp pixel-text labels (item 6)

- `drawPixelLabel` / `refreshPixelLabels` draw every control label with the file's
  own `PIXEL_FONT` and `paintPixelText`. `n = round(scale × devicePixelRatio)` is a
  whole number of device pixels per font pixel; the canvas CSS size is `n / dpr`.
- The action label is redrawn when a game opens (`setActionLabel`), and all labels
  are redrawn on resize, orientation change, visual-viewport change and after the
  first layout. No arrows, SVG, emoji or system-font words remain on game controls.

### Verification and limits

- Viewports (CSS px, DPR): 280×653 (3), 390×844 (3), 768×1024 (2), 844×390 (3),
  1280×720 (1), 1920×1080 (1). Games: PANDASNACK and CATNAPCATCH for layout; all
  eight action labels at 390×844.
- A1 pass: no `#btnMenu`, `#menuOverlay`, `#menuSheet`, `#menuIcon`, `#prefs`,
  `#btnPadMode`, `#btnPadSize`, `#btnHandMode`, no `KeyM` and no `PADS ·` /
  `PAD SIZE` / `DIR PAD` text remains.
- A2 pass: SHELF is at (8, 8) in both games at every viewport; RESTART sits
  immediately to its right with a 12 px gap when side by side, and at (8, 68)
  when the pair stacks at 280; heights 48 / 48 / 52 / 56; sizes per class.
- A3 pass: directions left of the stage and action right in landscape at 844×390,
  1280×720 and 1920×1080; both below the stage with directions left at 280×653,
  390×844 and 768×1024; controls visible with touch emulation off at 1280/1920.
- A4 pass: measured sizes match the class table; every tappable ≥ 48 × 48; 8 px
  direction gaps; 24 px direction-to-action gap in portrait; all eight action
  labels fit (widest REACH/STOMP 57 px in a 112 px button at 390).
- A5 pass: every control label is a canvas with an `aria-label`; no arrows or
  symbols; `canvas.width / pixelTextWidth(text, 1)` is an integer at DPR 1, 2 and 3.
- A6 pass: a CDP touch on LEFT fired `onDir("left", true)` then `false`; the action
  fired `onAction`; W/A/S/D, Space, R and Esc worked; a `blur` paused the run and
  the next key only resumed.
- A7 pass: five stage sizes are unchanged from build 017 and the sixth grew:
  233.33, 333.33, 600, 300 (was 266.66 at 844×390), 600, 600 CSS px. No page
  scroll and no horizontal overflow.
- A8 pass: all eight game IIFE hashes are identical to build 017: PANDASNACK
  f6dd1614db8ca9d6, BOOPEEK f321297984175b84, DUCKLINE 6a62f23a0d747a5a,
  SPROUTUP adff7441c41aef44, SLIMEHOP a92efde40ca8618a, SNAILRACE
  457fa4b4750da245, HUGPARADE 151deb6e718b23a6, CATNAPCATCH 26f6be1af791ee73.
  `node --check` clean; one footer build ID; zero console errors.
- A9 pass: README is 97 lines and 6.4 KB; old CHANGELOG/MODELS entries and ledger
  rows are byte-identical; the same build ID is in `APP.fileVersion`, the index
  header, the rendered footer, README, the top CHANGELOG entry and the plan row;
  ledger totals recomputed.
- Screenshots: four files captured (390×844 PANDASNACK, 844×390 PANDASNACK,
  1280×720 CATNAPCATCH, 768×1024 CATNAPCATCH); the 844×390 file was refreshed
  after the final fit, and all four were inspected (one more than the suggested
  three).
- Not verified: no real iOS/Android hardware, no screen reader, no 3440 px screen
  (the build's limit was the six named viewports). The Run guard section was not
  present in CHANGELOG; the owner confirmed step 5's six-viewport and one-repair
  limits were the operative guard. No git command was run.

### Edits to existing text

- `deploy/index.html`: header "Current" and "Build log" lines; `APP.fileVersion`;
  the size-variable block, focus rule, game-screen/corner-bar CSS, top-row reserve,
  landscape grid, controls row, direction cluster, `.pbtn`, `#pDash`, small-screen
  top row and reduced-motion rule; the shelf how-to chips; the game-screen markup
  and the runtime element handles, keyboard handler, hints, menu/pad code and
  listeners. The eight game IIFEs were not touched.
- `CONTROLS.md`: rewritten for the pinned pair, always-on pads, fixed sizes, pixel
  labels and no menu; every removed passage is archived verbatim in Appendix A11.
- `README.md`: "Current build" 018; the one pad bullet replaced; 018 added to the
  DeepSeek V4.1 Flash Free row. No other README text changed.
- `MODELS.md`: one Usage ledger row for build 018 and recomputed totals. No dated
  observation was added because the owner notes were blank.
- `CHANGELOG.md`: this entry and Appendix A11 only; entries 000–017 are untouched.
- `plans/micro-games-v2.md`: one ledger row and one tool-log row.

### Build record (owner request: duration + tokens/credits)

- Duration: ~35 min wall clock (from the first snapshot/tool call at about 19:25 to
  the final swap at about 20:00 WIB; measured with the shell clock).
- Usage: not visible to the model; the owner notes were blank and no meter reading
  was supplied. No token or credit figure is claimed.
- Mode and owner notes: owner supplied two decisions only — use 018-20261104, and
  use step 5 as the guard. Model/tool and meter fields were blank.
- Tools used: file view/edit, shell, Python exact-match patch scripts, Node.js
  `--check`, headless Chrome over CDP (Node WebSocket helper), `curl`, screenshots.
- Iterations: 1 repair cycle pair. First pass measured a 280 px clash (side-by-side
  pair left 0 px for the title and overflowed the row by 1 px); the fix stacked the
  pair under 360 px and dropped the 280 px page padding to 4 px. Re-measured green.

### Documentation review/edit attempts (standing rule)

- No separate documentation review model was used. The build's own documentation
  edits were checked against the Conventions and the per-build checklist; the old
  CONTROLS passages were copied verbatim into A11 before the rewrite.


## 017-20261103 — 2026-11-03 (Shell UX and process: MENU, PAD SIZE, crisp+ stage, tidy shelf)

Built from prompt: P-17 (a process-and-shell prompt authored by Claude.ai Sonnet 5.5
Extra, pasted verbatim with the owner-notes fields left blank; private archive file
`prompts/P-17_shell-ux-and-process.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
Games in the one file: 8 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101 **frozen**, HUGPARADE
015-20261102 (unchanged this build), CATNAPCATCH 016-20261102 (unchanged this build);
file build **017-20261103**)

### Changed — shelf cards align (deploy/index.html, PART 3)

- `.card` is a flex column that starts at the top (preview, name, concept) and the
  "best" line is pinned to the card bottom with `margin-top: auto`. Before, each card
  was a plain button whose content was vertically centred, so cards in one row showed
  their art at different heights (measured offsets 38 / 19 / 28 px in one row at 1280
  wide before the fix).

### Added — the game menu replaces the loose RESTART and ⌂ SHELF buttons (PART 4)

- A MENU button sits in the top-right corner of the game screen in both orientations
  (about 91 px wide and 48 px tall as rendered; the prompt's floor is 48x48; 77 px
  wide under 440 px), with a three-bar icon drawn from an 8×8 pixel map through
  `paintPixels` and the word MENU. It is at least 24 px from every pad control (it
  shares no row with them). Header text keeps `--menu-reserve` (104 px, 92 px under
  380 px) of the right edge clear so the corner button never covers the tagline, the
  hint line or the SCORE/BEST chips; on a phone the title yields first and truncates
  with an ellipsis (full name from 360 px up; below that it truncates). Found by
  looking at the build's
  screenshots, then fixed and re-measured with client rects at six viewports across
  all eight games.
- MENU or the M key opens a paused dialog (`role="dialog"`, `aria-modal="true"`, label
  "Game menu") with RESUME (focused first), RESTART · R, ⌂ SHELF and the game's own
  how-to line. Each button is 56 px tall with 12 px between them. Opening it pauses
  with the existing paused state (the PAUSED plate stays hidden behind the sheet) and
  releases every held direction. RESUME, a tap outside the sheet, R, M and Esc-from-
  play all behave as documented: Esc still leaves for the shelf (from the menu too),
  R still restarts at once.
- Focus is trapped inside the sheet (Tab cycles and wraps both ways) and returns to
  MENU on close. RESTART sets the score to 0 and returns to the ready state; ⌂ SHELF
  returns to the shelf; all three work by tap and by keyboard.
- Ghost-click safety: the sheet's backdrop consumes the pointer that closes it, and the
  touch that lands exactly on the hidden action button's spot fired zero `onAction`
  calls in testing.
- The RESTART · R button is gone from the action cluster (it sat 8 px under the thumb,
  on top of the action button, at every touch size tested) and ⌂ SHELF is gone from
  the top row.

### Changed — crisp+ stage scaling and a slimmer chrome (PART 4)

- `stageScaleFor` now computes whole device pixels per art pixel:
  `floor(availableCssPx x devicePixelRatio / 100)`, and the canvas CSS size is that
  ratio times 100 / dpr, so every art pixel covers a whole number of device pixels.
  The old fractional fallback applies only when the result is under 2x. The canvas is
  nudged so its edges land on whole device pixels (margin corrections, never a CSS
  transform); `image-rendering: pixelated` stays.
- On screens up to 480 px wide the bezel padding drops from 12 to 6 px and the page
  side padding from 14 to 8 px. The top row (title, SCORE, BEST chips; MENU lives in
  the corner) is capped at 44 px. The tagline and the one-line hint are hidden
  (`tight-top`) only when showing them would make the stage height-limited; a one-shot
  guard makes that decision once per fit so the ResizeObserver cannot oscillate.
- Measured stage widths after the change: 300 px at 360x640 DPR 3 (target 267),
  333.33 px at 390x844 DPR 3 (target 333), 380.94 px at 412x915 DPR 2.625 (target
  343), 300 px at 844x390 DPR 3 (target 267), 250 px at 667x375 DPR 2 (target 250).
  Stage width x dpr / 100 is an integer at DPR 1, 2, 2.625 and 3; no horizontal
  overflow and no page scroll while playing on the tested matrix.

### Added — PAD SIZE (S / M / L) on the shelf (PART 3 and PART 4)

- A PAD SIZE preference button sits between PADS and DIR PAD, cycles S / M / L with an
  aria-label, persists as `KANTMICROGAMES.ui.padsize` with the existing try/catch
  pattern and is restored on load. Default M.
- Pad sizes: on viewports wider than 380 and taller than 620, S = 58 px, M = 66 px,
  L = 76 px; on smaller screens S = 48, M = 56, L = 64. The action button is
  1.7 x the pad size. Pad-to-pad gaps are 9 px (8 px on small screens) and the gap
  between the direction cluster and the action button is 24 px, so the action button
  stays at least 24 px from every other tappable.
- On narrow widths where L (76 px) could not keep that 24 px separation without
  wrapping under the pads, L renders one step down (66 px under 416 px wide, 56 px
  under 357 px wide) — the prompt's "shrink the pads toward S before the stage drops
  below its target". Full 76 px L applies from 416 px wide.
- Action labels still come from each module (`actionLabel`) and are not clipped at S,
  M and L for all eight games; multi-touch (hold a direction, tap the action) and
  sliding across the pad still work, re-tested after the change.

### Edits to existing text — CHANGELOG Conventions

- The Entry template's Build record line used to read:
      `### Build record (owner request: duration + tokens/credits)   (honest; credits are not tokens)`
  and is now the five-line block (Duration / Usage / Mode and owner notes / Tools
  used / Iterations) shown in the template above.
- The Per-build checklist keeps items 1-11 unchanged and adds items 12-14 (git
  suggestions at the end of the report, never run; meters recorded as the tool
  reports them or "not visible to the model"; every new image is a pixel map).
- A new Conventions block, "Continuity when a free tier runs out", records the
  hand-over rules. No older entry, checklist item or convention line was edited or
  removed.

### Verification and limits

- **Games untouched:** the eight game IIFEs hash identical to build 016 and start with
  the F6 values (PANDASNACK `f6dd1614…`, BOOPEEK `f3212979…`, DUCKLINE `6a62f23a…`,
  SPROUTUP `adff7441…`, SLIMEHOP `a92efde4…`, SNAILRACE `457fa4b4…`, HUGPARADE
  `151deb6e…`, CATNAPCATCH `26f6be1a…`). `node --check` on the extracted inline script
  is clean. Full hashes and the checks are in `tests/build-017-report.md`.
- **Render and behaviour:** tested in headless Chrome 156.0.8078.80 over the DevTools
  protocol on a 22-viewport matrix (280x653 to 3440x1440, portrait, landscape,
  desktop): steps 1-4 assertions pass; no horizontal overflow; no page scroll while
  playing; every tappable is at least 48x48; touch and keyboard play work in all
  eight games; pause on hide works; the footer shows exactly one build ID
  (017-20261103); zero console errors. Screenshots of the shelf, PANDASNACK and
  CATNAPCATCH at 360x640, 390x844, 844x390 and 1280x720 are in
  `tests/screenshots/build-017/` and were looked at.
- **Docs checks:** README stays at most 150 lines and 10 KB and avoids the banned
  words; the build ID is the same in APP.fileVersion, the index header, the footer,
  README "Current build", the top CHANGELOG entry and the plan ledger row; older
  CHANGELOG entries, MODELS dated entries and ledger rows are byte-identical (diff);
  relative links resolve; every table keeps a constant column count; the ledger
  totals were recomputed by script.
- **Limits:** headless Chrome only — no physical phone, Safari, Firefox or iOS/Android
  run. The owner-notes fields in the prompt were blank, so credits remaining, trial
  end date and anything else are recorded as "not provided", and the Qoder usage meter
  is not visible to the model (checklist item 13). No audio exists in the project, so
  none was tested.

### Build record (owner request: duration + tokens/credits)

- Duration: **about 40 min** wall-clock at the time this entry was written
  (2026-11-03, 17:21 → about 18:00 WIB, from the prompt paste to the records). The
  final figure is in the addendum below.
- Usage: **52.7558 credits across 104 billable requests** at the time of writing
  (2026-11-03, 17:21-17:49 WIB), summed from the per-request credits in the session
  transcript, deduplicated by `request_id`. Credits are not tokens, and no token
  number is invented. The final figure is in the addendum below.
- Mode and owner notes: model selection mode **Auto** (from the prompt). Qoder credits
  remaining at start: not provided. Trial ends on: not provided. Anything else to
  record: not provided. The Qoder usage meter itself is not visible to the model.
  (The owner supplied the exit figures after the session; see the addendum below.)
- Tools used: file view and edit, shell (node, curl, diff, sed), `node --check`,
  headless Chrome 156 driven over the DevTools protocol with small Node scripts
  (viewport/touch/keyboard emulation, screenshots), python3 for hashing and for
  summing the per-request credits, WebFetch for the Qoder/OpenCode/Antigravity pricing
  pages.
- Iterations: 4 rebuild loops. (1) The tight-top decision re-entered `fitStage`
  through the ResizeObserver and toggled itself back and forth — a `RangeError:
  Maximum call stack size exceeded` at 390x844 with L pads; fixed with a one-shot
  guard so the hide-tagline decision is made once per fit. (2) At 390x844 with L the
  action button wrapped 8 px under the direction cluster (the spec wants at least
  24 px); fixed with a 24 px cluster gap plus a width cap that steps L down one size
  on narrow screens before the stage would lose its target. A third scare — the same
  RangeError reappearing after the fix — turned out to be the test browser serving
  stale cached HTML; a cache-busted reload showed zero errors and no code change was
  needed. (3) The screenshots exposed the corner MENU button covering header text —
  the tagline and hint tails at 360 px, and on narrow phones the BEST chip too;
  fixed with the `--menu-reserve` right padding, a title that truncates before the
  chips move, and a compressed row under 440 px, re-verified over the whole matrix.
  (4) A final hand-over pass found the title still truncated at 390-430 px because
  the compact row only applied below 380 px; the breakpoint was raised to 440 px and
  all eight titles re-measured from 280 to 600 px (full names from 360 px up).

### Documentation review/edit attempts (standing rule)

- 2026-11-03 — Qwen3.8-Flash (Qoder CLI), P-17 build: completed. README gained one
  sentence (R1) and the "Current build" line; CONTROLS was rewritten for the menu, the
  M key and PAD SIZE with "Applies to" 017-20261103; CHANGELOG received this new entry
  and the Conventions edits quoted above, nothing else; MODELS gained "How this
  project is paid for" and "Usage meters explained" above the Usage ledger, one
  ledger row and the recomputed totals plus the two new totals lines; the plan gained
  one ledger row, one tool-log row and the roadmap; LICENSE is byte-identical; no
  section was deleted, shortened or restructured. Results in
  `tests/build-017-report.md`.

### Addendum — final session figures and hand-over (added after the Qoder trial ended)

- The session above ran until the Qoder trial's credit limit was reached. The figures
  in the Build record (52.7558 credits / 104 requests at 17:49 WIB) are a mid-session
  snapshot; the final verification loop ran after they were written.
- **Owner-supplied Qoder exit report for this session:** plan credits used **300/300**;
  session credits used **300.8933**; wall time **1 h 38 min 49 s** (5,810.5 s); agent
  active **1 h 13 min 18 s**; API time **44 min 26 s**; tool time **28 min 51 s**;
  **398 tool calls** (397 succeeded); code changes **+1,041 / −104** lines.
- These are Qoder's own meter readings and are **not tokens**. The 300.8933 figure is
  a different meter reading from the per-request transcript total (52.7558) and is not
  added to the usage ledger; both are recorded rather than guessing which unit to keep.
- Trial end date: **2026-11-15 at 15:24:49 GMT+7**.
- **Hand-over:** the work copies were complete and verified when the trial ran out.
  The swap into the live files, the post-swap checks, this addendum, the build report
  and the P-17 prompt copy were finished by **DeepSeek V4.1 Flash Free (OpenCode)**.
  The build itself remains attributed to Qwen3.8-Flash (Qoder CLI).
- The hand-over pass also fixed one real defect found in the screenshots: the game
  title still truncated at 390-430 px because the compact top row only applied below
  380 px. The breakpoint is now 440 px; all eight titles fit from 360 px up.

### Addendum 2 — hand-over task, time and tokens (added while completing the MODELS record)

- **Task:** finish build 017 after the Qoder trial ran out — verify the work copies,
  fix the title breakpoint, swap the six work files into the live files in one step,
  re-run the checks, write `tests/build-017-report.md` and the P-17 prompt copy, and
  update CHANGELOG.md and MODELS.md.
- **Model and tool:** DeepSeek V4.1 Flash Free (OpenCode).
- **Duration:** about **25 min** wall-clock (2026-11-03, 19:05-19:30 WIB).
- **Usage:** **165,312 tokens processed** (116,561 input + 23,506 output + 25,245
  reasoning), **107 assistant turns**, measured from the session's per-message token
  telemetry; 11.82 M cached reads are not counted. No credits were used (OpenCode free
  model). This is a token count, not a Qoder credit count, and it is never added to the
  credit totals in MODELS.md.
- **Result:** live files at `017-20261103`; all eight game IIFEs hash-identical to build
  016; docs 26/26 at the swap and **27/27** after the MODELS append (the harness gained a
  separate check that the old dated entries stay a byte-identical prefix); focused
  20-viewport check 1,184 checks / 0 fails; live render check 175 checks / 0 fails; 12
  screenshots retaken and looked at.
- **Git:** no git command was run. The suggested commands in
  `tests/build-017-report.md` are suggestions only, now and always.
- **Test-matrix highlight (owner request, after the hand-over):** README gained a short
  "How the builds are checked" section and MODELS gained a dated owner observation
  recording that the viewport matrix started with **build 009** (prompt P-09, authored by
  Claude.ai Sonnet 5.5 Extra and executed by Qwen3.8-Flash): 24 viewports, 1,409 automated
  assertions and 120 screenshots, later reused in build 017's 20-viewport run. The record
  is kept as a quality highlight of self-testing and validation.

## 016-20261102 — 2026-11-02 (Round 8: CATNAPCATCH)

Built from prompt: P-16 (the owner's Round 8 request for CATNAPCATCH, pasted verbatim,
typos included; private archive file `prompts/P-16_catnapcatch.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
Games in the one file: 8 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101 **frozen**, HUGPARADE
015-20261102 (unchanged this build), CATNAPCATCH 016-20261102; file build
**016-20261102**)

### Added — CATNAPCATCH, the eighth game (deploy/index.html, PART 5-H)

- A new sealed IIFE before PART 6, registered in `GAMES` as `CATNAPCATCH`, content
  `016-20261102`: Mochi, a butter-ginger kitten, sleeps on a floor cushion in a night
  nursery while a paper pillow slides under the shelf to catch falling noisemakers.
- Play: the pillow moves only left and right, at 62 px/s within x 16–84. Four
  noisemakers (alarm clock, jingle bell, tin pot, toy block) drop from y 29 at a speed
  that ramps from 28 to 40 px/s; the spawn gap tightens from 1.55 s to 0.82 s over the
  round. A catch at y 60 scores **+1** (the tracked quantity is catches). A miss at
  y 82 costs one of three clang slots; the third clang ends the run. The round lasts
  **45 s**. The one action is **POUF**: it widens the pillow from half-width 10 to 16
  for 1.4 s on a 4.5 s cooldown, so a catch window of ±13 px becomes ±19 px.
- Art: a 100×100 night nursery — striped violet wall with 16 deterministic stars, a
  round window with a crescent moon and four panes, a fish picture, a wooden shelf
  with books, a jar and a block, warm floorboards, a lavender rug, a mint cushion, and
  Mochi in a ginger coat with cream muzzle and paws, closed happy eyes, blush and a
  curled tail. The paper pillow has a centre crease, seam stitches and fluff corners
  when puffed. Items fall with a one-pixel streak; catches make a spark burst, a ring
  and a rising `+1`; clangs shake the cat, show a `!` bubble and spray sparks on the
  floor. Zzz drift above the sleeper.
- HUD: a plate at the top shows `TIME n` and `CATCH n`, three bell pips for the quiet
  slots remaining, `POUF` and five cooldown pips. The title plate states the rules
  (`CATCH THE CLATTER`, `EACH CATCH +1`, `3 CLANGS END THE NAP`, `POUF MAKES IT
  BIGGER`), and the game-over plate reads `CLATTER TOO LOUD` or `THE NAP HELD`, the
  catch count, and `BEST n`.
- Shelf preview: a private 200×96 `paintCatnapCatchPreview` with the night wall, moon
  window, loaded shelf, three falling items with streaks, the rug, cushion, Mochi and
  the pillow, plus drifting Zzz.
- Best catches are stored under `KANTMICROGAMES.CATNAPCATCH.best`. This is a new key,
  so no migration is needed. Desktop hint: `A` and `D` slide the pillow, `SPACE` or a
  stage tap puffs it wider, `R` restarts, `ESC` returns to the shelf.

### Changed — build identity and index notes (deploy/index.html)

- `APP.fileVersion` is `016-20261102`; the header "Current" line names Round 8,
  CATNAPCATCH and eight games, and "Build log" names this build. The footer follows
  `APP.fileVersion` and reads `KANTMICROGAMES — build 016-20261102`.
- READ ME FIRST now introduces eight modules and adds the
  `CATNAPCATCH -> cat / CAT_*` prefix rule. Its frozen list records that build 016 left
  all six frozen modules byte-identical and left HUGPARADE unchanged at content
  `015-20261102`; the numbering note records CATNAPCATCH as new at 016. The PART 5
  boundary note marks CATNAPCATCH live at content 016-20261102.

### Note — legibility and HUD choices found in review

- The shared 3×5 pixel font's `W` is hard to read at scale 1 (it reads as an `M`), so
  CATNAPCATCH's on-canvas strings avoid `W`: the title says `3 CLANGS END THE NAP` and
  `POUF MAKES IT BIGGER`, and the clang ending says `CLATTER TOO LOUD`. The shared font
  was **not** changed, because that would alter frozen games' text (SPROUTUP uses it).
- The three bell pips show **quiet slots remaining** (three gold at the start, one
  dimmed per clang), not a tally of clangs. The first draft lit them as clangs arrived,
  which read as empty lives on the title-to-play swap; the remaining-slots reading is
  the one that matches "3 CLANGS END THE NAP".
- A rising `+1` was added after the first play captures showed that the spark burst alone
  was easy to miss; the coin-sized pop makes each catch legible without adding sound.

### Changed — public and private records

- README: "Eight tiny…", current build `016-20261102` — eight games, CATNAPCATCH added
  to the games table, Qwen3.8-Flash's builds cell gains 016 and now says four new
  games. Nothing else changed.
- CONTROLS: "Applies to" is build `016-20261102 · eight games`; the guide and the table
  now say eight; the table gains the CATNAPCATCH row (**POUF**, 1.4 s on a 4.5 s
  cooldown, catches in 45 s with three clang slots); the action-label list adds POUF;
  one sentence records that CATNAPCATCH uses the horizontal axis only (up and down do
  nothing).
- MODELS: one new Usage ledger row for 016, with the totals and bars recomputed from
  the final Build record. No observation entry was added because the owner supplied no
  new observation this round.
- plans/micro-games-v2.md: one ledger row, one tool-log row, and the CATNAPCATCH
  backlog row moved from `backlog` to "in the file (round 8)" with the shipped rules.
- prompts/P-16_catnapcatch.txt saved with the owner's request verbatim; verification
  in `tests/build-016-catnapcatch.md`, with eleven screenshots under
  `tests/screenshots/build-016/`; pre-edit snapshot and hashes in
  `plans/archive/pre-016/`.

### Verification and limits

- **Frozen modules:** each IIFE hashed as the exact `(function () {` … `})();` block
  with no trailing newline. PANDASNACK `f6dd1614…`, BOOPEEK `f3212979…`, DUCKLINE
  `6a62f23a…`, SPROUTUP `adff7441…`, SLIMEHOP `a92efde4…`, SNAILRACE `457fa4b4…` —
  all equal to build 015. HUGPARADE is unchanged at `151deb6e…ddd12c65` (37,311
  characters). CATNAPCATCH's new IIFE is `26f6be1a…4a8ee78` (34,524 characters). Full
  hashes and character counts are in the test report.
- **Code:** `node --check` on the extracted inline script clean; eight module IIFEs and
  eight `GAMES` registrations found; all five CATNAPCATCH sprite maps are 7×7; no
  `console.log` remains inside the page.
- **Render:** headless Chrome 156 at 1280×800 shows eight game cards plus COMING SOON,
  every preview at ratio 2.083, stage 600×600, no page scroll and zero console errors.
  At 390×844 DPR 2 with touch, the Catnap Catch card preview is 324.0×155.5
  (ratio 2.083), the stage is 300×300, the pads are 58 px, and the page does not scroll
  sideways.
- **Gameplay (23 assertions, 0 failures):** on an instrumented copy built from the
  final module, `SPACE` started from the title; real `D` and `A` moved the pillow and
  clamped at x 84 and x 16; a catch at the centre scored 1; a miss away from the
  pillow cost one clang and read "clang! 2 more and mochi wakes"; POUF caught an
  offset-15 item that a normal pillow would miss, ran 1.4 s, refused a second POUF
  during its 4.5 s cooldown, became ready again after it, and lasted 1.35 s on the
  second use; the third clang ended the run with `endReason` `clang`; real `R`
  restarted at score 0; the 45 s clock ended the run with `endReason` `time`; best 1
  was saved and survived a reload; `ESC` returned to the shelf.
- **Mobile touch:** real CDP touch opened the Catnap Catch card, a stage tap started
  the run, holding the left pad moved the pillow from 50 to about 18, and a stage tap
  started POUF (`poufT` 1.2 s, `readyT` 4.3 s). The pads and stage stayed inside
  390×844.
- **Limits:** headless Chrome only; no physical phone, Safari, Firefox or iOS/Android
  run. The Cloudflare site serves build 015 until the owner deploys build 016. No audio
  exists in the project, so none was tested.

### Build record (owner request: duration + tokens/credits)

- Duration: **about 15 min** wall-clock at the time this entry was written
  (2026-11-02, 21:37 → about 21:52 WIB, from the prompt paste to the records). The
  final figure is in the addendum below.
- Tokens: **not exposed by the tool.** Qoder reports a `credits` value per request, so
  the build records **8.4440 credits used across 162 billable requests**
  (21:37-21:52 WIB), summed from the per-request credits in the session transcript,
  deduplicated by `request_id`. Credits are not tokens, and no token number is
  invented.

### Documentation review/edit attempts (standing rule)

- 2026-11-02 — Qwen3.8-Flash (Qoder CLI), P-16 build: completed. README and CONTROLS
  edits are limited to the lines listed above; CHANGELOG received this new entry only;
  MODELS gained one ledger row and recomputed totals; the plan gained two rows and one
  updated backlog row; LICENSE is byte-identical; no section was deleted, shortened or
  restructured. The six frozen IIFEs and HUGPARADE were hashed, and CATNAPCATCH was
  hashed, after the code edits. Results in `tests/build-016-catnapcatch.md`.

### Addendum — 2026-11-02 (final figures after the records were saved)

The lines above were written at 21:52 WIB with the telemetry then available. The session's
final figures, taken at 21:55 WIB just before this addendum was written, are **10.2413
credits across 198 billable requests** (2026-11-02, 21:37-21:55 WIB), for a final duration
of **about 18 minutes**. The Usage ledger in `MODELS.md` uses these figures. Credits are
not tokens.

## 015-20261102 — 2026-11-02 (Round 7 fixes: HUGPARADE rails and hug scoring)

Built from prompt: P-15 (the owner's request to correct HUGPARADE before starting
CATNAPCATCH, pasted verbatim, typos included; private archive file
`prompts/P-15_hugparade-fixes.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
Games in the one file: 7 (PANDASNACK 007-20261101 **frozen**, BOOPEEK 006-20261101
**frozen**, DUCKLINE 005-20261101 **frozen**, SPROUTUP 007-20261101 **frozen**,
SLIMEHOP 010-20261101 **frozen**, SNAILRACE 011-20261101 **frozen**, HUGPARADE
015-20261102; file build **015-20261102**)

### Changed — HUGPARADE movement now runs on cell rails (deploy/index.html, PART 5-G)

- The owner reported that Momo could stick between maze walls and that movement was hard
  to steer. The cause was the continuous walk checked against wall rectangles with the
  player's circle: near a junction the sprite could be stopped by a wall it was not
  actually entering, and it never snapped to a corridor centre.
- Movement is now cell centre to cell centre. One press always completes one whole cell,
  even if the key is released early; a perpendicular press made mid-step waits and turns
  at the next centre; a new press during a step is remembered, not dropped. A step is
  blocked only when the hedge between the two cells is closed. There is no diagonal
  travel and no wedging, and the old circle-versus-wall test is removed.
- A maze redraw that comes due while Momo is between centres waits until the step lands,
  so a shift can never move the player mid-step or outside the hedges (the build-014
  post-redraw wall clearing is kept as a second guard).

### Changed — HUGPARADE objective and scoring (the tracked quantity is hug points)

- The score is now **hug points**: each hug scores **1 + one point for every heart held**,
  so 1 with no hearts, 2 with one, 3 with two and 4 with all three (the HUD shows this as
  `X1`–`X4` beside the time). Hearts no longer add points when collected; they are
  multipliers for the next hug, and they reset when the fresh layout appears after a hug.
  The 45 s round, the three hearts per layout, PEEK (2 s on a 6 s cooldown) and the 10 s
  maze shift are unchanged.
- The title plate now states the objective before play: `HUG BIBI +1`,
  `EACH HEART +1X`, `MAZE SHIFTS 10S`, `PEEK SEES AHEAD`, under the HUGPARADE name on
  the 100×100 canvas. The shell line under the canvas repeats the rule on the title and
  reports the bonus when a hug lands.
- The game-over plate now reads `HUG POINTS`, and the shell message reports "N hug
  points" instead of "N hugs", so the unit on screen matches what is counted.
- Best scores from build 014 used a 100+ scale and cannot be compared with the 1–4 scale.
  The first 015 launch writes `KANTMICROGAMES.HUGPARADE.best.epoch` = `015` and clears
  the old best once; later launches keep the 015 best. The save key itself is unchanged.
- The `hugCount` variable left over from build 014 is removed.

### Note — owner observation (recorded in MODELS.md as a dated entry)

- The owner's note: the first HUGPARADE build is amazing work for Qwen and Qoder, but it
  shipped logic problems (movement and unclear scoring) and needed correction. The full
  note, with the owner's words verbatim, is in `MODELS.md` above its entry marker.

### Changed — build identity and records

- `APP.fileVersion` is `015-20261102`; the header "Current" line names the Round 7 fixes
  and seven games, "Build log" names this build, and the numbering note records
  HUGPARADE as new at 014 and corrected at 015. The footer follows `APP.fileVersion`.
- README: "Current build" is `015-20261102`, the HUGPARADE pitch is rewritten for rails
  and the heart multiplier, and Qwen3.8-Flash's builds cell gains 015 with a note that
  015 corrected HUGPARADE's movement and scoring. Nothing else changed.
- CONTROLS: "Applies to" is build `015-20261102 · seven games`; the HUGPARADE row and
  the movement paragraph describe whole-cell rail steps, queued turns, hedge-only
  blocking and the 1-plus-hearts hug, replacing the continuous-walk sentence.
- MODELS: one new dated owner-observation entry above the marker, and one new Usage
  ledger row for 015 with the totals and bars recomputed from the final Build record.
- plans/micro-games-v2.md: one ledger row, one tool-log row, and the HUGPARADE backlog
  row now records rails, hug points and the title plate. CATNAPCATCH stays `backlog` for
  the next round.
- prompts/P-15_hugparade-fixes.txt saved with the owner's request verbatim; verification
  in `tests/build-015-hugparade-fixes.md`, with ten screenshots under
  `tests/screenshots/build-015/`; pre-edit snapshot and hashes in
  `plans/archive/pre-015/`.

### Verification and limits

- **Frozen six:** each IIFE hashed as the exact `(function () {` … `})();` block with no
  trailing newline. PANDASNACK `f6dd1614…`, BOOPEEK `f3212979…`, DUCKLINE `6a62f23a…`,
  SPROUTUP `adff7441…`, SLIMEHOP `a92efde4…`, SNAILRACE `457fa4b4…` — all equal to
  build 014, with unchanged character counts. HUGPARADE 015 is `151deb6e…ddd12c65`
  (37,311 characters, up from 34,568 in build 014). Full hashes in the test report.
- **Code:** `node --check` on the extracted inline script clean; seven module IIFEs
  found; no stale movement or scoring identifiers remain.
- **Movement:** one press moved exactly one cell (0,6) → (0,5) and ended at a centre; a
  press into a hedge changed nothing; a release mid-step still finished the step; a
  perpendicular press during a step turned at the next junction (up then right reached
  (1,5)); a redraw forced mid-step left the walls unchanged until the step landed.
- **Scoring:** a hug with no hearts scored 1; with one heart 2; with three hearts 4
  (1 → 5 in one run); hearts reset after the hug; a heart pickup alone left the score
  unchanged; the round ended with the score and the message "2 hug points"; the best was
  saved as 2, the epoch key written as `015`, and a build-014 best of 132 was migrated
  to 0 exactly once.
- **Render:** headless Chrome 156 at 1280×800 shows seven cards plus COMING SOON, every
  preview at ratio 2.083, stage 600×600, no page scroll and zero app errors. At 390×844
  DPR 2 with touch, previews are 324.0×155.5 (ratio 2.083), the stage is 300×300, real
  touch opened the card, started the run, moved Momo one cell and used PEEK.
- **Limits:** headless Chrome only; no physical phone, Safari, Firefox or iOS/Android
  run. The Cloudflare site serves build 014 until the owner deploys build 015.

### Build record (owner request: duration + tokens/credits)

- Duration: **about 15 min** wall-clock at the time this entry was written
  (2026-11-02, 21:00 → 21:15 WIB, from the prompt paste to the records). The final
  figure is in the addendum below.
- Tokens: **not exposed by the tool.** Qoder reports a `credits` value per request, so
  the build records **6.9288 credits used across 121 billable requests** (21:00-21:15
  WIB), summed from the per-request credits in the session transcript, deduplicated by
  `request_id`. Credits are not tokens, and no token number is invented.

### Documentation review/edit attempts (standing rule)

- 2026-11-02 — Qwen3.8-Flash (Qoder CLI), P-15 build: completed. README and CONTROLS
  edits are limited to the lines listed above; CHANGELOG received this new entry only;
  MODELS gained one observation entry, one ledger row and recomputed totals; the plan
  gained two rows and one updated backlog row; LICENSE is byte-identical; no section was
  deleted, shortened or restructured. The six frozen IIFEs and HUGPARADE were hashed
  after the code edits. Results in `tests/build-015-hugparade-fixes.md`.

### Addendum — 2026-11-02 (final figures after the records were saved)

The lines above were written at 21:15 WIB with the telemetry then available. The session's
final figures, taken at 21:16 WIB just before this addendum was written, are **7.8667
credits across 147 billable requests** (2026-11-02, 21:00-21:16 WIB), for a final duration
of **about 17 minutes**. The Usage ledger in `MODELS.md` uses these figures. Credits are
not tokens.

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
### A11 — CONTROLS.md passages removed in build 018

Moved from CONTROLS.md in build 018 — verbatim, not edited. The whole build-017
file is reproduced below so no removed passage is lost; the rewritten CONTROLS.md
is the current guide.

````markdown
<!-- Applies to: build 017-20261103 · eight games · changes to controls are recorded in CHANGELOG.md -->
# KANTMICROGAMES — Controls

Which controls exist, how they behave on each kind of device, and why.
This guide applies to all eight games, on every kind of device.

## One table for all eight games

| Game | Move | Action (`SPACE`, action pad, stage tap) | Goal |
|---|---|---|---|
| PANDASNACK | scurry with `W A S D` / arrows / the direction pad | **DASH** — 0.7 s at 1.75×, 2.2 s cooldown | munch bamboo, dodge wasps, keep three hearts |
| BOOPEEK | tiptoe with `W A S D` / arrows / the direction pad | **POKE** — 20 px reach, 0.1 s cooldown | poke Boo while he peeks; 10 in 20 s, then beat your score |
| DUCKLINE | swim with `W A S D` / arrows / the direction pad | **GO** — quack boost, 0.55 s at 1.7×, 2 s cooldown | gather three ducklings, reach the far bank in 22 s |
| SPROUTUP | weave with `W A S D` / arrows / the direction pad | **REACH** — leap burst, 0.5 s at 1.85×, 2 s cooldown | gather 15 drops in 24 s to bloom |
| SLIMEHOP | hop one pad per press with `W A S D` / arrows / the direction pad | **STOMP** — bloom the pad underfoot, 1.2 s cooldown, stuns a nearby snail | bloom all nine pads in 30 s before the snail eats them |
| SNAILRACE | steer with `W A S D` / arrows / the direction pad | **ZOOM** — 1.55× burst for 0.7 s, 2.6 s cooldown | reach the strawberry first in 20 s; lettuce boosts, salt locks |
| HUGPARADE | step cell to cell along the hedge rails with `W A S D` / arrows / the direction pad | **PEEK** — see the next hedges for 2 s, 6 s cooldown | gather up to three hearts, then hug Bibi: a hug scores 1 plus 1 per heart held; the maze redraws every 10 s |
| CATNAPCATCH | slide the pillow left and right with `A` / `D`, ← → or the direction pad | **POUF** — widen the paper pillow for 1.4 s, 4.5 s cooldown | catch falling noisemakers for 45 s; three clangs wake Mochi |

The action button carries the game's own label (DASH / POKE / GO / REACH / STOMP / ZOOM / PEEK / POUF),
so one pad serves every game. SLIMEHOP is the one game where a direction press is a single
**discrete hop** rather than a continuous walk: holding a direction does not repeat, and
each new press hops one pad (or bonks harmlessly at the pond edge). SNAILRACE steers
continuously on both axes; holding right and up moves diagonally with each axis at full
speed, so a lane change does not cost forward ground. HUGPARADE moves on cell rails
instead: every press carries Momo a whole cell, a release mid-step still finishes that
step at the next centre, a perpendicular press waits for the next junction, and only a
hedge blocks a step. It never moves diagonally, so Momo cannot wedge between two hedges.
CATNAPCATCH uses the horizontal axis only: left and right slide the paper pillow, and up
and down do nothing.

## Input devices

| Device | Move | Act | Menu / start / restart | Leave |
|---|---|---|---|---|
| Keyboard | `W A S D` or arrow keys | `SPACE` | `SPACE` / `ENTER` / any unmodified key starts the title card; `M` opens or closes the game menu; `R` restarts a run (from play or from the menu) | `ESC` (from the menu too) |
| Mouse | drag the direction pad (optional) | click the action button or the stage | click the card on the shelf; click `MENU`, then `RESTART` in the menu | click `MENU`, then `⌂ SHELF` in the menu |
| Touch / pen | thumb-drag the direction pad; slide from one arrow to the next without lifting | tap the action button or the stage | tap the card; tap `MENU`, then `RESTART` in the menu | tap `MENU`, then `⌂ SHELF` in the menu |
| Assistive tech | the pads are direct-manipulation only (see below); keyboard mappings still work | `SPACE` | `ENTER` on a focused card; `MENU` is a real button | `ESC` or `⌂ SHELF` in the menu |

## The game menu

The MENU button sits in the top-right corner of the game screen in both
orientations, with a three-bar pixel icon and the word MENU. It (or the `M` key)
opens a paused dialog with **RESUME**, **RESTART · R**, **⌂ SHELF** and the game's
own how-to line. Opening it pauses the run and releases every held direction.
RESUME, a tap outside the sheet, `M` (from the menu) close it and resume; focus is
trapped inside the sheet and returns to MENU on close. There are no loose
RESTART or shelf buttons in the play area any more — the corner MENU button and
the menu are the only chrome. The tap that closes the menu by landing outside the
sheet never reaches a pad, the stage or a card underneath.

Rules that apply everywhere:

- **One tap = one action.** A tap on the stage acts once (`onStageTap`). A drag on
  the stage does not act; a mouse drag that starts on a shelf card does not open it.
- **Drag does not leak.** After `⌂ SHELF`, a tap that ends where a card now sits does
  not open anything (a short ghost-click guard, and one tap must both start and end
  on the card).
- **Browser shortcuts pass through.** `Ctrl` / `Cmd` / `Alt` combinations are never
  consumed: copy, paste, reload, tab switching and OS gestures reach the browser.
  Tab, CapsLock, the modifier keys and F1–F12 are never treated as "any key".
- **Arrows and Space do not scroll the page** while a game is open.

## On-screen pads

The direction cluster and the action button appear when the last real
input was touch or pen. If the last input was a key or the mouse they hide, giving
the stage the whole screen. The circle in the middle of the direction cluster is
empty: sliding across it keeps the current direction instead of releasing it.

| Preference | Values | Effect |
|---|---|---|
| `PADS` | **AUTO** (default) · **SHOW** · **HIDE** | AUTO follows the last input type; SHOW always shows the pads; HIDE hides them even in touch mode (the stage and the keyboard still work) |
| `DIR PAD` | **LEFT** (default) · **RIGHT** | puts the direction cluster and the action column on opposite sides — in landscape beside the stage, in portrait within the controls row |
| `PAD SIZE` | **M** (default) · **S** · **L** | sets the touch-pad size: S = 58 px, M = 66 px, L = 76 px; the action button is 1.7 x the pad size. On small screens (≤ 380 px wide or ≤ 620 px tall) the sizes are 48 / 56 / 64 px |

All three preferences sit on the shelf under the how-to chips, are announced with an
`aria-label`, and persist across reloads in `localStorage` under
`KANTMICROGAMES.ui.pads`, `KANTMICROGAMES.ui.hand` and `KANTMICROGAMES.ui.padsize`.
To reset them, clear those keys (or all `KANTMICROGAMES.*` keys) in the browser's
site data. Best scores use the same prefix: `KANTMICROGAMES.<GAME>.best`.

Pads and buttons are at least **48 × 48 CSS px** at every viewport. The direction
pads keep a 9 px gap (8 px on small screens) and the action button sits 24 px from
the direction cluster. On viewports narrower than 416 px the L size renders one
step down (66 px, then 56 px below 357 px) so the pads never crowd the stage or
each other.

### Why the pads are not Tab stops

The four direction buttons and the action pad use `tabindex="-1"` on purpose.
They are held controls, not buttons you press once: tabbing to them would add five
stops in front of the menu button and would not let a keyboard user hold a direction.
Every pad action has a keyboard equivalent (`W A S D` / arrows, `SPACE`), so the
game is fully operable from the keyboard without them. The tab order is kept
short and predictable: shelf cards and preferences on the shelf, then the MENU
button in a game (and the three menu buttons while the menu is open).

## Pause

A game pauses when the tab is hidden, the window loses focus, or the page is being
put away (`visibilitychange`, `blur`, `pagehide`). Every held direction is released
first, so nothing runs into a wall while the phone rings. A `PAUSED` plate appears
over the stage.

The next tap or key press only resumes: it is swallowed, so you cannot dash or poke
straight out of a pause. `M` opens the menu while paused (it also works from the
menu). `ESC` still leaves to the shelf while paused. While the menu is open the
sheet replaces the `PAUSED` plate; behind it the game stays paused.

## Layout and scaling

- The stage keeps its 100 × 100 design pixels and is scaled "crisp+": the shell
  computes whole device pixels per art pixel from the room available and the
  device pixel ratio (about 2×–10× on today's phones), and only falls back to a
  fractional scale when the whole-number result would be under 2× — very short
  landscape phones. Canvas edges land on whole device pixels; the canvas is never
  stretched with a CSS transform.
- The shell measures the room left by the header, the hint and the controls in
  both layouts, picks the layout that yields the bigger stage, and only then sizes
  the canvas. Portrait screens put the stage on top and one controls row below;
  landscape screens put the direction cluster and action column beside the stage.
- During play the page never scrolls: the shell is exactly one viewport tall
  (`100dvh` with a `100vh` fallback), uses `overscroll-behavior: none`, and gives
  the stage and pads `touch-action: none` so a swipe cannot drag or pull-to-refresh
  the page. The shelf still scrolls normally, and the page keeps
  `touch-action: manipulation` so double-tap zoom is not triggered on chrome.
- Safe areas (`env(safe-area-inset-*)`) are applied as padding on the page and the
  top bar, so notches, rounded corners and the home-indicator strip never cover a
  control.
- **Page zoom is allowed** (the viewport meta has no `maximum-scale` and no
  `user-scalable=no`), so a player who needs it can pinch-zoom the shelf and the
  chrome.

## Accessibility

- Visible focus ring (`:focus-visible`) on shelf cards, preference buttons, the
  MENU button and the menu buttons.
- Cards are real buttons with an accessible name; `ENTER` and `SPACE` open them.
- The game menu is a labelled dialog (`aria-modal`) whose buttons are real buttons;
  focus is trapped inside while it is open and returns to MENU on close.
- Stage messages (`#msg`) are a polite live region, so screen readers hear
  "PAUSED", "GAME OVER" and similar shell-level text.
- Prefers-reduced-motion turns off the card lift, chip pulse and button press
  transforms.

## Known control quirks

- The frozen modules still carry their original desktop hint strings. The shell
  strips the `desktop:` prefix for the keyboard hint and writes its own touch
  line from the game's action label, so no game code had to change.
- HIDE hides the action button as well as the direction pad. On a touch-only
  device the action is still available by tapping the stage.
- PAD SIZE only resizes the touch pads; keyboard play is unchanged. On the
  narrowest widths the L choice renders one step down (see the pad table above)
  so the action button keeps its 24 px gap instead of wrapping.
- Below 360 px wide the game title in the top row truncates with an ellipsis
  so SCORE and BEST stay clear of the corner MENU button; from 360 px up the
  full name fits. The full name is also on the shelf card and in the browser tab.
- The mascot animation and the shelf's hover lift are decorative only; they are
  disabled under reduced motion and do not affect play.
````

### A12 — CONTROLS.md sentences removed in build 019

Moved from CONTROLS.md in build 019 — verbatim, not edited.

From § Controls on the game screen:

> The title, SCORE and BEST sit to their right in one slim row; the tagline and hint step out of the way when they would crowd the stage.

From § Layout and scaling:

> The shell measures the room left by the header, the hint and the controls in both layouts, picks the layout that yields the bigger stage, and only then sizes the canvas.

### A13 — README section and CONTROLS sentence removed in build 020

Moved from README.md § How the builds are checked and from CONTROLS.md in build 020 — verbatim, not edited.

From README.md § How the builds are checked:

## How the builds are checked

Since build 009, each shell change is checked against a viewport test matrix before it ships: a list of screen sizes from small phones to wide desktops, with automated layout checks and screenshots inspected by eye. The matrix began with the responsive-shell rebuild (prompt P-09, written by Claude.ai Sonnet 5.5 Extra and run by Qwen3.8-Flash): 24 viewports, 1,409 automated checks and 120 screenshots. Build 017 reused it as a 20-viewport check (1,184 checks) and found a real title-truncation defect at 390–430 px that the numbers alone had missed. The point is simple: measure every size, look at the pictures, and fix what the measurements do not show.

From CONTROLS.md § Known control quirks (first bullet):

- The shell writes its own hint line from the game's action label, so the frozen
  modules' original desktop hint strings are not shown. No game code had to change.
