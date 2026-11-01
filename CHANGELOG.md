# KANTMICROGAME Changelog

## 20261031-004 — 2026-11-01

Built from prompt: P-04 (Round 3 — DUCKLINE module add, the duck-family micro game)  
Tool and model: Flint 40B Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 3 (PANDASNACK module content 20261031-001, BOOPEEK module content 20261031-003, DUCKLINE module content 20261031-004; file build 20261031-003)

### Added

- Added the DUCKLINE module as the third game inside the one-file app (module content 20261031-004): a mother duck crosses the pastel pond with three ducklings in a waddling line behind her (WASD lead-a-chain), timer-limited round (12 s), victory at the far shore.

### Documentation

- Added prompt copy: prompts/P-04_round_3_duckline.txt.
- Updated the project README (round 3 status), the current plan (v2 backlog row for DUCKLINE).

### Build record (owner request: duration + tokens)

- Duration taken to build this round: about 25 minutes (DUCKLINE module add, prompt and plan updates, verification).
- Tokens used in this change: approximately 20,000 (DUCKLINE module add, prompt and plan updates, verification).

## 20261031-003 — 2026-10-31

Built from prompt: P-03 (Round 2 — BOOPEEK, the poke-the-ghost micro game)  
Tool and model: GLM-5.3-Flash Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 2 (PANDASNACK module content 20261031-001, BOOPEEK module content 20261031-003; file build 20261031-003)

### Added

- Added BOOPEEK as the second game module inside the one-file app: a shy ghost peeks from a cozy door on a small floor-and-wall pastel stage, the visitor (the panda mover) walks up with WASD and pokes with SPACE / the POKE pad or a stage tap; reaching the ghost within 10 design pixels scores a poke and pops six star sparkles, victory is at 10 pokes (BOO! YOU FOUND HIS HEART!), and the goal readout is drawn as "BOO LOVE n/n" in the shared pixel font.
- Wired BOOPEEK into the one-file runtime: shelf card, module registry entry, action button label (DASH → POKE per module), input routing, hash route `#game=BOOPEEK`, module-level restart/save/read.
- Updated the file version to 20261031-003 and stamped the footer accordingly; PANDASNACK's module content keeps its round 1 version number.

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
- Tokens used in this change: approximately 27,000 (BooPeek module, registry wiring, docs and changelog edits for build 20261031-003).

## 20261031-002 — 2026-10-31

Built from prompt: P-02 (the one-file pivot)  
Tool and model: GLM-5.3-Flash Free (OpenCode) — recorded per the owner's standing request in changelog, README, plan and prompt copies  
Games in the one file: 1 (PANDASNACK, module content still -001)

### Added

- Added the one-file architecture: the arcade shelf and the game view are two screens that swap inside a single `index.html` — no navigation, no iframes, no game folders; the file build number steps to 20261031-002 while PANDASNACK's module content keeps its round 1 number.
- Added the module contract: every game is a self-contained IIFE with its own SETTINGS, palette and maps, registered into a GAMES registry (start/stop/restart/update/paint/onDir/onAction/onStageTap/onAnyKey), and the runtime ticks and paints only the open module through one shared loop.
- Added one shared stage canvas and one shared pad deck with global keyboard routing (WASD + arrows move, SPACE action, R instant restart, ESC back to the shelf), hash routing (`#game=PANDASNACK` lands straight in a game) and whole-number stage scaling kept as before.
- Kept the shared pixel helper layer defined once in the file (paintPixels with scale and flip, paintRoundBlob, paintEyes, the 3x5 pixel font, paintPixelText) so the mascot, card previews and game modules all share the same drawing language; best-score save keys stay unchanged so old scores survive.
- Removed the `games/` folder after folding PANDASNACK into the file; the folder now holds only documentation.
- Updated docs for the pivot: README (one-file layout plus the PANDASNACK manual section), plan v2 (micro-games-v2.md) with a history note left on plan v1, and the P-02 prompt copy. Ran the lint checks (map widths, balanced tags, zero external URLs) and an extended headless smoke test: hash routing into the shelf and game, 1,500 frames of walking, dashing and restarting, round trip back to the shelf and reopen — zero exceptions. A hands-on phone (Safari) test remains pending.

## 20261031-001 — 2026-10-31

Built from prompt: P-01  
Tool and model: GLM-5.3-Flash Free (OpenCode) — recorded per the owner's request in changelog, README, plan and prompt copies  
Games on the shelf: 1 (PANDASNACK)

### Added

- Added the first micro game, PANDASNACK: a chubby panda scurries on a tiny 100 x 100 design-pixel pastel meadow, munches two always-available bamboo shoots (each worth +1), and dodges drifting wasps that cost one heart per sting with 1.6 seconds of shy flashing; three hearts end the run, and the difficulty climbs through a four-band table (1 to 4 wasps, speeds 13 to 26) as the score grows.
- Added a dash (SPACE, DASH pad or stage tap): a 0.7-second 1.75 times scurry with a 2.2-second cooldown shown as a rounded pixel gauge plus a tiny leaf that refills beside the three pixel hearts.
- Added the hand-drawn pixel art: blob-composed panda (lean-and-waddle walking, random blinks, happy munch mouth, dust puffs, droopy ears and a rolling tear at game over), two-frame flapping wasps, swaying bamboo shoots, sparkle bursts, dot-flowers on a cached two-tone checker background, and a shared 3 x 5 pixel font for all stage text with an optional one-pixel shadow pass.
- Added the toy-console page chrome: score/best chips with a munch pulse, a state message line, a four-pad plus DASH plus RESTART touch layout using pointer capture and touch-action none, WASD and arrow keys with instant R restart, and stage-tap dashing; the panda hides on every other beat while sting-protected.
- Wired the PANDASNACK card into the shelf page: code-drawn preview scene (panda, two bamboo shoots, two wasps), concept line, best score from the shared save key, COMING SOON blurb refreshed, shelf version raised to 20261031-001.
- Added games/PANDASNACK/README.md with controls, settings table with allowed ranges, difficulty bands and the full named palette, and saved the P-01 prompt copy.
- Ran a headless smoke test of the shipped file: the patched stub DOM ran 1,200 frames of walking, dashing and restarting with zero exceptions and a correctly auto-sized stage. A hands-on phone (Safari) play test is still pending.

## 20261031-000 — 2026-10-31

Built from prompt: P-00 (Round 0 — project scaffold)  
Tool and model: GLM-5.3-Flash Free (OpenCode)  
Games on the shelf: 0 (one COMING SOON slot)

### Added

- Created the KANTMICROGAME project as the home for tiny, cute, pixel-art HTML5 micro games and the seven micro-game rules (single file, offline, tiny stage, pixel art, WASD touch controls, one concept, short play).
- Added the single-file offline selection page `index.html`: toy-shelf look with warmth and soft colors, a code-drawn pixel panda mascot that bobs and blinks, how-to-play chips, a card area for game links, best-score display from browser saves, a dashed COMING SOON slot that keeps the shelf open for growth, and a version footer.
- Added the project README with the seven rules, folder layout, round table and the honest "not built yet" list.
- Added the project plan `plans/micro-games.md` with the full stage spec, control spec, per-game settings recipe, selection-page spec, definition of done, round table and eight-game concept backlog.
- Saved this round's prompt copy in `prompts/P-00_round-0_project-kickoff.txt`.
