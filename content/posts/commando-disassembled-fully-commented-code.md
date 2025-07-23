---
author: ricardoquesada
category: retro computing
date: "2019-10-02T15:51:34+00:00"
guid: http://retro.moe/?p=2224
tag:
  - c64
  - commando
  - mos6526
title: Commando disassembled - fully commented code
url: /2019/10/02/commando-disassembled-fully-commented-code/

---
{{< figure align=alignnone width=384 src="https://user-content.gitlab-static.net/a81ba2eb9033ba9e3fc62303fbc37f5563420774/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f6438776f6e45766a326d6355326b7032677374456d5a4e465655675a386d4756784e694254694850584c694543327463732d616176546d73796f556e776d386f4642617172376751724853756876466c32316758424d4456374d55516d56374668376c65664d4d5a5664643146734471474c3557785a347047703350764b4d6b2d70747954313233476c6f3d2d6e6f" alt="" >}}

In order to create [Commando 2084](/2019/09/29/commando-2084-a-game-for-the-commodore-64/), I had to disassemble Commando. My original intention was to patch what was only needed and stop there. But I got carried away and I ended up analyzing and commenting the entire Commando code.

The commented code (that can be recompiled to generate the exact original binary) is here:

- [https://gitlab.com/ricardoquesada/c64-commando-2084/tree/orig](https://gitlab.com/ricardoquesada/c64-commando-2084/tree/orig)

### Findings - Level 2

Apparently, the original idea was to ship Commando with 4 levels instead of 3. There is a lot of code/data that indicates that a "level 2" (the levels that are shipped with Commando are level 0, 1 and 3) was in progress, or even finished.

All the actions, charset-mask, trigger rows are present. What's missing is the map and a partial charset. The charset used for the main screen is likely the one designed for level 2.

Speculation from my part, "Level 2" was probably removed due to lack of time (?) or due lack of RAM to create a single-load game (?).

For more info about this level, search for "LVL2" in the [`main.asm`](https://gitlab.com/ricardoquesada/c64-commando-2084/blob/orig/src%2Fmain.asm).

### Map and actions

- Each level consist of 40x200 map.
- Each level consists of:
  - Charset unique for the level: LVL0 at `$C000`, LVL1 at `$C800`, LVL3 at `$D800`
  - Each char in the charset contains a mask that indicates the background priority. See `LVL0_CHARSET_MASK_TBL` in [main.asm](https://gitlab.com/ricardoquesada/c64-commando-2084/blob/orig/src%2Fmain.asm).
  - A map: LVL0 is at `$6000`, LVL1 at `$8000`, LVL3 at `$A000`
  - List of actions: each action represents a sprite that must be created. But an action can perform non-related sprite tasks as well, like opening a door. See `LVL0_ACTION_TBL` in [main.asm](https://gitlab.com/ricardoquesada/c64-commando-2084/blob/orig/src%2Fmain.asm).
  - List of rows: when the master row index (see `V_SCROLL_ROW_IDX`) matches this number, the associated action is executed. See `LVL0_TRIGGER_ROW_TBL` in [main.asm](https://gitlab.com/ricardoquesada/c64-commando-2084/blob/orig/src%2Fmain.asm).
  - Actions can receive an optional "sprite X position" argument. See `LVL0_SPRITE_X_LO_TBL` and `LVL0_SPRITE_X_HI_TBL` in [main.asm](https://gitlab.com/ricardoquesada/c64-commando-2084/blob/orig/src%2Fmain.asm)

### Sprites

The game supports up to 16 virtual sprites.

- Sprite 0 is used for the hero
- Sprites 1-3 are used for hero's bullets
- Sprite 4 is used for hero grenades
- Sprites 5-15 are used for enemies, including its bullets/grenades.

Each sprite has:

- X and Y coordinates (including X LSB and X MSB)
- Sprite frame (which sprite to render). `$FF` is an empty frame.
- Sprite color
- Background priority (e.g: should it be rendered behind a tree?)
- Animation type (see below). If it is `0`, it means it is an empty sprite.
- Extra variables that are used for different things. Varies from anim type to anim type.

Some enemies, like the motorcycle, take two sprites.

### Animation type

An animation represents what the sprite should do during the game. For example, the animation type `TYPE_ANIM_SOLDIER_BULLET`, animates the bullet. See `TYPE_ANIM_TBL` in [main.asm](https://gitlab.com/ricardoquesada/c64-commando-2084/blob/orig/src%2Fmain.asm) for the complete list of animation types.

An sprite can change its animation in runtime. For example, the `TYPE_ANIM_SOLIDER_BEHIND_SMTH` has certain logic. But when the hero is at the same Y position as it is, then it changes its animation to `TYPE_ANIM_SOLDIER`. Similar, the `TYPE_ANIM_SOLDIER_JUMPING` animates the "jumping" solider. But when the solider lands, it changes its animation to `TYPE_ANIM_SOLDIER`. Those are only two examples, but most animations change its animation type in runtime.

### Animation type 0

When a sprite goes out of bounds, or an enemy dies, or an animation ends, that sprite is set with animation type `0`, which is the `TYPE_ANIM_SPAWN_SOLIDER`.

What this animation does, is to create random enemies. And when an enemy is created, it changes in animation type to something different than 0.

That means, that when there map is "full" of enemies (all animation types are different than `0`), the `TYPE_ANIM_SPAWN_SOLDIER` is not called. And when there many empty sprites, it gets called more often.

### Collision detection

Collision detection is done in software (no hardware collision detection is used).

There is a routine to check whether the hero is hit (see `CHECK_COLLISION`) and another for enemies (see `TYPE_ANIM_HERO_BULLET`, `TYPE_ANIM_HERO_GRENADE_END`).

Each animation type has contains a mask (see `f2544`) that indicates whether it can collide with bullet, grenades, both or nothing. For example, when the soldier is in the trench, it can only be killed with a grenade.

### Personal thoughts

From a high-level (architecture) point of view, the code is very well designed. It is pretty easy to add new types of actions, or create new levels, or modify existing ones with little change in the code/data.

From lower-level point of view, it seems that parts of the code could be improved (see `FIXME` in [main.asm](https://gitlab.com/ricardoquesada/c64-commando-2084/blob/orig/src%2Fmain.asm)), specially regarding performance and flickers. Seeing many Level-2 traces, plus seeing certain bugs makes me think that the development team was under pressure to release the game ASAP (something fairly common in the gaming industry).

Additionally, it seems that the assembler used didn't optimize the code to use zero page. For example, calls to:

```
    STY $FB,Y
```

are assembled to:

```
   STY $00FB,Y      ;3 byte variation, instead of the two-one.
```
