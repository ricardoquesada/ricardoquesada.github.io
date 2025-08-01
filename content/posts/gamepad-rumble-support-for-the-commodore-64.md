---
author: ricardoquesada
category: retro computing
tag:
- unijoysticle
- rumble
- commodore 64
date: "2022-10-02T19:29:53+00:00"
guid: https://retro.moe/?p=2557
title: Gamepad rumble support for the Commodore 64
url: /2022/10/02/gamepad-rumble-support-for-the-commodore-64/

---

I discovered a way to send 1-bit of data from the Commodore 64 to the Joysticks.
And I use this one-bit of data to turn on/off the rumble in the gamepads through
the Unijoysticle.

{{< youtube vCj45OX43JE >}}

(
Note: [Spanish version of the video is here](https://www.youtube.com/watch?v=0pEDP2tvvQc))

## How does it work

![](https://lh3.googleusercontent.com/pw/AL9nZEW1jK6IsMJQrHdXyUQtQ2jVnDTAlWXk8G6kQvQT29BoMz0-0LXujgGXfnAHvCBB1Bsy9WG5JEOhvlBItmWf_HOl115fwNGnTTd1IMNns1dfZeJLLGnNt8aot6KIbwbmKJLuOZi-eYgzk84GfuVOrji_rw=-no?authuser=0)

I strongly suggest viewing the video (see above) which contains technical
info [starting at 1:24](https://youtu.be/vCj45OX43JE?t=84)

As a summary, it works like this:

- The SID generates pulses that go from 0 to ~1.3v every ~520us
- Those pulses go to the Joystick POT lines
- The pulses can be filtered from the CIA #1, Port A, Pins 6 and 7.
- The Unijoysticle receives the pulses and with the help of a timer and pull-up
  resistors it does the following:
    - If the line is High, turn on Rumble. Otherwise, turn it off.

So, to turn on/off the rumble, we just need to do this in our games:

```asm
;
; Example that shows all 4 possible combinations
;
lda #%00000000   ;turn off rumble in both ports
sta $dc00

lda #%01000000   ;turn on rumble in port 1. Port #2 is Off
sta $dc00

lda #%10000000   ;turn on rumble in port 2. Port #1 is Off
sta $dc00

lda #%10000000   ;turn on rumble in both ports
sta $dc00
```

Note: What this discovery is about, is that by combining different well-known
C64 features, we can now use to send 1-bit of data to the Joystick ports. For
those who are curious about how the ADC works, read this
article: [Commo Pad](https://janderogee.com/projects/COMMO_PAD/COMMO_PAD.htm),
or just
Google ["Mouse 1351 internals"](https://letmegooglethat.com/?q=Mouse+1351+internals).

## The different parts

The project consists of three parts:

- [Unijoysticle Flashparty edition](https://github.com/ricardoquesada/unijoysticle2/tree/main/board/unijoysticle2_flashparty2022)
- [Bluepad32](https://github.com/ricardoquesada/bluepad32): The firmware that
  runs inside the Unijoysticle device (
  requires [v3.5.1](https://github.com/ricardoquesada/bluepad32/releases/tag/release_v3.5.1)
  or newer)
- Modified games: [Rambo](https://github.com/ricardoquesada/c64-rambo)
  and [Lemans](https://github.com/ricardoquesada/c64-lemans)

### Unijoysticle 2 Flashparty edition

|                           Front                           |                          Back                           |
|:---------------------------------------------------------:|:-------------------------------------------------------:|
| ![Front](/images/2022_10_02_flashparty_edition_front.png) | ![Back](/images/2022_10_02_flashparty_edition_back.png) |

This board is based on the original Unijoysticle 2 board, and includes the
following changes:

- Lines that connect to the POT lines
- Some external pull-up resistors
- Improved layout

Schematic and Layout files can be found
here: [unijoysticle2\_flashparty2022](https://github.com/ricardoquesada/unijoysticle2/tree/main/board/unijoysticle2_flashparty2022)

### Bluepad32 v3.5.1

This is the firmware that runs in the Unijoysticle device.

- Includes the code needed to read the POT lines and turn on/off the rumble
  accordingly.

Pre-compiled binary can be found
here: [bluepad32-unijoysticle\_v3.5.1](https://github.com/ricardoquesada/bluepad32/releases/tag/release_v3.5.1)

### Rambo: First Blood, Part II

|                                          Intro                                          |                                          Game                                           |                                          Music Debug                                          |
|:---------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------:|
| ![](https://gitlab.com/ricardoquesada/c64-rambo/-/raw/main/images/screenshot_intro.png) | ![](https://gitlab.com/ricardoquesada/c64-rambo/-/raw/main/images/screenshot_game1.png) | ![](https://gitlab.com/ricardoquesada/c64-rambo/-/raw/main/images/screenshot_music_debug.png) 

Things that I did to the game:

- Took the NTSC (ThunderMountain) version and cracked it
- Disassembled the game and added comments to it
- Patched it to support rumble
- Make it easier to switch weapons (Put Unijoysticle in "Enhanced" mode!). Works
  by pressing space as well.
- Added intro and converted it to a single-file game

While doing it, I discovered Martin Galway's Music Debug routine that can be
accessed by pressing 'P' in the intro. While in the Music Debug routine, press
letters A to Z to turn on the different songs. '1' and '2' switches the
different music bank songs.

The complete disassembled code can be found here:

- [https://github.com/ricardoquesada/c64-rambo](https://github.com/ricardoquesada/c64-rambo)

### Lemans

|                                          Intro                                           |                                          Title                                           |                                          Game                                           |
|:----------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------:|
| ![](https://gitlab.com/ricardoquesada/c64-lemans/-/raw/main/images/screenshot_intro.png) | ![](https://gitlab.com/ricardoquesada/c64-lemans/-/raw/main/images/screenshot_title.png) | ![](https://gitlab.com/ricardoquesada/c64-lemans/-/raw/main/images/screenshot_game.png) |

Things that I did to the game:

- Took the original cartridge binary, disassembled it and fully commented it
- Patched it to support rumble
- Patched other things like: Use joystick instead of paddle, fixed typo in
  message and other minor things
- Added intro

The complete disassembled code can be found here:

- [https://github.com/ricardoquesada/c64-lemans](https://github.com/ricardoquesada/c64-lemans)

## Flashparty

This project was presented
at [Flashparty 2022](https://flashparty.rebelion.digital/) (a demoscene event),
where it got 2nd place in the Wild category.

Many thanks to the organizers, who also setup a Commodore 64 with the
Unijoysticle Flashparty edition so that the public can try it.

![booth](/images/2022_10_02_flashparty_booth.jpeg)

The "Retro Station" at Flashparty with a C64 + Unijoysticle
