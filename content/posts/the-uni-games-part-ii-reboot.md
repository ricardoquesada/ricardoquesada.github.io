---
author: ricardoquesada
category:
  - commodore-64
  - programming
date: "2016-03-27T15:46:20+00:00"
guid: http://retro.moe/?p=1257
summary: |-
  A reboot was needed. I rewrote most of the code. The game is no longer called "The Muni Race". Instead it is called "The Uni Games" since it will have more than one event (think of "Summer Games" but for unicycles. [UNICON](http://eng.unicon18.com/) basically).

  The game will have a more-retro look and feel than before. It will only use PETSCII chars, plus sprites. No redefined characters, no bitmaps. Pure PETSCII. Pure retro effects.

  ![](https://lh3.googleusercontent.com/-u6cUHJ6Fg9A/VvfhKfa9ctI/AAAAAAABdm4/t8b5283PpzUtEmfZuy0xCN6-2W2pflOSwCCo/s640-Ic42/Screen%2BShot%2B2016-03-27%2Bat%2B6.31.23%2BAM.png)
tag:
  - c64
  - the-muni-race
title: The Uni Games - Part II. Reboot
url: /2016/03/27/the-uni-games-part-ii-reboot/

---
A reboot was needed. I rewrote most of the code. The game is no longer called "The Muni Race". Instead it is called "The Uni Games" since it will have more than one event (think of "Summer Games" but for unicycles. [UNICON](http://eng.unicon18.com/) basically).

The game will have a more-retro look and feel than before. It will only use PETSCII chars, plus sprites. No redefined characters, no bitmaps. Pure PETSCII. Pure retro effects.

![](https://lh3.googleusercontent.com/-u6cUHJ6Fg9A/VvfhKfa9ctI/AAAAAAABdm4/t8b5283PpzUtEmfZuy0xCN6-2W2pflOSwCCo/s640-Ic42/Screen%2BShot%2B2016-03-27%2Bat%2B6.31.23%2BAM.png)

The sprites are going to be very small, and it will have split screen to play it with two players at the same time (human vs. human, or human vs. computer).

![](https://lh3.googleusercontent.com/-QiIgft0QftI/VvfhKePWLZI/AAAAAAABdm8/3NvWD_WkXkwNKt0tRpX5YptCaXNdeYseQCCo/s640-Ic42/Screen%2BShot%2B2016-03-27%2Bat%2B6.32.20%2BAM.png)

The most important change is the controllers: Using real unicycles (playing it with joystick will also be supported).

**How:**

- The idea is "attach" an smartphone to the pedal of the unicycle
- Read the accelerometer. If it does down send a "joystick left". If it goes up send a "joystick right"
- A Wifi-receiver with some GPIOs ( [like the NodeMCU D1 mini](http://www.aliexpress.com/af/d1-mini.html?ltype=wholesale&d=y&origin=n&isViewCP=y&initiative_id=QRW_20160327064240&SearchText=d1+mini&productId=32529101036)) will send these commands to the C64 using the Joystick port
- This Remote Controller could be used as a general purpose C64 remote controller as well.

More on this later.

Further reading:

- Source code: [https://github.com/ricardoquesada/c64-the-muni-race](https://github.com/ricardoquesada/c64-the-muni-race)
- Part I: [The Muni Race - Part I](/2015/09/07/the-muni-race-part-i/)
