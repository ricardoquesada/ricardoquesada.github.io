---
author: ricardoquesada
category: cocos2d
date: "2014-06-03T17:59:57+00:00"
guid: http://towp8.com/?p=270
tag:
  - metal
  - scenekit
  - spritekit
  - swift
  - wwdc2014
title: WWDC 2014 announcements as a game developer
url: /2014/06/03/wwdc-2014-announcements-and-the-game-developers/

---
At WWDC 2014, Apple announced new features for iOS and OS X. These are my thoughts:

## **Swift**

 [![Image](/wp-content/uploads/2014/06/swift.jpg?w=610)](/wp-content/uploads/2014/06/swift.jpg) [Swift](https://developer.apple.com/swift/) is a new programming language by Apple.

At first sight, it seems to be easier to learn and easier to master than Objective-C. Objective-C is not particular difficult to learn and master, but its syntax looks foreign to C# / C++ / Python developers.

Swift, on the other hand, has a more conventional design. You can read Swift code the same way you can read C# code, even if you are not a Swift or C# developer.

Swift is a compiled language, although it looks like an scripting language. It is strongly typed, it is object-oriented with functional features. It does not have garbage collection. It uses ARC instead.

You can call any Objective-C API from Swift (at least Apple's APIs) , and Apple claims it is faster than Objective-C. Objective-C wasn't the fastest language out there, but it wasn't particularly slow either.

Perhaps the **killer feature** for me is Playground, a kind of sandbox for testing ideas / rapid development / rapid prototyping. BTW, Playground seems to be inspired (or copied if you prefer) from [Bret Victor's Inventing on Principle talk](http://vimeo.com/36579366), which is a MUST WATCH video for everybody.

Also, Swift has pretty much what John Siracusa asked for in his [Copland 2010](http://arstechnica.com/apple/news/2010/06/copland-2010-revisited.ars) article.

So, if Swift is easier to learn, easier to master, less error-prone, faster to develop code, performs better than Objective-C and you can call Objective-C code from it, why Apple should keep adding features to Objective-C ?

I expect that:

- Objective-C code will be supported on iOS / OS X for the foreseeable future.
- But new APIs will be added on Swift only. Developers will be forced to migrate to Swift to use the new ones (similar to what happened years ago with Carbon vs. Cocoa APIs ).

Unknowns:

- Can you call any Objective-C library from it ? or only Apple's APIs ? Will Apple release the binding generator ? **\[UPDATE\]**: Yes, it is possible to call [3rd party Obj-C libraries from Swift](http://ericasadun.com/2014/06/03/swift-combining-objc-and-swift-in-one-project/).
- Will Apple open source the language ? Or at least submit the language to the standard committee ?
- Can you call C and/or C++ libraries from it ?

For me:

- Swift is a very attractive language, so if Apple decides to open source it, it has the potential to gain a lot of developers from other platforms as well. I would definitely use it, and would seriously analyze the possibility of porting cocos2d to it.
- Bret Victor's Inventing on Principle was very inspiring. Since the day I watched that video, I wanted to add similar features to cocos2d. Playground showed us that it is possible to do it with a compiled language.

## **Metal**

 [![Image](/wp-content/uploads/2014/06/apple-metal-api-640x393.jpg?w=630)](/wp-content/uploads/2014/06/apple-metal-api-640x393.jpg) [Metal](https://developer.apple.com/library/prerelease/ios/documentation/Miscellaneous/Conceptual/MTLProgGuide/Introduction/Introduction.html) is an API that lets you talk to the GPU in a more direct (but non cross-platform) way than OpenGL.

Apple claims that it is 10x faster than OpenGL ES when drawing, although I usually take those numbers with grain of salt. Don't get me wrong, Metal probably is much faster than OpenGL ES, and a 3X would already be compelling reason to support Metal... it is just that the numbers presented at the Keynote are not always very accurate.

It supports:

- Multi-threading
- Pre-compiled shaders
- And I think we are allowed to use the GPU for general computing. Think of OpenCL (I have to double check this).

So...:

- For game players, this is great news. They will be able to play more graphics-intensive games on Apple's devices.
- For game engine developers, this means more work. Eventually, we will add Metal support in cocos2d-x.
- For Android... well, I guess they will need to add something similar, otherwise games on high-end Apple devices will perform much much better than on high end Android devices. Apple has a big edge here, because it is easier to create an API like Metal for iOS than for Android, since Apple controls the GPU and writes its drivers... and Google doesn't.
- For Windows Phone: I'm not sure if Direct3D on Windows Phone 8 is already that fast or not.
- And an Apple TV with Metal + Game Controllers, could be a serious competition for the console market.

## **SpriteKit / SceneKit**

 [![Image](/wp-content/uploads/2014/06/spritekit-scenekit.jpg?w=440)](/wp-content/uploads/2014/06/spritekit-scenekit.jpg) [SpriteKit](https://developer.apple.com/library/ios/documentation/GraphicsAnimation/Conceptual/SpriteKit_PG/Introduction/Introduction.html) was introduced at WWDC 13. It is a clone of cocos2d with some nice improvements. And [SceneKit](https://developer.apple.com/library/mac/documentation/3DDrawing/Conceptual/SceneKit_PG/Introduction/Introduction.html) is a 3d renderer. It has been in OS X for while, but it will included in iOS8 too.

SpriteKit and SceneKit seems to be Apple's bet for creating casual / mid-core games. And with Swift, they are a great combination... assuming that you are interested on iOS only.

If you are interested in developing casual/mid-core multi-platform games, you should try something like [cocos2d-x](http://www.cocos2d-x.org/), of course :-) Recently we started adding 3d features: in v3.1 we added Sprite3D, in v3.2 we will add 3d animations, and in v3.3 we will add lights and other effects.

## **Misc observations**

- Tim Cook said that 50% of the Chinese iPhone users were coming from Android. That is misleading. In China, almost everybody has an Android phone. And Apple introduced iPhone on China at the end of last year. So of course that most of the Chinese iPhone users came from Android. I'm surprised that that number was not 100%. (That is just one of the reasons why I take the Apple's numbers with a grain of salt)
- Why bashing Android ? Is Apple so afraid of Android ? I mean, leave the WWDC for developers-only news and use marketing events for bashing the competition.
- I really liked the new iOS additions: Continuity, the new features for iMessage, and sharing the phone with the Mac... Some of them are totally rip-off of other products. And although Apple innovates, Apple also copies.
