# Real-device checklist — build 009-20261101

Things a headless browser cannot prove. **None of these were run in build 009** —
the automated suite covered Chrome 156 on macOS only (see the
[test report](responsive-shell-report.md)). Tick each item on the device in the
"Device / browser" column and note the result.

How to load the file on a device: open the hosted copy
<https://kantmicrogames.lohyapkant.workers.dev/>, or copy `deploy/index.html` to the
device and open it from Files (iOS: share sheet → Safari; Android: file manager →
Chrome). Turn the network off after loading to confirm it still runs.

Tip: clear the two preference keys if a test needs defaults —
`KANTMICROGAME.ui.pads` and `KANTMICROGAME.ui.hand` in the site's localStorage.

## iOS / iPadOS Safari

- [ ] **Address bar collapse.** Open a game in portrait and scroll-wrestle the page:
      the stage stays fully visible while the bar collapses and expands; nothing
      jumps under the thumb and the page never gains a scrollbar.
- [ ] **Home indicator.** In portrait and landscape, the direction pad and action
      button sit above the home-indicator strip and never trigger a swipe-up.
- [ ] **Notch in landscape.** Rotate to landscape on a notched iPhone: `⌂ SHELF`,
      SCORE/BEST and the pad clear the notch; nothing hides under the rounded
      corners.
- [ ] **Double-tap zoom.** A quick double tap on the shelf does not zoom;
      a deliberate pinch does zoom (zoom is allowed by design).
- [ ] **Pull-to-refresh.** Swiping down on the stage or the shelf does not reload
      the page; swiping on the shelf scrolls the cards.
- [ ] **Tab switching / app switch.** Press the home gesture or switch apps while
      holding a direction: the game shows `PAUSED` on return, and the first tap only
      resumes.
- [ ] **Best score survives** a Safari reload and a full close/reopen.
- [ ] **Add to Home Screen** (optional): the page opens standalone, still without
      scrolling during play.

## Android Chrome

- [ ] **Back gesture / Back button.** In a game, the system back gesture returns to
      the shelf (hash routing), and a second back leaves the page. It never exits
      the page from a running game.
- [ ] **Pull-to-refresh.** A downward swipe that starts on the stage does not
      refresh; a swipe on the shelf scrolls the cards.
- [ ] **Address bar / toolbar.** The game shell stays one screen tall while the
      toolbar hides and shows, in both orientations.
- [ ] **Cutout in landscape.** The pad and the action button clear the camera cutout.
- [ ] **Dark mode / forced dark.** The pastel palette is unchanged and readable
      (no auto-inverted canvas).
- [ ] **Vibration and audio** do nothing unexpected (the games use neither).

## Foldables

- [ ] **Fold / unfold while playing.** The stage re-fits without restarting the run;
      the score is unchanged; no direction is stuck.
- [ ] **Hinge / dual-screen posture.** In a half-folded posture the stage stays on
      one side of the hinge and the controls remain reachable; nothing is split
      under the hinge.
- [ ] **Near-square inner display.** The shell picks the layout that gives the larger
      stage; controls never overlap the stage.

## Large screens and windows

- [ ] **Split-screen / Stage Manager / freeform window.** Resizing the window while
      playing re-fits the stage and never restarts the game; at narrow widths the
      portrait layout returns.
- [ ] **Tablet with hardware keyboard.** Typing `W A S D` hides the pads; touching
      the screen brings them back (AUTO). `R` restarts, `ESC` returns to the shelf,
      and `Cmd/Ctrl` shortcuts reach the browser.
- [ ] **Touchscreen laptop (hybrid).** Mouse use hides the pads; a finger on the
      screen shows them; the preference `PADS · SHOW` keeps them visible regardless.
- [ ] **Left-handed play.** `DIR PAD · RIGHT` mirrors the controls in both layouts
      and survives a reload.
- [ ] **Hover lift.** On a mouse device a card lifts on hover; on a touch device it
      does not stick after a tap.

## Display and performance

- [ ] **120 Hz display.** Movement is smooth; the whole-number stage scale does not
      shimmer during play.
- [ ] **Low-end phone.** The game holds a playable frame rate with rain, sparkles
      and the full stage; no visible input lag on the pads.
- [ ] **Reduced motion** (OS setting): card lift, chip pulse and button press
      transforms are gone; gameplay is unaffected.
- [ ] **Large text / browser font size.** The chrome (hints, buttons, footer) grows
      with the user's setting; the stage keeps its pixel scale.
- [ ] **Zoom to 200%.** The shelf and chrome remain usable, and a game still opens.

## Accessibility

- [ ] **VoiceOver / TalkBack.** Cards announce their names; `⌂ SHELF` and `RESTART`
      are reachable; the pause overlay and stage messages are announced.
- [ ] **Switch access / keyboard only.** A card can be opened with `ENTER`/`SPACE`;
      `W A S D`, `SPACE`, `R` and `ESC` play and leave the game without touching the
      screen.
- [ ] **Colour perception.** Score, best and hints stay readable (the counters carry
      text labels, not colour alone).

## Reporting

If something fails, note the device, OS version, browser version, orientation, the
game, what you expected and what happened. The shell's layout decision is visible
as `document.body.dataset.layout` (`port` / `land`), and the input mode as
`dataset.input` (`touch` / `keys`) if a developer needs to inspect it.
