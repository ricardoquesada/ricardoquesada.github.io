---
author: ricardoquesada
category:
  - commodore-64
date: "2016-06-19T11:20:16+00:00"
guid: http://retro.moe/?p=1756
summary: "I assumed that the Commodore 1581 was failing because of a bad WD1772 IC (as documented in [Part I](https://retro.moe/2016/03/14/repairing-the-commodore-1581-floppy-disk-drive-part-1/)). So I ordered a WD1772 replacement + the IC socket, I developed some basic desoldering skills, watched some [desoldering](https://www.youtube.com/watch?v=239okViumdA) [videos](https://www.youtube.com/watch?v=t2j_8LvpTNk), and also got a cheap [desoldering iron from Radio Shack](https://www.radioshack.com/products/radioshack-45-watt-desoldering-iron?variant=5717855877):\n\n \n\nSo, I removed the board from the Commodore 1581 and started to desolder the IC. To my surprise the $11-buck desolder iron worked pretty well. I was able to remove all the solder from the the pins in a few minutes. The desolder iron just takes some time to reach the needed temperature, but besides that, it seems to be a great tool for occasional desoldering tasks (a hobbyist desoldering iron [cost more than $250](https://www.amazon.com/Hakko-FR300-05-P-Desoldering-Tool/dp/B00KWM69C4))"
tag:
  - c1581
  - soldering
title: Repairing the Commodore 1581 floppy disk drive. Part 2
url: /2016/06/19/repairing-the-commodore-1581-floppy-disk-drive-part-2/

---
I assumed that the Commodore 1581 was failing because of a bad WD1772 IC (as documented in [Part I](/2016/03/14/repairing-the-commodore-1581-floppy-disk-drive-part-1/)). So I ordered a WD1772 replacement + the IC socket, I developed some basic desoldering skills, watched some [desoldering](https://www.youtube.com/watch?v=239okViumdA) [videos](https://www.youtube.com/watch?v=t2j_8LvpTNk), and also got a cheap [desoldering iron from Radio Shack](https://www.radioshack.com/products/radioshack-45-watt-desoldering-iron?variant=5717855877):

{{< figure align=alignnone width=400 src="https://lh3.googleusercontent.com/-SehpVpK4DzM/V2YrH%5FZ%5FkpI/AAAAAAABea4/44jumdMcoQQ9L2CbhWJn9%5FY-MUgafqMqwCCo/s400/IMG%5F4671.jpg" alt="" >}}

So, I removed the board from the Commodore 1581 and started to desolder the IC. To my surprise the $11-buck desolder iron worked pretty well. I was able to remove all the solder from the the pins in a few minutes. The desolder iron just takes some time to reach the needed temperature, but besides that, it seems to be a great tool for occasional desoldering tasks (a hobbyist desoldering iron [cost more than $250](https://www.amazon.com/Hakko-FR300-05-P-Desoldering-Tool/dp/B00KWM69C4))

{{< figure align=alignnone width=400 src="https://lh3.googleusercontent.com/-ftwQNQVTmQQ/V2YrGZxhVGI/AAAAAAABebQ/dTLrvWjj5LEzhCRzWOKo9Va2ob%5FwsPlIwCCo/s400/IMG%5F4664.jpg" alt="" >}}

{{< figure align=alignnone width=400 src="https://lh3.googleusercontent.com/-mmHKq16zDoI/V2YrGZZLvSI/AAAAAAABebE/PiZf0gy5T74aXtjCLHuI%5Fu3pmI7k0sOkQCCo/s400/IMG%5F4665.jpg" alt="" >}}

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-I1AVePft-tE/V2YrHGonMsI/AAAAAAABebE/D8yT-mTayA0xS8-vCnKcO2-pz3y6M1mtACCo/s400/IMG_4667.jpg) Board with the IC socket soldered\[/caption\]

I removed the old WD1772 IC, solder an IC socket, installed the new WD1772 IC, assembled everything together again, plugged the Commodore 1581 into the Commodore 64, did a LOAD"$",8 and...

![](https://lh3.googleusercontent.com/-SPyqUHDL2GE/V2YrH8XbYjI/AAAAAAABebE/h-Lhhmb3yqMbK2SNkujnyFIl0a21FiwfgCCo/s400/IMG_4670.jpg)

and got again the FILE NOT FOUND ERROR. Sigh.😞

Time to double check everything:

- Did I solder the IC socket correctly? Did I clean the pin holes correctly?
- Is there any trace broken?
- What happens if I remove the WD1772? Will it behave the same way?
- And if the problem is not related to the WD1772, what's the origin of this problem?

Unfortunately I didn't have time to keep testing.
