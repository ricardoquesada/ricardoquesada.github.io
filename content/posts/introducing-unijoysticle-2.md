---
author: ricardoquesada
category:
  - programming
date: "2021-10-20T17:10:17+00:00"
guid: https://retro.moe/?p=2459
summary: |-
  ![](https://lh3.googleusercontent.com/pw/AM-JKLUXjtgKSpJq7tH98-28yuaWiBRLN9y0tF5wdYgk4cfPPnoVxpX2astdSZLqT5JVz2Sddw7OIjZ4xDtDL2yf04rxHvgVgu_m74OlERyXDkTKn1VnrxQWaQpGT-xA0ydgKCcCqVGhh9a_0VpfasM_PGLnOg=-no?authuser=0)Unijoysticle 2+

  For those not familiar with Unijoysticle 2, it is a device that allows you to use modern Bluetooth gamepads like [Sony DualSense](https://www.playstation.com/en-us/accessories/dualsense-wireless-controller/) or [Nintendo Switch controllers](https://store.nintendo.com/nintendo-switch/joy-con-controllers.html) (to name just a few) on old computers like the Commodore 64 or Amiga.

  What's new in version 2+:

  - Case friendly: lower profile, LEDs & buttons are close the border and has mounting holes.
  - Looks nicer: Uses SMD components for almost everything
  - Supports buttons 2 & 3 in port #2. Some Amiga games might use them.
  - Cheaper to manufacture. I reduced the price from $60 to $35
tag:
  - commodore-64
  - unijoysticle
title: Introducing Unijoysticle 2+
url: /2021/10/20/introducing-unijoysticle-2/

---
![](https://lh3.googleusercontent.com/pw/AM-JKLUXjtgKSpJq7tH98-28yuaWiBRLN9y0tF5wdYgk4cfPPnoVxpX2astdSZLqT5JVz2Sddw7OIjZ4xDtDL2yf04rxHvgVgu_m74OlERyXDkTKn1VnrxQWaQpGT-xA0ydgKCcCqVGhh9a_0VpfasM_PGLnOg=-no?authuser=0)Unijoysticle 2+

For those not familiar with Unijoysticle 2, it is a device that allows you to use modern Bluetooth gamepads like [Sony DualSense](https://www.playstation.com/en-us/accessories/dualsense-wireless-controller/) or [Nintendo Switch controllers](https://store.nintendo.com/nintendo-switch/joy-con-controllers.html) (to name just a few) on old computers like the Commodore 64 or Amiga.

What's new in version 2+:

- Case friendly: lower profile, LEDs & buttons are close the border and has mounting holes.
- Looks nicer: Uses SMD components for almost everything
- Supports buttons 2 & 3 in port #2. Some Amiga games might use them.
- Cheaper to manufacture. I reduced the price from $60 to $35

### Comparison between the two

|                                          Feature                                           | Unijoysticle 2 | Unijoysticle 2+ |
|:------------------------------------------------------------------------------------------:|:--------------:|:---------------:|
|                                           Image                                            | ![uni2](https://lh3.googleusercontent.com/pw/AM-JKLUphquTBg9JoV-L7wuMtze_aKIJ8LvfokTakuBKSVFClziLWCViggcrlNZtqGUMgv6u6yYpZ_RuE2jdGSn3Q0oYl0jOQzzGcutRt-JiMjLZY_oAvK4LehrawNj_aNbthCJ-VEJzsW3dywhJNekjhTsfNQ=-no)|![uni2p](https://lh3.googleusercontent.com/pw/AM-JKLWV2Zo912VtOfuM71AluanNXGwVQiAehNEiQ1VL3L7SkWDl-9k0fA6tfza9QpGL52petBfFFFHMb8rh_ybSj17LOQA70IycMDQw6AVqlN8Jp4HDWT8sWcXHIPEQZTxNuQ-RFygKbmVpW2n52wwi5cJgwA=-no)|
|                                       Case friendly                                        |No (1) | Yes |
|                                            Size                                            | 63 x 66 x 17 mm| 64 x 64 x 12 mm |
|                                           Weight                                           | 35 grams | 24 grams |
|                                          Current                                           | ~95 mA (2) | ~100 mA (2) |
|                             Amiga / Atari ST 2nd & 3rd buttons                             | No | Yes (3) |
| Filter noise in C128 ( [bug](https://gitlab.com/ricardoquesada/unijoysticle2/-/issues/17)) | No | Yes |
|                                        Self-powered                                        | Yes, can be turned on/off with switch | Yes, always on |
|                                       External power                                       | Both USB and Barrel Jack | 5V+USB only |
|                                       Easy to solder                                       | Yes | No |
|                                           Price                                            | $60 (assembled) / $35 (kit) | $35 (assembled) |

Notes:

- 1: Work-around: turn off the "self power" switch.
- 2: Tested with only one gamepad connected in "Basic" mode. In "Enhanced" mode, both draw ~102 mA.
- 3: Requires firmware update. Work in progress.

### The rationale behind the changes

**Barrel Jack removed:** It was no longer needed. It was added in the first revision of Unijoysticle 2 because "self-power" was not supported back then. But I added "self-power" in Rev. D, and the Barrel Jack was no longer needed. In case a user needs to power the device from an external source, the USB port can be used.

**Self-power switch removed:** I originally added this feature as a "just in case". And in fact, it fixes the ["C128 noise"](https://gitlab.com/ricardoquesada/unijoysticle2/-/issues/17) when the switch is off. In any case, a capacitor was added in Unijoysticle 2+ to prevent to noise, so the switch was no longer needed.

**Case friendly:** Many users requested a case for the Unijoysticle 2. I tried to design one, but it was not easy and I gave up. But it should be easier to design one for the 2+. BTW, I haven't designed one yet... but I should have one ready soon™.

**Kit vs assembled unit:** I'm only offering the Unijoysticle 2+ as an assembled unit. Doesn't make sense to offer a kit where most of the components are SMD.

**Price :** The new price for the assembled unit is $35 (from $60), and I'm no longer offering the Kit (which was $35). This is two-fold:

- Time (main reason): I'm using [JLCPCB](https://jlcpcb.com/) for manufacturing + assembly. This reduces the time that I have to spend on each unit.
- Components price: SMD components are slightly cheaper than through-hole ones. But on the other hand I'm using a 4-layer PCB which increases the price a little bit.

**Tindie:** To further reduce my time, I'm using Tindie as the store-front. Better for the users (don't have to send me an email), better for me (spend less time).

[![](https://d2ss6ovg47m0r5.cloudfront.net/badges/tindie-mediums.png)](https://www.tindie.com/products/riq/unijoysticle-2/)

### This that hasn't changed

##### Open source / open hardware

- Firmware source code: [http://github.com/ricardoquesada/bluepad32](http://github.com/ricardoquesada/bluepad32)
- Hardware schematic + layout: [https://github.com/ricardoquesada/unijoysticle2](https://github.com/ricardoquesada/unijoysticle2)

Not only I'm making everything open source & open hardware so that you can create your own device, but I also welcome "competition". If you want to sell your own devices, please go ahead. All the profit is for you. Just let me know so that I can add your product in the ["3rd party devices" section](/unijoysticle2/).

##### Available for trade

I trade a Unijoysticle 2+ unit for one of your own retro inventions / creations. It works like this:

- I send you a Unijoysticle 2+ device (I pay the shipping)
- You send me one of your retro inventions/creations (you pay the shipping)
  - It could be a magazine, video game, device, etc... (must be retro-related)
