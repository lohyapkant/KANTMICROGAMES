# KANTMICROGAMES — Changelog

A short record of every build, newest first. Each entry gives the build ID, the prompt, the model and tool, and what changed. Time and usage for every build are in the Usage ledger in MODELS.md. The long-form build records are kept in the author's private archive.

- **Build IDs are `NNN-YYYYMMDD`:** a zero-padded build number, then the date. A game's version number is the build where its content last changed.
- **The project name is `KANTMICROGAMES`.** Entries up to build 009 used older singular spellings; they are historical records and are not rewritten.
- **Corrections are dated, not silent.** A wrong past record is corrected by a dated line that names the build that corrected it.
- **Corrected in build 028:** 13 lines in entries 000 to 018 were cut off mid-sentence when this record was made in build 027; they were restored in full from the private record. (The build 028 prompt expected 15: entries 001 and 000 were named too, but their lines were already whole, so nothing there needed changing.)

<!-- NEW ENTRIES: paste the newest short entry on the line below this comment, above the previous newest. Never edit older entries except to add a dated correction line in the header. -->
## 046-20261121 — 2026-11-21 (SIMONENUTS: twelfth microgame, smashing acorns on an oak table)

Built from prompt: P-46, planned by the owner with Gemini 3.8 Flash (High) on Google Antigravity CLI and pasted verbatim; build completed by Gemini 3.8 Flash (Google Antigravity CLI) at High effort.  
Tool and model: **Gemini 3.8 Flash** (Google Antigravity CLI); effort High  
What changed: SIMONENUTS (twelfth microgame). A top-down 3/4 pseudo-isometric nut-smashing game on an oak table stage. Player slides a wooden mallet with directions and swings with SMASH / Space / Stage Tap. Incoming nuts roll across the table: Cute Acorns (+1 pt, 1 hit), Tough Walnuts (+5 pts, 2 hits with cracked state and golden burst), Rotten Poison Nuts (-3 pts penalty, red flash/shake), and Simone's Love Nut (+10 pts, bursts into floating pink hearts with fanfare and 'SIMONE LOVES YOU!' banner). Added shelf card with preview canvas showing walnut, acorn, love heart nut and mallet. Updated About overlay catalog to display 12 games. All eleven existing games remain frozen and byte-identical.  
Games changed: SIMONENUTS (added as 12th game)  
Checked: check-project.py 12/12 PASS; readable check 3/3 PASS (100% compliant with plans/code-style.md); all eleven frozen game module hashes match plans/game-versions.txt byte-for-byte; headless Chrome passed all seven stage sizes, gameplay loop, scoring, Love Nut praise, and 0 console errors. Live checks follow the swap.  
Not checked: Safari, a physical phone, sound playback and owner visual approval.  
Time and usage: see Build 046 entry in MODELS.md.  

## 045-20261121 — 2026-11-21 (About reflection, catalog wrapping and comic art polish)

Built from prompt: P-45, owner request and design confirmed; reflection edited by Claude.Ai Sonnet 5.5 (High).  
Tool and model: **GPT-6-Luna** (OpenAI Codex CLI); effort High  
What changed: Replaced the About reflection with the approved wording, cleared the right scrollbar inset, and let game descriptions wrap. Redrew the four comic panels with larger, more detailed pixel maps and added flight and space details.  
Games changed: none  
Checked: staged checker 12/12 PASS; readable check 3/3 PASS; headless Chrome passed all seven stage sizes, 11 wrapped descriptions, four comic panels, dialog and focus flows, with zero console errors or external requests. Live checks follow the swap.  
Not checked: Safari, a physical phone, sound playback and owner visual approval.  
Time and usage: duration not supplied; final Codex CLI snapshot 1,556,975 total tokens (not a build delta); start total not captured; 51,818,112 cached input shown separately.  

## 044-20261121 — 2026-11-21 (Shelf About overlay: animated 4-panel comic, reflections, games catalog, credits and license)

Built from prompt: P-44, planned by the owner with Claude Opus 4.6 (Thinking) and Gemini 3.8 Flash (High) on Google Antigravity CLI and pasted verbatim; build completed by Gemini 3.8 Flash (Google Antigravity CLI) at High effort.  
What changed: Shell About overlay on the shelf. Added an ABOUT button on the shelf bar; opens an accessible modal dialog featuring an animated 2x2 pixel-art comic depicting the "Programmer vs Non-Programmer after 1 year of refining vs AI vibe coding" meme with custom themed borders; owner reflections on AI-assisted development (written strictly without contractions); a live dynamic shelf catalog listing all eleven games with mini preview thumbnails rendered via game.previewPaint; a directory of all models, harnesses, and platforms used with external links; and an interactive collapsible MIT License viewer with copyright to Loh Yap Kant. All eleven game modules are frozen and byte-identical.  
Checked: logic and readable checks PASS (100% compliant with plans/code-style.md); check-project.py 12/12 PASS; all eleven frozen game module hashes match plans/game-versions.txt byte-for-byte; stage rectangle and shelf layout stable across all seven named viewports; zero console errors.  
Not checked: Safari, a physical phone, sound or owner visual approval.  
Time and usage: see the Build 044 rows in MODELS.md.  

