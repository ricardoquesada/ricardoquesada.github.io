---
author: ricardoquesada
category: retro computing
date: "2016-10-15T00:40:58+00:00"
guid: http://riq64.wordpress.com/?p=2
tag:
  - commodore 64
  - retrochallenge
title: 'RetroChallenge: C64 I.D.IoT.R Update #2'
url: /2016/10/14/retrochallenge-c64-i-d-iot-r-update-2/

---
{{< figure align=alignnone width=374 src="/wp-content/uploads/2016/10/img%5F5276.jpg" alt="" >}}

- Ordered a rubber belt + pulley to control the dimmer from the printer header
- New UniJoystiCle PCB arrived (v0.4.0). I assembled one and works Ok both on the SX64 and the C128D. I just need to create a "user port" power cable for the SX64 since it doesn't have a datasette port.
- Started the UniJoystiCle desktop client in order to control the dimmer from the PC/Mac.

{{< figure align=alignnone width=444 src="/wp-content/uploads/2016/10/screen-shot-2016-10-14-at-5-34-36-pm.png" alt="" >}}

**TODO:**

- UniJoystiCle Desktop Client: Linear Mode, finish it.
- UniJoystiCle Desktop Client: Commando Mode, finish it (although not needed for the dimmer)
- UniJoystiCle Desktop Client: DPad Mode, finish it (although not needed for the dimmer)
- Assemble the rubber belt + pulley and connect it to the printer header
- Create user-port power cable to be used with the SX64 for the UniJoystiCle WiFi module
- C64 I.D.IoT.R app: Add voice, probably using SAM or similar.
- UniJoystiCle iOS/Android Client: Support voice commands in Linear Mode so people can say: _"Ok Commodore, turn on the lights"_
  - Quick and Easy: Just support keyboard input
  - More complex but more "professional": Add [api.ai](https://api.ai/) support

And I guess that's it.
