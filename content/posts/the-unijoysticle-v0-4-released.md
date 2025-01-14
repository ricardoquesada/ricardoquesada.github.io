---
author: ricardoquesada
category:
  - commodore-64
date: "2016-11-28T14:45:26+00:00"
guid: http://retro.moe/?p=1979
summary: "Christmas is coming. Treat yourself with The UniJoystiCle v0.4, and be the cool kid in the block by playing [The Uni Games](https://github.com/ricardoquesada/c64-the-uni-games) like a pro (that's it with real unicycles!):\n\nhttps://www.youtube.com/watch?v=ZLAgooXx4bo\n\n### Highlights of v0.4\n\n#### WiFi Device\n\n \n\n- Smaller real estate: Fits in all C64/128 models, including the C128D / SX-64 machines\n- Using Wemos D1 Mini instead of NodeMCU\n- Blue instead of red"
tag:
  - c64
  - unijoysticle
title: The UniJoystiCle v0.4 released
url: /2016/11/28/the-unijoysticle-v0-4-released/

---
Christmas is coming. Treat yourself with The UniJoystiCle v0.4, and be the cool kid in the block by playing [The Uni Games](https://github.com/ricardoquesada/c64-the-uni-games) like a pro (that's it with real unicycles!):

{{< youtube ZLAgooXx4bo >}}

### Highlights of v0.4

#### WiFi Device

{{< figure align=alignnone width=332 src="https://lh3.googleusercontent.com/BiJfN9HyXSthFJ09gKXZ92JVhZPIWnccandi8EwisTMjRML7XeNcxW3VqltVvPZLDBq-vn4MbG7uXQ=-no" alt="" >}}

- Smaller real estate: Fits in all C64/128 models, including the C128D / SX-64 machines
- Using Wemos D1 Mini instead of NodeMCU
- Blue instead of red

#### Firmware

- New WiFi modes: Station and WPS modes
- Auto-reset joystick state after inactivity timeout
- Online-firmware update
- Stats:
  - How many joystick movements
  - How many seconds spent in joystick movements

#### Clients

- Android Client: Yay, Android has its own client. Similar to iOS, but without the Gyruss mode.
  - Supports any Android game controller like OUYA, Amazon Fire, Moya, etc.
- Desktop Client:
  - Supports Dpad, Commando and Commodore Home modes
  - Windows version: Supports any Xinput game controller (like the Xbox 360 or newer controllers)
  - Mac version: Supports any MFi game controller
- iOS Client: Added Commodore Home mode
  - Supports both MFi and iCade game controllers

Read the [complete Changelog here](https://github.com/ricardoquesada/unijoysticle/releases/tag/unijoysticle-v0.4.0).

### Game Controllers support

![](https://lh3.googleusercontent.com/pnXRSCt9jaEiloZ0l-1ADgyVWXbanCn2wlnhT2qBOEuV7yxNHz0EA7DnSF_2fz6IiFxfAu3HWJLEcw=-no)

Most, if not all of the existing game controllers can be used with The UniJoystiCle:

- Windows controllers: All Xinput game controllers are supported natively ( [Xbox 360](https://www.microsoft.com/accessories/en-us/gaming) or newer controllers)

  - DirectInput game controllers can be used with [x360ce](http://www.x360ce.com/)
- iOS / Mac controllers:
  - Native support for both [MFi](https://afterpad.com/mficontrollers/) and [iCade game](http://www.8bitdo.com/) controllers
- Android controllers:
  - Native support for Android game controllers, including forks like OUYA

#### "Commando Mode" button mapping

Improved button mapping in Commando Mode:

- Button A:  Fire Joy#2
- Button B: Fire Joy#1 (eg: grenades in Commando, special weapon in Turrican II, bombs in Drop Zone)
- Button X: Down Joy #1 (eg: cloak in DropZone)
- Button Y: Right Joy #1 (eg: cloak in DropZone)

#### Video

{{< youtube 2lZSAKbrHTo >}}

### Documentation

Believe it or not, I wrote documentation, yay!

- [DOCUMENTATION.md](https://github.com/ricardoquesada/unijoysticle/blob/master/DOCUMENTATION.md)

### Download

- Precompiled binaries: [http://ricardoquesada.github.io/unijoysticle/](http://ricardoquesada.github.io/unijoysticle/)
- Source code: [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)
