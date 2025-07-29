---
author: ricardoquesada
category: retro computing
date: "2016-06-30T23:05:01+00:00"
guid: http://retro.moe/?p=1771
tag:
  - unijoysticle
title: UniJoystiCle v0.2.1 released
url: /2016/06/30/unijoysticle-v0-2-1-released/

---
![](/images/unijoysticle-v0-2-1-released-battery.jpg)
<small>*v0.2.1 powered from a battery. Can be powered from USB as well.*</small>

Changes in v0.2.1:

- Commodore 64 works Ok when the UniJoystiCle board is unpowered.
  The issue was that the 4066 chips were in an unknown state when they were unpowered.
  In v0.2.1 the 4066 ICs get power from the C64 Joy #2 port.
- Smaller holes for the DC Jack making it compatible with "common" DC Jacks.

Unfortunately, v0.2.1 has a bug, and the way to fix it is to cut the 3v3 trace
that comes from the NodeMCU.

![](/images/unijoysticle-v0-2-1-released-board.jpg)
<small>*The trace that should be cut in order to fix the bug in v0.2.1.*</small>

I ordered a new batch (v0.2.2) which should arrive soon, with:

- the above-mentioned bug fixed
- uses ground plate for grounds
- nice UniJoystiCle logo printed in silk screen

Download firmware + PCB files + iOS client from here:

- [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)
