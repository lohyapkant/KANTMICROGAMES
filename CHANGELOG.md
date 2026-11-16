# KANTMICROGAMES — Changelog

A short record of every build, newest first. Each entry gives the build ID, the prompt, the model and tool, and what changed. Time and usage for every build are in the Usage ledger in MODELS.md. The long-form build records are kept in the author's private archive.

- **Build IDs are `NNN-YYYYMMDD`:** a zero-padded build number, then the date. A game's version number is the build where its content last changed.
- **The project name is `KANTMICROGAMES`.** Entries up to build 009 used older singular spellings; they are historical records and are not rewritten.
- **Corrections are dated, not silent.** A wrong past record is corrected by a dated line that names the build that corrected it.
- **Corrected in build 028:** 13 lines in entries 000 to 018 were cut off mid-sentence when this record was made in build 027; they were restored in full from the private record. (The build 028 prompt expected 15: entries 001 and 000 were named too, but their lines were already whole, so nothing there needed changing.)

<!-- NEW ENTRIES: paste the newest short entry on the line below this comment, above the previous newest. Never edit older entries except to add a dated correction line in the header. -->
## 039-20261116 — 2026-11-16 (CHASEKILLKANT v2: a clearer hallway and a five-line card)

Built from prompt: P-39, written by the owner with DeepSeek V4.1 Flash Free in OpenCode CLI and pasted verbatim after review (an art-and-teaching pass on the hallway: replace the blue-barrier read and teach crate from pot, with no gameplay change); prompt effort High  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort High  
What changed: CHASEKILLKANT v2 (frozen build 039-20261116), an art-and-teaching pass with zero gameplay change: the teal locker wall became two short runs of sage lockers with a wooden door between them, a skirting board, a warmer six-band floor whose boards widen toward the camera, two wall props (a NO RUNNING sign and a noticeboard with a pot poster and a crate poster), a dark pot rim, a gold-lidded crate and a blinking gold outline on the crate that arrives when the ammo runs out; the how-to card now teaches crate from pot in five lines (THROW AT KANT / FIVE HITS TO WIN / CATCH CRATES / DODGE THE POTS / TAP TO START); the shelf preview and the module banner match. The status bar, the shell and the other nine games are byte-identical; the play, the clock, the scoring and the difficulty are unchanged  
Games changed: CHASEKILLKANT v2 (frozen build 039-20261116)  
Checked: the fairness harness prints 1699 of 1699 assertions with the four skill bands unchanged to the digit (perfect and sharp 100 percent, regular 30 percent, rookie 12.5 percent); both inline scripts parse; readable-code counts are zero; the stage is identical at all seven named viewports; the hallway's worst saturation is 0.283 in both wall windows (limit 0.363); the pot rim is 71.6 percent darker than the floor and 86.1 percent darker than the wall; all nine other module hashes are unchanged; headless Chrome reports 0 console errors and 0 external requests; `check-project.py` prints 12 of 12 PASS on the mirror  
Not checked: no Safari, real phone or sound test; the art check is a self-review, not an owner approval; the rookie and regular difficulty gap stays open and reported  
Time and usage: about 31 min; 0.45 M tokens processed

## 038-20261115 — 2026-11-16 (CHASEKILLKANT: a hallway chase with thrown cutlery)

Built from prompt: P-38, written by the owner with DeepSeek V4.1 Flash Free in OpenCode CLI and pasted verbatim after review (add a tenth game, CHASEKILLKANT, and sweep stale counts out of the current-state docs); prompt effort High  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort High  
What changed: added CHASEKILLKANT as the tenth game (v1, frozen build 038-20261115): a warm school hallway where a girl seen from behind strafes along the bottom and throws forks, knives and scissors at Kant, who runs at the top, ducks after a glance and must be hit five times in sixty seconds. Pots drift down and daze her for 1.5 s; crates drift down and add one piece of cutlery to a shared count. A gold hint marks every punish window, and the how-to, win (KANT DOWN!) and lose (KANT LAUGHS AT YOU!) cards live inside the stage. The same build corrected stale game counts in the handbook, the conventions, the new-game guide, the prompt template, CONTROLS, README and the app header; a long game name now takes its own line in the phone header instead of being cut short  
Games changed: CHASEKILLKANT v1 (frozen build 038-20261115)  
Checked: both inline scripts parse (`node --check`); readable-code counts are zero; a headless fairness harness proves the 17-member contract, the how-to card text and action gate, and rules F1-F7 over 40 seeds and runs four seeded skill profiles (perfect 100 percent, sharp 100 percent, regular 30 percent, rookie 12.5 percent); `check-project.py` prints 12 of 12 PASS on the mirror; headless Chrome is stable at all seven named viewports with 0 console errors and 0 external requests  
Not checked: no Safari, real phone or sound test; the art check is a self-review, not an owner approval  
Time and usage: about 70 min (two sittings); 1,052,704 tokens processed

