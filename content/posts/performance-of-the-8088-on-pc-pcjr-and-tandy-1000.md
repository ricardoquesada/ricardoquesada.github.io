---
author: ricardoquesada
category: retro computing
date: "2018-03-05T05:34:26+00:00"
guid: http://retro.moe/?p=2088
tag:
- "8088"
- ibm-pcjr
- pcjr
- tandy1000
title: Performance of the 8088 on PC, PCjr and Tandy 1000
url: /2018/03/04/performance-of-the-8088-on-pc-pcjr-and-tandy-1000/

---

![](/images/performance-of-the-8088-on-pc-pcjr-and-tandy-1000.jpg)

It's well-known that you
should [measure the performance of your code](https://github.com/jagregory/abrash-zen-of-asm/blob/master/src/chapter-04.md),
and not rely only on the opcode's "cycle counts".

But how fast is an IBM PC 5150 compared to a PCjr ? or to a Tandy 1000? or how
fast is the Tandy 1000 HX in fast mode (7.16Mhz) compared to the slow mode (
4.77Mhz) ? Or how fast is a `nop` compared to a `cwd` ?

I created a
test ( [perf.asm](https://github.com/ricardoquesada/pc-8088-misc/blob/master/opcodes_perf/perf.asm))
that measures the performance of different opcodes and run it on different Intel
8088 machines. I run the test multiple times just to make sure the results were
stable enough. All interrupts were disabled, except the Timer (of course). And
on the PCjr the NMI is disabled as well.

Without further ado, here are the results:

- [Intel 8088 opcodes performance](https://docs.google.com/spreadsheets/d/1geGxh76SVFHNi3xR6HEKpHHVckLLz9DsK3JNdPi6pBA/edit?usp=sharing)

And these are my conclusions:

- As expected, 1-byte size + 3-cycles opcodes are the fastest: `nop`,
  `xchg ax,xx`, `inc ax` (note that
  `nop` [is literally a](https://en.wikipedia.org/wiki/NOP) `xchg ax,ax`)
- 2-byte + 2-cycle opcodes (like `mov al,al`) are twice as slow as the 1-byte +
  3-cycle opcodes.
- CPU intensive instructions like `mul` and `div` perform exactly the same in
  all machines. Cycle-eaters don't affect them that much (kind of expected).
- In theory, the 7.16Mhz Tandy 1000 HX should be 50% faster than the 4.77Mhz
  mode. And that's true for CPU-intensive opcodes like `mul` and `div`. But
  opcodes that are "cycle-eaters"-bound the performance gain is 0% in most of
  them.
- IBM PCjr vs. IBM PCjr: The PCjr could be by far the slowest of the 4.77Mhz
  machines, or the fastest:
    - When running code in the first 128 Kb RAM the performance is terrible! A
      simple `mov al,al` is **2.6 times slower**! [This is due to additional wait-states](https://en.wikipedia.org/wiki/IBM_PCjr#Processor_speed).
    - On the other hand, when running code above the 128 Kb RAM, it is the
      fastest (albeit by a tiny bit).
- One of my IBM PCjr is a tiny bit faster than the other one. Couldn't find out
  why. The CPU is the same, same clock speed. Something in the bus (?) perhaps ?
  It is faster enough to break some cycle-dependent code.
- From fastest to slowest:
    - IBM PCjr (code running above 128 Kb RAM)
    - IBM PC 5150 (tiny bit slower)
    - Tandy 1000 (tiny bit slower)
    - Tandy 1000 HX 4.77Mhz-mode (tiny bit slower)
    - IBM PCjr (code running below 128 Kb RAM) (slower by a huge margin)

One opcode that is worth-noting is `cwd`:

- It is a 1-byte size, 5 cycles opcode
- It is a tiny bit slower than a `nop`
- The negative side is that it destroys `ax` and `dx`

What I like about it, is that it is between 7%~17% slower than a `nop` (
depending on the machine).
And when doing timing dependent code, sometimes you
need an opcode that is just a tiny bit faster or slower than another one. In my
case, I was able to have a stable raster bar on the Tandy 1000 thanks to it (
more on this in a future post).
