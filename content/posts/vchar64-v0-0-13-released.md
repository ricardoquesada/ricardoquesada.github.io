---
author: ricardoquesada
category:
  - commodore-64
  - programming
date: "2016-04-15T21:35:58+00:00"
guid: http://retro.moe/?p=1601
summary: |-
  Download:

  - Mac: [vchar64-0.0.13.mac.dmg](https://github.com/ricardoquesada/vchar64/releases/download/0.0.13/vchar64-0.0.13.mac.dmg)
  - Win32: [vchar64-0.0.13.win32.zip](https://github.com/ricardoquesada/vchar64/releases/download/0.0.13/vchar64-0.0.13.win32.zip)
  - Source code: [https://github.com/ricardoquesada/vchar64](https://github.com/ricardoquesada/vchar64)

  https://www.youtube.com/watch?v=lb7UNIhoyoI



  Changelog:
tag:
  - c64
  - vchar64
title: VChar64 v0.0.13 released
url: /2016/04/15/vchar64-v0-0-13-released/

---
Download:

- Mac: [vchar64-0.0.13.mac.dmg](https://github.com/ricardoquesada/vchar64/releases/download/0.0.13/vchar64-0.0.13.mac.dmg)
- Win32: [vchar64-0.0.13.win32.zip](https://github.com/ricardoquesada/vchar64/releases/download/0.0.13/vchar64-0.0.13.win32.zip)
- Source code: [https://github.com/ricardoquesada/vchar64](https://github.com/ricardoquesada/vchar64)

{{< youtube lb7UNIhoyoI >}}

Changelog:

- \[NEW\] Charset and Tilset widgets have grid and zoom levels
- \[NEW\] Map Widget: can enter tiles by using the keyboard
- \[NEW\] Map Widget: can enter tiles by using ALT + tile\_number
- \[NEW\] Beeps are only played when there is an error. Before two beeps were used on errors. Now a single beep.
- \[BUGFIX\] Export: uses the name of recently saved project
- \[BUGFIX\] Export Dialog: tab-order fixed
- \[BUGFIX\] Copy/Paste: doesn't allow copy paste invalid buffers
- \[BUGFIX\] Cut: works as expected when using "inverse" range state->cut() no longer receives an offset since the offset is taken from the range
- \[BUGFIX\] Cut: doesn't crash if cut is triggered when no window has focus
- \[BUGFIX\] Map widget: selecting with keyboard for the first time works as expected
- \[BUGFIX\] Maps scrolls normal speed (even big maps)
- \[BUGFIX\] TilesetWidget and CharsetWidget use zoomLevel to instead of pixelSize for zooming. Faster and less memory(?)
- \[BUGFIX\] Resizing maps works as expected
- \[BUGFIX\] Displays correct tile in map when tile is resized. Doesn't crash on debug mode as well.
