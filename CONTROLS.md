<!-- Applies to: build 018-20261104 · eight games · changes to controls are recorded in CHANGELOG.md -->
# KANTMICROGAMES — Controls

Which controls exist, how they behave on each kind of device, and why.
This guide applies to all eight games, on every kind of device.

## One table for all eight games

| Game | Move | Action (`SPACE`, action button, stage tap) | Goal |
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
so one button serves every game. SLIMEHOP is the one game where a direction press is a single
**discrete hop** rather than a continuous walk: holding a direction does not repeat, and
each new press hops one pad (or bonks harmlessly at the pond edge). SNAILRACE steers
continuously on both axes; holding right and up moves diagonally with each axis at full
speed, so a lane change does not cost forward ground. HUGPARADE moves on cell rails
instead: every press carries Momo a whole cell, a release mid-step still finishes that
step at the next centre, a perpendicular press waits for the next junction, and only a
hedge blocks a step. It never moves diagonally, so Momo cannot wedge between two hedges.
CATNAPCATCH uses the horizontal axis only: left and right slide the paper pillow, and up
and down do nothing.

## Controls on the game screen

Two chrome buttons are pinned to the viewport's upper-left corner, inside the safe area,
on every game and every device: **SHELF** and **RESTART**. They never move with the
centred content column and never move between games. The title, SCORE and BEST sit to
their right in one slim row; the tagline and hint step out of the way when they would
crowd the stage.

- **SHELF** returns to the shelf. **RESTART** starts the current run again.
- There is no menu and no `M` key. `R` restarts, `ESC` leaves, and both work from play
  and from a pause.
- The corner pair is at least 12 px apart and each button is at least 48 px tall.
- On screens under 360 px wide the pair stacks vertically, so the title, SCORE and BEST
  keep their own row instead of being squeezed to nothing.

The direction cluster is always on the left and the action button always on the right.
They are shown on every device, including a desktop with a mouse and keyboard; nothing
is hidden or moved because of the device type.

| Layout | Where the controls are |
|---|---|
| Portrait (phones held normally, tablets upright) | the stage on top, one controls row below it: directions left, action right |
| Landscape (phones sideways, tablets sideways, desktop browsers) | three columns: directions left, the stage in the middle, the action right |

The three-column group is centred with fixed gaps and capped at 1100 px, so the controls
do not drift to the far edges of a very wide screen.

## Fixed sizes by screen class

The class comes from the **shorter side** of the viewport. Sizes are CSS px. There is no
size option and no preference to remember.

| Class | Shorter side | Direction button | Action button | Direction label scale | Action label scale | SHELF / RESTART height | Corner label scale |
|---|---|---|---|---|---|---|---|
| XS | under 360 | 48 | 88 | 2 | 3 | 48 | 2 |
| SM | 360–479 | 60 | 112 | 2 | 3 | 48 | 2 |
| MD | 480–819 | 72 | 132 | 3 | 4 | 52 | 3 |
| LG | 820 and up | 84 | 156 | 3 | 5 | 56 | 3 |

The direction buttons keep an 8 px gap, the direction cluster keeps at least 24 px from
the action button, and SHELF and RESTART keep at least 12 px between them. Every
tappable is at least 48 × 48 CSS px. The XS direction and action sizes are two steps
below the table in the owner's request (52 and 96): 52 × 3 + 8 × 2 + 24 + 96 = 292 px
does not fit the 280 px test screen, while 48 × 3 + 8 × 2 + 24 + 88 = 272 px does.

## Labels are pixel text

Every game-control label is a small canvas drawn with the file's own 3 × 5 pixel font:
UP, DOWN, LEFT, RIGHT, the game's action word, SHELF and RESTART. There are no arrows,
SVG, emoji or system-font words on the controls. Each button also has an `aria-label`
with the full word (the action button says, for example, `DASH (action)`).

The label scale is a nominal CSS px per font pixel. The shell chooses a whole number of
**device** pixels per font pixel (`n = round(scale × devicePixelRatio)`) and sets the
canvas CSS size to `n / devicePixelRatio`, so glyph edges stay crisp at DPR 1, 2 and 3.

## Input devices

