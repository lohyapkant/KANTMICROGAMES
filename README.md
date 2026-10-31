# KANTMICROGAME

A home for tiny, cute, pixel-art HTML5 micro games. Each game is one single-file
`index.html` that runs offline by double-clicking, with a small pixel stage, simple
controls and short, smiley sessions. The plan is that some of these games may one day
live inside a bigger KANT game — but nothing about them depends on that today.

**Current state:** round 0 — the shelf exists, no games on it yet.
**Shelf version:** 20261031-000

## How to open and play (so far)

- Double-click `index.html` to open the game shelf. It works fully offline.
- It currently shows the shelf with one `COMING SOON` slot; the first game
  (`PANDASNACK`, Round 1) has no page yet.

## Every micro game follows the seven rules

| # | Rule | Meaning |
|---|---|---|
| 1 | Single file | One `index.html` per game; no other files, no imports, no network use. |
| 2 | Offline | It must work with the internet off. webfont blocks, CDN links and downloaded pictures are all forbidden. |
| 3 | Tiny stage | The game world is a small fixed canvas of `100 x 100` design pixels (or smaller), scaled up with crisp pixels on screen. |
| 4 | Pixel art | Everything inside the stage is drawn as pixels. Rounded cute shapes, big eyes, short 2 to 6 frame animations, pastel colors. Emoji are allowed only outside the stage. |
| 5 | Simple controls | `W A S D` always moves the player, `Space` is the optional action button, phones get big on-screen pads outside the stage. |
| 6 | One concept | One screen, one verb, one rule short enough to say in one sentence. |
| 7 | Short play | A run lasts about 30 to 120 seconds and restarts in one press at any moment (`R` or a restart button). |

## How things are organized

```
KANTMICROGAME/
  index.html            the game shelf (this is what you open)
  games/<NAME>/         one folder per game, NAME short and ALL-CAPS
  plans/micro-games.md  the round-by-round project plan (v1 today)
  prompts/              a saved copy of every prompt per round, like our other projects
  CHANGELOG.md          one entry per finished round
```

- Games never depend on each other, on the shelf, or on anything else. Copy a game
  folder anywhere and it still works.
- The shelf is a plain link list with pixel previews drawn in code; it never uses
  iframes (those misbehave when opened from files).
- Each game writes its best score to a browser save key named
  `KANTMICROGAME.<GAME>.best`; the shelf shows that number on the card.

## Where things will go round by round

| Round | Status | Deliverable |
|---|---|---|
| 0 | done | This scaffold: shelf page, README, CHANGELOG, plans, prompts folder. |
| 1 | next | First game: **PANDASNACK**, a chubby panda scurries for bamboo while wasps drift past. |
| 2 | planned | Second game with a different control idea (an action button added). |
| 3 | planned | Third game; then a review of whether the shared drawing helpers are good enough. |
| 4+ | planned | One finished game per round, plus polish rounds whenever a card feels rough. |

## What is not in round 0

No games yet, no sound, no sharing between games, no score sending, no big-game
hooks, and nothing outside this folder is read, moved or edited.

## Files in this folder

- `index.html` — the selection page (arcade shelf).
- `README.md` — this project guide.
- `CHANGELOG.md` — the history of finished rounds.
- `plans/micro-games.md` — the full project plan (rounds, specs, game backlog).
- `prompts/P-00_round-0_project-kickoff.txt` — this round's prompt copy.

## Prompt history

The `prompts` folder holds the prompt copies used to build this project, one file
per round, in the same way our other KANT projects keep them.
# KANTMICROGAMES
