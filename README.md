# KANTMICROGAMES

Eight tiny pixel-art games in one HTML file. Open it, pick a game, play a minute.

Play online: <https://kantmicrogames.lohyapkant.workers.dev/>

**Current build:** `026-20261113` — eight games, one file.

## About this project

KANTMICROGAMES is made with AI. I brainstorm game ideas with AI models, write the requests, play-test the games and decide what works and what doesn't. AI coding models write the code and the documentation, and some of the prompts were written with an AI chat assistant.

It is also a small experiment. I try different models on different builds to see which ones handle a real project well and which don't. It isn't a controlled test: the tasks and the tools differ. Every build records which model and tool did the work and, for most builds, how long it took and what it used. Dated notes on each model, recorded from my feedback, are in MODELS.md. Same house rules, different models.

The full record of every build is in CHANGELOG.md.

## The games

| Game | Pitch |
|---|---|
| PANDASNACK | Munch bamboo, dodge wasps, keep three hearts. |
| BOOPEEK | Pip the lantern mouse chases Boo, a peek-a-boo nightcap ghost. |
| DUCKLINE | Mama mallard gathers three ducklings and leads them home. |
| SPROUTUP | Sproutlet the baby seedling gathers raindrops to bloom in the sun. |
| SLIMEHOP | Slimey hops a 3×3 lily-pad pond, blooming every pad before a sleepy snail undoes the work. |
| SNAILRACE | Nibbles races two garden snails to a picnic strawberry; lettuce zooms, salt stings. |
| HUGPARADE | Momo steps along hedge rails, gathers hearts, and hugs Bibi before the maze reshapes; each heart makes the hug worth more. |
| CATNAPCATCH | Slide a paper pillow under a sleeping kitten and catch the falling noisemakers; three clangs wake the nap. |

## How to play

- Use the play link above, or download `deploy/index.html` and double-click it.
- `W A S D` or the arrow keys move. `SPACE`, the action pad or a tap on the stage acts.
- `R` restarts at any time. `ESC` or the shelf button takes you back.
- The on-screen pads are always shown: directions on the left, the action on the right.
- Sound effects are on by default; switch them off under SETTINGS on the shelf.
- The shelf offers a pick of the day and can sort the games by name, best score, unplayed or most opened.
- Badges reward what you try, from your first game to scoring in all eight; see them under BADGES on the shelf.
- The background colour changes each visit; pick your own under SETTINGS on the shelf.
- SETTINGS can erase your scores, counts and badges on this device.
- Switching tabs or apps pauses the run. Page zoom is allowed.
- Tip: add `#game=PANDASNACK` (or any game name) to the play link to jump straight into a game.

Keyboard, touch and device details are in CONTROLS.md.

## The experiment so far

<!-- BEGIN:tools-table  (add or edit rows only) -->
| Tool | What it is | Link |
|---|---|---|
| OpenCode | open-source coding agent for terminal, desktop and IDE | https://opencode.ai/ |
| Google Antigravity | agent-first development platform | https://antigravity.google/ |
| Qoder CLI | terminal coding agent | https://qoder.com/ |
| Claude.ai | chat assistant (used to write some of the prompts) | https://claude.ai/ |
<!-- END:tools-table -->

<!-- BEGIN:models-table  (add or edit rows only) -->
| Model | Developer | Used via | Builds | How it went (owner notes, 2026-11-01) |
|---|---|---|---|---|
| DeepSeek V4.1 Flash Free | [DeepSeek](https://www.deepseek.com/) | OpenCode | 000, 001, 005, 006, 017, 018, 019, 020, 021, 022, 023, 024, 025, 026 | Clear pixel art and clean code (owner: "amazing"). |
| GLM-5.3 Flash Free | [Z.ai (Zhipu AI)](https://z.ai/) | OpenCode | 002, 003 | Worked mechanically; one game needed a full rework. |
| Flint 40B Free | [Recursive](https://recursive.com/) | OpenCode | 004 | A working module, but its art had to be rebuilt. |
| Gemini 3.8 Flash | [Google](https://gemini.google.com/) | Antigravity | 006, 007, 022 (started, halted) | Picked up cleanly after a session limit; delivered SPROUTUP. |
| GPT-OSS 120B Medium | [OpenAI](https://openai.com/index/introducing-gpt-oss/) | Antigravity | 008 (attempt) | Abandoned: it deleted sections of the docs instead of editing them. |
| Claude Opus 4.6 Thinking | [Anthropic](https://www.anthropic.com/) | Antigravity | 008 | Did most of the docs work, then halted mid-round. |
| Qwen3.8-Flash | [Alibaba Qwen](https://qwen.ai/) | Qoder CLI | 008 (finish), 009, 010, 011, 012, 013, 014, 015, 016, 017 | Delivered the responsive shell and four new games, corrected HUGPARADE's movement and scoring in 015, then delivered CATNAPCATCH in 016; older games stayed unchanged. |
| Claude.ai Sonnet 5.5 Extra | [Anthropic](https://claude.ai/) | Claude.ai chat | 009, 012, 013, 017, 018, 019, 020, 021, 022, 023 (prompt only), 024 (prompt only), 025 (prompt only), 026 (prompt only) | Wrote the responsive-shell prompt that Qwen executed, and later the prompts for builds 017 onward. |
<!-- END:models-table -->

One person's dated snapshots from a handful of builds. Not a ranking. Time and usage for every build are tabulated in MODELS.md; the full record is in CHANGELOG.md. Most builds run on free or trial plans; how that works is in MODELS.md.

## The rules every game follows

1. One file — the shelf and every game live inside one `index.html`.
2. Offline — it works with the internet off: no web fonts, CDNs or downloads.
3. Tiny stage — a 100 × 100 pixel canvas, scaled up in whole numbers.
4. Pixel art — everything in the stage is drawn as pixels; emoji stay outside it.
5. Simple controls — `W A S D`, arrows and one action button on every device.
6. One concept — one screen, one verb, one rule short enough to say in a sentence.
7. Short play — a run lasts about 20 to 120 seconds and restarts in one press.

## What's in this repo

- `deploy/index.html` — the whole game collection in one file.
- `README.md`, `CHANGELOG.md`, `MODELS.md`, `CONTROLS.md` — this page, the build history, notes on the models, and the controls.
- `LICENSE`, `wrangler.jsonc` — the MIT licence and the Cloudflare Workers settings.

Design notes, prompts and test evidence are kept in the author's private archive.

## Links

- GitHub: <https://github.com/lohyapkant/KANTMICROGAMES>
- Play online: <https://kantmicrogames.lohyapkant.workers.dev/>
- Hosting: [Cloudflare Workers](https://workers.cloudflare.com/)

## License

MIT — see [LICENSE](LICENSE). Copyright © 2026 Loh Yap Kant.
