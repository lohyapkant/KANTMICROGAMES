# KANTMICROGAMES — Controls

Which controls exist, how they behave on each kind of device, and why. The shell
was made responsive and input-aware in build **009-20261101**. Build **010-20261101**
adds the fifth game (SLIMEHOP) using the same contract and controls; the four older
modules were not touched (PANDASNACK, BOOPEEK and DUCKLINE are frozen, and SPROUTUP
needed no change).

## One table for all five games

| Game | Move | Action (`SPACE`, action pad, stage tap) | Goal |
|---|---|---|---|
| PANDASNACK | scurry with `W A S D` / arrows / the direction pad | **DASH** — 0.7 s at 1.75×, 2.2 s cooldown | munch bamboo, dodge wasps, keep three hearts |
| BOOPEEK | tiptoe with `W A S D` / arrows / the direction pad | **POKE** — 20 px reach, 0.1 s cooldown | poke Boo while he peeks; 10 in 20 s, then beat your score |
| DUCKLINE | swim with `W A S D` / arrows / the direction pad | **GO** — quack boost, 0.55 s at 1.7×, 2 s cooldown | gather three ducklings, reach the far bank in 22 s |
| SPROUTUP | weave with `W A S D` / arrows / the direction pad | **REACH** — leap burst, 0.5 s at 1.85×, 2 s cooldown | gather 15 drops in 24 s to bloom |
| SLIMEHOP | hop one pad per press with `W A S D` / arrows / the direction pad | **STOMP** — bloom the pad underfoot, 1.2 s cooldown, stuns a nearby snail | bloom all nine pads in 30 s before the snail eats them |

The action button carries the game's own label (DASH / POKE / GO / REACH / STOMP), so
one pad serves every game. SLIMEHOP is the one game where a direction press is a single
**discrete hop** rather than a continuous walk: holding a direction does not repeat, and
each new press hops one pad (or bonks harmlessly at the pond edge).

## Input devices

| Device | Move | Act | Start / restart | Leave |
|---|---|---|---|---|
| Keyboard | `W A S D` or arrow keys | `SPACE` | `SPACE` / `ENTER` / any unmodified key starts the title card; `R` restarts a run | `ESC` |
| Mouse | drag the direction pad (optional) | click the action button or the stage | click the card on the shelf; click `RESTART` | click `⌂ SHELF` |
| Touch / pen | thumb-drag the direction pad; slide from one arrow to the next without lifting | tap the action button or the stage | tap the card; tap `RESTART` | tap `⌂ SHELF` |
| Assistive tech | the pads are direct-manipulation only (see below); keyboard mappings still work | `SPACE` | `ENTER` on a focused card | `ESC` or `⌂ SHELF` |

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

The direction cluster and the action + restart column appear when the last real
input was touch or pen. If the last input was a key or the mouse they hide, giving
the stage the whole screen. The circle in the middle of the direction cluster is
empty: sliding across it keeps the current direction instead of releasing it.

| Preference | Values | Effect |
|---|---|---|
| `PADS` | **AUTO** (default) · **SHOW** · **HIDE** | AUTO follows the last input type; SHOW always shows the pads; HIDE hides them even in touch mode (the stage and the keyboard still work) |
| `DIR PAD` | **LEFT** (default) · **RIGHT** | puts the direction cluster and the action column on opposite sides — in landscape beside the stage, in portrait within the controls row |

Both preferences sit on the shelf under the how-to chips, are announced with an
`aria-label`, and persist across reloads in `localStorage` under
`KANTMICROGAMES.ui.pads` and `KANTMICROGAMES.ui.hand`. To reset them, clear those
keys (or all `KANTMICROGAMES.*` keys) in the browser's site data. Best scores use the
same prefix: `KANTMICROGAMES.<GAME>.best`.

Pads and buttons are at least **48 × 48 CSS px** at every viewport. On the
smallest phones (≤ 380 px wide or ≤ 620 px tall) the pad shrinks to exactly 48 px;
on larger screens it grows to 58 px.

### Why the pads are not Tab stops

The four direction buttons and the action pad use `tabindex="-1"` on purpose.
They are held controls, not buttons you press once: tabbing to them would add six
stops in front of `RESTART` and would not let a keyboard user hold a direction.
Every pad action has a keyboard equivalent (`W A S D` / arrows, `SPACE`), so the
game is fully operable from the keyboard without them. The tab order is kept
short and predictable: shelf cards and preferences on the shelf, then `⌂ SHELF` →
`RESTART` in a game.

## Pause

A game pauses when the tab is hidden, the window loses focus, or the page is being
put away (`visibilitychange`, `blur`, `pagehide`). Every held direction is released
first, so nothing runs into a wall while the phone rings. A `PAUSED` plate appears
over the stage.

The next tap or key press only resumes: it is swallowed, so you cannot dash or poke
straight out of a pause. `ESC` still leaves to the shelf while paused.

## Layout and scaling

- The stage keeps its 100 × 100 design pixels and is scaled by whole numbers
  **2×–6×** (200–600 px) while that fits. Below 200 px — very short landscape
  phones — the scale becomes fractional rather than clipping or scrolling.
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

- Visible focus ring (`:focus-visible`) on shelf cards, preference buttons and the
  two chrome buttons.
- Cards are real buttons with an accessible name; `ENTER` and `SPACE` open them.
- Stage messages (`#msg`) are a polite live region, so screen readers hear
  "PAUSED", "GAME OVER" and similar shell-level text.
- Prefers-reduced-motion turns off the card lift, chip pulse and button press
  transforms.
- Colours and pixel art are untouched; this build only changed the shell.

## Known control quirks

- The frozen modules still carry their original desktop hint strings. The shell
  strips the `desktop:` prefix for the keyboard hint and writes its own touch
  line from the game's action label, so no game code had to change.
- HIDE hides the action button as well as the direction pad. On a touch-only
  device the action is still available by tapping the stage.
- The mascot animation and the shelf's hover lift are decorative only; they are
  disabled under reduced motion and do not affect play.
