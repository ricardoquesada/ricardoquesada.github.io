---
author: ricardoquesada
category: retro computing
date: "2016-03-02T07:16:41+00:00"
guid: http://retro.moe/?p=1243
tag:
  - c64
  - vchar64
title: VChar64 v0.0.12 released
url: /2016/03/01/vchar64-v0-0-12-released/

---
New version, new features.

### Download

- Mac: [vchar64-0.0.12.dmg.zip](https://github.com/ricardoquesada/vchar64/releases/download/0.0.12/vchar64-0.0.12.dmg.zip)
- Win32: [vchar64-0.0.12.win32.zip](https://github.com/ricardoquesada/vchar64/releases/download/0.0.12/vchar64-0.0.12.win32.zip)

### Changes

- \[NEW\] Koala Import: supports importing subregions. Useful when 256 chars are not enough to import the whole bitmap
- \[NEW\] Added unknown font. Ripped from [here](http://csdb.dk/release/?id=144857)
- \[NEW\] VICE snapshot import: Default charset address is the one that was used at the moment the snapshot was taken
- \[NEW\] Save/Export: Plays one beep on success, two beeps on error
- \[NEW\] Main Window: Status Bar shows the coordinates of the different widgets
- \[BUGFIX\] Export: shows correct extension when browsing file
- \[BUGFIX\] VICE/Koala Import: sets the name of the imported file in the tab
- \[BUGFIX\] Koala Import: detects duplicates chars, making the conversion smaller

{{< youtube 2avAMmbQqRA >}}
