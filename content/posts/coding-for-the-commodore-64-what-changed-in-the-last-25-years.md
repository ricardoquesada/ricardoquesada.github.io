---
author: ricardoquesada
category: retro computing
date: "2015-02-02T06:17:03+00:00"
guid: http://towp8.com/?p=514
tag:
- 8-bit
- c64
- retro
title: 'Coding for the Commodore 64: What changed in the last 25 years'
url: /2015/02/01/coding-for-the-commodore-64-what-happened-in-the-last-25-years/

---

[![c64logo](/wp-content/uploads/2015/02/c64logo.png)](/wp-content/uploads/2015/02/c64logo.png)

I stopped developing for the Commodore 64 in 1993. Since then a lot has
happened:

## Back in late 80's ~beginning of 90's

- I did all my coding using the Commodore
  128's[MONITOR](http://www.commodore.ca/manuals/128_system_guide/app-j.htm)
  command
    - That means no text editor, no compiler, no linker.
      Similar to
      the [debug.com](http://en.wikipedia.org/wiki/Debug_%28command%29) command
      that used to be in DOS.
- Since I didn't use a text editor, I put all my comments in a notepad (I still
  have that notepad somewhere)
- I used the Commodore
  128's [SPRDEF](http://www.commodore.ca/manuals/128_system_guide/sect-06b.htm)
  as the Sprite editor.
