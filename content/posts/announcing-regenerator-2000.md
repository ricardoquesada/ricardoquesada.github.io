---
author: ricardoquesada
category: retro-computing
tag:
  - c64
  - assembly
  - 6502
  - regenerator2000
  - disassembler
date: "2026-01-24T14:45:00-08:00"
title: "Announcing Regenerator 2000"
url: /announcing-regenerator-2000/
---

I am excited to announce the release of **Regenerator 2000**, a modern take on the classic [Regenerator tool][regenerator] for the Commodore 64 and other 6502-based computers.

![Regenerator 2000 Logo](/images/regenerator2000_logo.png)

**Regenerator 2000** is an interactive disassembler for the CPU 6502, focused mostly on Commodore 8-bit computers. It features a modern Terminal User Interface (TUI) with features like x-ref, undo/redo, arrows, keyboard-driven navigation, and more! Better yet, it is multiplatform and runs natively on **Windows**, **macOS**, and **Linux**.

## Main Features

- **Full 6502 Support**: Includes all standard and undocumented opcodes.
- **Side-by-Side Views**: Visualize your data while disassembling with integrated views for:
  - **Hex Dump**
  - **Sprites** (Single Color and Multicolor)
  - **Bitmaps** (Hi-Res and Multicolor)
  - **Character Sets** (Single and Multicolor)
- **Project Management**: Define "Blocks" to mark regions as Code or Data; save and load progress via `.regen2000proj` files.
- **Comprehensive Import**: Supports `.prg`, `.crt` (Commonly used in C64), `.t64`, `.vsf` (Vice Snapshot), `.bin`, and `.raw` formats.
- **Flexible Export**: Export your work to popular assemblers including `64tass`, `ACME`, `Kick Assembler`, and `ca65`.
- **Interactive TUI**: A modern, keyboard-driven Terminal User Interface with:
  - Cross-references (X-Ref) and Jump to label features.
  - Full Undo/Redo support.
  - Visual Mode (Vim-inspired) for selecting ranges.

## Screenshots

### Hex Dump View

![Hex Dump](/images/regenerator2000_hexdump.png)

### Character Set View

![Character Set](/images/regenerator2000_charset.png)

### Sprites View

![Sprites](/images/regenerator2000_sprites.png)

### Bitmap View

![Bitmap](/images/regenerator2000_bitmap.png)

## Download and Links

You can find more information, download the latest release (v0.5.0), and contribute to the project on the official GitHub page:

**[https://github.com/ricardoquesada/regenerator2000](https://github.com/ricardoquesada/regenerator2000)**

Happy hacking!

[regenerator]: https://csdb.dk/release/?id=247992
