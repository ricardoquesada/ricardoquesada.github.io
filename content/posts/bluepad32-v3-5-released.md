---
author: ricardoquesada
category: embedded
date: "2022-07-11T00:52:50+00:00"
guid: https://retro.moe/?p=2537
tag:
- bluepad32
- esp32
- unijoysticle
title: Bluepad32 v3.5 released!
url: /2022/07/10/bluepad32-v3-5-released/

---

**TL;DR:** Support for Amiga and Atari ST mice, USB console, and re-connect
improvements.

I 'm happy to announce that Bluepad32 v3.5 has been released. It contains two
new big features:

- Mouse support
- Console

and many fixes & improvements here and there.

### Mouse support

![](https://lh3.googleusercontent.com/pw/AM-JKLXCbot-0O4NAF-2BWhf62lrRxDvdhXbfFaWhrWXQ_Hv_mAPRj1e-XF4-SxpoX_sTzBEcr_PDMqlsOz4ePWibi3h7IrfaevQW_jxMRlG2j0wnROhzf37BvG6IRvA1PPveChSrSLBy7yndHY2eMiJB1-NNA=-no)
<small>*Some of the supported mice.*</small>

Mouse support has been added both at the "core" level, and at a "platform"
level.

By "core" level, I mean that all platforms (Unijoysticle, NINA/AirLift, Arduino,
etc.) receive the mouse information: x & y movement and the Left, Middle and
Right buttons.

And by "platform" level, I mean that the Unijoysticle platform transforms the
mouse data into quadrature events that both Amiga and Atari ST computers can
understand.

{{< youtube cE4u50y5TOI >}}

<small>*Using mouse on the Amiga 500.*</small>

See the complete list of supported mice
here: [supported mice](https://gitlab.com/ricardoquesada/bluepad32/-/blob/main/docs/supported_mice.md)

### Console support

Before v3.5, it was possible to see the logs by connecting to a serial
terminal (e.g: via a USB cable).

Now, it is possible to interact with the serial terminal. Just connect the
device with a USB cable, and type:

```shell
minicom -D /dev/ttyUSB0
```

[![](https://asciinema.org/a/506468.svg)](https://asciinema.org/a/506468)

Some useful commands are:

- `list_devices`: dumps info about connected devices
- `set_bluetooth_enabled <1 | 0>`: To enable/disable Bluetooth pairing mode
- `set_mouse_scale <scalee>:` To change how fast/slow the mouse should move
- `set_autofire_cps`: To change the rate of autofire
- `help`: To see all the available commands :)

### Other improvements

- DualSense and DualShock 3 / 4: Reconnect works!
- Improved Switch controllers re-connection
- DualShock 3 works without the need to recompile the firmware.
- Added support for Wii Balance board (experimental)
- Improvements in different platforms:
    - Unijoysticle: Added support for the A500 device, supports console, and
      more.
    - NINA/AirLift: Added support for enabling/disabling Bluetooth
    - Arduino: Added support for enabling/disabling Bluetooth, added Console
      class (that uses the new USB Console).

### Download and Changelog

Download it from the usual
place: [Bluepad32 releases](https://gitlab.com/ricardoquesada/bluepad32/-/releases)

And the complete changelog is
here: [CHANGELOG](https://gitlab.com/ricardoquesada/bluepad32/-/blob/main/CHANGELOG.md)

### Thanks

Many thanks for the community for the testing, contributing patches and ideas.

See complete credits
here: [AUTHORS](https://gitlab.com/ricardoquesada/bluepad32/-/blob/main/AUTHORS)
