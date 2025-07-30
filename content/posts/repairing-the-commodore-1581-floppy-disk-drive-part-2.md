---
author: ricardoquesada
category: retro computing
date: "2016-06-19T11:20:16+00:00"
guid: http://retro.moe/?p=1756
tag:
- commodore 64
- commodore 1581
- soldering
title: Repairing the Commodore 1581 floppy disk drive. Part 2
url: /2016/06/19/repairing-the-commodore-1581-floppy-disk-drive-part-2/

---

I assumed that the Commodore 1581 was failing because of a bad WD1772 IC (as
documented
in [Part I](/2016/03/14/repairing-the-commodore-1581-floppy-disk-drive-part-1/)).

So I ordered a WD1772 replacement and the IC socket, I developed some basic
desoldering skills, watched some [desoldering](https://www.youtube.com/watch?v=239okViumdA) [videos](https://www.youtube.com/watch?v=t2j_8LvpTNk),
and also got a cheap [desoldering iron from Radio Shack](https://www.radioshack.com/products/radioshack-45-watt-desoldering-iron?variant=5717855877):

![](/images/repairing-the-commodore-1581-floppy-disk-drive-part-2-desoldering-iron.jpg)

So, I removed the board from the Commodore 1581 and started to desolder the IC.
To my surprise, the $11-buck desolder iron worked pretty well.
I was able to remove all the solder from the pins in a few minutes.

The desolder iron just takes some time to reach the necessary temperature,
but besides that, it seems to be a great tool for occasional desoldering tasks
(a hobbyist desoldering iron [cost more than $250](https://www.amazon.com/Hakko-FR300-05-P-Desoldering-Tool/dp/B00KWM69C4)).

![](/images/repairing-the-commodore-1581-floppy-disk-drive-part-2-soldered.jpg)
![](/images/repairing-the-commodore-1581-floppy-disk-drive-part-2-desoldered.jpg)
![](/images/repairing-the-commodore-1581-floppy-disk-drive-part-2-socket.jpg)

<small>*Board with the IC socket soldered*</small>

I removed the old WD1772 IC, solder an IC socket, installed the new WD1772 IC,
assembled everything together again, plugged the Commodore 1581 into the
Commodore 64, did a `LOAD"$",8` and...

![](/images/repairing-the-commodore-1581-floppy-disk-drive-part-2-c64.jpg)

and got again the `FILE NOT FOUND ERROR`. Sigh.😞

Time to double-check everything:

- Did I solder the IC socket correctly? Did I clean the pin holes correctly?
- Is there any trace broken?
- What happens if I remove the WD1772? Will it behave the same way?
- And if the problem is not related to the WD1772, what's the origin of this
  problem?

Unfortunately, I didn't have time to keep testing.