## 037-20261115 — 2026-11-15 (PENGUINSLIDE v9: Seal Patrol, a belly-slide dash and six fish)

Built from prompt: P-37, authored by the owner in the session (abandon the penguin-sliding puzzle for a mechanic where Pip moves, collects fish and faces a challenge; keep six fish to win as a start and add the second seal at fish three; then execute); the verbatim text was not preserved in the compressed session, so the prompt copy records the requirements and says so; prompt effort not recorded  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort not shown  
What changed: replaced the sliding-block puzzle with Seal Patrol. Pip waddles one tile per arrow or WASD press (holding the key repeats) and SPACE, the action button or a stage tap fires a two-tile belly-slide dash with a one-second recharge. One golden fish appears at a time on safe, reachable ice; eat six to win. Three hearts; a seal touch costs one heart, knocks Pip back one tile and gives 1.2 seconds of blinking safety. A second seal surfaces at fish three at the route point farthest from Pip, with a splash and a one-second wake-up, so it cannot ambush him. Two permanent two-tile bridges cross the river at rows 2 and 4; Seal A patrols the north bridge and Seal B the south. There is no clock: time only adds a shrinking bonus to the score (fish x100 + hearts x100 + seconds under 60 x5), and a lost run keeps its fish points. Fish spawns flood-fill from Pip, so a fish can never appear in an unreachable pocket. The how-to card reads EAT 6 FISH TO WIN / DODGE THE SEALS / SPACE TO BELLY-SLIDE / TAP OR PRESS A KEY; the result cards are FISH FEAST! and THE SEALS GOT YOU!, and the shelf preview shows the board, a bridge, Pip, a seal and the fish. A sharper seal sprite (head, eye, nose, forked tail and white belly) keeps the warm top-down look.  
Games changed: PENGUINSLIDE v9 (frozen build 037-20261115)  
Checked: both inline scripts parse (`node --check`); readable-code counts are zero; a headless logic harness proves the 17-member contract, the cards, spawn safety, seal bounds and the two-bridge fairness rule (both bridges never blocked at once for more than 3.07 s), and eight seeded bots each eat six fish and win; `check-project.py` prints 12 of 12 PASS on the mirror with `--unfrozen PENGUINSLIDE`; headless Chrome ran for real: the stage is stable at all seven named viewports, the title, play, win and lose screens were captured at 360x640@3 and 1280x800@1, a two-seal shot was captured, and there were 0 console errors and 0 external requests.  
Not checked: no Safari, real phone or sound test.  
Time and usage: about 52 min; 863,602 tokens processed

## 036-20261115 — 2026-11-15 (PENGUINSLIDE v8 rebuilt from scratch: a warm top-down 3/4 ice puzzle)

Built from prompt: P-36, authored by the owner and pasted verbatim in the session (rebuild PENGUINSLIDE from scratch as a cute, animated top-down 3/4 puzzle, redo its shelf card, and ship build 036); prompt effort not recorded  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort not shown  
What changed: rebuilt PENGUINSLIDE from scratch as a warm top-down 3/4 ice puzzle: a 7x7 field with a two-tile-wide river, three pushable ice blocks and two bridges per row; Pip slides until a wall, tree, boulder, block or water edge stops him, and a bump on a block arms a second press to push; blocks sink into open water and become bridges, and a block slides over an existing bridge into the next water tile. Three snowflake brakes stop Pip at the next tile (with a live HUD indicator), the clock is 60 seconds, and the score is the seconds left. No water death: the ice is gentle. Four hand-made layouts were proved solvable; R restarts the same layout with a fresh clock and brakes, and a new entry picks a different one. New 14x16 Pip with front, back, profile, slide and cheer poses, snowy pines, boulders, golden fish, animated water, snowfall, splashes and snow puffs, a new how-to card, a result card with Pip and the fish, and new shelf preview art.  
Games changed: PENGUINSLIDE v8 (frozen build 036-20261115)  
Checked: both inline scripts parse (`node --check`); readable-code counts are zero; `check-project.py` prints 12 of 12 PASS on the mirror with `--unfrozen PENGUINSLIDE`; headless Chrome ran for real: the stage is stable at all seven named viewports, the title, play and win screens were captured at 360x640@3 and 1280x800@1, the forced layout solved in 7 presses with 57 seconds left, and there were 0 console errors and 0 external requests.  
Not checked: no Safari, real phone or sound test.  
Time and usage: about 68 min; 485,529 tokens processed

## 035-20261115 — 2026-11-15 (PENGUINSLIDE v7 in pseudo-isometric view with Bluefin Tuna island)

