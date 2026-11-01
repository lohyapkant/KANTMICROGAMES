# Responsive shell test report — build 009-20261101

Test report for the build that made the shared shell responsive, input-aware and
safe on phones, tablets, foldables and desktops. The four game modules were not
touched; see the hash proof in [Frozen modules](#frozen-modules).

- **Build:** `009-20261101`
- **Tested file:** `deploy/index.html`
- **Test date:** 2026-11-01
- **Prompt:** P-09 (authored by Claude.ai Sonnet 5.5 Extra, executed in Qoder CLI)
- **Verdict:** every automated check passed. No physical device, Safari, Firefox or
  Edge was available — see [What was not verified](#what-was-not-verified).

## Environment

| Item | Value |
|---|---|
| Machine | macOS 27.2.0 on Apple silicon (arm64) |
| Browser | Google Chrome **156.0.8078.74**, headless |
| Driver | `playwright-core` **1.64.1** driving the installed Chrome binary |
| Page load | `file:///…/deploy/index.html` (the offline path) |
| Touch input | CDP `Input.dispatchTouchEvent`, `hasTouch` context, scale factor 1 |
| Keyboard input | CDP `Input.dispatchKeyEvent` and Playwright `keyboard` |
| Viewports | 24 sizes from 280 × 653 to 3440 × 1440 |
| Screenshots | 120 JPEGs (24 viewports × shelf + 4 games), 3 contact sheets |

The harness was run from a scratch directory (`/tmp/kant-009`) and is not shipped
in this folder, to keep the project's "documentation only beside `index.html`"
rule. The raw output of the final run is in
[`results/verification.json`](results/verification.json); the frozen-module proof
is in [`results/frozen-modules.json`](results/frozen-modules.json).

## Viewport matrix

Every row is one `playwright` context opened at that size with touch available.
"Stage" is the CSS size of the 100 × 100 canvas; "scroll" is
`documentElement.scrollHeight − innerHeight` with a game open (0 everywhere).

| Viewport | Layout | Stage px | Page scroll |
|---|---|---:|---:|
| 280 × 653 | portrait | 155 (fractional) | 0 |
| 320 × 568 | portrait | 200 | 0 |
| 360 × 640 | portrait | 200 | 0 |
| 375 × 667 | portrait | 300 | 0 |
| 390 × 844 | portrait | 300 | 0 |
| 412 × 915 | portrait | 300 | 0 |
| 430 × 932 | portrait | 300 | 0 |
| 568 × 320 | landscape | 187 (fractional) | 0 |
| 667 × 375 | landscape | 200 | 0 |
| 844 × 390 | landscape | 200 | 0 |
| 932 × 430 | landscape | 200 | 0 |
| 600 × 700 | portrait | 300 | 0 |
| 720 × 720 | landscape | 300 | 0 |
| 884 × 1104 | portrait | 600 | 0 |
| 768 × 1024 | portrait | 600 | 0 |
| 820 × 1180 | portrait | 600 | 0 |
| 1024 × 1366 | portrait | 600 | 0 |
| 1024 × 768 | landscape | 600 | 0 |
| 1280 × 600 | landscape | 400 | 0 |
| 1280 × 720 | landscape | 500 | 0 |
| 1366 × 768 | landscape | 600 | 0 |
| 1920 × 1080 | landscape | 600 | 0 |
| 2560 × 1440 | landscape | 600 | 0 |
| 3440 × 1440 | landscape | 600 | 0 |

The two fractional values are the D3 fallback for a stage that cannot reach
200 px without scrolling: the shortest phones and the shortest landscape ones.

## Assertions

**1,409 assertions, 0 failures, 0 console errors, 0 page errors.**

- 1,368 matrix assertions: 24 viewports × (1 shelf check + 4 games × 14 checks)
- 41 interaction assertions (table below)

| # | Assertion | Applied to | Result |
|---|---|---|---|
| A1 | Shelf has no horizontal overflow (`scrollWidth ≤ innerWidth`) | 24 viewports | pass |
| A2 | Open game has no horizontal overflow | 96 game states | pass |
| A3 | Open game has no page scroll (`scrollHeight ≤ innerHeight`) | 96 | pass |
| A4 | Stage is fully inside the viewport | 96 | pass |
| A5 | Pads are fully inside the viewport when visible | 96 | pass |
| A6 | Every visible control is ≥ 48 × 48 CSS px (back, restart, 4 arrows, action) | 96 × 7 | pass |
| A7 | Stage has `touch-action: none` | 96 | pass |
| A8 | Every pair of visible controls is at least 8 CSS px apart | 96 | pass |
| A9 | No control overlaps the stage | 96 | pass |

The shelf was also measured separately for card geometry: one column at 280–360 px,
two columns at 568–932 px, three columns at 844 px and above, never exceeding its
760 px column. No card or chip leaves the viewport.

## Interaction checks at 390 × 844

| Finding | Check | Evidence | Result |
|---|---|---|---|
| F2 | A drag on a card does not open the game | `dragOpened: false` | pass |
| F2 | A tap on a card opens it | `tapOpened: true` | pass |
| F2 | `⌂ SHELF` returns home and no ghost tap opens a card | `afterBackGameOpen: false` | pass |
| F3 | Tab order on the shelf is preferences, then cards | `["btnPadMode","btnHandMode","card","card","card"]` | pass |
| F3 | `ENTER` opens a focused card | `enterOpened: true` | pass |
| F3 | `SPACE` opens a focused card | `spaceOpened: true` | pass |
| F3/F13 | In-game tab order is back, then restart | `["btnBack","btnRestart"]` | pass |
| F7 | Ctrl/Cmd/Alt shortcuts, Tab, Shift and F1 never reach the game | only `onDir:*:false` releases (from the blur that ends the check); no `:true`, `onAction`, `restart`, `onAnyKey` | pass |
| F7 | Enter still counts as an "any key" (starts a title card) | `enterAnyKey: ["onAnyKey"]` | pass |
| F12 | Sliding the thumb from ← to ↑ switches direction and releases ← | `onDir:left:true → left:false → up:true → up:false` | pass |
| F12 | A second finger on the action pad while holding a direction works | `onDir:left:true`, `onAction`, `onDir:left:false` | pass |
| F8 | Hiding the tab pauses and shows the overlay | `paused: true, overlay: true` | pass |
| F8 | All four directions are released on pause | four `onDir:*:false` entries | pass |
| F8 | The first key after pausing only resumes | `paused: false, overlay: false`, log `[]` | pass |
| F6 | Keyboard input switches hints, chips and pads | hint `WASD swim · SPACE or tap stage to quack-boost · R restart · ESC shelf`, pads hidden | pass |
| F6 | Touch input switches them back | hint `pad to move · GO or tap the stage · ⌂ to leave`, pads shown | pass |
| D2 | `PADS · SHOW` survives a reload | `label: "PADS · SHOW"`, `pads: "show"` | pass |
| F9/F10 | Resizing and rotating mid-run never restarts | `start: 0, restart: 0` | pass |
| F9/F10 | The score survives the layout change | score `7` before and after | pass |
| F9/F10 | No scroll after three size changes | `docX: 0, docY: 0` | pass |
| F11 | A simulated 47 px top inset does not scroll the page | `docY: 0` | pass |
| F11 | The stage clears the simulated notch | `stageTop: 235.8 ≥ 47` | pass |
| F9 | A swipe on the stage neither scrolls nor taps | `scrollY: 0`, `log: []` | pass |
| F8 | `pointercancel` releases a held direction | `onDir:left:true → left:false` | pass |
| F8 | `pagehide` releases a held key and pauses | left released, `paused: true`, overlay shown | pass |
| F7 | Ctrl+S, Cmd+D, Alt+← and bare Shift/Tab/F1 never reach the game | no pressed direction, action, restart or any-key | pass |
| F7 | WASD, arrows, Space and R reach every module; Esc leaves every module | pressed directions, `onAction` and `restart` logged for all four games; each Esc closed the game | pass |
| F11 | Landscape notch (0/47/21/47) does not scroll and clears both edges | `docY: 0`, stage left 342, pad left 61, pad bottom 301 ≤ 369 | pass |

An additional manual check (not part of the 1,199) confirmed that `DIR PAD ·
RIGHT` also mirrors the controls in **portrait** (`actionCluster` at x 41,
`dirCluster` at x 157 at 390 × 844), so the preference has the same meaning in
both layouts.

## Visual inspection

All 120 screenshots were rendered into three contact sheets and looked at:

- [`screenshots/contact-sheet-1.jpg`](screenshots/contact-sheet-1.jpg) — 280 × 653
  to 568 × 320
- [`screenshots/contact-sheet-2.jpg`](screenshots/contact-sheet-2.jpg) — 667 × 375
  to 820 × 1180
- [`screenshots/contact-sheet-3.jpg`](screenshots/contact-sheet-3.jpg) — 1024 × 1366
  to 3440 × 1440

Full-size samples are kept for the tiniest phone, a standard phone, a landscape
phone, a desktop, plus both ends of the shelf:
[`screenshots/`](screenshots/).

Two problems were found by eye and fixed before the final run:

1. **Stage stuck at ~200 px on wide phones.** The measurement box was
   content-sized instead of stretched; `#stageBlock` now fills its grid area
   (`align-items: stretch` plus `align-self: stretch`), which lifted a 390 × 844
   phone from 200 px to 300 px.
2. **Controls far from the stage on tablets and desktops.** In landscape the grid
   used to stretch the side columns to the screen edges; the arena is now capped
   at 960 px and centred, so on 1024–3440 px screens the pads sit beside the
   600 px stage instead of at the corners.

After the fixes the sheets show: two-column shelf cards with no clipped text,
portrait layouts with the stage above one controls row, landscape layouts with
the pad and action beside the stage, and no controls under a notch-like top bar.

## Frozen modules

The four game IIFEs are byte-identical between the pre-build file and the final
file. Method: take the text from the `PART 5` banner to the `PART 6` banner, split
it at the `PART 5-B`, `PART 5-C` and `PART 5-D` banners, and compare SHA-256
hashes.

| Slice | Bytes | SHA-256 | Identical |
|---|---:|---|---|
| Whole PART 5 region | 109,070 chars | `2ea0a919…ff570b3e0` | yes |
| PANDASNACK | 26,177 | `0c3a1321…c3db2ecf` | yes |
| BOOPEEK | 30,660 | `a9d7a548…d8c1cf4c` | yes |
| DUCKLINE | 28,528 | `650ebc84…08b64bf4` | yes |
| SPROUTUP | 23,779 | `fcd91ebf…b26b7106` | yes |

Full hashes:
[`results/frozen-modules.json`](results/frozen-modules.json).

## What was not verified

Honest gaps — none of these were exercised:

- **No physical device.** iOS Safari, Android Chrome, a foldable, a tablet with a
  hardware keyboard, a pen, a low-end phone or a 120 Hz display were not available.
- **No Safari, Firefox or Edge.** Only Chrome 156 on macOS was driven.
- **No screen reader.** `aria-label` values and the polite live region were
  inspected in the DOM, but VoiceOver/TalkBack/NVDA were not run.
- **No real notch or home indicator.** `env(safe-area-inset-*)` is 0 in headless
  Chrome; the notch tests override the `--sai-*` custom properties (47 px portrait
  top and 0/47/21/47 landscape) instead of reading real insets.
- **No real pinch-zoom.** Allowing zoom was verified by inspecting the viewport
  meta (no `maximum-scale`, no `user-scalable=no`), not by performing the gesture.
- **No iOS address-bar motion.** `visualViewport` resize is wired, but the real
  Safari bar was not observed.
- **No foldable posture events.** Hinge/fold changes were approximated with viewport
  resizes.
- **No more than two simultaneous pointers**, no palm rejection, no stylus hover.
- **No performance measurement** (frame pacing, battery, thermal).

## Browser caveats and known limitations

- **`100dvh`** is used with a `100vh` fallback. Older browsers without `dvh` keep
  the fallback and may still show a tiny scroll in a game; the target is current
  iOS/Android/desktop browsers.
- **Fractional stage scale** below 200 px (280 × 653, 568 × 320) means the canvas is
  not an integer multiple of 100; `image-rendering: pixelated` still keeps the art
  crisp, but pixel widths can vary by one CSS pixel.
- **`PADS · HIDE`** hides the action button too. On a touch-only device the stage
  tap still acts, and the preference is reachable on the shelf.
- **Pads are not Tab stops** (`tabindex="-1"`, documented in `CONTROLS.md`): every
  pad action has a keyboard equivalent, and this keeps the tab order short.
- **Pause on `blur` can fire when an OS dialog opens** (for example a save dialog).
  The game pauses and releases directions; that is intended, but it means a
  desktop player may see `PAUSED` after dismissing a system dialog.
- **Hybrid laptops** guess "touch" when `maxTouchPoints > 0`; the first real
  keyboard or mouse event flips the pads off (AUTO), so the initial hint can be
  wrong for one interaction.
- **`SCREEN_SETTLE_MS = 400`:** for a moment after a screen swap, taps on cards
  are ignored, guarding against ghost clicks. A deliberately very fast second tap
  would be dropped.
- **The four frozen modules keep their own hint metadata.** The shell strips the
  `desktop:` prefix and writes its own touch line; no module code was changed.
- **The shelf still scrolls** vertically by design (it is a list of cards); only
  the game shell is scroll-locked.

## What changed, by file section

Line numbers are approximate and refer to the final `deploy/index.html`.

| Section | Change |
|---|---|
| `<head>` (~37) | Viewport meta now `width=device-width, initial-scale=1.0, viewport-fit=cover`; zoom allowed; comment explains why double-tap zoom is handled by `touch-action` instead. |
| `:root` (~58) | Added `--sai-t/-r/-b/-l` safe-area variables, `--pad`, `--pad-gap`. |
| `body`, `#page` (~90–130) | `min-height: 100dvh` with `100vh` fallback; page padding adds safe-area insets; `body.playing` locks height, hides page scroll and meta footer; `overscroll-behavior: none`. |
| `#shelfScreen`, `#prefs`, `#shelf`, `.card` (~146–350) | Shelf column capped at 760 px and centred; grid uses `minmax(min(228px, 100%), 1fr)`; cards are real buttons, opened on `click`, `touch-action: manipulation`, hover styles only under `(hover: hover)`; focus-visible ring. |
| Game shell CSS (~350–460) | `#arena` grid, `#controlsRow`, stage/controls areas; landscape grid with dir/action columns and a 960 px cap; portrait right-hand `row-reverse`; `#stageBlock` stretch + `overflow: hidden`; stage `touch-action: none`. |
| Pads and chrome CSS (~460–590) | 58 px pads (48 px at ≤ 380 px wide / ≤ 620 px tall), 3 × 3 direction grid with an empty dead centre, action + restart column, pause overlay, hide rules for `data-pads` / `data-input`. |
| Reduced motion (~615) | Card lift, chip pulse and button press transforms off under `prefers-reduced-motion`. |
| HTML (~642–694) | `#prefs` group with two preference buttons; hint element in the game header; `#pauseOverlay`; `#msg` as `role="status" aria-live="polite"`; pads with `tabindex="-1"` and `aria-label`s; `#controlsRow` wrapper. |
| `buildCard` (~1031) | Cards become buttons with an accessible label; opening is gated by the screen-settle and ghost-click guards. |
| `openGame` / `openShelf` (~1153–1200) | Idempotent open, pause flag and overlay reset, `body.playing` toggle, hint refresh, measured fit and deferred refit, hash routing updates. |
| Stage measuring (~1208–1258) | `stageScaleFor(layout)` measures the real box in each layout; `fitStage()` picks the larger scale, whole 2–6 or fractional below 200 px; `ResizeObserver` + `visualViewport` + rAF coalescing. |
| Lifecycle (~1280–1315) | `pauseForLifecycle()` releases directions and shows the overlay; `resumeFromUserInput()` resets the frame clock; listeners on `visibilitychange`, `blur`, `pagehide`. |
| Keyboard (~1320–1400) | `DIR_KEYS` for WASD + arrows; editable-target and non-any-key guards; Ctrl/Meta/Alt pass through; paused keys resume and are swallowed; Space/arrows `preventDefault`; `R`, `ESC`, any-key. |
| Input mode and preferences (~1390–1485) | `INITIAL_INPUT_MODE` from media queries (no UA sniffing); live switches on real pointer/key events; `KANTMICROGAME.ui.pads` and `.ui.hand` persistence; hint, chip and label refresh. |
| Direction cluster (~1486–1560) | Per-`pointerId` direction map, slide between buttons, tolerance in the dead centre, release on up/cancel/lost capture, suppression of the context menu; multi-touch with the action pad. |
| Action, stage tap, chrome (~1560–1600) | Action on pointerdown with press visual (or resume when paused); stage tap fires only after a short, still pointerup; back/restart/overlay handlers; final `applyUi()`. |
| Build stamps (~699, ~774) | Footer and `APP.fileVersion` say `009-20261101`. |

The four game IIFEs, the module contract, `STAGE_SIZE = 100` and the PART 1 pixel
helpers are untouched.

## How this was checked, in one paragraph

A Playwright script launched the installed Chrome with `hasTouch`, opened
`file://…/deploy/index.html`, and for each of the 24 viewports captured the shelf
and each game after `openGame()`. For every game state it measured
`scrollWidth`/`scrollHeight` against the viewport, the stage and pad rectangles
against the viewport, the computed `touch-action` of the stage, and the size of
every visible control. A second phase at 390 × 844 dispatched real CDP touch and
key events to test tap vs drag, the ghost-click guard, tab order, shortcuts,
sliding, multi-touch, lifecycle pause, input-mode switching, preference
persistence, mid-run resize and a simulated notch. Screenshots were rendered into
contact sheets and inspected by eye, and a SHA-256 comparison proved the four
frozen game modules unchanged.
