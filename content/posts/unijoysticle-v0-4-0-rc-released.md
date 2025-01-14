---
author: ricardoquesada
category:
  - commodore-64
date: "2016-11-08T08:52:02+00:00"
guid: http://retro.moe/?p=1959
summary: "UniJoystiCle v0.4.0-RC (Release Candidate) released. Mega update!\n\n \n\n**Download:**\n\n- iOS client v0.4.6: [App Store](https://itunes.apple.com/us/app/unijoysticle-controller/id1130131741?mt=8)\n- Android client v0.4.10: [Google Play](https://play.google.com/store/apps/details?id=moe.retro.unijoysticle)\n- macOS client v0.4.0: [UniJoystiCle Controller.dmg](http://ricardoquesada.github.io/unijoysticle/bin/UniJoystiCle%20Controller-v0.4.0.dmg)\n- win32 client v0.4.0: [unijoysticle\\_controller.win32.zip](http://ricardoquesada.github.io/unijoysticle/bin/unijoysticle_controller-v0.4.0.win32.zip)\n- Firmware v0.4.5: [unijoysticle\\_firmware.bin](http://ricardoquesada.github.io/unijoysticle/bin/unijoysticle_firmware.bin)\n- Source code + schematic + layout: [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)\n\nLatest versions can be downloaded from here:  [http://ricardoquesada.github.io/unijoysticle/](http://ricardoquesada.github.io/unijoysticle/)"
tag:
  - c64
  - commodore-home
  - unijoysticle
title: UniJoystiCle v0.4.0-RC released!
url: /2016/11/08/unijoysticle-v0-4-0-rc-released/

---
UniJoystiCle v0.4.0-RC (Release Candidate) released. Mega update!

{{< figure align=alignnone width=460 src="https://lh3.googleusercontent.com/OmLhbq2kLmIZC0WUcI8J8vpe8m5mMwCQfM414QkjSXIkV9tuEEtxiied4YfagVgNWJMujdTqMisa9A=w1808-h1356-no" alt="" >}}

**Download:**

- iOS client v0.4.6: [App Store](https://itunes.apple.com/us/app/unijoysticle-controller/id1130131741?mt=8)
- Android client v0.4.10: [Google Play](https://play.google.com/store/apps/details?id=moe.retro.unijoysticle)
- macOS client v0.4.0: [UniJoystiCle Controller.dmg](http://ricardoquesada.github.io/unijoysticle/bin/UniJoystiCle%20Controller-v0.4.0.dmg)
- win32 client v0.4.0: [unijoysticle\_controller.win32.zip](http://ricardoquesada.github.io/unijoysticle/bin/unijoysticle_controller-v0.4.0.win32.zip)
- Firmware v0.4.5: [unijoysticle\_firmware.bin](http://ricardoquesada.github.io/unijoysticle/bin/unijoysticle_firmware.bin)
- Source code + schematic + layout: [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)

Latest versions can be downloaded from here:  [http://ricardoquesada.github.io/unijoysticle/](http://ricardoquesada.github.io/unijoysticle/)

**Summary:**

- Use your Xbox game controllers to play C64 games! (from the Win32 client)
- Use any iOS or Android game controller to play C64 games! (from the iOS/ Android client)
- Play games like [Commando](http://gamebase64.com/game.php?id=1602&d=18&h=0) and [Turrican II](http://gamebase64.com/game.php?id=8234&d=18&h=0) by only using your game controller. "Space" is mapped to button "B". There is no need to press the "spacebar"
- Put your device in Station mode (share your local Wifi network).

**Full Changelog**:

- \[NEW\] Docs: Added documentation. See [DOCUMENTATION.md](https://github.com/ricardoquesada/unijoysticle/blob/master/DOCUMENTATION.md)
- \[NEW\] ESP8266 Schematic: Reduced real state. Compatible with C128D and SX-64
- \[NEW\] ESP8266 Schematic: Uses [Wemos D1 Mini v2](https://www.aliexpress.com/store/product/D1-mini-Mini-NodeMcu-4M-bytes-Lua-WIFI-Internet-of-Things-development-board-based-ESP8266/1331105_32529101036.html) instead of NodeMCU to reduce the real state even more. Making it smaller than 5x5cm. Cheaper to produce

  - D1 Mini v2 uses [CH340 USB-to-UART](https://www.wemos.cc/downloads) chip instead of the CP2102.
- \[NEW\] Firmware: Added support for Station mode with or without WPS.
- \[NEW\] Firmware: Added stats: how many joysticks movements are done, and how
  many seconds are spent in each movement
- \[NEW\] Firmware: Added mini webserver (http://unijoysticle.local). Use it to
  view the stats, to set SSID/passwd, to change to Station mode, to
  change the MDNS name, to set the interval timeout, and more
- \[NEW\] Client: Added Commando Mode:
  - Control both c64 joysticks with one game controller.
  - Ideal for games like [Commando](http://gamebase64.com/game.php?id=1602&d=18&h=0) or [Turrican 2](http://gamebase64.com/game.php?id=8234&d=18&h=0) were the grenades can be thrown with button B.
  - Buttons B, X and Y are mapped to Joy#1 fire (or space), Joy#1 down and
    Joy#1 right respectively
- \[NEW\] Client: Added Commodore Home mode:
  - It's "Home automation for the masses, not the classes"
  - Replaced the old Linear mode
- \[NEW\] Android Client: new client for android. Supports:
  - UniJoystiCle mode
  - Dpad mode + controllers: Generic and OUYA game controllers
  - Commando mode: Generic and OUYA game controllers
  - Commodore Home mode
  - Settings
  - Resolves unijoyticle.local address
  - Can display the server stats from Settings
  - Basically it supports all iOS features except Gyruss mode
- \[NEW\] iOS Client: D-Pad works with MFi and iCade game controllers.
  - When in iCade mode, button A and D act as Fire, and buttons B and C and jump
- \[NEW\] iOS Client: When using game controllers, optionally jump with button B.
- \[NEW\] iOS Client: When using game controllers, buttons A and B can be swapped
- \[NEW\] Tests: New Commodore 64 prg to test the UniJoystiCle + instructions
- \[FIX\] Android Client / iOS Client: In settings, the default WiFi address is 'unijoysticle.local'
  (instead of 192.168.4.1). Needed when in Station mode
- \[FIX\] Android Client / iOS Client: Instead of sending the state 60 times per
  seconds, it sends twice per state change. Saves battery life!
- \[FIX\] iOS Client: Gravity Mode renamed to Gyruss Mode
- \[FIX\] iOS Client: UniJoystiCle Mode: rotation direction fixed.
- \[FIX\] iOS Client: Settings: refactored. Looks nicer. Using Navigation Controller + TableView
- \[FIX\] iOS Client: Launch screen is the same as the first initial screen. Better UX
- \[FIX\] iOS Client: Settings + Launch screen work both in Portrait and Landscape modes
- \[FIX\] iOS Client: source code migrated to Swift 3.0 (Xcode 8.1)
