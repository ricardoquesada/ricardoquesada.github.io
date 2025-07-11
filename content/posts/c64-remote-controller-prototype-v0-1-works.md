---
author: ricardoquesada
category:
  - commodore-64
  - programming
date: "2016-04-01T08:38:41+00:00"
guid: http://retro.moe/?p=1318
tag:
  - c64
  - esp8266
  - joystick
title: 'C64 Remote Controller: Prototype v0.1 works!...'
url: /2016/04/01/c64-remote-controller-prototype-v0-1-works/

---
...or How to use a 64-bit machine to control a Commodore 64.

{{< youtube L_Gdwa1DCD8 >}}

No schematics or PCBs yet. But at least I have the materials that I'm using:

- One [Lolin NodeMCU](http://www.ebay.com/sch/i.html?_from=R40&_trksid=p2050601.m570.l1313.TR0.TRC0.H0.Xlolin+nodemcu.TRS0&_nkw=lolin+nodemcu&_sacat=0) (should work with any other ESP8266 that have at least five GPIOs)
- Two 4066 ICs. I'm using [this one](http://www.ti.com/lit/ds/symlink/sn74hc4066.pdf).

...and this is the software that I'm using both for the NodeMCU firmware and the iOS client:

- [https://github.com/ricardoquesada/c64-remote-controller](https://github.com/ricardoquesada/c64-remote-controller)

More info and upgrades coming soon.

#### Todo list:

- Support two joysticks at the same time (for multiplayer games)
- Support mouse
- Support paddle
- Save/Replay commands so that you can kind-of-replay your game
- Service discovery so that you don't have to hardcore the IP address
