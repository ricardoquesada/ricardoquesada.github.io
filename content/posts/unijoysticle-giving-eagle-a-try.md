---
author: ricardoquesada
category: retro computing
date: "2016-04-26T19:57:46+00:00"
guid: http://retro.moe/?p=1612
title: 'UniJoystiCle: Giving Eagle a try'
url: /2016/04/26/unijoysticle-giving-eagle-a-try/
tag:
  - unijoysticle

---
I like [Fritzing](http://fritzing.org/home/). I think it is great for small projects and it is very easy to use. But it has its limitations when creating the PCB, mostly because its component library is not very complete.

[Eagle](http://www.cadsoftusa.com/), on the other hand, is more difficult to use. But its component library is very polished. Also, companies like [Adafruit](https://www.adafruit.com/) and [SparkFun](https://www.sparkfun.com/) create components for Eagle, so that is a big plus if you purchase components from them.

So, I re-wrote the schematic again in Eagle, and then created this PCB:

![](https://lh3.googleusercontent.com/-qKyn_dhdhas/Vx_FBz09y8I/AAAAAAABd60/9Wn3IuWfPWoS6Y2xNsOB2Xm0yKRn8L5tgCCo/s800/unijoysticle_board.png)

Another thing that I added is an external power supply. UniJoystiCle works with any DC external power supply from v4.5 to v9. In theory it should work with a v3.3 battery as well.

I also added a diode to protect the battery in case the USB and the battery are both plugged in at the same time. I don't know if it is needed, but I guess it doesn't hurt having one.

{{< figure align=alignnone width=640 src="https://lh3.googleusercontent.com/-ZXr-b5--tdw/Vx%5FFM0RsDLI/AAAAAAABd7E/iYkvnRSRrC8wUrcB00obI5RiM%5Fs9XmbxACCo/s640/IMG%5F0115.jpg" alt="" >}}