| Device | Move | Act | Start / restart | Leave |
|---|---|---|---|---|
| Keyboard | `W A S D` or arrow keys | `SPACE` | `SPACE` / `ENTER` / any unmodified key starts the title card; `R` restarts a run | `ESC` |
| Mouse | drag the direction pad | click the action button or the stage | click the card on the shelf; click `RESTART` | click `SHELF` |
| Touch / pen | thumb-drag the direction pad; slide from one direction to the next without lifting | tap the action button or the stage | tap the card; tap `RESTART` | tap `SHELF` |
| Assistive tech | the pads are direct-manipulation only (see below); keyboard mappings still work | `SPACE` | `ENTER` on a focused card; `SHELF` and `RESTART` are real buttons | `ESC` or `SHELF` |

Rules that apply everywhere:

- **One tap = one action.** A tap on the stage acts once (`onStageTap`). A drag on
  the stage does not act; a mouse drag that starts on a shelf card does not open it.
- **Drag does not leak.** After `SHELF`, a tap that ends where a card now sits does
  not open anything (a short ghost-click guard, and one tap must both start and end
  on the card). The same settle gate protects `SHELF` and `RESTART`.
- **Browser shortcuts pass through.** `Ctrl` / `Cmd` / `Alt` combinations are never
  consumed: copy, paste, reload, tab switching and OS gestures reach the browser.
  Tab, CapsLock, the modifier keys and F1–F12 are never treated as "any key".
- **Arrows and Space do not scroll the page** while a game is open.

## On-screen pads

The direction cluster and the action button are always shown. The circle in the middle
of the direction cluster is empty: sliding across it keeps the current direction instead
of releasing it. Pads and buttons are at least **48 × 48 CSS px** at every viewport.

Build 018 removed the PADS (AUTO / SHOW / HIDE), DIR PAD and PAD SIZE options and their
shelf buttons. Older saved values under `KANTMICROGAMES.ui.pads`, `KANTMICROGAMES.ui.hand`
and `KANTMICROGAMES.ui.padsize` are left in storage untouched and are never read. Best
scores still use `KANTMICROGAMES.<GAME>.best`.

### Why the pads are not Tab stops

The four direction buttons and the action button use `tabindex="-1"` on purpose.
They are held controls, not buttons you press once: tabbing to them would add five
stops in front of the pinned pair and would not let a keyboard user hold a direction.
Every pad action has a keyboard equivalent (`W A S D` / arrows, `SPACE`), so the
game is fully operable from the keyboard without them. The tab order is kept short
and predictable: shelf cards on the shelf, then `SHELF` and `RESTART` in a game.

## Pause

A game pauses when the tab is hidden, the window loses focus, or the page is being
put away (`visibilitychange`, `blur`, `pagehide`). Every held direction is released
first, so nothing runs into a wall while the phone rings. A `PAUSED` plate appears
over the stage.

The next tap or key press only resumes: it is swallowed, so you cannot dash or poke
straight out of a pause. `ESC` still leaves to the shelf while paused. `R` restarts
once the run is resumed.

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
  landscape screens put the direction cluster and action button beside the stage.
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

- Visible focus ring (`:focus-visible`) on shelf cards, `SHELF`, `RESTART` and the
  action button.
- Cards are real buttons with an accessible name; `ENTER` and `SPACE` open them.
- `SHELF` and `RESTART` are real buttons with pixel-text labels and full-word
  `aria-label`s. The direction and action buttons carry full-word `aria-label`s too.
- Stage messages (`#msg`) are a polite live region, so screen readers hear
  "PAUSED", "GAME OVER" and similar shell-level text.
- Prefers-reduced-motion turns off the card lift, chip pulse and button press
  transforms.

## Known control quirks

- The shell writes its own hint line from the game's action label, so the frozen
  modules' original desktop hint strings are not shown. No game code had to change.
- The title truncates with an ellipsis when the top row is tight, so SCORE and BEST
  stay clear of the pinned pair. The full name is on the shelf card and in the
  browser tab.
- Below 360 px wide the pinned pair stacks vertically; the title, SCORE and BEST
  keep a readable row to its right.
- The mascot animation and the shelf's hover lift are decorative only; they are
  disabled under reduced motion and do not affect play.
