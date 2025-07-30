---
author: ricardoquesada
category: retro computing
date: "2016-03-14T16:52:29+00:00"
guid: http://retro.moe/?p=1248
tag:
- commodore 64
- commodore 1581
title: Repairing the Commodore 1581 floppy disk drive. Part 1
url: /2016/03/14/repairing-the-commodore-1581-floppy-disk-drive-part-1/

---

[![IMG_3905](/wp-content/uploads/2016/03/img_3905.jpg?w=700)](/wp-content/uploads/2016/03/img_3905.jpg)

I got my 1581 like one year ago. It worked for 2 or 3 weeks and it stopped
working.
The stepper and the motor weren't moving.
So I guessed that the "floppy drive" was broken.

Quick introduction: the Commodore floppy disk drives have 2 major components:

- The controller board: which has the 6502, RAM, ROM and other ICs to control
  the drive
- The floppy disk drive: which is the "thing" that has the header, the stepper,
  the motor to spin the floppy disk, etc.

So, in my case, my quick guess was that the "floppy disk drive" was broken
because the stepper and the motor were not moving.

So, I got different replacements:

- Chinon FB-354 Rev. B: Was moving the stepper but making strange noises, so
  then I got a...
- ...a Panasonic JU-257: Was moving the motor, but not the stepper, so then I
  got a...
- ...a Chinon FB-354 Rev. E: Was not moving anything. Same symptoms as the
  original one.

When you purchase untested things from Ebay is hit-or-miss.
Sometimes they work, sometimes they don't.
But what are the chances of getting three broken floppy disk drives?

So, this time I decided to read more about the 1581 and I
found [this info](http://personalpages.tds.net/~rcarlsen/cbm/1581/1581.txt) that
says:

> The original fault with a failing 1770 was directory corruption. Other
> symptoms of a failing U4 include intermittent "file not found" and spindle
> motor not spinning when the drive is accessed. One recent U4 failure showed
> no stepper activity at power up (no "burp"), the green LED flashed once per
> second repeatedly and the spindle ran continuously.

So my new guess is that I have 3 fully working floppy disk drives and one broken
controller,
in particular
the [WD-1770](https://en.wikipedia.org/wiki/Western_Digital_FD1771) IC which is
responsible for controlling the floppy disk drive.
The WD-1770 is soldered into the PCB, so desoldering skills are required...
which I have zero.
So time to learn how to desolder ICs. See you soon.

UPDATE: [Part II here](/2016/06/19/repairing-the-commodore-1581-floppy-disk-drive-part-2/)