- I used my own character editor called vchar... (later I created a similar one
  for [DOS](https://github.com/ricardoquesada/vintage/blob/master/progs/dos/vchar/vchar333.asm)
  and [Linux](https://github.com/ricardoquesada/vintage/tree/master/progs/linux/vchar/vchar-1.01))
- I did some basic graphics using a graphics editor... but I can't remember
  which one.
- I didn't know any other C64 developer, so I did everything kind of isolated
    - My sources of information
      were[Commodore Magazine](http://www.bombjack.org/commodore/magazines/commodore-magazine/commodore-magazine.htm), [Tu Micro Commodore](http://scans.bytemaniacos.com/es/tu_micro_commodore/1-semanal/)
      and some books.
    - I reversed engineer some games / demos in order to learn tricks.
    - I had a 300 bps modem but I didn't find any good C64 BBS.
    - I did some cracks for a local company that was "publishing" (AKA pirating)
      games. In exchange they were providing me games. To put things into
      perspective it was impossible (I mean IMPOSSIBLE) to get original games in
      Argentina back then.
- I knew some basic tricks like how to use more than 8 sprites, how to open the
  top and bottom borders, some raster effects... but nothing very advanced.
- I loaded all my programs / games using
  the [disk drive](http://en.wikipedia.org/wiki/Commodore_1571), which was much
  faster than the [datasette](http://en.wikipedia.org/wiki/Commodore_Datasette),
  but still very slow
- I had a fast-loader cartridge to accelerate the disk drive loading times. It
  also had a rudimentary MONITOR.
- Although Argentina was using the PAL-N standard I had a NTSC Commodore 128. In
  Argentina we also had the Argentinean Commodore,
  called [Drean Commodore](http://es.wikipedia.org/wiki/Commodore_64#Clones_de_Commodore_64),
  which was a PAL-N machine assembled in Argentina

## And now, in 2015

- You have different cross-assemblers like:
    - [ACME](http://sourceforge.net/projects/acme-crossass/)
    - [KickAssembler](http://www.theweb.dk/KickAssembler/Main.php)
    - a [more](http://www.6502.org/tools/asm/)
- And native assemblers like (the native assemblers were available back then, I
  simply didn't know of their existence):
    - [Turbo Assembler](http://turbo.style64.org/about-the-turbo-assembler-homepage)
- Many editors like:
    - [CharPad](http://www.coder.myby.co.uk/charpad.htm) (a level editor using
      characters for Windows. Works with Wine)
    - [SpritePad](http://www.coder.myby.co.uk/spritepad.htm) (a sprite editor
      for Windows. Works with Wine)
    - [HermIRES](http://sourceforge.net/projects/hermires/)(a PC/Mac/Linux
      graphics editor)
    - [GoatTracker](http://www.sidmusic.org/goattracker/mac/) (a music tracker)
- You even have complete IDEs like:
    - [Relaunch64](http://www.popelganda.de/relaunch64.html)
    - [C64Studio](http://www.georg-rottensteiner.de/en/index.html)
    - [C64 KickAss IDE](http://csdb.dk/release/?id=116290)
- Cross-crunchers(compressors) like:
    - [Exomizer](http://hem.bredband.net/magli143/exo/)
- All the existing C64 tricks are documented here (if it is not there, then it
  doesn't exist):
    - [Codebase64](http://codebase64.org/doku.php):
        - [How to open the side borders](http://codebase64.org/doku.php?id=base:removing_the_sideborders)
        - [Sprite multiplexers](http://codebase64.org/doku.php?id=base:sprites#multiplexing)
        - [3d effects](http://codebase64.org/doku.php?id=base:6502_6510_maths#the_art_of_3d)
        - and much much more
- Many tutorials. A good place to start is here:
    - [Dustlayer](http://dustlayer.com/)
- All books and magazines from the old days were scanned and are available here:
    - [Magazines](http://www.bombjack.org/commodore/magazines.htm)
    - [Books](http://www.bombjack.org/commodore/books.htm)
- Active community:
    - [Lemon64](http://www.lemon64.com/) (English)
    - [Commodore Mania](http://retroinvaders.com/commodoremania/foro/) (Spanish)
- An active demo scene:
    - [csdb.dk](http://csdb.dk/)
- New games... yes people are still releasing new games for the C64, and selling
  them!
    - [RGCD](http://www.rgcd.co.uk/)
    - Even recent popular games were
      ported ( [demakes](http://en.wikipedia.org/wiki/Video_game_remake#.22Demakes.22))
      to the C64:
        - [Canabalt](http://www.rgcd.co.uk/2011/09/c64anabalt-preview-c64.html)(
          C64nabalt)
        - [Super Crate Box](http://superbreadbox.com/)(Super Bread Box)
        - [Super Hexagon](http://csdb.dk/release/?id=125132)(Micro Hexagon)
- Cartridges that support loading games from SD memory cards... no more disk
  drives or datasettes. These cartridges act as fast loaders among other things:
    - [Turbo Chamaleon](http://www.c64-wiki.de/index.php/Turbo_Chameleon_64)
    - [Ultimate 1541](http://www.1541ultimate.net/content/index.php)
- Great Emulators (they emulate everything, including VIC bugs, undocumented
  opcodes, etc.):
    - [VICE](http://vice-emu.sourceforge.net/) (Win/Mac/Linux)
    - [CCS64](http://www.ccs64.com/) (Win only)
- Multi system TVs... (one TV both for PAL and NTSC machines)
    - [220 electronics](http://www.220-electronics.com/multisystem-tvs.html)
- And probably many other things that I'm forgetting

As a reminder, **the Commodore 64 was released in 1982!**.
It is impressive all the things that can be done in a 30+ years old computer!

What I'm doing right now is to code a Unicycle game for the C64. I noticed that
I needed a good map editor (CharPad is a very good one, but it doesn't look good
on the Mac), so I started one
called [VChar64](https://github.com/ricardoquesada/vchar64).
I can re-invent the wheel as many times as I want since I'm doing this for
fun :). I'm also documenting my c64 discoveries
here: [c64-tips-n-tricks](https://github.com/ricardoquesada/c64-tips-n-tricks).
I might never finish this game, since time is very limited. But for me, the goal
is to enjoy the ride.

## My development environment is

- Cross-Assembler: KickAssembler
- Cross-Cruncher: Exomizer
- Text Editor: Vim
  with [KickAssembler syntax highlighting](http://www.vim.org/scripts/script.php?script_id=4121)
- Emulator: VICE
- Machines:
    - Commodore 64 PAL + Turbo Chamaleon + PC monitor
    - Commodore 128 NTSC + 1571 disk drive + Commodore 1802 monitor

Stay tuned for more c64 news!
