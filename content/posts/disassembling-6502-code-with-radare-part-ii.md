---
author: ricardoquesada
category: retro computing
date: "2015-12-10T02:54:47+00:00"
guid: http://retro.moe/?p=1187
summary: "Let's crack a simple game. If you are not familiar with Radare, read [Part I](http://retro.moe/2015/11/18/disassembling-6502-code-with-radare-part-i/) first.\n\n### Creating and opening a VICE Snapshot file\n\nLet's crack BC's Quest For Tires since its copy-protection is easy to bypass.\n\n- Unzip this file: [http://tapes.c64.no/tapes/BCsQuestForTires.zip](http://tapes.c64.no/tapes/BCsQuestForTires.zip)\n- Open the tap file with [VICE](http://vice-emu.sourceforge.net/) (the most popular Commodore 64 emulator), and..\n\n \n\n- ...the game has some kind of copy-protection. If we enter invalid codes, we won't be able to play the game.\n\nSince Radare supports VICE Snapshot File format, we can save an snapshot of the game, and analyze it with Radare.\n\n- In VICE, go to the menu, Snapshot -> Save Snapshot Image...\n  - If we select \"Save ROMs\", then the BASIC ROM and the KERNAL ROM will be saved inside the Snapshot file, and will be included as Radare sections.\n\n[![save_snapshot_dialog](https://retro.moe/wp-content/uploads/2015/12/save_snapshot_dialog.png?w=700)](https://retro.moe/wp-content/uploads/2015/12/save_snapshot_dialog.png)\n\n\n\nRadare VICE Snapshot File (VSF) support lets us inspect:\n\n- The 64k RAM of the computer at the moment the snapshot was saved\n- The BASIC and KERNAL ROMs in case they were saved.\n\nTo open a VSF file, just pass the VSF file as the first argument:\n\n```\n$ r2 bc_copy_protection_screen.vsf\n[0x00005689]>\n```\n\n `0x00005689` is the PC (program counter) at the moment the snapshot was saved."
tag:
  - c64
  - disassembler
  - radare
  - vice
title: Disassembling 6502 code with Radare - Part II
url: /2015/12/09/disassembling-6502-core-with-radare-part-ii/

---
Let's crack a simple game. If you are not familiar with Radare, read [Part I](/2015/11/18/disassembling-6502-code-with-radare-part-i/) first.

### Creating and opening a VICE Snapshot file

Let's crack BC's Quest For Tires since its copy-protection is easy to bypass.

