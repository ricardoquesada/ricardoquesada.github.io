---
author: ricardoquesada
category: embedded
date: "2021-07-26T04:47:39+00:00"
guid: https://retro.moe/?p=2388
tag:
- arduino
- bluepad32
- circuitpython
- esp32
title: Bluepad32 support for Arduino and CircuitPython
url: /2021/07/25/bluepad32-support-for-arduino-and-circuitpython/

---

[![](/wp-content/uploads/2021/07/bluepad32-arduino-circuitpython.png?w=800)](/wp-content/uploads/2021/07/bluepad32-arduino-circuitpython.png)

It is now possible to use Bluetooth gamepads both in Arduino and CircuitPython
projects.

This means that you can use your PlayStation (PS3, PS4, PS5), Nintendo (Wii, Wii
U, Switch) and Xbox One S gamepads in your electronics project: control a robot,
home-automation, video games, etc... everything controlled from your favorite
gamepad.

The catch is that not every Arduino or CircuitPython boards are supported. In
fact, only a few of them are supported.

For Arduino, the boards that have
the [NINA-W10x](https://www.u-blox.com/en/product/nina-w10-series-open-cpu) (
ESP32) co-processor are supported, like:

- [Arduino Nano RP2040 Connect](https://store.arduino.cc/usa/nano-rp2040-connect-with-headers) (
  great board, get one if you haven't already)
- [Arduino Nano 33 IoT](https://store.arduino.cc/usa/nano-33-iot)
- [Arduino MKR WiFi 1010](https://store.arduino.cc/usa/mkr-wifi-1010)
- [Arduino MKR VIDOR 4000 WiFi](https://store.arduino.cc/usa/mkr-vidor-4000)
- [Arduino Uno WiFi Rev 2](https://store.arduino.cc/usa/arduino-uno-wifi-rev2)
- ...and probably a few more. If it has the NINA-W10x co-processor, it is
  supported.

And similar for CircuitPython, the boards that have the AirLift (ESP32)
co-processor are supported, like:

- [Adafruit MatrixPortal M4](https://www.adafruit.com/product/4745) (great to
  create [a video-game console](/2020/12/13/designing-a-modern-retro-console-for-my-kids-adding-chiptune-music/))
- [Adafruit Metro M4 Express AirLift](https://www.adafruit.com/product/4000)
- [Adafruit PyPortal](https://www.adafruit.com/product/4116)
- [Adafruit PyBadge](https://www.adafruit.com/product/4200)

With the additional benefit that you can use any CircuitPython board by
attaching the stand-alone AirLift module:

- [AirLift module](https://www.adafruit.com/product/4201)

## How does the co-processor work

Before describing how Bluepad32 works, it is better to first describe how WiFi
works on NINA and AirLift co-processors (ESP32).

Both Arduino and CircuitPython use the co-processor mostly as WiFi modules. In
order to use WiFi, you would use:

- [WiFiNINA library](https://www.arduino.cc/en/Reference/WiFiNINA), in Arduino
- [ESP32SPI library](https://circuitpython.readthedocs.io/projects/esp32spi/en/latest/api.html),
  in CircuitPython

These two libraries (WiFiNINA and ESP32SPI) have the same functionality. In fact
they are compatible. The only difference is that WiFININA is written in C++ ,
and ESP32SPI in Python.

The co-processor (ESP32) comes pre-flashed with the
Arduino [NINA firmware](https://github.com/arduino/nina-fw).

[![](/wp-content/uploads/2021/07/arduino-wifi.png?w=952)](/wp-content/uploads/2021/07/arduino-wifi.png)

The ESP32 (A) connects to the internet using WiFi. And then sends the data back
to the main processor (B). It uses a protocol that has some predefined messages
like:

- Open HTTP connection and get data
- Enumerate SSID networks
- Connect to SSID network
- etc.

## How does Bluepad32 work

Now that we know how WiFi works, it is easier to explain how Bluepad32 works.
Similar to WiFi, Bluepad32 has two main parts:

- [Bluepad32 firmware](https://gitlab.com/ricardoquesada/bluepad32)
- Bluepad32 library

[![](/wp-content/uploads/2021/07/arduino-bluepad32.png?w=952)](/wp-content/uploads/2021/07/arduino-bluepad32.png)

The gamepad connects to the ESP32 (A) using Bluetooth. And the ESP32 (A) sends
the gamepad data to the main processor (B). It uses the same protocol used by
the NINA firmware, but with some extended messages like:

- Get gamepad data
- Set rumble on gamepad
- Set player LEDs on gamepad
- etc.

Bluepad32 firmware has the following features:

- Has Bluetooth gamepad support
- Runs on the co-processor (ESP32)
- Replaces the Arduino NINA firmware
- Uses the same NINA firmware protocol
- There are two variants of the firmware:
    - [Bluepad32 firmware for NINA co-processors](https://gitlab.com/ricardoquesada/bluepad32/blob/main/docs/plat_nina.md)
    - [Bluepad32 firmware for AirLift co-processors](https://gitlab.com/ricardoquesada/bluepad32/blob/main/docs/plat_airlift.md)

Bluepad32 library has the following features:

- Runs on the main processor
- Fetches that gamepad data from the co-processor
- There are two version of the library:
    - [Bluepad32 library for Arduino](https://gitlab.com/ricardoquesada/bluepad32-arduino)
    - [Bluepad32 library for CircuitPython](http://Bluepad32 library for
      CircuitPython)

## How to use it in Arduino

![](https://gitlab.com/ricardoquesada/bluepad32-arduino/-/raw/main/img/bluepad32-arduino-logo.png)

Bluepad32 library is part of the
official [Arduino library registry](https://github.com/arduino/library-registry),
so, you can install like any other Arduino library:

Arduino IDE -> Tools -> Manage Libraries -> Search for "bluepad32" and install.

[![](/wp-content/uploads/2021/07/screenshot-from-2021-07-25-19-01-23.png?w=861)](/wp-content/uploads/2021/07/screenshot-from-2021-07-25-19-01-23.png)

And it comes already with an example that shows how to use it:

Arduino IDE -> File -> Examples -> Bluepad32 -> Gamepad

To flash the Bluepad32 firmware in your Arduino board, please follow these
instructions:

- [How to flash Bluepad32 firmware for NINA co-processors](https://gitlab.com/ricardoquesada/bluepad32/-/blob/main/docs/plat_nina.md)

## How to use it in CircuitPython

![](https://gitlab.com/ricardoquesada/bluepad32-circuitpython/-/raw/main/img/bluepad32-circuitpython-logo.png)

Bluepad32 library is part of the
official [CircuitPython Community Library Bundle](https://circuitpython.readthedocs.io/en/latest/docs/drivers.html).
You can install it like any other CircuitPython library.
Install [circup](https://circup.readthedocs.io/en/latest/) and then do:

```
$ circup install bluepad32
```

This example shows how to use Bluepad32 library for CircuitPython:

- [bluepad32\_simpletest.py](https://gitlab.com/ricardoquesada/bluepad32-circuitpython/-/blob/main/examples/bluepad32_simpletest.py)

And to flash the Bluepad32 firmware in your CircuitPython board, please follow
these instructions:

- [How to flash Bluepad32 firmware for AirLift co-processors](https://gitlab.com/ricardoquesada/bluepad32/-/blob/main/docs/plat_airlift.md)

## NINA vs AirLift vs ESP32

**[NINA-W10x](https://www.u-blox.com/en/product/nina-w10-series-open-cpu)** are
ESP32 modules. They are similar in functionality to
the [ESP32-WROOM-32](https://www.espressif.com/en/products/modules/esp32)
modules. Although the NINA modules are built by u-blox, and not by Espressif (do
not confuse a ESP32 module with the ESP32 chip).

u-blox, in addition to the NINA-W10x modules, makes other modules that are not
ESP32-based. But for the sake of simplicity, in this article, when we mention "
NINA", we talk about the NINA ESP32-based modules.

The NINA modules come pre-flashed with the
Arduino [NINA firmware](https://github.com/arduino/nina-fw), and in order to
talk to them, you use the
the [WiFiNINA library.](https://www.arduino.cc/en/Reference/WiFiNINA)

Makes sense, it is consistent:

- Module
  name: [NINA-W10x](https://www.u-blox.com/en/product/nina-w10-series-open-cpu)
- Firmware name: [Arduino NINA-W10x firmware](http://Arduino NINA-W102 firmware)
- Library name: [WiFiNINA](https://www.arduino.cc/en/Reference/WiFiNINA)

**AirLift modules**, on the other hand,
are [ESP32-WROOM-32](https://www.espressif.com/en/products/modules/esp32)
modules. I guess "AirLift" was created as a marketing name. But what is
confusing is that they come pre-flashed with a fork of the Arduino NINA
firmware, and the library name is called ESP32SPI.

It is confusing:

- Module name: [AirLift](https://www.adafruit.com/product/4201)
- Firmware
  name: [Adafruit NINA-W10x firmware](https://github.com/adafruit/nina-fw) (fork
  of Arduino's).
- Library
  name: [ESP32SPI](https://circuitpython.readthedocs.io/projects/esp32spi/en/latest/api.html)

(Adafruit, if you are reading, I'd rename them to "AirLift firmware", and "
AirLift library").

Whether it is a NINA-W10x, an AirLift module or an ESP32-WROOM32, all of them
have the ESP32 chip inside. And all of them can run the NINA firmware, or the
Bluepad32 firmware, or mostly any other ESP32 firmware that are out there.

So, if all of them are ESP32-based, and if WiFiNINA and ESP32SPI library are
compatible, why did Adafruit fork Arduino's NINA firmware? So far, the only
incompatibility that I found, is that the MOSI pin (from SPI) is different.

- [NINA uses GPIO 12 for MOSI](https://github.com/arduino/nina-fw/blob/fc6bd42754ecf8e32079f9f2f3bec22d177ce0bf/arduino/libraries/SPIS/src/SPIS.cpp#L116)
- [AirLift uses GPIO 14 for MOSI](https://github.com/adafruit/nina-fw/blob/0e267bc8858f188f5ac7c1527d0554d8294ca756/arduino/libraries/SPIS/src/SPIS.cpp#L116)

GPIO 12 is strapping pin, and at boot time it is used internally by the
ESP32. [It seems that it was causing some interference with some modules](https://github.com/adafruit/nina-fw/commit/9e76479a7e1e11682009078c45ad307cb96c1066#diff-c04b1ff645810e3a002a1166ab130c6fd92b997e695b9bdf61008fd83015326a).

And just because of that change (different MOSI pins) I needed to create a "
Bluepad32 firmware for NINA" and a "Bluepad32 firmware for AirLift".