## 043-20261121 — 2026-11-21 (HESHETHEYIT v2: solid petals, a chosen sky and a night saucer)

Built from prompt: P-43, written by the owner with DeepSeek V4.1 Flash Free (OpenCode CLI) at High effort and pasted verbatim after review; build completed by GPT-6-Luna (OpenAI Codex CLI) at High effort.  
What changed: HESHETHEYIT v2. Petals now rasterize solidly; the PICK card lets the player choose among all four skies, while the device clock remains the suggestion; the night witch and broom became a small saucer; the flower recoils on a pull, the petal pops before falling, the bare heart arrives in two steps, and the how-to card teaches the sky control. All eleven games are frozen.  
Checked: logic harness 574/574; art harness 69/69, including a measured zero pinholes in head petals, loose petals and the how-to icon (same-seed Build 42 comparison: 269/4/1 before, 0/0/0 after); headless Chrome 60/60 flow checks, stage rectangle identical to Build 42 at all seven named viewports, zero console errors and zero external requests. Ten other game modules unchanged.  
Not checked: Safari, a physical phone, sound or owner visual approval.  
Open issue: the saved-sheet planning counts were 416 head and 25 loose-petal pinholes; the same-seed probe against the saved Build 42 file measured 269 and 4. The before and after counts above are from the probe, not the planning estimates. Usage readings and duration were not captured consistently; MODELS.md records the available readings and the recovery request.  
Time and usage: see the Build 043 rows in MODELS.md.  
Usage/time update (2026-11-21): the owner supplied the Codex CLI end display: 1,008,937 total tokens (832,968 input + 175,969 output, with 86,596 reasoning included in output; 39,387,264 cached input shown separately). The Codex UI showed 2 h 39 min 28 s worked. The start meter was not captured, so this is not a build usage delta; OpenCode's final reading and time remain unavailable.  

## 042-20261119 — 2026-11-19 (HESHETHEYIT: the eleventh game, and the last petal answers)

Built from prompt: P-42, written by the owner with DeepSeek V4.1 Flash Free in OpenCode CLI at High effort and pasted verbatim after reviewing the planning sheet (a new game about pulling flower petals, with a clock-driven sky and the last answer on the shelf); prompt effort High  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort High  
What changed: HESHETHEYIT v1 (frozen build 042-20261119), the eleventh microgame. You pick HE, SHE, THEY or IT with left and right, then pull one petal per action press; the last petal is the answer (`SHE LOVES ME!`, `THEY LOVE ME NOT!`), and the shelf's usual score line becomes `last: ...` with no gold star. Every reading grows a different flower from six curated palettes, four centres, several petal shapes and 5 to 8 petals, with a green stem, leaves or thorns, a gentle sway and the pulled petal falling to the grass. The sky follows the device clock: dawn 05-08, day 08-17, dusk 17-20, night 20-05, each with its own three bands and life (birds, bees, fireflies, stars, a witch on a broom); the sky is fixed for each flower. The how-to card inside the stage names the game, gives four short lines, a small five-petal flower and a blinking TAP TO START. The owner kept 5 to 8 petals rather than a single minute-long flower: the minute comes from playing four or five flowers in a row with AGAIN, because a 60-second bloom would need 60 to 90 petals at 100 x 100. The shelf card carries the description and the dedication `(Inspired by Yuan Ning)` at the end of the message, with public use of the name approved. Shell changes are small and shared: a saved last result per game, a plain card line for it, hidden SCORE and BEST chips for this game only, and a device-hour reader so the module never touches `Date`. The other ten games, the shelf art, the badges, the settings and the pads are unchanged  
Games changed: HESHETHEYIT v1 (frozen build 042-20261119)  
Checked: the logic harness prints 554 of 554 assertions; the art harness prints 51 of 51 (four skies, six palettes, at least three shapes, four centres, a green stem, one petal removed per pull, a falling petal that moves, the how-to text clear of its icon, the bare centre still joined to its stem, a painted shelf preview, the witch flyby); headless Chrome reports 44 of 44 flow checks at phone and desktop sizes, the stage stable and 100 x 100 at all seven named viewports, 0 console errors and 0 external requests; all ten other module hashes are unchanged; `check-project.py` prints 12 of 12 PASS on the mirror  
Not checked: no Safari, real phone or sound test; the art check is a self-review, not an owner approval  
Time and usage: about 3 h across two sittings, with a long pause; the two-day stats window slid past midnight during the build, so the ledger shows the start and final readings instead of a delta
## 041-20261118 — 2026-11-18 (CHASEKILLKANT v4: a living office with a cactus and a callout)

