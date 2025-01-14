---
author: ricardoquesada
date: "2015-12-13T08:28:26+00:00"
guid: http://retro.moe/?p=1220
summary: |-
  ### MOS 6526: The CIA chip

  You turn on your beloved SX-64 and you don't see the blinking cursor. Don't panic. Most probably one of the [CIA chips (MOS 6526)](https://en.wikipedia.org/wiki/MOS_Technology_CIA) is not working correctly.

  \[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-MF1kSO83zr4/Vm0Vsppqc2I/AAAAAAABcwQ/b0jjYSaIl80/s400-Ic42/WP_20151212_001.jpg) No blinking cursor\[/caption\]

  The Commodore 64 has two CIA chips. What you need to do is to replace the one that controls the keyboard, the CIA 1. But if you don't know which one is CIA 1 and which is CIA 2, then you can either replace both, or do trial-and-error, or look at the [IO schematics](http://personalpages.tds.net/~rcarlsen/cbm/sx64/SCHEMATICS/IO.gif) (hint: it is the one with the `UB3` legend).

  As far as I know any MOS 6526 should work:

  - MOS 6526 (found in the very first C64s)
  - MOS 6526 R4 (found in newer C64s)
  - MOS 6526A (the 2Mhz version, and I read somewhere that it works Ok)

  So, in order to get the replacement chip, you can get it on [eBay](http://www.ebay.com/sch/i.html?_from=R40&_trksid=p2050601.m570.l1313.TR0.TRC0.H0.XMOS+6526.TRS0&_nkw=MOS+6526&_sacat=0), or extract it from another another C64 or SX-64. The MOS 6526 chips on a regular C64, are located at the top-left corner.

  \[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-LV9IKHaXhzI/Vm0mJFmCDLI/AAAAAAABcyU/nUfu6Y-9F2s/s400-Ic42/WP_20151212_007.jpg) I removed the 6526 from a regular C64\[/caption\]

  I suggest using a [chip extractor](https://www.google.com/search?q=chip+extractor&oq=chip+ext&aqs=chrome.0.69i59j69i57.2495j0j8&sourceid=chrome&es_sm=91&ie=UTF-8#tbm=shop&q=IC+extractor) to extract the chips, although a flat screwdriver can work as well.
tag:
  - commodore-64
  - mos6526
  - repair
  - sx-64
title: 'Fixing the Commodore SX-64: Replacing the MOS 6526'
url: /2015/12/13/fixing-the-commodore-sx-64-replacing-the-mos-6526/

---
### MOS 6526: The CIA chip

You turn on your beloved SX-64 and you don't see the blinking cursor. Don't panic. Most probably one of the [CIA chips (MOS 6526)](https://en.wikipedia.org/wiki/MOS_Technology_CIA) is not working correctly.

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-MF1kSO83zr4/Vm0Vsppqc2I/AAAAAAABcwQ/b0jjYSaIl80/s400-Ic42/WP_20151212_001.jpg) No blinking cursor\[/caption\]

The Commodore 64 has two CIA chips. What you need to do is to replace the one that controls the keyboard, the CIA 1. But if you don't know which one is CIA 1 and which is CIA 2, then you can either replace both, or do trial-and-error, or look at the [IO schematics](http://personalpages.tds.net/~rcarlsen/cbm/sx64/SCHEMATICS/IO.gif) (hint: it is the one with the `UB3` legend).

As far as I know any MOS 6526 should work:

- MOS 6526 (found in the very first C64s)
- MOS 6526 R4 (found in newer C64s)
- MOS 6526A (the 2Mhz version, and I read somewhere that it works Ok)

So, in order to get the replacement chip, you can get it on [eBay](http://www.ebay.com/sch/i.html?_from=R40&_trksid=p2050601.m570.l1313.TR0.TRC0.H0.XMOS+6526.TRS0&_nkw=MOS+6526&_sacat=0), or extract it from another another C64 or SX-64. The MOS 6526 chips on a regular C64, are located at the top-left corner.

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-LV9IKHaXhzI/Vm0mJFmCDLI/AAAAAAABcyU/nUfu6Y-9F2s/s400-Ic42/WP_20151212_007.jpg) I removed the 6526 from a regular C64\[/caption\]

I suggest using a [chip extractor](https://www.google.com/search?q=chip+extractor&oq=chip+ext&aqs=chrome.0.69i59j69i57.2495j0j8&sourceid=chrome&es_sm=91&ie=UTF-8#tbm=shop&q=IC+extractor) to extract the chips, although a flat screwdriver can work as well.

### Opening the SX-64

So now that you have the replacement chip, you have to put it on the SX-64. Opening an SX-64 is easy, but it has more screws than the regular C64.

#### Step 1: Remove the cover

- From the back, remove the upper 3 screws, both from left and right.
- Then remove the side panel
- Then remove the upper screws from both sides
- Then remove the upper cover

\[caption id="" align="alignnone" width="381"\]![](https://lh3.googleusercontent.com/-7ul45M4bKuk/Vm0lieBOyzI/AAAAAAABcyM/0VrTW2vEeoA/s400-Ic42/WP_20151212_016.jpg) Remove the upper 3 screws.\[/caption\]

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-5wQvmgWL67w/Vm0lS8erchI/AAAAAAABcyE/_MocjuO4xBw/s400-Ic42/WP_20151212_014.jpg) Remove the uppers screws from the border\[/caption\]

#### Step 2: Identify and remove the I/O card

- Identify the I/O card. It is easy to find it (look at the picture below).
- Detach all connected cables from the I/O card...
- ...including the top-left black "thing"
- An extract the card carefully

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-NBFbmZauN6o/Vm0lQ2loluI/AAAAAAABcxw/NGKbARMutks/s400-Ic42/WP_20151212_002.jpg) The I/O card\[/caption\]

#### Step 3: Replace the chip

Then locate the CIA1 chip, the one with the UB3 legend. And replace it.

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-UE6v8p_iVQ4/Vm0lRPHfFqI/AAAAAAABcx4/XL-KE9ROspA/s400-Ic42/WP_20151212_006.jpg) Replace the chip with the UB3 legend. That's the CIA 1 chip.\[/caption\]

\[caption id="" align="alignnone" width="400"\]![](https://lh3.googleusercontent.com/-oUnkKDfl_n0/Vm0qhiKkVnI/AAAAAAABcyw/JdHNzguuL9w/s400-Ic42/WP_20151212_008.jpg) In my case, I replaced both CIA 6526 chips with the newer MOS 6526 R4 version.\[/caption\]

#### Step 4: done.

Assemble everything and test it. Keyboard should work Ok.

![](https://lh3.googleusercontent.com/-mFtKibL1ysY/Vm0o2X4IPMI/AAAAAAABcyk/cOlgDvhjgYA/s400-Ic42/WP_20151212_011.jpg)

{{< youtube 3rTViXuASTw >}}
