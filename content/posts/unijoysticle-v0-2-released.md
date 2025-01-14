---
author: ricardoquesada
category:
  - commodore-64
date: "2016-06-13T00:31:38+00:00"
guid: http://retro.moe/?p=1752
summary: |-
  ![](https://lh3.googleusercontent.com/-OjX88hA0O9I/V12OOZiJjpI/AAAAAAABeXo/0AZYzH5x3xIiYRy--uza0qhJhuFwW18NACCo/s400/IMG_4523.jpg)**Download**(firmware, iOS client and schematics + board):

  - [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)
tag:
  - esp8266
  - unijoysticle
title: UniJoystiCle v0.2 released
url: /2016/06/12/unijoysticle-v0-2-released/

---
![](https://lh3.googleusercontent.com/-OjX88hA0O9I/V12OOZiJjpI/AAAAAAABeXo/0AZYzH5x3xIiYRy--uza0qhJhuFwW18NACCo/s400/IMG_4523.jpg)**Download**(firmware, iOS client and schematics + board):

- [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)

**Changes in v2.0:**

- \[NEW\] - ESP8266 Schematic: PCB board version. Protoboard version deprecated
- \[NEW\] - ESP8266 Schematic: Added EAGLE board and schematic files. Fritzing diagrams deprecated
- \[NEW\] - ESP8266 device: supports 2 joysticks (uses three 4066 ICs instead of two
- \[NEW\] - ESP8266 firmware uses AP mode by default. Uses SSID "unijosyticle" + last 2 bytes of mac address
- \[NEW\] - iOS Client: Can be configured to use either joystick port
- \[NEW\] - iOS Client: Auto-discover ESP8266 firmware using mDNS
- \[NEW\] - iOS Client: UniJoystiCle mode also supports up, down and fire (jump)
- \[FIX\] - iOS Client: Uses correct aspect rations in all iPhones: 4, 5, 6 and 6+
- \[FIX\] - iOS Client: D-Pad mode uses arrows + circle instead of colored squares
- \[FIX\] - iOS Client: D-Pad mode highlights buttons when they are pressed
- \[FIX\] - Name: Renamed project from Uni-Joysti-Cle to UniJoystiCle (easier to search, shorter to type)
- \[FIX\] - ESP8266 device: replaced NodeMCU LoLin with NodeMCU Amica since it is breadboard friendly.
- \[FIX\] - Sophisticated Glue Material: Uses gaffer tape, instead of duct tape

{{< youtube Xrdhg8S6HJ4 >}}
