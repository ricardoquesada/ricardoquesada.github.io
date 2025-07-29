---
author: ricardoquesada
category: retro computing
date: "2016-03-11T09:54:00+00:00"
draft: "true"
guid: http://retro.moe/?p=1234
tag:
  - c64
  - ethernet
title: Ethernet for the Commodore 64
url: /ethernet-and-the-commodore-64

---
Back in the 80's, the way to connect the c64 to other computers was by using a modem. Since then different devices were created and new technologies were developed. Here, I'll only focus on the Ethernet devices and what you can do with it.

#### Ethernet cards

Let's start from the beginning. Basically there are two group of Ethernet cards:

- Those who use the CS8900a chip:
  - [RR-NET](http://ar.c64.org/wiki/RR-Net)
  - [64Nic+](http://www.go4retro.com/products/64nic/) (and 64Nic)
  - [The Final Ethernet](http://dunkels.com/adam/tfe/)
  - FB-Net
  - Net64
- Those who use the LAN91C96 chip:
  - [ETH64](http://www.ide64.org/eth64.html)

This is important due to the drivers.

**TCP/IP Stack**

Having only 64k RAM, and 1Mhz CPU it is expected to have a limited TCP/IP stack.  However, they are functional, at least these two stacks:

- [IP65](https://github.com/oliverschmidt/ip65): Which is also part of the [Contiki OS](https://github.com/contiki-os/contiki). Implemented mostly in C with small parts in assembly. It also supports IPv6.
- Netlib64: Coded in Assembly. I couldn't find the official homepage, but it is bundled in these games: [NetRacer](https://github.com/LeifBloomquist/NetRacerClient) and [Artillery Duel](https://github.com/LeifBloomquist/ArtilleryDuel).

I found other "stacks" like:
