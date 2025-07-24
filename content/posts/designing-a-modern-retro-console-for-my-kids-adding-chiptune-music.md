---
author: ricardoquesada
category: embedded
date: "2020-12-13T16:30:49+00:00"
guid: http://retro.moe/?p=2294
tag:
  - bluepad32
  - circuitpython
  - esp32
  - sn76489
  - quico
title: 'Designing a modern retro console for (my) kids: Adding chiptune music'
url: /2020/12/13/designing-a-modern-retro-console-for-my-kids-adding-chiptune-music/

---
### The ideal modern-retro video game console

{{< youtube G_Fzt8RlbFc >}}

My goal is to build a video game console for (my) kids. I want to teach them programming in a fun way: fun for them... and also fun for me. The video-game console features are:

- Modern components, with a retro "spirit".
- Easy to program, a must.
  - Chosen: Python, in particular [CircuitPython](https://circuitpython.org/)
- Gamepad support: Multiple gamepads at the same time (multiplayer is a must).
  - Chosen: [Bluepad32 firmware](https://gitlab.com/ricardoquesada/bluepad32) since it supports all modern Bluetooth gamepads ( [see my previous post](/2020/11/24/bluepad32-gamepad-support-for-esp32/))
- "Retro" sound:
  - Chosen: SN76489 (more info down below)
- "Retro" screen:
  - Chosen: 64x32 LED matrix. Let's see what we can do in this extremely low-resolution screen.
- A powerful enough micro-controller:
  - Chosen: [Matrix Portal M4](https://www.adafruit.com/product/4745), mostly for convenience since it comes with an ARM Cortex M4, ESP32, "expansion port" + header to connect to the matrix LED. It already supports CircuitPython. As a bonus it has an accelerometer.
- Portability: It should be portable, no need to use an external power supply.

In other words, I'm building a **Nintendo Switch killer**. What will happen next is that Nintendo will run out of business. If this happens, my 7-year-old kid will kill me, since his dream is to be a video game designer at Nintendo... so probably I shouldn't be that aggressive in my marketing campaign.

### Adding music support: the SN76489 chip

![](https://upload.wikimedia.org/wikipedia/commons/a/a8/SN76489_01.jpg)

The SN76489 is a "chiptune" music chip that was used in many video game consoles and computers back in the 80's. It is the ideal candidate for the "modern retro console" because:

- It is easy to get one: [Ebay](https://www.ebay.com/sch/i.html?_from=R40&_trksid=p2047675.m570.l1313&_nkw=sn76489&_sacat=0), [Aliexpress](https://www.aliexpress.com/af/sn76489.html?d=y&origin=n&SearchText=sn76489&catId=0&initiative_id=SB_20201212230428)
- It is cheap: ~$1
- It is easy to program
- Songs don't take that much space
- 3 "square" channels + 1 noise

### The MatrixPortal M4 "expansion" bus

MatrixPortal M4 has 11 lines that can be used to expand (and debug) the board. In our case, we are going to use the A1-A4 lines to control the SN76489 chip.

![](https://cdn-learn.adafruit.com/assets/assets/000/095/061/small360/led_matrices_matrixportal_pinout_analog.jpg?1600991865)

According to the [schematic](https://learn.adafruit.com/assets/95095), these 4 lines (A1-A4) are SERCOM lines, meaning that they can be used for SPI among other things. And in the [SAMD51 datasheet](http://ww1.microchip.com/downloads/en/DeviceDoc/SAM_D5xE5x_Family_Data_Sheet_DS60001507F.pdf), we can see that A1 (real name is PA05) can be used as clock, and A2 (real name is PA04) as MOSI ( [not every combination is valid](https://github.com/adafruit/circuitpython/issues/3798)).

We are going to use SPI to drive a 74HC595, which is a serial-to-parallel chip. And the 74HC595 will connect to the SN76489. This is the schematic:

[![](/wp-content/uploads/2020/12/soundcard.png?w=799)](/wp-content/uploads/2020/12/soundcard.png)

The most important to keep in mind is how the Matrix Portal is connected to the 74HC595:

- A1 <--> SRCLK in 74HC595
- A2 <--> SER (MOSI) in 74HC595
- A3 <--> RCLK in 74HC595
- A4 <--> /WE in SN76489

![](https://lh3.googleusercontent.com/pw/ACtC-3dORo_lpySdKGT5dLdLvUfUZKtyNs6ztvrgDdFwALVFVt3hSyBq_36oJtYJmOmveAeGzAbx89Ij4dtyXqrM9qkNiaNmSRR51FfDpHIhPCfH8i_IwymCXy0wWViVhJgYZ9PM_pydHpfk6YJetyWsNhmd_Q=-no)

The rest is very similar to other existing schematics. E.g: this one from [Aidan Lawrence](https://github.com/AidanHockey5):

- [https://github.com/AidanHockey5/ESP8266\_VGM\_Player](https://github.com/AidanHockey5/ESP8266_VGM_Player)

**BOM:**

- 1 x [SN76489](https://www.ebay.com/sch/i.html?_from=R40&_trksid=p2380057.m570.l1313&_nkw=sn76489&_sacat=0)
- 1 x [74HC595](https://www.digikey.com/en/products/detail/texas-instruments/SN74HC595N/277246)
- 1 x [3.579545MHz oscillator](https://www.digikey.com/en/products/detail/ecs-inc/ECS-100AX-035/827253)
- 1 x [LM386 audio amplifier module](https://www.amazon.com/gp/product/B01FDD3FYQ/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)
- 1 x [3-watt, 8-ohm speaker](https://www.amazon.com/gp/product/B07YX9QLLN/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

I chose a 3.579545Mhz oscillator to be compatible with IBM PC Jr / Tandy 1000. But you can choose any oscillator up to 4.0 Mhz.

### SN76489 pinout

If you have never used a SN76489 before, then **pay special attention to the pinout!**

![](https://lh3.googleusercontent.com/pw/ACtC-3c0Ob7F4qSneQUY91I_RjecYUPU6W91R77-CRxYtnV9EjJo1tZXFgZvbnO7N_YBNZL0ze2jck99TjJjsWwpKj0Z7upHslsdY7r5gpZCvcJgc7nK8zPt8B4FAMX4UqzQ42p48G9RdbKgV0gi-dDyeQQWBA=-no)

The answer is: **both**. The left one is using the lines in MSB (WTF Texas Instruments!) and the right one is in LSB. If that is confusing, **then just use the one from the right!**

Since I did the wiring in the wrong order (I used the left pinout without knowing it was in MSB order) and was too lazy to re-wire it, I "fixed" it in software by converting MSB <--> LSB while writing the data to the 74HC595:

- [music76489.py hack](https://gitlab.com/ricardoquesada/bluepad32/-/blob/ddf293cd48156b8ad73452b4dc20e1309ca6c736/tools/circuitpython/music76489.py#L195)

Notice that I'll remove the hack in the future, once the wiring is fixed.

### Playing music from CircuitPython

The good thing about using SPI, is that we can do everything from Python, without resorting to C. CircuitPython already [has a library to drive the 74HC595](https://learn.adafruit.com/74hc595/usage), so it was pretty easy to support it.

I wrote a simple python library to [play VGM music files](https://www.smspower.org/Music/VGMFileFormat).

- [music76489.py](https://gitlab.com/ricardoquesada/bluepad32/-/blob/master/tools/circuitpython/music76489.py)

And they way to use it is very simple:

```
import music76489

m = music76489.Music76489()
m.load_song('my_song.vgm')
while True:
  # This is your game main loop
  m.play()
```

The complete source code of the game that [appears in the video](https://www.youtube.com/watch?v=G_Fzt8RlbFc) is here:

- [code\_snake.py](https://gitlab.com/ricardoquesada/bluepad32/-/blob/master/tools/circuitpython/code_snake.py)

### Creating your own song

For the time being, the music library plays VGM sound files (more coming, see down below).

VGM files can be created with different "trackers". I recommend using the [Deflemask tracker](https://www.deflemask.com/) since it is free and multiplatform.

https://www.deflemask.com/deflemask\_full\_7.png

Whereas writing a Deflemask tutorial is outside the scope of this project, you should basically target the SN76489 chip (Sega Master System) at 3.579545Mhz (NTSC) if you want to give it a try.

More information about VGM here:

- [VGM file format](https://www.smspower.org/Music/VGMFileFormat)

### What's next

- Polish the code: remove hacks, cleaner, faster, more documentation, more examples.
- Add support to play music notes, sound effects. Similar to the [Commodore 128 BASIC](https://www.commodore.ca/manuals/128_system_guide/sect-07a.htm) `play` and `sound` commands.
- [Support PVM file format](https://gitlab.com/ricardoquesada/pc-8088-misc/-/tree/master/pvmplay) (less RAM, less disk space).
- Design PCB / Shield for the Matrix Portal M4.
- Design 3D "enclosure" to attach to the speaker.
- Attach a battery.
- Create more games...
- ...in sum, a real Nintendo Switch killer! :)
