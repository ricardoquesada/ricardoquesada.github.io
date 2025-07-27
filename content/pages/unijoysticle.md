---
author: ricardoquesada
date: "2016-04-06T08:41:41+00:00"
guid: http://retro.moe/?page_id=1338
title: Unijoysticle™
url: /unijoysticle/

---
![logo.png](/wp-content/uploads/2016/04/logo2.png)

### What is The UniJoystiCle?

It is a unicycle simulator for the Commodore 64. It allows you to play a unicycle video game using a real unicycle.

It also allows you to play games with real Game Controllers, or by using gravity. But that is secondary.
[More info here](https://github.com/ricardoquesada/unijoysticle/blob/master/DOCUMENTATION.md).

{{< youtube ZLAgooXx4bo >}}

It consists of:

- The video game: _The Uni Games_ for the Commodore 64
- The WiFi device, and its firmware
- The smartphone application

### The _The Uni Games_ video game

|            Main Menu            |             Level 1             |             Level 2             |
|:-------------------------------:|:-------------------------------:|:-------------------------------:|
| ![](/images/uni1_unigames1.png) | ![](/images/uni1_unigames2.png) | ![](/images/uni1_unigames3.png) |

Coded 100% in 6502 assembly language, this video game features:

- Player-vs-Player or Player-vs-Computer mode
- Three events:
  - Road Race
  - Cyclo Cross
  - Cross Country
- Realistic physics
- Cutting edge graphics
- Awesome music

Available for the Commodore 64 (and Commodore 128). Supports PAL, NTSC and Drean machines.

![floppy](/images/uni1_diskette.jpg)
<small>The _Uni Games_ 5 1/4"floppy disk</small>

**Download**:

- Binary version: [unigames.d64](https://github.com/ricardoquesada/c64-the-uni-games/raw/master/bin/unigames.d64) v0.4 (Compatible with [VICE C64](http://vice-emu.sourceforge.net/) emulator)
- Source code: [https://github.com/ricardoquesada/c64-the-uni-games](https://github.com/ricardoquesada/c64-the-uni-games)

### The UniJoystiCle WiFi device

Decodes joystick movements sent from your smartphone. It forwards the received data back to the Commodore 64.

![](/images/uni1_unigames_title.jpg)
<small>_The UniJoystiCle in all its beauty_</small>

The WiFi device consists of:

- The firmware, that runs in the ESP8266 WiFi microcontroller
- And the [board](https://oshpark.com/shared_projects/ylE6XNMG):

![](/images/uni1_device.jpg)
<small>_UniJoystiCle WiFi device v0.4.1_</small>

Coded 100% in C++, the firmware uses a fast network protocol. Responsiveness is a top priority. Works with any ESP8266 module, and its range is more than 1000ft.

**Download:**

- Circuit: [https://github.com/ricardoquesada/unijoysticle/tree/master/schematic](https://github.com/ricardoquesada/unijoysticle/tree/master/schematic)
- Firmware for the ESP8266: [https://github.com/ricardoquesada/unijoysticle/tree/master/esp8266\_firmware](https://github.com/ricardoquesada/unijoysticle/tree/master/esp8266_firmware)

### The UniJoystiCle smartphone application

|                                |                                |                                |
|--------------------------------|--------------------------------|--------------------------------|
| ![](/images/uni1_iphone1.jpeg) | ![](/images/uni1_iphone2.jpeg) | ![](/images/uni1_iphone3.jpeg) |

This smartphone application reads the accelerometer data from the smartphone and converts it to joystick movements. It sends the data to the UniJoystiCle WiFi device in a fast and reliable way. Reliability a responsiveness is a top priority.

Features:

- UniJoystiCle mode: Use this mode to play [_The Uni Games_](https://github.com/ricardoquesada/c64-the-uni-games) and any other game that can be played in rotating
the joystick, like the Bike event in _[Summer Games II](http://gamebase64.com/game.php?id=7547&d=18&h=0)._
- D-pad mode: To play the rest of the games, like [Commando](http://gamebase64.com/game.php?id=1602&d=18&h=0), [Bruce Lee](http://gamebase64.com/game.php?id=1135&d=18&h=0), etc.
  - D-pad + Game Controller: To play the rest of the games using a real Game Controller. Ideal for [Giana Sisters](http://gamebase64.com/game.php?id=3275&d=18&h=0), [Super Bread Box](http://gamebase64.com/game.php?id=24140&d=18&h=0), etc.
- Commando mode: Control both joysticks at the same time from just one Game Controller.
- Gyruss mode: A novel way to play [Gyruss](http://gamebase64.com/search.php?f=0&t=0&s=gyruss&searchSubmit=Go%21&d=18&h=1&a=0) and Gyruss-like video games.
- Commodore Home mode: For "[Commodore Home](/2016/10/31/retro-challenge-commodore-home/)", home automation for the masses, not the classes

**Download**

Download it directly from the iOS App Store / Google Play Store:

[![UniJoystiCle App Store](https://lh3.googleusercontent.com/-688E2CSvrkU/V3soSoi1n2I/AAAAAAABevw/LzjvUtBv5yAEiWmm9B4YhkrYTDctbr89gCCo/s800/Download_on_the_App_Store_Badge_US-UK_135x40.png)](https://itunes.apple.com/us/app/unijoysticle-controller/id1130131741?mt=8)
[![Get it on Google Play](https://lh3.googleusercontent.com/nUm_upw_pznWfcD9pp71LPhpwdTMd6L7LVBK2Bw3UoAaiD0AFkTc1P6Gfl1MXiy7mOaApxVLdUMWXA=w564-h168-no)](https://play.google.com/store/apps/details?id=moe.retro.unijoysticle&utm_source=global_co&utm_medium=prtnr&utm_content=Mar2515&utm_campaign=PartBadge&pcampaignid=MKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1)

Or alternatively, you can download the [source code and compile it yourself](https://github.com/ricardoquesada/unijoysticle/tree/master).

## What people are saying

 [![](https://lh3.googleusercontent.com/-IcyQi5pYYyA/V2l6oehKBDI/AAAAAAABecU/22wcMzCV-fYoOSjHRFW9UnjyzR6SryxJwCCo/s400/The_Verge_logo.svg.png)](http://www.theverge.com/circuitbreaker/2016/5/2/11564612/unicycle-video-game-controller-hack-commodore-64) [_"Unicycles are totally the next immersive video game experience"_](http://www.theverge.com/circuitbreaker/2016/5/2/11564612/unicycle-video-game-controller-hack-commodore-64)
 [![](https://lh3.googleusercontent.com/-zeMkobWc6sU/V2lzf2cfGuI/AAAAAAABeb4/weFs1GtVva0lBL0rdPwRL3epBfikqd9lACCo/s800/hack-a-day_site_logo_2.png)](http://hackaday.com/2016/04/27/the-immersive-vr-internet-of-things-unicycle) [_"The world’s first unicycle controller, and the first video game to use this truly immersive, better than Oculus"_](http://hackaday.com/2016/04/27/the-immersive-vr-internet-of-things-unicycle/)
 [![](https://lh3.googleusercontent.com/-PYqpZ5-9FEc/V2l2Jz3j0qI/AAAAAAABecI/FK3Qrl3MKKUmKie4HONIjewtSuSJVcpnACCo/s800/finalLogo_croppedx253.png)](http://www.epicthings.com/control-your-videogames-with-a-unicycle/) [_"You Can Finally Control A Video Game With A Unicycle"_](http://www.epicthings.com/control-your-videogames-with-a-unicycle/)

## Documentation

- HTML version: [UniJoystiCle Documentation](https://github.com/ricardoquesada/unijoysticle/blob/master/DOCUMENTATION.md)

## Order The UniJoystiCle WiFi device today!

### Option A) The Board

![](/images/uni1_device_assembled.jpg)
<small>_The UniJoystiCle WiFi Board_</small>

- $50 + shipping
- Fully tested + assembled + soldered

### Option B) The Kit

![](/images/uni1_device_kit.jpg)
<small>_The UniJoystiCle WiFi Kit_</small>

- $30 + shipping
- Includes all the needed components
- Soldering required. All components are through-hole
- Firmware comes pre-installed

### Option C) DIY

- Free!
- All the [schematics + PCB + firmware files are available for FREE](https://github.com/ricardoquesada/unijoysticle/tree/master/schematic)
- The Bill Of Material (BOM) is here: [DOCUMENTATION.md](https://github.com/ricardoquesada/unijoysticle/blob/master/DOCUMENTATION.md#building-the-wifi-device)

To order it, contact me at: [https://twitter.com/ricardoquesada](https://twitter.com/ricardoquesada) or [unijoysticle@gmail.com](mailto:unijoysticle@gmail.com)
