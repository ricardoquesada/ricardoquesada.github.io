---
author: ricardoquesada
category:
  - programming
date: "2021-09-05T21:35:04+00:00"
guid: https://retro.moe/?p=2417
summary: |-
  https://www.youtube.com/watch?v=nCzAlfXOOXo

  "Amor para Dos" is a multi-platform 256-byte intro. The binary, without any kind of modification, can run both on:

  - a 80386 (or better) + DOS
  - and on a Commodore 64.

  We ( [L.I.A](http://lia.rebelion.digital/)) released it at [Flashparty 2021](https://file+.vscode-resource.vscode-webview.net/home/riq/progs/lia/flash-2021/flash2021). I did the coding.
tag:
  - c64
  - commodore-64
  - dos
  - intro
title: A multi-platform 256-byte intro
url: /2021/09/05/a-multi-platform-256-byte-intro/

---
{{< youtube nCzAlfXOOXo >}}

"Amor para Dos" is a multi-platform 256-byte intro. The binary, without any kind of modification, can run both on:

- a 80386 (or better) + DOS
- and on a Commodore 64.

We ( [L.I.A](http://lia.rebelion.digital/)) released it at [Flashparty 2021](https://file+.vscode-resource.vscode-webview.net/home/riq/progs/lia/flash-2021/flash2021). I did the coding.

## Multi-platform internals

A bit of context:

- DOS: A `.com` file has no header. The first byte of the `.com` is code: this first byte will get executed first.
- C64: A `.prg` file has a header of two bytes. These two bytes indicate the load address of program. E.g: If the first two bytes are `0x01` and `0x08`, it means that program will be loaded at address: `0x0801`.

Taking that into account, there are different ways to support both DOS and C64 at the same time:

- Using the standard `0x0801` address (the one used by this intro).
- Or autorun: using an address like `0x02NN`, where `NN` could be any of the [single-byte instructions](http://xxeo.com/single-byte-or-small-x86-opcodes). E.g: A good candidate for autorun could be `0x02cc`.

Let's see in detail how using `0x0801` start address work:

```
$01 $08         ; Start Address ($0801)
$0b $08         ; Next basic instruction: Address $080b
$75 $08         ; BASIC line number. E.g: 2165, but could be any number
$9e             ; BASIC "SYS" token
$32 $32 $32 $34 ; "2224"
$00             ; End of line
$00 $00         ; Address: $080b. End of BASIC program

```

- In summary, the first two bytes are fixed: `$01 $08`.
- Bytes 2 and 3 can be somewhat controlled.
- Bytes 4 and 5 can be fully controlled.
- ...and the rest is not important since we can fully control bytes 4 and 5.

[![](/wp-content/uploads/2021/09/c64-sys.png?w=384)](/wp-content/uploads/2021/09/c64-sys.png)

If we disassemble our C64 program like if it were a DOS .com, it would look like:

```asm
.org 0x100

    ; Assumes: (see: http://www.fysnet.net/yourhelp.htm)
    ;  BX=0x0000
    ;  CX=0x00ff
    ;  SI=0x0100
    add     [bx + si], cx           ; Bytes $01 08$
    or      cx, [bx + si]           ; Bytes $0b $08

    ; we control the next 2 bytes: $0875 (2165)
    ; Meaning that the BASIC line will be 2165
    ; "Z" won't be set, so the jump is guaranteed.
    jnz     start                   ; Bytes $75 $08

    db      0x9e                    ; BASIC "SYS" opcode
    db      0x32, 0x32, 0x32, 0x34  ; "2224" or 0x08b0: C64 start address
    db      0x00                    ; End of line
    db      0x00, 0x00              ; End of BASIC program

start:
    ;Our start code

```

The first 2 instructions could potentially break our DOS program. But if you look at the [initial values of `BX`, `SI` and `CX`](http://www.fysnet.net/yourhelp.htm), it is safe to assume that:

- `BX = 0x0000`
- `SI = 0x0100`
- `CX = 0x00FF`

What will happen is that the first instruction will overwrite itself, and the second will overwrite `CX`. The `OR` will set `Z=0`. And the following instruction will jump to our start address.

The generated binary will run both on a DOS machine and on a C64. This technique does not use any emulator trick. The binary runs in real hardware.

What's nice about this technique is that it doesn't add any overhead: no additional bytes are needed to support both platforms.

**Challenge**: Create a binary that can run in 3 different platforms.

## Size distribution

The 256 bytes of the intro are distributed like the following:

[![](/wp-content/uploads/2021/09/size_distribution.png?w=748)](/wp-content/uploads/2021/09/size_distribution.png)

- Green: C64 bootstrap ( `SYS 2224`), 14 bytes (~5%)
- Blue: DOS code, 112 bytes (~43%)
- Pink: C64 scroller text, 51 bytes (~20%)
- Red: C64 code, 79 bytes (~30%)

Total:

- DOS: 112 bytes (~43%)
- C64: 14 + 51 + 79: 144 bytes (~57%)

## Download + Source code + Misc links

Binary is available here:

- [amor\_para\_dos\_lia2.zip](https://csdb.dk/release/download.php?id=256784)

Commented source code is available here:

- [https://gitlab.com/ricardoquesada/c64-pc-intro-amor-para-dos](https://gitlab.com/ricardoquesada/c64-pc-intro-amor-para-dos)

Misc links:

- Pouet: [https://www.pouet.net/prod.php?which=89786](https://www.pouet.net/prod.php?which=89786)
- CSDB: [https://csdb.dk/release/?id=207946](https://csdb.dk/release/?id=207946)