Built from prompt: P-41, written by the owner with DeepSeek V4.1 Flash Free in OpenCode CLI at High effort and pasted verbatim after review (an art-and-copy pass on CHASEKILLKANT — keep every number, make the office feel alive, and give the punish window a short callout); prompt effort High  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort High  
What changed: CHASEKILLKANT v4 (frozen build 041-20261118), an art-and-copy pass with zero gameplay change: the still office gained a wide glass meeting room with two seated silhouettes and a walker crossing every ten seconds, a grounded fire door with a visible threshold and contact shadow, and a six-row tonal carpet with a socket, cable and scuff details; the falling pot became a flowering saguaro in a terracotta pot and the crate became a labeled delivery box, both keeping their old hit sizes, spawn rates and drift; a short HIT NOW! plaque appears under Kant only while he is off balance, not dazed, with cutlery in hand, and bobs one pixel vertically for a third of a second after the window closes. The how-to card now reads CATCH BOXES and DODGE THE CACTUS, the concept line says delivery boxes and potted cacti, and the shelf preview matches the room. The status bar, the shell and the other nine games are byte-identical; the play, the clock, the scoring and the difficulty are unchanged  
Games changed: CHASEKILLKANT v4 (frozen build 041-20261118)  
Checked: the fairness harness prints 1700 of 1700 assertions with the four skill bands unchanged to the digit (perfect and sharp 100 percent, regular 30 percent, rookie 12.5 percent); the frozen-behaviour probe proves every gameplay function, HUD and card painter and shared setting unchanged except the named cosmetic blocks; the art probe passes every colour, cactus, glass and carpet check; both inline scripts parse; the stage is identical at all seven named viewports; headless Chrome reports 32 of 32 art checks, 16 of 16 flow checks, 0 console errors and 0 external requests; all nine other module hashes are unchanged; `check-project.py` prints 12 of 12 PASS on the mirror  
Not checked: no Safari, real phone or sound test; the art check is a self-review, not an owner approval; the rookie and regular difficulty gap stays open and reported  
Time and usage: about 40 min; 1.27 M tokens processed
## 040-20261117 — 2026-11-17 (CHASEKILLKANT v3: a still office corridor and a gold rim)

Built from prompt: P-40, written by the owner with DeepSeek V4.1 Flash Free in OpenCode CLI and pasted verbatim after review (an art-and-copy pass on the room: a still office corridor, a quiet grey carpet floor, a cardboard archive crate and a gold rim hint, with no gameplay change); prompt effort High  
Tool and model: **DeepSeek V4.1 Flash Free** (OpenCode); effort High  
What changed: CHASEKILLKANT v3 (frozen build 040-20261117), an art-and-copy pass with zero gameplay change: the scrolling wooden hallway with side wedges became a still office corridor, with a cream upper wall over a sage dado and wood rail, a sage fire door with a frosted panel and gold handle, a cork noticeboard, a two-pixel skirting board and a static cool-grey carpet of six widening tile rows with a faint checker and soft seams; the lockers, the NO RUNNING sign and the floor scroll are gone. The ammo crate keeps its 9x7 silhouette but is now a cardboard archive box with a gold tape strip, and the punish hint is a steady one-pixel gold rim around Kant while he is off balance instead of a floating bar. The shelf preview and the module banner match the room; the `concept` line now says "warm office corridor". The status bar, the shell and the other nine games are byte-identical; the play, the clock, the scoring and the difficulty are unchanged  
Games changed: CHASEKILLKANT v3 (frozen build 040-20261117)  
Checked: the fairness harness prints 1699 of 1699 assertions with the four skill bands unchanged to the digit (perfect and sharp 100 percent, regular 30 percent, rookie 12.5 percent); the frozen-behaviour probe proves every gameplay function, HUD and card painter and shared setting unchanged; both inline scripts parse; the stage is identical at all seven named viewports; the art probe finds no retired teal, wood floor or wood crate colour and puts the gold rim 64 points above the carpet; headless Chrome reports 18 of 18 art checks, 16 of 16 flow checks, 0 console errors and 0 external requests; all nine other module hashes are unchanged; `check-project.py` prints 12 of 12 PASS on the mirror  
Not checked: no Safari, real phone or sound test; the art check is a self-review, not an owner approval; the rookie and regular difficulty gap stays open and reported  
Time and usage: about 52 min; 0.33 M tokens processed
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
