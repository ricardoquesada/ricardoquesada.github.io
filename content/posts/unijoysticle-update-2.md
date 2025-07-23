---
author: ricardoquesada
category: retro computing
date: "2016-09-27T18:18:00+00:00"
guid: http://retro.moe/?p=1883
tag:
  - c64
  - unijoysticle
title: 'UniJoystiCle update #2'
url: /2016/09/27/unijoysticle-update-2/

---
### TL;DR

- Station Mode (with or without WPS)
- Inactivity timeout  & Joystick statistics
- Auto-firmware upgrade
- Better ways to power the WiFi device

### Station mode and other features

![](https://lh3.googleusercontent.com/0IWKb6TdvqIj-p_fx7QMHMIiL7Zt-AuS_-vOG0K9o_J2ievuhhanZz7u3fnAkPSwNHbvCJD-K_M94w=w1047-h1320-no)

One thing that bothered me was that I needed to switch WiFi networks every time that I wanted to use the UniJoystiCle. Not a major issue, but not ideal specially if you use your phone both for the UniJoystiCle and for "regular" stuff.

To solve that issue, I added WiFi Station mode support (Access Point mode is still supported). Basically the UniJoystiCle WiFi device, when in Station mode, can connect to any WiFi network. It also supports [WPS](https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup) (an auto-auth way to connect to a network). If Station mode fails, it will default to Access Point mode.

In order to switch to Station mode you have to:

- Install firmware v0.4.3 (see below for more info)
- Boot the UniJoystiCle WiFi device (it will boot in Access Point mode)
- Connect to the unijoysticle-xxyyzz WiFi Network
- Open the web page: [http://unijoysticle.local](http://unijoysticle.local)
- Select "Station" mode, put the credential (SSID and password) and reboot!

From [http://unijoysticle.local](http://unijoysticle.local) you can also configure the "Inactivity timeout": how many seconds without activity should elapse before all the joystick lines are set to Low (simulates no joystick movements).

I also added statistics: It tells you how many seconds you spent on the different joystick positions, and how many movements you did. Useful, right? :)

### Installing a new firmware

Another thing that needed to be improved was flashing a new firmware. Before v0.4.3, you had to do compile the firmware yourself, and upload it. Not ideal, specially if you are not a developer.

Since then, manually flashing the firmware was simplified a bit:

1. Install the [CP2104 USB-to-Serial drivers](https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)
1. Download the latest [firmware from here](http://ricardoquesada.github.io/unijoysticle/bin/unijoysticle_firmware.bin)
1. Install esptool & flash the new firmware:

```
$ pip install esptool

# Mac
$ esptool.py --port /dev/cu.SLAB_USBtoUART write_flash -fm dio -fs 32m 0x00000 /path/to/unijoysticle_firmware.bin

# Linux
$ esptool.py --port /dev/ttyUSB0 write_flash -fm dio -fs 32m 0x00000 /path/to/unijoysticle_firmware.bin

# Windows (I haven't tried it. I don't know what is the serial port there)
```

For Windows, esptool.py should work as well, but [NodeMCU-Flasher](https://github.com/nodemcu/nodemcu-flasher) seems easier to use.

And once you have v0.4.3 installed, you no longer need to manually flash new updates. Upgrades can be done from the WiFi device itself:

- Make sure that the WiFi device is in Station mode (needs internet connectivity)
- Open this URL, and follow the instructions:
  - [http://unijoysticle.local/upgrade](http://unijoysticle.local/upgrade)

### Powering the WiFi Device

![](https://lh3.googleusercontent.com/s69EPOF4EnTb23CztCpkqPE_c-eTqILBmAteYfSievi48mHasxSDYgsZvnPvBW5RWq2cbv1fjqtgTQ=w1218-h1624-no)

Powering the device with a USB cable works. In fact, that is what I do with my devel WiFi board. But if you are not a developer powering the device from the Datasette port is a better alternative: self-powered, looks better.

An inexpensive (less than $3) DIY cable can be done with:

- 1 x [Molex](http://www.mouser.com/Search/ProductDetail.aspx?R=172879-0206virtualkey53850000virtualkey538-172879-0206) [172879-0206](http://www.mouser.com/Search/ProductDetail.aspx?R=172879-0206virtualkey53850000virtualkey538-172879-0206) ($0.49)
- 2 x [Molex 172160-1803](http://www.mouser.com/Search/ProductDetail.aspx?R=172160-1803_(Loose_Piece)virtualkey59680000virtualkey538-172160-1803-LP) ($0.10 ea)
- 1 x [Barrel Power Cable CA-2185](https://www.digikey.com/product-detail/en/tensility-international-corp/CA-2185/CP-2185-ND/568576) ($2.10)

The benefits of this cable are:

- Soldering is not required
- It fits in the C128D

The drawback, is that it is not a pass-through cable: You cannot use the datasette while using this cable. But hey, it costs less than $3.

Another thing is that the WiFi device needs less current than initially thought:  320mA instead of 400mA (this is the max needed current).  In fact, on regular usage (no more than 5 High lines at the same time, and connected to a N WiFi network), it doesn't need more than 150mA.

### iOS & Android clients

I noticed some bugs with the UniJoystiCle mode (both on iOS and Android) and added support for multicast DNS on Android (already built-in on iOS). The WiFi device advertises itself as _unijoysticle.local._ That means that you can use "unijoysticle.local" as the WiFi device address, and this will work both on Station and Access Point modes.
