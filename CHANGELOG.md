# KANTMICROGAMES — Changelog

A short record of every build, newest first. Each entry gives the build ID, the prompt, the model and tool, and what changed. Time and usage for every build are in the Usage ledger in MODELS.md. The long-form build records are kept in the author's private archive.

- **Build IDs are `NNN-YYYYMMDD`:** a zero-padded build number, then the date. A game's version number is the build where its content last changed.
- **The project name is `KANTMICROGAMES`.** Entries up to build 009 used older singular spellings; they are historical records and are not rewritten.
- **Corrections are dated, not silent.** A wrong past record is corrected by a dated line that names the build that corrected it.
- **Corrected in build 028:** 13 lines in entries 000 to 018 were cut off mid-sentence when this record was made in build 027; they were restored in full from the private record. (The build 028 prompt expected 15: entries 001 and 000 were named too, but their lines were already whole, so nothing there needed changing.)

<!-- NEW ENTRIES: paste the newest short entry on the line below this comment, above the previous newest. Never edit older entries except to add a dated correction line in the header. -->

## 030-20261114 — 2026-11-14 (PENGUINSLIDE syntax repair restores app startup)

Built from prompt: P-30 (repair the broken index page; the owner unfreezes PENGUINSLIDE)  
Tool and model: **GPT-6** (Codex); effort not visible  
What changed: fixed a missing comma in PENGUINSLIDE's settings object. The syntax error stopped the shared page script from loading, so the shelf and game controls did not initialize.  
Games changed: PENGUINSLIDE v2 (frozen build 030-20261114)  
Checked: inline JavaScript syntax and project checker passed on the work copy  
Not checked: interactive browser play, Safari, real phone or sound  
Time and usage: under 10 min; not recorded — time only

## 029-20261114 — 2026-11-14 (PENGUINSLIDE: ninth game with slide-and-push ice puzzle)

Built from prompt: P-29, authored by Claude.ai Sonnet 5.5, effort High (pasted verbatim by the owner)
Tool and model: **Mistral Medium 3.5 High** (Vibe CLI); effort High
What changed: new game PENGUINSLIDE added — Pip the penguin slides on ice tiles and pushes ice blocks to build a path to a frozen fish within 60 seconds, score equals remaining time. The badge count now reflects nine games. No existing game changed.
Games changed: PENGUINSLIDE v1 (new, frozen build 029-20261114)
Checked: V1-V4 pending (check script, node --check, hashes, readable counts to be verified); V5 not run (browser checks pending)
Not checked: Safari, real phone, sound test; full readable compliance has known exceptions to be listed
Time and usage: about 60+ min; Last Turn Tokens: ~96.3k (96,334 total, 95,104 cached); Session Total: ~35.1M LLM tokens; Cost: ~$6.62; Model: Mistral Medium 3.5 via mistral provider

## 028-20261114 — 2026-11-14 (Handbook v2 and game identity: ALL-CAPS names, revisions, checked rules)

Built from prompt: P-28, authored by Claude.ai Sonnet 5.5 at High effort and pasted verbatim by the owner (handbook v2 and game identity)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort High  
What changed: game names now show in ALL CAPS on the shelf and in play; each game records a revision number and a small identity line shows it with the game's frozen build when the screen has room; the build rules moved into a checked handbook and the public changelog's cut-off lines were restored. No game changed.  
Games changed: none (all eight game modules are byte-identical to build 027)  
Checked: V1-V7 passed: eight module hashes unchanged, both inline scripts parse, the check script prints 12 of 12 PASS on the mirror and live trees, the readable counts are zero, 13 changelog lines matched the frozen full copy, and the browser checks passed at 7 viewports x 8 games with the identity line shown only at 1280x800 and 1920x1080.  
Not checked: no Safari, real phone or sound test; the identity line was checked in headless Chrome only; the new rules, check script and templates have not yet been used by a cold model.  
Time and usage: about 26 min; 303,053 tokens processed

## 027-20261114 — 2026-11-14 (Records: a short public changelog; long-form records kept private)

Built from prompt: P-27 (records split: a short public changelog and private long-form build records)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort High  
What changed: the public changelog is now a short record of every build and the long-form records moved to the author's private archive; no game, control, layout or sound changed.  
Games changed: none (all eight game modules are byte-identical to build 026)  
Checked: V1-V6 passed: eight module hashes unchanged, both inline scripts parse, one headless load at 360x640 with 0 console errors, 28 short entries, the full-copy hash matched, and the docs diffs touched only the listed spots.  
Not checked: no Safari, phone or sound test; the two-record flow has not yet been used by a cold model.  
Time and usage: about 6 min; 117,458 tokens processed

