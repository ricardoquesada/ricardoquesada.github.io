---
author: ricardoquesada
category:
  - commodore-64
date: "2016-10-31T20:13:49+00:00"
guid: http://retro.moe/?p=1913
summary: |-
  ### **Home automation for the masses, not the classes**

  > We need to build computers for the masses, not the classes - Jack Tramiel, Commodore founder

  ### [![commodore_home](https://retro.moe/wp-content/uploads/2016/10/commodore_home.png)](https://retro.moe/wp-content/uploads/2016/10/commodore_home.png)

  - A: Commodore 64 computer running the "Commodore Home" application
  - B: [UniJoystiCle WiFi device](https://retro.moe/unijoysticle/) connected to the joystick ports
  - C: Alarm sensor using a WiFi device
  - D: Smartphone running the UniJoystiCle Controller app with the Commodore Home plugin
  - E: Commodore MPS 803 printer
  - F: Pulleys + gears connected to the printer header + dimmer knot
tag:
  - c64
  - commodore-home
  - esp8266
  - retrochallenge
  - unijoysticle
title: 'Retro Challenge: announcing Commodore Home'
url: /2016/10/31/retro-challenge-commodore-home/

---
### **Home automation for the masses, not the classes**

> We need to build computers for the masses, not the classes - Jack Tramiel, Commodore founder

### [![commodore_home](/wp-content/uploads/2016/10/commodore_home.png)](/wp-content/uploads/2016/10/commodore_home.png)

- A: Commodore 64 computer running the "Commodore Home" application
- B: [UniJoystiCle WiFi device](/unijoysticle/) connected to the joystick ports
- C: Alarm sensor using a WiFi device
- D: Smartphone running the UniJoystiCle Controller app with the Commodore Home plugin
- E: Commodore MPS 803 printer
- F: Pulleys + gears connected to the printer header + dimmer knot

## About

Why pay hundreds of dollars to automate your home, when you can automate it for free with existing tools/computers that you might already have in your garage?

Automate your home using a smartphone, a Commodore 64 and a dot matrix printer!

## Features

It supports:

- Music player
- Smart light system
- Alarm system

### Music Player

{{< figure align=alignnone width=384 src="/wp-content/uploads/2016/10/capture.png" alt="" >}}

It comes preloaded with classics from the 80's, like Billie Jean, The Final Countdown and Pop Goes the World.  Listen to the unmatched chiptune sound. Control the music player from your smartphone!

### **Smart Light System**

{{< figure align=alignnone width=474 src="/wp-content/uploads/2016/10/printer%5Flights.jpg" alt="" >}}

Don't pay hundreds of dollars to have "smart" light bulbs. Instead, control them with your dot matrix printer! Attach a few pulleys and gears to your printer header, and control the lights and dimmers from your smartphone!

It is possible to control more than one light by daisy chaining the printers! **How handy!**

### Alarm System

{{< figure align=alignnone width=384 src="/wp-content/uploads/2016/10/intruder.png" alt="" >}}

Know when an authorized person enters your home. A siren sound + a blinking "Intruder Alert" screen will be displayed on the C64.

Future versions will have modem support: When an intruder is detected, it will dial your favorite BBS and leave you a message there. **How handy!**

## Building the Commodore Home

#### **The UniJoystiCle WiFi device**

Commodore Home uses the [UniJoystiCle technology](/unijoysticle/) to communicate with the C64. It is a device that allows you to control the two joysticks from your smartphone.

{{< figure align=alignnone width=366 src="/wp-content/uploads/2016/10/img%5F5276.jpg" alt="" >}}

The instructions to build and setup one are here: [DOCUMENTATION.md](https://github.com/ricardoquesada/unijoysticle/blob/master/DOCUMENTATION.md). ( [Ping me](mailto:unijoysticle@gmail.com) if you want an already built+assembled+tested unit. I sell them for $40+shipping).

#### **The alarm system**

{{< figure align=alignnone width=431 src="/wp-content/uploads/2016/10/alarm%5Fmodules.jpg" alt="" >}}

It consists of a magnetic sensor + WiFi device. When the sensor is open, the WiFi device will send the "trigger alarm" command to the C64.

Bill of Materials:

- [Wemos D1 Mini v2](https://www.aliexpress.com/store/product/D1-mini-Mini-NodeMcu-4M-bytes-Lua-WIFI-Internet-of-Things-development-board-based-ESP8266/1331105_32529101036.html) ($4.00)
- [Wemos Proto Shield for D1 Mini](https://www.aliexpress.com/store/product/ProtoBoard-Shield-for-WeMos-D1-mini-double-sided-perf-board/1331105_32627711647.html) ($0.99)
- [Wemos Battery Shield for D1 Mini](https://www.aliexpress.com/store/product/Battery-Shield-For-WeMos-D1-mini-single-lithium-battery-charging-boost/1331105_32679485736.html) ($2.50)

  - Warning: it comes with an XH2.54 connector. You might need an adaptor
  - Warning: check the polarity!
- [Magnetic Sensor](http://www.ebay.com/itm/like/221517946005?lpid=82&chn=ps&ul_noapp=true) ($1.89)
- v3.7 LiPo Battery

Connect "A0" (analog input) to the NC (Normally Closed) magnetic pin. And connect "v3.3" to the Com magnetic pin.

{{< figure align=alignnone width=286 src="/wp-content/uploads/2016/10/untitled-sketch%5Fbb.png" alt="" >}}

And then upload the firmware to the device:

- Download [Platform.io](http://platformio.org/)
- Install the [CH340 USB-to-serial driver](https://www.wemos.cc/downloads)
- Clone the Commodore Home project:
  - [https://github.com/ricardoquesada/c64-home.git](https://github.com/ricardoquesada/c64-home.git)
- And build and upload:
  - ```
    $ cd alarm_firmware
    $ make upload

    ```

(pre-compiled firmware coming soon. **done: see below)**.

The Alarm WiFi will boot in Access Point mode. Connect to its WiFi network  (it is called "commodore home alarm") and open this URL:

- [http://commodore\_home\_alarm.local/](http://commodore_home_alarm.local/)

Then configure the network parameters:

- Put it in Station mode
- Put the correct SSID and password
- Put the UniJoystiCle IP address

[![alarm_syste_setup](/wp-content/uploads/2016/10/alarm_syste_setup.png)](/wp-content/uploads/2016/10/alarm_syste_setup.png)

...and done. The alarm system is ready to go!

#### The Commodore 64 application

{{< figure align=alignnone width=384 src="/wp-content/uploads/2016/10/printer%5Ferror.png" alt="" >}}

The latest binary version can be downloaded from here:

- [c\_home\_exo.prg](https://github.com/ricardoquesada/c64-home/raw/master/bin/c_home_exo.prg)

The source code is here: [https://github.com/ricardoquesada/c64-home](https://github.com/ricardoquesada/c64-home)

If you don't have a UniJoystiCle WiFi device, it can be controlled with the keyboard. Just DO NOT use it with a joystick in port #2.

If there is an error with the printer (like printer not connected), it will change the border color.

#### The Smartphone application

{{< figure align=alignnone width=165 src="/wp-content/uploads/2016/10/commodore%5Fhome%5Fandroid.png" alt="" >}}

The Android application can be download from Google Play:

[![Get it on Google Play](https://lh3.googleusercontent.com/nUm_upw_pznWfcD9pp71LPhpwdTMd6L7LVBK2Bw3UoAaiD0AFkTc1P6Gfl1MXiy7mOaApxVLdUMWXA=w564-h168-no)](https://play.google.com/store/apps/details?id=moe.retro.unijoysticle&utm_source=global_co&utm_medium=prtnr&utm_content=Mar2515&utm_campaign=PartBadge&pcampaignid=MKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1)

The Source code is here: [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)

The iOS and Desktop UniJoystiCle applications don't have the "Commodore Home" plugin yet (coming soon. **done: see below)**.

#### Connecting the printer

{{< figure align=alignnone width=700 src="/wp-content/uploads/2016/10/printer.jpg" alt="" >}}

Just connect the printer as device "4" (not "5"). Insert a piece of paper (doesn't work without one), and connect the gears to the printer header.

It was tested with the MPS 803 printer and it works Ok. But it doesn't work with the Okimate 10 printer since it places the printer header back to the left after each command. So, use the MPS 803.

## Videos

{{< youtube wH3g09zsTdY >}}

{{< youtube dEgbWc3G7pQ >}}

{{< youtube GhbnYS\_Yj\_s >}}

## Things that I did for the Retrochallenge

- C64 application (Assembly). Mostly a copy & paste from projects that I worked on before:
  - Reused the music player from [chipdisk](https://github.com/c64scene-ar/chipdisk)
  - Reused menu system from [The Uni Games](https://github.com/ricardoquesada/c64-the-uni-games)
  - Reused "UniJoystiCle Compatible" intro screen from [The Uni Games](https://github.com/ricardoquesada/c64-the-uni-games)
  - I knew how to move the printer header using the BASIC "print#" command. But I had to do some research to move it using assembly.
  - Used [VChar64](https://github.com/ricardoquesada/vchar64) to design the screens/fonts.
  - I didn't compose the songs. I grabbed them from [HVSC](http://www.hvsc.c64.org/).
- Android application(Java)

  - Wrote the "Commodore Home" UniJoystiCle plugin. It replaced the old "Linear mode" plugin.
- Firmware for the Alarm system (C):
  - It was mostly a copy & paste from the [UniJoystiCle firmware](https://github.com/ricardoquesada/unijoysticle/tree/master/esp8266_firmware/firmware) that I did before.
- Alarm design:
  - Quick and dirty design: using the A0 (analog pin) from the ESP8266.
- UniJoystiCle Desktop application (C++):
  - I was able to have a working prototype using the "linear mode" but in the end I haven't used it. I'll continue working on it later. It will be useful for UniJoystiCle users.
- UniJoystiCle PCB v0.4.1 (Eagle):
  - Designed v0.4.1 during the Retro Challenge, but I received the PCBs only two days before the deadline. So, for Commodore Home I used the previous version (v0.4.0).
- Pulley / Gear system:
  - I was able to move the dimmer knot with pulleys+gears. Only by [moving the gears manually](https://www.youtube.com/watch?v=Xu7uzjWlCcM).
  - I didn't have the time to attach the toothed bar to the printer header.

## Postmortem

This was my first participation in the [Retro Challenge](http://retrochallenge.net/) competition. Overall, I'm happy with the outcome: I was able to finish most of the stuff that I wanted to do, but I'm exhausted. A few things to improve:

- Decide what to do from day 1. I started building the C64 I.D.IoT.R project, but ended doing the Commodore Home, a more challenging project. I built the "desktop client" for the C64 I.Di.IoT.R (took me like a week) and in the end I didn't use it.
- Manage my time better. Don't work until late. I wake up at 6:00 / 7:00am no matter what.

Things that I would like to do in the near future:

- UniJoystiCle iOS client: Add Commodore Home plugin **(done: see below)**
- UniJoystiCle Desktop client: finish it and add Commodore Home plugin **(done: see below)**
- iOS/Android/Desktop client: Add voice support for the smartphone. You should be able to control the C64 by saying "Hey Commodore, activate the alarm".
- C64 app: Add sound support for NTSC/PAL-N. Right now it only sounds Ok on PAL-B.
- C64 app: Add modem support: when the alarm is triggered, it dials a BBS or something.
- Create a video mocking [Google Home](https://madeby.google.com/home/), [Amazon Echo](https://www.amazon.com/Amazon-Echo-Bluetooth-Speaker-with-WiFi-Alexa/dp/B00X4WHP5E) and other home automation products.
- Add support for unlocking/locking doors with the printer.

**Update (2016-11-08):**
iOS, Mac and Win32 UniJoystiCle clients with Commodore Home support & the precompiled version of the Commodore Home firmware are available here: [http://ricardoquesada.github.io/unijoysticle/](http://ricardoquesada.github.io/unijoysticle/)
