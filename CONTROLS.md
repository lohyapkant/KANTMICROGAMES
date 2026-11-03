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
