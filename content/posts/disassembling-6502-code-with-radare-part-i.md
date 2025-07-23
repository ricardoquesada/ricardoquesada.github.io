---
author: ricardoquesada
category: retro computing
date: "2015-11-19T06:52:23+00:00"
guid: http://retro.moe/?p=988
summary: |-
  [Radare](http://radare.org/) is an open source portable reversing framework that can do many things, among those things it can disassemble 6502 code.

  ### Download and install radare

  - First, download [radare from github](https://github.com/radare/radare2). You need a recent version in order to disassemble 6502 code.
  - And then install it by running _sys/install.sh_ (or _sys/user.sh_ for local installation):

  ```
  $ git clone https://github.com/radare/radare2.git
  $ cd radare2
  $ ./sys/install.sh

  ```

  ### Loading a c64 .prg

  Radare has many command line options. But in order to load 6502 programs we need just two:

  - _-a6502_ to specify the 6502 architecture.
  - _-mMemoryAddress_ to map the file to a certain memory address. Use 2047 for "normal" programs. Usually they start at $0801 (2049), but we have to subtract 2 from the .prg header.

  Example:

  ```
  $ r2 -a6502 -m2047 mygame.prg
  ```

  ### Disassembling

  Radare doesn't have a GUI, like IDA. Instead is has a powerful command line interface (think of GDB). Example:

  ```
  $ r2 -a6502 -m2047 musicplayer.prg
  [0x000007ff]>

  ```

  And _0x7ff_ (2047) is the seek address, meaning that all commands will use that address as the base address. Let's print the first 32 bytes. ( _px_ = print hexa):

  ```
  [0x000007ff]> px 32
  offset   0 1  2 3  4 5  6 7  8 9  A B  C D  E F  0123456789ABCDEF
  0x07ff  0108 0b08 3905 9e32 3036 3100 0000 78ad  ....9..2061...x.
  0x080f  0ddc a212 a000 b9d4 1a99 f020 c8d0 f7ce  ........... ....

  ```

  The "2061" that we see, is part of the BASIC "SYS 2061" command that usually appears in all C64 programs. So, let's disassemble the first 12 instructions from 2061. ( _pd_ = print disassemble):

  ```
  [0x000007ff]> pd 12 @ 2061
              0x0000080d    78             sei
              0x0000080e    ad0ddc         lda 0xdc0d
              0x00000811    a212           ldx #0x12
              0x00000813    a000           ldy #0x00
         ┌┌─> 0x00000815    b9d41a         lda 0x1ad4,y
         ││   0x00000818    99f020         sta 0x20f0,y
         ││   0x0000081b    c8             iny
         └──< 0x0000081c    d0f7           bne 0xf7
          │   0x0000081e    ce1708         dec 0x0817
          │   0x00000821    ce1a08         dec 0x081a
          │   0x00000824    ca             dex
          └─< 0x00000825    d0ee           bne 0xee
  ```

  In case we don't know the meaning of a certain opcode, we can print its description with _?d_:

  ```
  [0x00000815]> ?d sei
  set interrupt disable status
  ```

  Or if we want to print the description in every disassembled line, we can do:

  ```
  e asm.describe=true
  ```

  And then disassemble again:

  ```
  [0x0000080e]> pd 12 @2061
      0x080d  78        sei           ; set interrupt disable status
      0x080e  ad0ddc    lda 0xdc0d    ; load accumulator with memory
      0x0811  a212      ldx #0x12     ; load index x with memory
      0x0813  a000      ldy #0x00     ; load index y with memory
  ┌─> 0x0815  b9d41a    lda 0x1ad4,y  ; load accumulator with memory
  │   0x0818  99f020    sta 0x20f0,y  ; store accumulator in memory
  │   0x081b  c8        iny           ; increment index y by one
  └─< 0x081c  d0f7      bne 0xf7      ; branch on result not zero
      0x081e  ce1708    dec 0x0817    ; decrement memory by one
      0x0821  ce1a08    dec 0x081a    ; decrement memory by one
      0x0824  ca        dex           ; decrement index x by one
      0x0825  d0ee      bne 0xee      ; branch on result not zero

  ```

  For more disassembling options just type `p?`
tag:
  - c64
  - disassembler
  - radare
title: Disassembling 6502 code with Radare - Part I
url: /2015/11/18/disassembling-6502-code-with-radare-part-i/

---
[Radare](http://radare.org/) is an open source portable reversing framework that can do many things, among those things it can disassemble 6502 code.

### Download and install radare

- First, download [radare from github](https://github.com/radare/radare2). You need a recent version in order to disassemble 6502 code.
- And then install it by running _sys/install.sh_ (or _sys/user.sh_ for local installation):

```
$ git clone https://github.com/radare/radare2.git
$ cd radare2
$ ./sys/install.sh

```

### Loading a c64 .prg

Radare has many command line options. But in order to load 6502 programs we need just two:

- _-a6502_ to specify the 6502 architecture.
- _-mMemoryAddress_ to map the file to a certain memory address. Use 2047 for "normal" programs. Usually they start at $0801 (2049), but we have to subtract 2 from the .prg header.

Example:

```
$ r2 -a6502 -m2047 mygame.prg
```

### Disassembling

Radare doesn't have a GUI, like IDA. Instead is has a powerful command line interface (think of GDB). Example:

```
$ r2 -a6502 -m2047 musicplayer.prg
[0x000007ff]>

```

And _0x7ff_ (2047) is the seek address, meaning that all commands will use that address as the base address. Let's print the first 32 bytes. ( _px_ = print hexa):

```
[0x000007ff]> px 32
offset   0 1  2 3  4 5  6 7  8 9  A B  C D  E F  0123456789ABCDEF
0x07ff  0108 0b08 3905 9e32 3036 3100 0000 78ad  ....9..2061...x.
0x080f  0ddc a212 a000 b9d4 1a99 f020 c8d0 f7ce  ........... ....

```

The "2061" that we see, is part of the BASIC "SYS 2061" command that usually appears in all C64 programs. So, let's disassemble the first 12 instructions from 2061. ( _pd_ = print disassemble):

```
[0x000007ff]> pd 12 @ 2061
            0x0000080d    78             sei
            0x0000080e    ad0ddc         lda 0xdc0d
            0x00000811    a212           ldx #0x12
            0x00000813    a000           ldy #0x00
       ┌┌─> 0x00000815    b9d41a         lda 0x1ad4,y
       ││   0x00000818    99f020         sta 0x20f0,y
       ││   0x0000081b    c8             iny
       └──< 0x0000081c    d0f7           bne 0xf7
        │   0x0000081e    ce1708         dec 0x0817
        │   0x00000821    ce1a08         dec 0x081a
        │   0x00000824    ca             dex
        └─< 0x00000825    d0ee           bne 0xee
```

In case we don't know the meaning of a certain opcode, we can print its description with _?d_:

```
[0x00000815]> ?d sei
set interrupt disable status
```

Or if we want to print the description in every disassembled line, we can do:

```
e asm.describe=true
```

And then disassemble again:

```
[0x0000080e]> pd 12 @2061
    0x080d  78        sei           ; set interrupt disable status
    0x080e  ad0ddc    lda 0xdc0d    ; load accumulator with memory
    0x0811  a212      ldx #0x12     ; load index x with memory
    0x0813  a000      ldy #0x00     ; load index y with memory
┌─> 0x0815  b9d41a    lda 0x1ad4,y  ; load accumulator with memory
│   0x0818  99f020    sta 0x20f0,y  ; store accumulator in memory
│   0x081b  c8        iny           ; increment index y by one
└─< 0x081c  d0f7      bne 0xf7      ; branch on result not zero
    0x081e  ce1708    dec 0x0817    ; decrement memory by one
    0x0821  ce1a08    dec 0x081a    ; decrement memory by one
    0x0824  ca        dex           ; decrement index x by one
    0x0825  d0ee      bne 0xee      ; branch on result not zero

```

For more disassembling options just type `p?`

### Searching

In order to search for something, like in Vi, we have to use the _/_ command. Examples:

Search for asm opcodes: _/c opcode_. The following will search for `sta $d020`, `sta $d021`, `sta $d022`, etc...

```
[0x0000080e]> /c sta 0xd02
0x00000829   # 3: sta 0xd020
0x0000082c   # 3: sta 0xd021
```

Search for strings (although this is not very useful since most probably the strings are stored in screen codes and not in PETSCII):

```
[0x0000080e]> / hello
```

Search for a sequence of hexadecimal bytes: _/x_. The following searches for the MSB of the music frequency table:

```
[0x0000080e]> /x 010101010102
Searching 6 bytes...
# 7 [0x80d-0x13d4]
hits: 1
0x0000098b hit0_0 010101010102
```

We can use the flag hit0\_0 to refer to that address. For example, in order to dump the  first 32 bytes from `hit0_0` we can do:

```
[0x080d]> px 32 @ hit0_0
offset   0 1  2 3  4 5  6 7  8 9  A B  C D  E F  0123456789ABCDEF
0x098c  0101 0101 0202 0202 0202 0203 0303 0303  ................
0x099c  0404 0404 0505 0506 0607 0707 0808 0909  ................
```

For more search options just type `/?`

### Visual Mode

Besides the Command Line Interface, Radare has another interface called the Visual Mode. It is similar to Vi, where each key has an associated function. In this mode, instead of entering commands, you just press one or two keys without pressing Enter.

In fact, some keys have the same Vi functionality:

- _hjkl_: move around
- _gG_: go top/bottom of page
- _:_ : Enter a command

Visual mode has 8 different view modes that can be activated by pressing _p_

- hex, the hexadecimal view
- disasm, the disassembly listing
- debug, the debugger
- words, the word-hexidecimal view
- buf, the C-formatted buffer
- annotated, the annotated op analysis color map
- annotated, the annotated hexdump

[![](https://asciinema.org/a/b5knu481rrx4nlw4lceddzo3r.png)](https://asciinema.org/a/b5knu481rrx4nlw4lceddzo3r?autoplay=1&t=1)

### Adding Comments

While analyzing code, sometimes it is useful to add comments. While in Visual Mode, we can add comments by pressing  _;_ plus the comment.

Example:
[![](https://asciinema.org/a/30374.png)](https://asciinema.org/a/30374?autoplay=1&t=2)

### Saving

After adding some comments, we should save the project in order not to loose the changes. To save a project just enter _Ps projectName_ (Project save), and to open an existing project enter _Po projectName_ (Project open). And enter _Pl_ to list existing projects.
Example:

```
[0x0000080d]> Ps myproject
myproject
[0x0000080d]> Pl
myproject
[0x0000080d]> Po myproject
Reloading project

```

And from the command line, we can open existing projects with the _-p_ argument. Example:

```
$ r2 -p myproject
```

### Getting help

Just append _?_ to each command to get more help about that command. Example:

- ?  :to list all the possible commands
- P?  :to get help about the Project (P) command
- p? :to get help about the Print (p) command
- p8?  :to get help about the Print 8bit hexpair command
- and so on.

When in Visual Mode, also press ? to get help.

### Other resources

- [Radare book](https://radare.gitbooks.io/radare2book/content/)
- IRC: [irc.freenode.net](http://irc.freenode.net) #radare
- Twitter: [@radareorg](https://twitter.com/radareorg)
