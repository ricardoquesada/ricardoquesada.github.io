---
author: ricardoquesada
category:
  - programming
date: "2018-01-03T15:29:57+00:00"
guid: http://retro.moe/?p=2071
tag:
  - "8088"
  - ibm-pcjr
  - ida-pro
  - pcjr
title: IBM PCjr BIOS dump
url: /2018/01/03/ibm-pcjr-bios-dump/

---
{{< figure align=alignnone width=512 src="https://lh3.googleusercontent.com/QwPdCQFbS4grTTTnEg0aZ1cxE2p2RzSpIH14RtQnXLq9mvLWZoXWBrOtN%5FWNUs10ocaQ-gvGGSAkjTsx78%5FRBw0NoiBoYXTEu6hV8MJ68vxkkysJznNz7yVmCDFmdc5h3xHmy23HnPM=-no" alt="" >}}

The IBM PCjr BIOS is very well documented in the [IBM PCjr Technical Reference manual](https://archive.org/details/IbmPcjrTechnicalReference) (a must read for every PCjr developer).

The only problem is that navigating that code is not easy. It has all the problems from scanned books:

- the fonts don't look good
- no hyper-links
- and difficult to search

So I dumped the BIOS and started analyzing it with [IDA Pro 5.0 - Free version](https://downloads.scummvm.org/frs/extras/IDA/idafree50.exe). I added some of the original comments from the Technical Reference manual, and added some comments of my own.

You can browse it using either:

- IDA Pro (the .idb file): [bios-f0000-fffff.idb](https://github.com/ricardoquesada/bios-8088/raw/master/ibm_pcjr/bios-f0000-fffff.idb)
- or by looking at the .lst file (just a text file): [ibm\_pcjr-bios.lst](https://github.com/ricardoquesada/bios-8088/blob/master/ibm_pcjr/ibm_pcjr-bios.lst)

Or just clone the project from github: [https://github.com/ricardoquesada/bios-8088/tree/master/ibm\_pcjr](https://github.com/ricardoquesada/bios-8088/tree/master/ibm_pcjr)

This is still Work-in-Progress. I add comments in " _let's see how this portion of the BIOS work_"-basis.

BTW, the Tandy 1000HX BIOS dump is here: [https://github.com/ricardoquesada/bios-8088/tree/master/tandy\_1000hx](https://github.com/ricardoquesada/bios-8088/tree/master/tandy_1000hx)

**Update:** Updated links