## 026-20261113 — 2026-11-13 (Freeze the last two games, and the agent handbook)  
Built from prompt: P-26, authored by Claude.ai Sonnet 5.5 Extra and pasted verbatim by the owner (freeze the last two games and write the agent handbook; private archive file `prompts/P-26_freeze-and-handbook.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode), effort High  
What changed: Added — the last two games are FROZEN (deploy/index.html, comment text only)  
Time and usage: See the Usage ledger in MODELS.md, build 026.

## 025-20261113 — 2026-11-13 (Reset my data: a two-step erase in settings)  
Built from prompt: P-25, authored by Claude.ai Sonnet 5.5 Extra and pasted verbatim by the owner (reset my data: a two-step erase in settings; private archive file `prompts/P-25_reset-my-data.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
What changed: Added — DATA row and two-step reset (deploy/index.html, settings only)  
Time and usage: See the Usage ledger in MODELS.md, build 025.

## 024-20261110 — 2026-11-10 (Badges: eight shell-level badges with pixel icons)  
Built from prompt: P-24, authored by Claude.ai Sonnet 5.5 Extra and pasted verbatim by the owner (badges: eight shell-level badges with pixel icons, a BADGES button and dialog, and a new-badge note; private archive file `prompts/P-24_badges.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
What changed: Added — badge data and rules (deploy/index.html, shelf and runtime only)  
Time and usage: See the Usage ledger in MODELS.md, build 024.

## 023-20261109 — 2026-11-09 (Shelf helpers: times opened, sort row, pick of the day)  
Built from prompt: P-23, authored by Claude.ai Sonnet 5.5 Extra and pasted verbatim by the owner (shelf helpers: times opened, sort row, pick of the day; private archive file `prompts/P-23_shelf-helpers.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
What changed: Added — times opened (deploy/index.html, shelf only)  
Time and usage: See the Usage ledger in MODELS.md, build 023.

## 022-20261107 — 2026-11-07 (Sound effects, a SOUND setting, and record corrections)  
Built from prompt: P-22, authored by Claude.ai Sonnet 5.5 Extra and pasted verbatim by the owner (sound effects, a SOUND setting, and record corrections; private archive file `prompts/P-22_sound-and-record-corrections.txt`)  
Tool and models: **Gemini 3.8 Flash (Medium)** (Antigravity) started the build at 22:18 WIB and halted at STEP 4 at about 22:53 WIB when it ran out of tokens. **DeepSeek V4.1 Flash Free** (OpenCode) verified the work copies, ran STEP 5, swapped the files in and wrote most of STEP 6 (23:04-23:32 WIB), then stopped during the docs check when it ran out of tokens; a second OpenCode run finished the docs check and the records on 2026-11-08  
What changed: Added — sound effects (deploy/index.html, shell Web Audio API only)  
Time and usage: See the Usage ledger in MODELS.md, build 022.

## 021-20261107 — 2026-11-07 (Settings and background colour: shelf-only dialog, six palettes; no game change)  
Built from prompt: P-21 (settings panel and background colour; shell only; private archive file `prompts/P-21_settings-and-colour.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
What changed: Added — background palettes (deploy/index.html, shell CSS only)  
Time and usage: See the Usage ledger in MODELS.md, build 021.

## 020-20261106 — 2026-11-06 (Documentation repair: README, CHANGELOG, MODELS, CONTROLS, plan; no game change)  
Built from prompt: P-20 (the owner's documentation-repair prompt; private archive file `prompts/P-20_docs-repair.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
What changed: Changed — documentation only; no game, layout or behaviour changed  
Time and usage: See the Usage ledger in MODELS.md, build 020.

## 019-20261106 — 2026-11-06 (Stage stability and crisp sizing: no idle vibration, whole-device-pixel cap)  
Built from prompt: P-19 (the owner's stage-stability and crisp-sizing prompt; private archive file `prompts/P-19_stage-stability.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
What changed: Fixed — the stage no longer vibrates at idle (F1)  
Time and usage: See the Usage ledger in MODELS.md, build 019.

## 018-20261104 — 2026-11-04 (Controls and top bar: pinned SHELF/RESTART, fixed pixel labels, no menu)  
Built from prompt: P-18 (the owner's controls-and-top-bar prompt; its text said "build 019" and "currently build 018", but the repo was at build 017 with no 018 anywhere, so the owner confirmed this run is build 018; private archive file `prompts/P-18_controls-and-top-bar.txt`)  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode)  
What changed: Removed — MENU and the three pad options (deploy/index.html, PART 3 + PART 4)  
Time and usage: See the Usage ledger in MODELS.md, build 018.

## 017-20261103 — 2026-11-03 (Shell UX and process: MENU, PAD SIZE, crisp+ stage, tidy shelf)  
Built from prompt: P-17 (a process-and-shell prompt authored by Claude.ai Sonnet 5.5 Extra, pasted verbatim with the owner-notes fields left blank; private archive file `prompts/P-17_shell-ux-and-process.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
What changed: Changed — shelf cards align (deploy/index.html, PART 3)  
Time and usage: See the Usage ledger in MODELS.md, build 017.

## 016-20261102 — 2026-11-02 (Round 8: CATNAPCATCH)  
Built from prompt: P-16 (the owner's Round 8 request for CATNAPCATCH, pasted verbatim, typos included; private archive file `prompts/P-16_catnapcatch.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
What changed: Added — CATNAPCATCH, the eighth game (deploy/index.html, PART 5-H)  
Time and usage: See the Usage ledger in MODELS.md, build 016.

## 015-20261102 — 2026-11-02 (Round 7 fixes: HUGPARADE rails and hug scoring)  
Built from prompt: P-15 (the owner's request to correct HUGPARADE before starting CATNAPCATCH, pasted verbatim, typos included; private archive file `prompts/P-15_hugparade-fixes.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
What changed: Changed — HUGPARADE movement now runs on cell rails (deploy/index.html, PART 5-G)  
Time and usage: See the Usage ledger in MODELS.md, build 015.

## 014-20261102 — 2026-11-02 (Round 7: HUGPARADE)  
Built from prompt: P-14 (the owner's Round 7 request for HUGPARADE, pasted verbatim, typos included; private archive file `prompts/P-14_hugparade.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
What changed: Added — HUGPARADE, the seventh game (deploy/index.html, PART 5-G)  
Time and usage: See the Usage ledger in MODELS.md, build 014.

## 013-20261102 — 2026-11-02 (usage ledger, copyright and README fixes)  
Built from prompt: P-13 (the owner's usage-ledger and consistency request, written by Claude.ai Sonnet 5.5 Extra and pasted verbatim; private archive file `prompts/P-13_usage-ledger-and-fixes.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
What changed: Added — Usage ledger in MODELS.md  
Time and usage: See the Usage ledger in MODELS.md, build 013.

## 012-20261101 — 2026-11-01 (documentation restructure)  
Built from prompt: P-12 (the owner's docs-restructure request, written by Claude.ai Sonnet 5.5 Extra and pasted verbatim; private archive file `prompts/P-12_documentation-restructure.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)**  
What changed: Changed — documentation restructure (no game changes)  
Time and usage: See the Usage ledger in MODELS.md, build 012.

## 011-20261101 — 2026-11-01 (Round 6 — SNAILRACE, SPROUTUP + SLIMEHOP frozen)  
Built from prompt: P-11 (the owner's Round 6 request, saved verbatim in `prompts/P-11_snailrace.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in changelog, README, plan, MODELS.md and the prompt copy  
What changed: Added — SNAILRACE module (PART 5-F)  
Time and usage: See the Usage ledger in MODELS.md, build 011.

## 010-20261101 — 2026-11-01 (SLIMEHOP + KANTMICROGAMES rename)  
Built from prompt: P-10 (the owner's Round 5 request, saved verbatim in `prompts/P-10_slimehop.txt`)  
Tool and model: **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in changelog, README, plan, MODELS.md and the prompt copy  
What changed: Added — SLIMEHOP module (PART 5-E)  
Time and usage: See the Usage ledger in MODELS.md, build 010.

## 009-20261101 — 2026-11-01 (responsive shell)  
Built from prompt: P-09 (responsive shell — phones, tablets, foldables, desktops); the prompt was **authored by Claude.ai Sonnet 5.5 Extra** and is saved unaltered in `prompts/P-09_responsive-shell.txt`  
Tool and model: **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in changelog, README, plan, MODELS.md and the prompt copy  
What changed: Changed — shelf (F1, F2, F3)  
Time and usage: See the Usage ledger in MODELS.md, build 009.

## 008-20261101 — 2026-11-01 (documentation cleanup)  
Built from prompt: P-08 (documentation cleanup — links, `deploy/` move, MIT license, model links, GPT-OSS attempt recorded)  
Tool and model: **Claude Opus 4.6 Thinking (Antigravity)**, completed by **Qwen3.8-Flash (Qoder CLI)** — recorded per the owner's standing request in changelog, README, plan and prompt copies  
What changed: Added — project links  
Time and usage: See the Usage ledger in MODELS.md, build 008.

## 007-20261101 — 2026-11-01 (Round 4 — SPROUTUP)  
Built from prompt: P-07 (Round 4 — SPROUTUP module, BOOPEEK freeze, PANDASNACK in-stage live HUD score tracking & refreeze)  
Tool and model: **Gemini 3.8 Flash (Antigravity)** — recorded per the owner's standing request in changelog, README, plan and prompt copies  
What changed: Added — SPROUTUP module (Round 4, content 007-20261101)  
Time and usage: See the Usage ledger in MODELS.md, build 007.

## 006-20261101 — 2026-11-01 (final special review)  
Built from prompt: P-06 (final special review before Round 4 — numbering, record correction, DuckLine freeze, BooPeek variability)  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode) / Gemini 3.8 Flash (Antigravity)** — recorded per the owner's standing request in changelog, README, plan and prompt copies (DeepSeek drafted the refactor and hit token limits; Gemini 3.8 Flash reviewed, verified and completed documentation)  
What changed: Changed — build numbering (retroactive)  
Time and usage: See the Usage ledger in MODELS.md, build 006.

## 005-20261101 — 2026-11-01 (pre-Round-4 cleanup)  
Built from prompt: P-05 (special in-between cleanup before Round 4 — docs, art, module independence)  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode)** — recorded per the owner's standing request in changelog, README, plan and prompt copies  
What changed: Changed — BOOPEEK re-skin (content 005-20261101)  
Time and usage: See the Usage ledger in MODELS.md, build 005.

## 004-20261101 — 2026-11-01 (superseded by -005 for the file build and for BOOPEEK/DUCKLINE art)  
Built from prompt: P-04 (Round 3 — DUCKLINE module add, the duck-family micro game)  
Tool and model: Flint 40B Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
What changed: Added — Added the DUCKLINE module as the third game inside the one-file app (module content 004-20261101): a mother duck crosses the pastel pond with three ducklings in a waddling line behind her (WASD…  
Time and usage: See the Usage ledger in MODELS.md, build 004.

## 003-20261031 — 2026-10-31  
Built from prompt: P-03 (Round 2 — BOOPEEK, the poke-the-ghost micro game)  
Tool and model: GLM-5.3-Flash Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
What changed: Added — Added BOOPEEK as the second game module inside the one-file app: a shy ghost peeks from a cozy door on a small floor-and-wall pastel stage, the visitor (the panda mover) walks up with WASD and pokes…  
Time and usage: See the Usage ledger in MODELS.md, build 003.

## 002-20261031 — 2026-10-31  
Built from prompt: P-02 (the one-file pivot)  
Tool and model: GLM-5.3-Flash Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
What changed: Added — Added the one-file architecture: the arcade shelf and the game view are two screens that swap inside a single `index.html` — no navigation, no iframes, no game folders; the file build number steps to…  
Time and usage: See the Usage ledger in MODELS.md, build 002.

## 001-20261031 — 2026-10-31  
Built from prompt: P-01  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode)** — corrected in build 006; this build was originally recorded as GLM-5.3 Flash Free, but the owner confirmed it was made with DeepSeek V4.1 Flash Free  
What changed: Added — Added the first micro game, PANDASNACK: a chubby panda scurries on a tiny 100 x 100 design-pixel pastel meadow, munches two always-available bamboo shoots (each worth +1), and dodges drifting wasps…  
Time and usage: See the Usage ledger in MODELS.md, build 001.

## 000-20261031 — 2026-10-31  
Built from prompt: P-00 (Round 0 — project scaffold)  
Tool and model: **DeepSeek V4.1 Flash Free (OpenCode)** — corrected in build 006; originally recorded as GLM-5.3 Flash Free  
What changed: Added — Created the KANTMICROGAME project as the home for tiny, cute, pixel-art HTML5 micro games and the seven micro-game rules (single file, offline, tiny stage, pixel art, WASD touch controls, one…  
Time and usage: See the Usage ledger in MODELS.md, build 000.
