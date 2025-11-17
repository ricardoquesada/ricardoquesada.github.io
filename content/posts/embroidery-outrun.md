---
author: ricardoquesada
date: '2025-10-06T22:29:41-07:00'
title: 'Embroidering Outrun'
tag:
  - embroidery
  - outrun
  - machine embroidery
---

![outrun](/images/embroidery-outrun-original.jpg)

The challenge with the Outrun sprite is that it has multiple colors, but many islands of only a few pixels,
so it requires multiple jump-stitches, or so I thought so.

To prevent the jump-stitches I decided to connect the different "islands" with a run-stitch.
I modified my Pixem editor to do that, and I embroidered the t-shirt.

![outrun](/images/embroidery-outrun-pixem.png)

The run-stitch path is "smart", in the sense that it will take shortest-path, but the weight is
measured by color difference.
This will prevent a black stitch running over a white if there is an alternative path going over brown.

The problems with my new "smart" algorithm, are:

* I cannot edit that the algorithm generates. I have to add support to edit the generated run-stitches.
* Connecting blocks of same colors with run-stitches is not optimized. On certain images it can cause going
  over the same run-stitch over and over, creating a "big" path.

![outrun_bugs](/images/embroidery-outrun-bugs.jpg)

Unfortunately I learned about the "connecting blocks" bug while I was embroidering Outrun.

*This post is 100% AI-free.*
