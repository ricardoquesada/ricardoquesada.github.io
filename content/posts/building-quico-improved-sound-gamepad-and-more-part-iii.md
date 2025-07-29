---
author: ricardoquesada
category: retro computing
date: "2020-12-31T18:20:10+00:00"
guid: http://retro.moe/?p=2335
tag:
- quico
- circuitpython
- sn76489
title: 'Building Quico: improved sound, gamepad, and more (part III)'
url: /2020/12/31/building-quico-improved-sound-and-more-part-iii/

---

This is the third blog-post regarding "building a video-game console for (my) kids".
See [Part II: chiptune,](/2020/12/13/designing-a-modern-retro-console-for-my-kids-adding-chiptune-music/)
and [Part I: gamepad](/2020/11/24/bluepad32-gamepad-support-for-esp32/).

{{< youtube Ne4RNotvTO0 >}}

## Quico

We have name: Quico. From now on, I'll refer to this project as "Quico":

- Quico ( _/ˈkiko/_), short for _Kids Console_ (or _Kids Computer_)
- Also, one of the main characters of [El Chavo del Ocho](https://es.wikipedia.org/wiki/El_Chavo_del_8)

## Sound Shield

I converted the [breadboard](/2020/12/13/designing-a-modern-retro-console-for-my-kids-adding-chiptune-music/)
into "shield" for the [MatrixPortal M4](https://learn.adafruit.com/adafruit-matrixportal-m4).

![](https://lh3.googleusercontent.com/pw/ACtC-3d8JU3Kzz2r_wpSNG22U2taDkWwqoxAV72PW8Z6FEA5HQqB6Bx3lFg0paf9F-F4xdNhFkXrngcvgbWlcq_hBVDT3Rhi8jgTY-20IZicE82JKaItYKpKWN7p1CgZvzQQFLQm_BkirXmkJyuTCwBT3HaHGQ=w1926-h1299-no)
<small>*Shield for the MatrixPortal M4.*</small>

"Shield" features:

- Output:
    - Headphones: Audio jack
    - or Speaker: 5V/GND/AudioOut pins
- Fits perfectly on top of the MatrixPortal M4
- Sturdy connection: 8 pins + 2 screws
- Easy to solder: All components are through-hole, except audio-jack (SMD) but
  it is as easy to solder as the rest.
- Open source / open
  hardware ( [docs, schematics, layout](https://gitlab.com/ricardoquesada/quico/-/blob/master/docs/shield_76489.md))

![](https://lh3.googleusercontent.com/pw/ACtC-3d1TU056cwMDxYY4IBkjUhEd28KIE88TKDuW2Hs8wluNMVKVfJmVq_R_5JAKY8i595GPtgTgMlUfbblmSIxG4L_-NhtDhNutWkcgKRPmB5UxGhhOtJaOE4dK-K_nlzxiYGtwFIZ71sYa-Z959tZKBOLCQ=w1732-h1299-no)
<small>*Shield + MatrixPortal M4 + LED matrix.*</small>

## Improved sound API

The sound API was improved:

- Added new "sync" methods (functions that return when music ends)
    - To be used mostly from [CircuitPython](https://circuitpython.org/) REPL
      console
    - But can be used for simple games as well
- Improved "async" VGM player
    - Easier to use

Examples of improved APIs:

```python
import music76489

m = music76489.Music76489()

# Sync APIs: can be used from REPL,
# like if you were using BASIC in a Commodore 128

# To play certain frequencies
m.play_freq(voice, freq)

# To play noise
m.play_noise(mode, shift_rate)

# To play notes: supports different voices, duration, semi-tones, and more.
m.play_notes('CDEFGAB')

# To set the volume
m.set_vol(voice, volume)

# To just play a VGM song:
m.play_vgm('data/mysong.vgm')

# Async API:
m.load_vgm('data/mysong.vgm')
while True:
    m.tick()
    time.sleep(1 / 60)
```

The latest version can be found here:

- [music76489.py](https://gitlab.com/ricardoquesada/quico/-/blob/master/src/music76489.py)

## Improved gamepad support

![](https://lh3.googleusercontent.com/pw/ACtC-3ehW50dw03lV8M7mpX9tQIHmt0ITR3g-H46fz3tIeTFVjOXCrBiCBIUiCtpLHnfcnyolnOYSAJeXMtp2iBBghtOm-Ahdd8NnHy6ZoK5kMG1JNKcxVga1_RhoIqEwLO0hNvjQQrCm-Y4xZ_7qMyh_98Kwg=w1732-h1299-no)

```python
# To change gamepad LED color.
# Valid for DualShock 4. DualSense coming soon.
spi.set_gamepad_color_led(gamepad_seat, rbg_color)

# To change gamepad players LED.
# Valid for Nintendo Switch, Wii, Wii U and other gamepads
spi.set_gamepad_player_leds(gamepad_seat, leds)

# To set rumble (AKA force-feedback).
# Valid for DualShock4, Xbox One S, Nintendo Switch controllers
spi.set_gamepad_rumble(gamepad_seat, force, duration)
```

The latest version can be found here:

- [bluepad32.py](https://gitlab.com/ricardoquesada/bluepad32/-/blob/master/tools/circuitpython/bluepad32.py)

## Parts

![](https://lh3.googleusercontent.com/pw/ACtC-3ehXagSfw4_d4GshrCSb8OsJ6Ro1M9sZjthuA3nbOVnnej1jXkUKSAJlqFnR6hUObkApTw2OYqwGvw48N9ADuytv7oV9raeanZThrELtKN9KlM8x9aqWIAx9hXA5ccIlSoBf64SOmdoVZz6TTVPbzTFew=w1856-h1299-no)

- A: [64x32 LED Matrix display](https://www.adafruit.com/product/2279)
- B: [Adafruit MatrixPortal M4](https://www.adafruit.com/product/4745)
- C: [Music shield for the MatrixPortal M4](https://gitlab.com/ricardoquesada/mpm4_sn76489)
- D: Bluetooth gamepad ( [any modern Bluetooh gamepad will work...](https://gitlab.com/ricardoquesada/bluepad32/-/blob/master/docs/supported_gamepads.md))
- E: [Audio amplifier](https://www.amazon.com/gp/product/B01FDD3FYQ/ref=ppx_yo_dt_b_asin_title_o05_s00?ie=UTF8&psc=1)
- F: [8 Ohm speaker](https://www.amazon.com/gp/product/B07YX9QLLN/ref=ppx_yo_dt_b_asin_title_o04_s00?ie=UTF8&psc=1)

## Official git repository

Quico-related stuff is hosted
here: [https://gitlab.com/ricardoquesada/quico](https://gitlab.com/ricardoquesada/quico)

## TODO

The project is still in its early stage, so there is many things left to do. To
name a few:

- Write games!
- Write documentation
- 3d-printed enclosure/border
- Polish
