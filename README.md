# Keir presentation

The single-file deck is published at <https://rore.im/keir/>.
It has no build step or runtime dependencies.

## Phone layout

In portrait at widths up to 960px, each slide becomes a vertically scrollable reading panel.
Cards and flow diagrams stack in reading order. The cover's SVG has a readable
HTML equivalent with the same operations and blocked call. Long code lines scroll
sideways. Landscape phones and larger screens use the original 1600×900 canvas.
Landscape phones and fullscreen presentations fit the maximum usable screen area,
respecting notch and home-indicator insets. Controls overlay the slide and never
shrink it. Normal desktop layout keeps its original spacing.

Phone navigation has 48px buttons and safe-area spacing. Controls start hidden on
phones and hide when entering fullscreen. Tap or click the slide to toggle them.
The small bottom-right `1/13` counter stays visible and can also toggle controls.
Keyboard focus returns to that counter when focused controls are hidden.

Swipe left for the next slide and right for the previous slide. A swipe hides the
controls. Vertical and mostly vertical gestures keep native reading scroll.
Horizontal code scrolling, links, pinch gestures and cancelled touches do not
advance slides. Horizontal slide gestures do not trigger browser back navigation.
Previous/next and overview navigation reset the destination slide to the top.
Selecting the current slide keeps its reading position.

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
  maximum viewport fit and no slide scrolling. Toggling controls does not resize
  the canvas. Simulated notch and home-indicator insets are also checked.
- Rotation checks start with a scrolled portrait slide and verify that landscape
  keeps the same slide, clears its scroll offset and fits it on screen. Rotating
  back restores the portrait reading layout.
- Compared every slide against the existing live site at 390×844, 1440×900 and
  1920×1080. With the intentionally changed controls and counter hidden on both
  versions, all 39 screenshots were pixel-identical.
- Checked overflow, readable text sizes, reachable slide bottoms, tap targets,
  keyboard navigation, scroll reset, overview selection, closing and focus.
- Used Chromium mobile emulation and native injected touch events to test vertical
  reading scroll, left/right swipes, immediate taps after swiping, button taps,
  sideways code scrolling and portrait/landscape resizing. Reading and code
  scrolling did not change slides. Swipes updated the persistent counter.
- Entered the browser Fullscreen API at 844×390 and 1920×1080. Controls hid, the
  canvas filled the usable screen, and revealing controls did not change its size.

These checks used Chromium, not physical phones, Safari or Firefox. Real mobile
browser toolbars, notches and OS text-size settings still need device testing.
