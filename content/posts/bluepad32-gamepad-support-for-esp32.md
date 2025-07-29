---
author: ricardoquesada
category: embedded
date: "2020-11-24T15:23:42+00:00"
guid: http://retro.moe/?p=2274
tag:
- bluepad32
- circuitpython
- unijoysticle
title: 'Bluepad32: Gamepad support for ESP32'
url: /2020/11/24/bluepad32-gamepad-support-for-esp32/

---

[![](/wp-content/uploads/2020/11/bluepad32-logo.png?w=842)](/wp-content/uploads/2020/11/bluepad32-logo.png)

I'm happy to announce the release of Bluepad32: gamepad support for the ESP32.

Bluepad32 is a firmware that runs in the ESP32 microcontroller. It supports all
the modern Bluetooth gamepads like Sony (PS5, PS4, PS3), Microsoft (Xbox One S)
and Nintendo (Switch, Wii) gamepads.

{{< youtube V0AGUe-CrEY >}}

### Who is this for?

This is for:

- ...tinkers / makers / electronic hobbyist
- ...that want to add gamepad support into their projects
- ...in a maintainable and easy way

For further info,
read: [Adding new platforms.](https://gitlab.com/ricardoquesada/bluepad32/-/blob/master/docs/adding_new_platform.md)

### Real world examples

- [Unijoysticle 2](/unijoysticle2/): Gamepad support for the Commodore 64 /
  Amiga / etc.
- [MatrixPortal M4](https://www.youtube.com/watch?v=dbEbiJZd4n8): Gamepad
  support for the [Adafruit AirLift](https://www.adafruit.com/product/4745)
  family of boards.
- [ULX3S](https://www.crowdsupply.com/radiona/ulx3s): An FPGA-based computer.

Just add an ESP32 to your project, and control it with a gamepad!

### Features

- [Supports most, if not all, modern Bluetooth gamepads](https://gitlab.com/ricardoquesada/bluepad32/-/blob/master/docs/supported_gamepads.md)
- Fast (very low latency)
- Small footprint
- Uses only one core (CPU0). The remaining one is free to use.
- C99 based
- Open Source (see below)

### Source Code, License et. al

- Bluepad32 is open source, Apache 2 licensed
- Source code:
    - Gitlab: [https://gitlab.com/ricardoquesada/bluepad32/](https://gitlab.com/ricardoquesada/bluepad32)
    - Github (mirror): [https://github.com/ricardoquesada/bluepad32](https://github.com/ricardoquesada/bluepad32)

However Bluepad32 depends on the
great [BTStack library](https://bluekitchen-gmbh.com/). Which is free to use for
open source projects. But commercial for closed projects. Contact them for
details. They are very friendly + helpful (I'm not affiliated with them).

### Support, bugs et. al

- [File bugs in Gitlab](https://gitlab.com/ricardoquesada/bluepad32/-/issues)
- Or use ["Bluepad32" channel is Discord](https://discord.com/channels/775177861665521725/775177925938642945)
- Or [use the Unijoysticle mailing list](https://groups.google.com/g/unijoysticle)

### How is this related to Unijoysticle 2

I realized that 3rd party projects where using the Unijoysticle 2 firmware. But
they needed to hack it here and there. And it was difficult for them to get
changes from upstream, etc.

So what I did was to:

- take the Unijoysticle 2 firmware
- make many changes to it to make it [super easy to integrate](https://gitlab.com/ricardoquesada/bluepad32/-/blob/master/docs/adding_new_platform.md)
- rename it to avoid confusion (Bluepad32 is the new name)
- host it in a new [git repo](https://gitlab.com/ricardoquesada/bluepad32)

(BTW, I'm also the author of Unijoysticle 2)