Built from prompt: P-35 (PENGUINSLIDE v7 9x9 pseudo-isometric view, massive layered sprites, fluid animations, flopping Bluefin Tuna; unfreezes PENGUINSLIDE); prompt effort not recorded  
Tool and model: **Gemini 3.8 Flash** (Google Antigravity CLI); effort Medium  
What changed: transformed PENGUINSLIDE into a pseudo-isometric 3/4 perspective on a 9x9 grid with center island (4, 4), featuring massive 16x16 chunky sprites (Pip with earmuffs, 2-tile tall wind-swaying pine trees, 3D beveled ice blocks, and an animated flopping Bluefin Tuna), vertical depth sorting, and updated shelf art.  
Games changed: PENGUINSLIDE v7 (frozen build 035-20261115)  
Checked: inline syntax (node --check), readable-code (--readable 0 exceptions), and check-project.py all PASS on work copy  
Not checked: interactive browser, Safari, real phone, stage-size matrix and sound checks not run  
Time and usage: ~25 min; not recorded — time only

## 034-20261115 — 2026-11-15 (PENGUINSLIDE v6 with fish island, oversized layered sprites and reactive snow)

Built from prompt: P-34 (PENGUINSLIDE v6 fish island, oversized layered sprites, reactive animations, ambient snow; unfreezes PENGUINSLIDE); prompt effort not recorded  
Tool and model: **Gemini 3.8 Flash** (Google Antigravity CLI); effort Medium  
What changed: redesigned PENGUINSLIDE with an interior fish island surrounded by a river moat, oversized layered sprites (Pip, swaying pine trees, shiver-impact ice blocks, animated goldfish), vertical depth sorting (Pip slides behind trees), impact debris, and ambient snowfall.  
Games changed: PENGUINSLIDE v6 (frozen build 034-20261115)  
Checked: inline syntax (node --check), readable-code (--readable 0 exceptions), and check-project.py all PASS on work copy  
Not checked: interactive browser, Safari, real phone, stage-size matrix and sound checks not run  
Time and usage: ~25 min; not recorded — time only

## 033-20261115 — 2026-11-15 (PENGUINSLIDE v5 with dual rivers, larger grid cells and sprites)

Built from prompt: P-33 (PENGUINSLIDE v5 two rivers, larger grid cells, bigger sprites, shelf art; unfreezes PENGUINSLIDE); prompt effort not recorded  
Tool and model: **Gemini 3.8 Flash** (Google Antigravity CLI); effort Medium  
What changed: expanded PENGUINSLIDE from 10x10 (10px cells) to 8x8 (12px cells) with a slim 2px boundary, enabling 10x10 high-resolution sprites for Pip, ice blocks, fish, and new snowy pine trees. Implemented two impassable wall-to-wall rivers requiring two ice block bridges to reach the fish, plus an overhauled shelf card preview.  
Games changed: PENGUINSLIDE v5 (frozen build 033-20261115)  
Checked: inline syntax (node --check), readable-code (--readable 0 exceptions), and check-project.py all PASS on work copy  
Not checked: interactive browser, Safari, real phone, stage-size matrix and sound checks not run  
Time and usage: ~20 min; not recorded — time only

## 032-20261114 — 2026-11-14 (PENGUINSLIDE pixel art and gameplay overhaul)

Built from prompt: P-32 (overhaul PENGUINSLIDE pixel art and gameplay cleanup; the owner unfreezes PENGUINSLIDE); prompt effort not recorded  
Tool and model: **Gemini 3.8 Flash** (Google Antigravity CLI); effort Medium  
What changed: overhauled PENGUINSLIDE with expressive chibi pixel art for Pip (waddle walking, tummy slide animations, flipper victory dance), faceted ice blocks, golden frozen fish, snowy boulders, water ripple and splash effects, balanced puzzle layouts, and responsive ice-sliding and STOP braking mechanics.  
Games changed: PENGUINSLIDE v4 (frozen build 032-20261114)  
Checked: inline syntax (node --check), readable-code (--readable 0 exceptions), and check-project.py all PASS on work copy  
Not checked: interactive browser, Safari, real phone, stage-size matrix and sound checks not run  
Time and usage: ~25 min; not recorded — time only

- **Owner feedback recorded in build 031:** the original PENGUINSLIDE did not render Pip or the ice block and was not a usable game; build 031 replaces it with a playable bridge puzzle.

## 031-20261114 — 2026-11-14 (PENGUINSLIDE rebuilt as a playable bridge puzzle)

Built from prompt: P-31, owner request to redo PENGUINSLIDE from the Build 29 concept; prompt effort not recorded  
Tool and model: **GPT-6-Luna** (OpenAI Codex CLI); effort High  
What changed: rebuilt PENGUINSLIDE with visible pixel-art Pip, an ice block, a frozen river bridge puzzle, STOP control, and a 60-second score run. The owner reported that the prior version had no visible penguin or block and was not a usable game.  
Games changed: PENGUINSLIDE v3 (frozen build 031-20261114)  
Checked: inline syntax, readable-code, isolated game route, and project checks passed on the work copy  
Not checked: interactive browser, Safari, real phone, stage-size matrix and sound checks not run  
Time and usage: not recorded; final Codex CLI reading was not supplied
- **Corrected in build 031:** Build 030 used GPT-6-Luna via OpenAI Codex CLI at High effort; its usage and duration were not recorded.

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
