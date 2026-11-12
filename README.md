# Keir presentation

The single-file deck is published at <https://rore.im/keir/>.
It has no build step or runtime dependencies.

## Phone layout

In portrait at widths up to 960px, each slide becomes a vertically scrollable reading panel.
Cards and flow diagrams stack in reading order. The cover's SVG has a readable
HTML equivalent with the same operations and blocked call. Long code lines scroll
sideways. Landscape phones and larger screens use the original 1600×900 canvas,
scaled to fit the whole slide. Landscape reserves room for the larger navigation
buttons, so slides do not need scrolling or sit underneath the controls.

Phone navigation has 48px buttons and safe-area spacing. Reading gestures never
change slides. Previous/next and overview navigation reset the destination slide
to the top. Selecting the current slide keeps its reading position.

Left/Right and Home/End navigate slides. In portrait, Up/Down, Page Up/Down and Space
scroll the current slide instead. Code blocks keep their own horizontal arrow
keys. O opens the overview, Escape closes it, and F toggles fullscreen where the
browser supports it. The overview also has a sticky Close button and keyboard
focus stays inside it while open.

## Checks and visual review

Serve this directory over HTTP and open `tests/check.html?run`, or use the
[published checks](https://rore.im/keir/tests/check.html?run).
The browser-only checks need no installed packages. The same page links to
full-content review panels at each viewport width.

Validation before publishing:

- Portrait review covers all 13 slides at 320px, 390px and 430px widths.
- Landscape checks cover all 13 slides at 667×375, 844×390 and 932×430, including
  viewport fit, no slide scrolling and no overlap with navigation.
- Rotation checks start with a scrolled portrait slide and verify that landscape
  keeps the same slide, clears its scroll offset and fits it on screen. Rotating
  back restores the portrait reading layout.
- Compared every desktop slide against the existing live site at 1440×900 and
  1920×1080. All 26 screenshots were pixel-identical. Desktop slide text matched.
- The landscape correction also kept all 13 portrait screenshots pixel-identical
  at 390×844.
- Checked overflow, readable text sizes, reachable slide bottoms, tap targets,
  keyboard navigation, scroll reset, overview selection, closing and focus.
- Used Chromium mobile emulation and native injected touch events to test vertical
  reading scroll, button taps, sideways code scrolling and portrait/landscape
  resizing. Reading and code scrolling did not change slides.

These checks used Chromium, not physical phones, Safari or Firefox. Real mobile
browser toolbars, notches and OS text-size settings still need device testing.
