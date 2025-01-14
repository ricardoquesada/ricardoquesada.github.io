---
author: ricardoquesada
category:
  - commodore-64
date: "2016-06-30T23:05:01+00:00"
guid: http://retro.moe/?p=1771
summary: |-
  \[caption id="" align="alignnone" width="480"\]![](https://lh3.googleusercontent.com/-wbKhFizysbk/V3Wh7rzaKoI/AAAAAAABetg/CS2OlIXzJz4Vx_dCfFOB3GAbViJf_wCCACCo/s640/IMG_0207.jpg) v0.2.1 powered from a battery. Can be powered from USB as well\[/caption\]

  Changes in v0.2.1:

  - Commodore 64 works Ok when the UniJoystiCle board is unpowered. The issue was that the 4066 chips were in an unknown state when they were unpowered. In v0.2.1 the 4066 ICs get power from the C64 Joy #2 port
  - Smaller holes for the DC Jack making it compatible with "common" DC Jacks.
tag:
  - unijoysticle
title: UniJoystiCle v0.2.1 released
url: /2016/06/30/unijoysticle-v0-2-1-released/

---
\[caption id="" align="alignnone" width="480"\]![](https://lh3.googleusercontent.com/-wbKhFizysbk/V3Wh7rzaKoI/AAAAAAABetg/CS2OlIXzJz4Vx_dCfFOB3GAbViJf_wCCACCo/s640/IMG_0207.jpg) v0.2.1 powered from a battery. Can be powered from USB as well\[/caption\]

Changes in v0.2.1:

- Commodore 64 works Ok when the UniJoystiCle board is unpowered. The issue was that the 4066 chips were in an unknown state when they were unpowered. In v0.2.1 the 4066 ICs get power from the C64 Joy #2 port
- Smaller holes for the DC Jack making it compatible with "common" DC Jacks.

Unfortunately, v0.2.1 has a bug, and the way to fix it is to cut the 3v3 trace that comes from the NodeMCU.

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-TX2rsCHewss/V3WkYjzVGzI/AAAAAAABets/ImuAhiauLcs75aRc-GRo_JgtJi5cpdyrgCCo/s400/IMG_0209.jpg) The trace that should be cut in order to fix the bug in v0.2.1\[/caption\]

I ordered a new batch (v0.2.2) which should arrive soon, with:

- the above mentioned bug fixed
- uses ground plate for grounds
- nice UniJoystiCle logo printed in silk screen

Download firmware + PCB files + iOS client from here:

- [https://github.com/ricardoquesada/unijoysticle](https://github.com/ricardoquesada/unijoysticle)
