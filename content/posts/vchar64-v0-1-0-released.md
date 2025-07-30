---
author: ricardoquesada
category: retro computing
date: "2016-07-15T13:16:41+00:00"
guid: http://retro.moe/?p=1778
tag:
- commodore 64
- vchar64
title: VChar64 v0.1.0 released
url: /2016/07/15/vchar64-v0-1-0-released/

---

This is mostly a bug-fix release, focused on improving the workflow.

Download:

- Mac: [vchar64-0.1.0.mac.dmg](https://github.com/ricardoquesada/vchar64/releases/download/0.1.0/vchar64-0.1.0.mac.dmg)
- Win32: [vchar64-0.1.0.win32.zip](https://github.com/ricardoquesada/vchar64/releases/download/0.1.0/vchar64-0.1.0.win32.zip)
- Source code: [https://github.com/ricardoquesada/vchar64](https://github.com/ricardoquesada/vchar64)

{{< figure align=alignnone width=354 src="https://lh3.googleusercontent.com/-jkXj58CQx5s/V4jgmQvSw4I/AAAAAAABe1c/TIH6T4giz3Y1xp2woZ1xGCAayHa-5SnxQCCo/s640/Screen%2BShot%2B2016-07-15%2Bat%2B6.09.13%2BAM.png" alt="" >}}

Changes:

- [NEW] Export: saves exported addresses in vcharproj file. Increased version to 3
- [BUGFIX] Compiles on Ubuntu 16.04
- [BUGFIX] Export: Export As shows most recent export addresses
- [BUGFIX] Export: generates an Undo event only if it is different than previous
  state
- [BUGFIX] Save: sets the Undo Stack as clean, but doesn't clear it
- [BUGFIX] Save: saved files are appended to the recent files entry
- [BUGFIX] Recent Files: Non existing entries appear as disabled
- [BUGFIX] Multicolor: radios are enabled/disabled accordingly
- [BUGFIX] Multicolor: copy & paste updates multicolor as well

Changes in the binaries:

- Binaries were compiled with Qt 5.7. Previous version was compiled with Qt 5.6
- Win32 binary was compiled with mingw v5.3. Previous version was using v4.9.2
