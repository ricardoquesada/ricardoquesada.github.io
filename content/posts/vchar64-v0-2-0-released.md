---
author: ricardoquesada
category: retro computing
date: "2016-08-29T04:34:06+00:00"
guid: http://retro.moe/?p=1859
tag:
- commodore 64
- vchar64
title: VChar64 v0.2.0 released
url: /2016/08/28/vchar64-v0-2-0-released/

---

VChar64 v0.2.0 is available for download:

- Win32: [vchar64-0.2.0.win32.zip](https://github.com/ricardoquesada/vchar64/releases/download/0.2.0/vchar64-0.2.0.win32.zip)
- Mac: [vchar64-0.2.0.mac.dmg](https://github.com/ricardoquesada/vchar64/releases/download/0.2.0/vchar64-0.2.0.mac.dmg)

![](https://lh3.googleusercontent.com/tB3Z3gksYisFmrUL1kE4iANPPsqMGaLrwizc-Ysm3SxFTrUseq-lZgAuB7zDTLayAMlguTSSsY9slw=w1192-h1052-no)
<small>*New "VICE Import Snapshot" dialog.*</small>

Changes:

- [NEW] Issue [#13](https://github.com/ricardoquesada/vchar64/issues/13): Import VICE Snapshot supports importing maps as well
- [NEW] Issue [#14](https://github.com/ricardoquesada/vchar64/issues/14 "Add Session concept"):
  Possibility to restore the last open files at launch. Enabled by default
- [NEW] Issue [#17](https://github.com/ricardoquesada/vchar64/issues/17): Added "File -> Clone Current Project"
- [NEW] Auto Update: Check if there is a new version every 7 days. Enabled by
  default
- [BUGFIX] Issue [#11](https://github.com/ricardoquesada/vchar64/issues/11): Doesn't crash when clicking radios on empty Koa file
- [BUGFIX] Issue [#15](https://github.com/ricardoquesada/vchar64/issues/15): Menu->Colors->Multicolor are enabled/disabled as expected
- [BUGFIX] Issue [#16](https://github.com/ricardoquesada/vchar64/issues/16): Map/Charset/Tileset: Backward selection works as expected
- [BUGFIX] Opening an already-open file will activate that window instead of
  opening a duplicate tab
- [BUGFIX] Moves references to retro.moe/pungas.space from empty charset to
  About dialog
- [BUGFIX] Fix memory leak when deleting a State instance
- [BUGFIX] Fix crash when using the Map widget with no open documents
- [BUGFIX] Settings code unified in Preferences code. OpenLastDir settings bug
  fixed
