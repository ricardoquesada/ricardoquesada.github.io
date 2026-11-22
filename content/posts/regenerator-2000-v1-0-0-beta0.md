---
author: ricardoquesada
category: retro-computing
tag:
  - c64
  - assembly
  - 6502
  - regenerator2000
  - disassembler
date: "2026-11-22T11:00:00-08:00"
title: "Regenerator 2000 v1.0.0-beta0"
url: /regenerator-2000-v1-0-0-beta0/
---

![Regenerator 2000 Logo](/images/regenerator2000_logo.png)

Regenerator 2000 `v1.0.0-beta0` is out!
A lot changed since I [announced v0.5.0](/announcing-regenerator-2000/) in January 2026.
Here is a quick look at what is new.

## Live VICE Debugger

Connect to [VICE](https://vice-emu.sourceforge.io/) from the `Debugger` menu, or pass `--vice <HOST:PORT>` when you start it.

- **Debug Live**: Set breakpoints and watchpoints, step through code, or run to cursor while watching the live program counter.
- **CPU & Memory**: Watch CPU registers, the stack, 6502 vectors, and a live memory dump right in the side pane.
- **Chip Registers**: See C64/C128 (6510/8502, VIC-II, CIA 1/2), VIC-20 (VIC-I), and Plus/4 (TED) registers with changed values highlighted.

![VICE Debugger View](/images/regenerator2000_v1_debugger.png)

## Built-in Binary Unpacker

Open a packed Commodore program and Regenerator 2000 spots it via packer signatures or high entropy, then unpacks it straight into the disassembler.

- **26 Packer Families**: Handles Exomizer, ByteBoozer, Dali, TinyCrunch, TSCrunch, ZX02, and many other classic crunchers.
- **Manual Tweaks**: Override the entry point, return address, depacker address, or step limit if auto-detection misses.

## AI-Assisted Disassembly (MCP Server)

Regenerator 2000 now ships with an MCP server so AI tools like Claude Code and Antigravity can work on a project with you.

- **29 MCP Tools**: AI assistants can read disassembly, search memory, label symbols, add comments, classify blocks, unpack files, and move the cursor.
- **Safe & Ready to Go**: Every AI edit goes into the undo history. Bundled skills and [regenerator2000-template](https://github.com/ricardoquesada/regenerator2000-template) let you run automated analysis right away.

## Disassembly, Scopes, and Enums

- **Scopes**: Group routines and local labels into named scopes for `64tass`, `ca65`, and `KickAssembler`.
- **Enums**: Replace raw numbers with readable names, including built-in color and PETSCII enums.
- **Symbolic Offsets & Typed X-Refs**: Write offsets like `label+$01` and see reference tags (`[R]`, `[W]`, `[R/W]`, `[C]`, `[J]`, `[O]`).
- **More Data Types & Comments**: Support Lo/Hi and Hi/Lo word tables, byte fills (`.fill`, `!fill`, `.res`), external labels, and multi-line comments.
- **Smarter Analysis**: Trace code from any address, detect BASIC `SYS` entry points, and export undocumented opcodes.

![Blocks View with Scopes and Minimap](/images/regenerator2000_v1_blocks.png)

## Formats, Systems, and Export

- **Disk, Tape & Cartridge Files**: Browse and open entries straight from `D64` (35–42 tracks), `D71`, `D81`, `T64`, and multi-bank `CRT` files.
- **Projects & Labels**: Open `6502bench` (`.dis65`) projects, import or export VICE `.lbl` files, and pick import settings in the new Import Context dialog.
- **HTML Export & CLI**: Export standalone HTML disassemblies with clickable links and light/dark themes. Run headless batch exports or `--verify` roundtrip checks.
- **More Systems**: Includes 7 Commodore machines (C64, C128, VIC-20, Plus/4, PET 2.0, PET 4.0, 1541), 6 experimental 6502 systems, and custom TOML overrides.

## Terminal UI, Graphics, and Themes

- **Sharp Pixel Graphics**: Show high-resolution bitmaps and the About screen with Kitty, iTerm2, or Sixel graphics (with half-block fallback).
- **Minimap & Side Panes**: Jump anywhere with the clickable top minimap. Use color-coded 8/16-column Hex Dump, 2-column Sprites, and 4-column Charsets with direct block editing.
- **9 Built-in Themes**: Pick from Dracula (now default), Solarized, Gruvbox, Monokai, Nord, and Catppuccin, or build your own TOML theme.
- **Better Navigation**: Enjoy mouse support, Bookmarks, Go to Symbol, Open Recent, unexplored-block jumps, multi-target operand jumps, and regex search.

### High-Resolution Bitmap View

![High-Resolution Bitmap View](/images/regenerator2000_v1_bitmap.png)

### Color-Coded Hex Dump View

![Color-Coded Hex Dump View](/images/regenerator2000_v1_hexdump.png)

### Catppuccin Latte Theme

![Catppuccin Latte Theme](/images/regenerator2000_v1_theme_catppuccin_latte.png)

## Docs and Live Examples

The docs moved to [retro.moe/regenerator2000](https://retro.moe/regenerator2000/) with a guided tutorial and keyboard reference.
You can also browse seven live HTML disassemblies right in your browser.
They cover Frogger, Moving Tubes, Burnin' Rubber, H.E.R.O. Is Back!, Lode Runner, Omega Race, and Kikstart.

## Download and Install

Grab `v1.0.0-beta0` from Crates.io, or download pre-built binaries for Linux (x86_64 and ARM64), macOS (signed and notarized), and Windows.

```bash
cargo install regenerator2000 --version 1.0.0-beta0
```

- Release & Binaries: [GitHub Release v1.0.0-beta0](https://github.com/ricardoquesada/regenerator2000/releases/tag/v1.0.0-beta0)
- Source Code: [github.com/ricardoquesada/regenerator2000](https://github.com/ricardoquesada/regenerator2000)
- Documentation: [retro.moe/regenerator2000](https://retro.moe/regenerator2000/)
- Live Examples: [retro.moe/regenerator2000/examples](https://retro.moe/regenerator2000/examples/)
- Crates.io: [crates.io/crates/regenerator2000](https://crates.io/crates/regenerator2000)
- Discord: `#regenerator2000` on [Discord](https://discord.gg/r5aMn6Cw5q)

Happy hacking!