- Unzip this file: [http://tapes.c64.no/tapes/BCsQuestForTires.zip](http://tapes.c64.no/tapes/BCsQuestForTires.zip)
- Open the tap file with [VICE](http://vice-emu.sourceforge.net/) (the most popular Commodore 64 emulator), and..

{{< figure align=alignnone width=308 src="/wp-content/uploads/2015/12/screen-shot-2015-12-09-at-3-03-39-pm.png?w=700" alt="" >}}

- ...the game has some kind of copy-protection. If we enter invalid codes, we won't be able to play the game.

Since Radare supports VICE Snapshot File format, we can save an snapshot of the game, and analyze it with Radare.

- In VICE, go to the menu, Snapshot -> Save Snapshot Image...
  - If we select "Save ROMs", then the BASIC ROM and the KERNAL ROM will be saved inside the Snapshot file, and will be included as Radare sections.

[![save_snapshot_dialog](/wp-content/uploads/2015/12/save_snapshot_dialog.png?w=700)](/wp-content/uploads/2015/12/save_snapshot_dialog.png)

Radare VICE Snapshot File (VSF) support lets us inspect:

- The 64k RAM of the computer at the moment the snapshot was saved
- The BASIC and KERNAL ROMs in case they were saved.

To open a VSF file, just pass the VSF file as the first argument:

```
$ r2 bc_copy_protection_screen.vsf
[0x00005689]>
```

 `0x00005689` is the PC (program counter) at the moment the snapshot was saved.

### Radare Sections

With the command `S` we can inspect the `S` ections of the VSF file.

```
[0x00005689]> S
[00] . 0x0001209d mr-x va=0xa000 sz=0x2000 vsz=0x2000 BASIC
[01] . 0x0001009d mr-x va=0xe000 sz=0x2000 vsz=0x2000 KERNAL
[02] * 0x00000084 mrwx va=0x0000 sz=0x10000 vsz=0x10000 RAM
```

With `S=`, we see the sections in a more visual way.

[![Radare S= command](/wp-content/uploads/2015/12/screen-shot-2015-12-09-at-3-41-46-pm.png?w=700)](/wp-content/uploads/2015/12/screen-shot-2015-12-09-at-3-41-46-pm.png)

As we can see:

- BASIC starts at `0xa000` and it takes 8k
- KERNAL starts at `0xe000` and it takes 8k
- RAM starts at `0x0000`, and takes 64k

Let's disassemble the KERNAL reset routine, the one at 64738:

```
[0x0000fce2]> s 64738
[0x0000fce2]> pd 14
            0xfce2      a2ff           ldx #0xff
            0xfce4      78             sei
            0xfce5      9a             txs
            0xfce6      d8             cld
            0xfce7      2002fd         jsr 0xfd02
        ┌─< 0xfcea      d003           bne 0x03
        │   0xfcec      6c0080         jmp (0x8000)
        └─> 0xfcef      8e16d0         stx sym.VIC_CTRL2
            0xfcf2      20a3fd         jsr 0xfda3
            0xfcf5      2050fd         jsr 0xfd50
            0xfcf8      2015fd         jsr 0xfd15
            0xfcfb      205bff         jsr 0xff5b
            0xfcfe      58             cli
            0xfcff      6c00a0         jmp (0xa000)
```

Actually we are not interested in disassembling the KERNAL at this moment, but we should know it is possible to do it. In case we want to disassemble the memory RAM that is beneath the KERNAL and/or BASIC we should remove the KERNAL and/or BASIC sections. We can add them again if needed.
Use the `S-` command to remove Sections:

```
0x0000fce2]> S
[00] . 0x0001209d mr-x va=0xa000 sz=0x2000 vsz=0x2000 BASIC
[01] * 0x0001009d mr-x va=0xe000 sz=0x2000 vsz=0x2000 KERNAL
[02] . 0x00000084 mrwx va=0x0000 sz=0x10000 vsz=0x10000 RAM
[0x0000fce2]> S-0
[0x0000fce2]> S-0
[0x0000fce2]> S
[00] * 0x0001009d mr-x va=0xe000 sz=0x2000 vsz=0x2000 KERNAL

```

And taking a look again at 64738 we find "nothing", just "empty" RAM, which was expected:

```
[0x0000fce2]> pd 14
 0x0000fce2 ffffff isb 0xffff,x
 0x0000fce5 ffffff isb 0xffff,x
 0x0000fce8 ffffff isb 0xffff,x
 0x0000fceb ffffff isb 0xffff,x
 0x0000fcee ffffff isb 0xffff,x
 0x0000fcf1 ffffff isb 0xffff,x
 0x0000fcf4 ffffff isb 0xffff,x
 0x0000fcf7 ffffff isb 0xffff,x
 0x0000fcfa ffffff isb 0xffff,x
 0x0000fcfd ffffff isb 0xffff,x
```

Remember that by appending `?` to any command, we can get help. In this case, `S?` will display the help for the `S` command.

### Symbols in Radare

By doing a quick analysis of the snapshot, we can safely assume that the boot routine starts at `0x5500`. So, let's disassemble that address, and let's see what we find:

{{< figure align=alignnone width=375 src="/wp-content/uploads/2015/12/radare%5Fsymbols.png?w=700" alt="" >}}

Radare will automatically import all the well-known symbols for the SID, VIC and CIA addresses. The symbols are imported in the symbols "flag space". In order to display all the imported symbols, we should do:

```
[0x00005689]> fs
0 0 . strings
1 101 . symbols
2 6 . sections
[0x00005689]> fs symbols
[0x00005689]> f
0x00005689 1 entry0
0x0000d000 2 sym.VIC_SPR0_X
0x0000d001 2 sym.VIC_SPR0_Y
0x0000d002 2 sym.VIC_SPR1_X
0x0000d003 2 sym.VIC_SPR1_Y
0x0000d004 2 sym.VIC_SPR2_X
0x0000d005 2 sym.VIC_SPR2_Y
...
```

- `fs`: displays all the available "flag spaces"
- `fs name`: switches to the selected "flag space"
- `f`: displays all the "flags" available in the selected "space"

We can also grep for certain symbols. Let's say that we want to know what are the CIA symbols.

```
[0x00005689]> f~CIA
0x0000dc00 2 sym.CIA1_PRA
0x0000dc01 2 sym.CIA1_PRB
0x0000dc02 2 sym.CIA1_DDRA
0x0000dc03 2 sym.CIA1_DDRB
0x0000dc08 2 sym.CIA1_TOD10
0x0000dc09 2 sym.CIA1_TODSEC
0x0000dc0a 2 sym.CIA1_TODMIN
0x0000dc0b 2 sym.CIA1_TODHR
...
```

Almost every command in Radare supports the `~` suffix which basically sends the output to grep (like pipes in Unix).

If we prefer raw addresses, we can just remove all the imported symbols by doing:

```
[0x00005689]> f-sym.*
```

And just remember that by appending `?`, we can see the help for the `f` command, in this case: `f?`.

### Radare Variables

So, after analyzing the boot code for a while we will realize that the `0x6000` looks suspicious, and it could be the address that we are looking for.  So, let's figure out is who calling `0x6000`.

As we have seen in [Part I](/2015/11/18/disassembling-6502-code-with-radare-part-i/), we can use `/c` or `/x`:

```
[0x00005500]> /c jmp 0x6000
0x000056ea # 3: jmp 0x6000

[0x00005500]> /x 4c0060
Searching 3 bytes...
# 7 [0x5500-0x10000]
hits: 1
0x000056ea hit1_0 4c0060
```

One thing that we didn't know is that we can tell Radare to automatically perform a command for all the "hits" found by editing the `cmd.hit` variable. For example, in order to disassemble the first 5 instructions automatically after each "hit", we should do:

```
[0x00005500]> e cmd.hit = pd 5
[0x00005500]> /x 4c0060
Searching 3 bytes...
# 7 [0x5500-0x10000]
hits: 1
0x000056ea hit3_0 4c0060
            ;-- hit3_0:
        ┌─< 0x000056ea      4c0060         jmp 0x6000
        │   0x000056ed      20f856         jsr 0x56f8
        │   0x000056f0      c8             iny
        │   0x000056f1      20f856         jsr 0x56f8
        │   0x000056f4      c8             iny
```

Radare has many built-in variables that can be changed with the `e` command. To display all the available variables, just type `e`. You can grep certain variables by using the `~` suffix.

```
[0x00005500]> e
anal.a2f = false
anal.afterjmp = false
anal.arch = 6502
anal.bbsplit = true
...
[0x00005500]> e~search
anal.searchstringrefs = false
search.align = 0
search.chunk = 0
search.contiguous = true
search.count = 0
search.distance = 0
search.esilcombo = 8
search.flags = true
...
```

Some variables support the `?` argument. For example:

```
[0x00005500]> e search.in=?
raw
block
file
io.maps
io.maprange
io.section
io.sections
io.sections.write
io.sections.exec
dbg.stack
dbg.heap
dbg.map
dbg.maps
dbg.maps.exec
dbg.maps.write
anal.fcn
anal.bb
```

The default option for `search.in` is `file`, which works Ok for us. But in some advance cases we might want to switch to either `io.sections` or `io.section`. More on this in future posts.

### Cross references

Actually the easiest way to find who is calling a certain function is to use cross references (xrefs). Just tell Radare to analyze the binary with `aa`:

```
[0x00005500]> aa
```

And then disassemble `0x6000` in Visual mode. While in Visual mode we can use the following shortcuts to navigate the xrefs:

- `x`: To open the "Goto xrefs" menu. It will appear at the top-left corner. Only available when we see a XREF legend above a function.
- Use `0-9` to jump to the displayed xrefs.

Let's see how to do it:

[![](https://asciinema.org/a/31539.png)](https://asciinema.org/a/31539?t=5)

### Modifying the game

First of all, in order to be able to modify and save a VSF file, we should start Radare with the `-w` argument. Example:

```
$ r2 -w bc_copy_protection_screen.vsf
```

Now, let's patch the game. After following the xrefs, we found that this is the code that jumps to `0x6000`:

```
│       │   0x56c8      c502           cmp 0x02
│      ┌──< 0x56ca      d003           bne 0x03
│     ┌───< 0x56cc      4cea56         jmp 0x56ea
│     │└──> 0x56cf      ad4f57         lda 0x574f

```

One quick way to cheat the copy-protection is by replacing the `bne 0x03` with two `nop` s.

The way to do it is by:

1. Enter in Cursor mode (by pressing `c`)
1. Position the cursor in the `d003` values (from `bne 0x03`)
1. Once the cursor is there, enter into Insert mode (by pressing `i`)
1. Then type `eaea` (two `nop` s) and then `enter`
1. Then `q` to quit

Example:
[![](https://asciinema.org/a/31541.png)](https://asciinema.org/a/31541)

### Reloading the VSF file in VICE

So, we have just patched the VSF file. If you load it from VICE, the game will be patched and we will be able to play the game, even if we enter invalid color codes.

Just open VICE -> Menu -> Snapshots -> Load Snapshot Image...

And when the game asks you to enter the color codes, just enter any code, and you should see the game screen:

[![Screen Shot 2015-12-09 at 6.26.18 PM](/wp-content/uploads/2015/12/screen-shot-2015-12-09-at-6-26-18-pm.png?w=700)](/wp-content/uploads/2015/12/screen-shot-2015-12-09-at-6-26-18-pm.png)

### Additional notes

- Radare also supports Commodore 128 VSF. If saved with ROMs, it will include the following sections:

```
[00] * 0x420a1 mr-x va=0x4000 sz=0x7000 vsz=0x7000 BASIC
[01] . 0x490a1 mr-x va=0xb000 sz=0x1000 vsz=0x1000 MONITOR
[02] . 0x4a0a1 mr-x va=0xc000 sz=0x1000 vsz=0x1000 EDITOR
[03] . 0x400a1 mr-x va=0xe000 sz=0x2000 vsz=0x2000 KERNAL
[04] . 0x0008c mrwx va=0x0000 sz=0x10000 vsz=0x10000 RAM_BANK_0
[05] . 0x1008c mrwx va=0x0000 sz=0x10000 vsz=0x10000 RAM_BANK_1
```

- In order to save VSF files for C128, use a recent [VICE version from SVN](http://sourceforge.net/p/vice-emu/code/HEAD/tree/).
- Radare VSF support was added a few days ago, so in order to use it, download [Radare from Github](https://github.com/radare/radare2)
- VSF files are not meant to be "distributable" files. If you want to release a "crack" you should create .D64 or .PRG files. It is possible to create them from VSF files. More on this on future posts.

### Other resources

- [Radare book](https://radare.gitbooks.io/radare2book/content/)
- IRC: [irc.freenode.net](http://irc.freenode.net/) #radare
- Twitter: [@radareorg](https://twitter.com/radareorg)
- [Disassembling 6502 code with Radare - Part I](/2015/11/18/disassembling-6502-code-with-radare-part-i/)
