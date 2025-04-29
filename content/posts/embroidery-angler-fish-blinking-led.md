---
author: ricardoquesada
tag:
  - embroidery
  - angler fish
  - machine embroidery
date: '2025-04-27T20:28:07-07:00'
title: 'Creating a machine-embroidery angler fish with a blinking LED'
---

![angler_fish_tshirt](/images/angler_fish_tshirt.jpg)

Long story short, a few months ago I started a new hobby: machine-embroidery.
Since then, I've been experimenting with machine-embroidery pixel-art.

The Angler Fish is my 18th machine-embroidery pixel-art work.

In a future post, I'll describe in more detail how it's been done.
In the meantime, here is the summary:

The design consists of:

- 3188 pixels
- 64,804 stitches
- Size: 223.1 x 131.1 mm (~8.78 x 5.16 in)
- Seven colors: six polyester threads, one metallic thread
- End-to-end total time: ~7 hours
- 1 blinking LED running on [Lilypad Arduino][lilypad_arduino] board

### Image using Gemini

I create the image using Gemini. Here is the Gemini session: https://g.co/gemini/share/13f7ace8b76b

![angler_fish_gemini](/images/angler_fish_gemini_prompt.png)

### GIMP to simplify the image

With [GIMP], I did the following:

- Scale it down so that each "pixel" actually is a pixel.
- Converted the image with "indexed" to reduce the colors
- Manually simplified the image: replaced pixels to make it look easier to embroider. Gradients are simpler.
- 
![angler_fish_gimp](/images/angler_fish_gimp.jpeg)

### Pixem to create the embroidery path

I create my own editor, Pixem, to trace the path for the embroidery machine.
This is to reduce the number of jump stitches, among other things.

My editor exports a file that Ink/Stitch can load.

BTW, I'll release my editor once it is stable enough, in a few months, probably.

![angler_fish_pixem](/images/angler_fish_pixem.jpeg)

### Ink/Stitch to generate embroidery files

I used [Ink/Stitch][inkstitch],
which is an [Inkscape][inkscape] plugin, to generate the PES file.

And I also flipped the image horizontally,
since I wanted the LED to be on the left side of the t-shirt.

BTW, PES is the file format needed for my Brother embroidery machine.

![angler_fish_inkscape](/images/angler_fish_inkscape.jpeg)

### Brother NQ3550W to embroider the t-shirt

I used a Brother NQ3550W to do the embroidery.
I bought it about ~6 months ago, and so far so good.

![brother_nq3550w](/images/brother_nq3550w.jpeg)

I used two fusible no-show-mesh cut-away stabilizers.
And I used a water-soluble embroidery topping to make the pixels look better.

![angler_fish_wip](/images/angler_fish_wip.jpg)

I also changed the palette.
Instead of using blue threads, I used red ones.
To make the gradient look good, it is important to choose the correct colors.

![embroidery_threads](/images/embroidery_threads.jpg)

### Cut away stabilizer

Carefully cut away the stabilizers, as close to the design as possible.

![angler_fish_stabilizer](/images/angler_fish_stabilizer.jpg)

### Blink the LED

I used a [Lilypad Arduino][lilypad_arduino] board as the microcontroller.
Which I manually sew it at the back of the t-shirt.

I used a regular blinking Arduino sketch. 

And I created some ad-hoc cables to connect the LED with the Lilypad.
I had to use hot glue, crocodile clips and heat shrink tubes to make the connection stable,
and short-circuit free.

![angler_fish_lilypad](/images/angler_fish_lilypad.jpg)

### Success!

I wear the t-shirt at a party for ~4 hours: dancing, jumping, playing games, without a single issue.
The LED kept blinking non-stop for the entire night. 

And everybody loved the t-shirt :-)

![angler_fish_party](/images/angler_fish_party.jpg)



[GIMP]: https://www.gimp.org/
[inkstitch]: https://www.inkstitch.org
[inkscape]: https://www.inkscape.org
[lilypad_arduino]: https://docs.arduino.cc/retired/boards/lilypad-arduino-usb/
[fruit_of_loom]: https://www.fruit.com/
