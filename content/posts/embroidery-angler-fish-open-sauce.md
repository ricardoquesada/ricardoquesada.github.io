---
author: ricardoquesada
tag:
  - embroidery
  - angler fish
  - machine embroidery
  - open sauce
date: '2025-07-21T17:46:48-07:00'
title: 'Improving Angler Fish for Open Sauce'
---

This past Saturday (2025-07-19) I went to [Open Sauce][open_sauce].
And since this is a maker event, I went with my best t-shirt so far:
the Angler Fish.

But it had some issues that I wanted to fix before using it again.

![angler_fish_tshirt](/images/angler_fish_20_front.jpg)

The two improvements that I made are:

* Added a pocket to place the battery and the microcontroller
* Improved how to attach the cables to the LED

## The pocket

![angler_fish_pocket](/images/angler_fish_20_pocket.jpg)

Instead of sewing the [Lilypad Arduino][lilypad_arduino] microcontroller
directly to the back of the t-shirt, I sewed a pocket in the back.

And I placed the microcontroller and the battery inside the pocket.

**Verdict**: Maybe happy with the result ?
I need to improve my sewing skills, and I don't know whether the pocket will get
stuck in the washing machine. The back looks good.

![angler_fish_back](/images/angler_fish_20_back.jpg)

## The LED

![angler_fish_led](/images/angler_fish_20_led.jpg)

For the LED, to make a secure connection, I used [3M Transpore Surgical Tape][transpore_surgical_tape]
to attach the pins with the cables and the t-shirt.

**Verdict**: Very happy with the result. The LED was easy to detach it. The connection was solid.

## The Arduino Sketch

The other change that I did, was to reduce the blinking frequency to 8 seconds.

```c++
// Arduino Sketch
void setup() {
  // Using pin 2 to drive the LED
  pinMode(2, OUTPUT);
}

void loop() {
  digitalWrite(2, HIGH);
  delay(1000);
  digitalWrite(2, LOW);
  delay(8000);
}
```

*This post is 100% AI-free.*


[open_sauce]: https://opensauce.com/
[lilypad_arduino]: https://docs.arduino.cc/retired/boards/lilypad-arduino-usb/
[transpore_surgical_tape]: https://www.google.com/search?q=3m+Transpore+Surgical+Tape&oq=3m+Transpore+Surgical+Tape
