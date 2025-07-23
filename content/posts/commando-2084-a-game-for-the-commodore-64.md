---
author: ricardoquesada
category: retro computing
date: "2019-09-29T14:45:14+00:00"
guid: http://retro.moe/?p=2215
summary: |-
  Commando 2084 is the mix between Commando and Robotron 2084: it is like the original Commando game, but using the Robotron 2084 controls.
tag:
  - c64
  - commando
  - unijoysticle
title: Commando 2084 - a game for the Commodore 64
url: /2019/09/29/commando-2084-a-game-for-the-commodore-64/

---
{{< figure align=alignnone width=384 src="https://user-content.gitlab-static.net/cc4101b18a0cfbcbfcbaed797977a0c0b3facd50/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f43596268634e31727055686d4c594e6a454a3177324478744733426b4d655351697671736b784c4b5f7243546a4b426e4c4278374e6b636469426d53765f6a514f33463658574267463443634564337675754438763554742d325f6878674e615154534a574e4164484c64317662594336373355745f49453075434d654a30552d4e56514e706f37495a513d2d6e6f" alt="" >}}

Commando 2084 is the mix between Commando and Robotron 2084: it is like the original Commando game, but using the Robotron 2084 controls.

You play it using the two joysticks at the same time:

- Joy #2 controls the hero direction
- Joy #1 controls the bullets direction

But better if you play it with a [Unijoysticle 2](/unijoysticle2) with a Dualshok4 gamepad (or similar).

{{< youtube iXdx9jOd0Ho >}}

### Download

- Download game: [commando-2084.d64](https://gitlab.com/ricardoquesada/c64-commando-2084/raw/master/bin/commando-2084.d64)
- Source code, fully commented: [https://gitlab.com/ricardoquesada/c64-commando-2084/](https://gitlab.com/ricardoquesada/c64-commando-2084/)

### Changes

- Controls are like in Robotron 2084. Use two joysicks (or one Unijoysticle):
  - Joystick #2 to control the hero direction
  - Joystick #1 to control the fire direction
  - Autofire is enabled
  - 'Space' to throw grenades.
- Levels 2 and 3 have bosses (enemies taken from Robotron 2084)
  - The SFX used when these bossed are killed, are unused SFX from the original Commando.
- Difficulty increased, otherwise the game would be too easy to play:
  - No extra lives
  - 28 soldiers are inside forts, instead of 20
- Flickers were reduced, but there are still a few. Changes made to reduce flickering:
  - Uses double-buffer multiplexer
  - Faster sorting algorithm
  - Faster "view port" rendering
  - Music is played outside IRQ
  - Unrolled some functions like "apply delta"
  - And other tiny improvements here and there
- Smaller binary, single load
  - Removed unused data/code
  - Packed everything in a single binary
  - Compressed binary using exomizer
- Misc fixes
