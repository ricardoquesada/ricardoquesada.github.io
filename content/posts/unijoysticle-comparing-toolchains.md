---
author: ricardoquesada
category: retro computing
date: "2016-10-02T09:37:20+00:00"
draft: "true"
guid: http://retro.moe/?p=1893
tag:
  - android
  - android-studio
  - c++
  - eagle
  - ios
  - java
  - platformio
  - qt
  - sprite-kit
  - unijoysticle
  - vchar64
title: 'UniJoystiCle: comparing toolchains'
url: /

---
I created the UniJoystiCle to have fun and to learn. And I decided to use editors/toolchains that I have never used before, and that I wanted to try.

- [Qt](https://www.qt.io/developers/)/QtCreator: Used for [VChar64](https://github.com/ricardoquesada/vchar64) (the editor used for The Uni Games)
- [Swift](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/) + [SpriteKit](https://developer.apple.com/library/content/documentation/GraphicsAnimation/Conceptual/SpriteKit_PG/Introduction/Introduction.html): Used for the [UniJoystiCle iOS client](https://itunes.apple.com/us/app/unijoysticle-controller/id1130131741?mt=8)
- Java + [Android Studio](https://developer.android.com/studio/index.html): Used for the [UniJoystiCle Android client](https://play.google.com/store/apps/details?id=moe.retro.unijoysticle&hl=en)
- [Eagle:](https://oshpark.com/shared_projects/JTZ3EO66) Used for the [UniJoystiCle board](https://github.com/ricardoquesada/unijoysticle) (also first time to design a schematic + PCB)
- [PlatformIO](http://platformio.org/): Used for the [UniJoystiCle firmware](https://github.com/ricardoquesada/unijoysticle) (also first time to try the Arduino thing)
- [cc65](http://cc65.github.io/cc65/): Used for [The Uni Games](https://github.com/ricardoquesada/c64-the-uni-games)

## Qt / QtCreator

I chose Qt because I wanted to do a multi-platform editor. I've been following the Qt project since the early days of [KDE](https://www.kde.org/), but I never had the chance to create something using it. I quickly evaluated [C# + Gtk#](http://www.mono-project.com/docs/gui/gtksharp/), but I didn't like how it looked in the different platforms. [WxWidgets](https://www.wxwidgets.org/) was another option, but I can't remember why I discarded it.

I initially started the project using JavaScript ( [QtQuick](http://doc.qt.io/qt-5/qtquick-index.html)).  Two weeks later I switched to C++. QtQuick was too limited for VChar64, and honestly I think it is too limited for any desktop project.

**What I liked:** I like how well supported the three platforms are (Linux, Mac and Windows). It looks native in all of them. I like the design of its API, how powerful it is, its documentation, and how well integrated is everything. Qt Creator (the IDE) looks clean, it is easy to discover features, the text editor is good, the shortcuts are easy to learn, and has a nice UI designer. It even has a Localization editor, [Qt Linguist](http://doc.qt.io/qt-5/qtlinguist-index.html). All the widgets and libraries that I needed were there. I didn't have the need to use any 3rd party library. Qt is muuuuch more than just a widget library. Hey, it is even open source!

**To keep in mind:** Be careful with the UI designer. It is super easy to connect emitters with slots. But that is a double-edge sword. Ideal for super small projects. A nightmare for bigger projects. I just connect them programatically.

**Weak point:** It is C++ based. I am seasoned C++ developer (15+ years), and I use it daily. But if a Rust/Swift-based-framework with similar features appears, I would use it instead of Qt. Qt, as a C++, library is great. C++ is evolving, and since C++11 it is a much better language. Qt added all the C++11 features, but C++ still feels complex and slow-to-develop-with.

**Toolchain productivity score:** Very productive

## Swift + SpriteKit + Xcode

I've using Xcode for the past 8 years both with C++ and Objective-C and like it. But this time I wanted to try Swift, SpriteKit and UIKit.

**Swift:** When it was first released two years ago, I read its programming guide and I liked the language. My first impression was that it felt like an scripting language without being one. It is not a dynamic language, in fact is as static a C++.  Java and Objective-C have more dynamic features than Swift.

Also, Swift was designed to be safe. Everything is explicit, no implicit casting, not even for the smallest thing, which is good from a safety point of view. But could be too verbose. For the UniJoystiCle I ended up using "rawValue" too much for my taste. If you are implementing a network protocol (UniJoystiCle has its own protocol), it is shorter to do it in C than in Swift. It is a matter of getting used to it.

Another thing that bothers me is, even if Swift is only 2 years old, they are already in version 3 and they broke backwards compatibility too many times for its age. Please, stop doing that... or use the correct names: v0.1, v0.2, v0.3, instead of v1, v2 and v3.

**SpriteKit:** SpriteKit is a nice 2D game engine (what can I say, it is a clone of Cocos2d with some nice improvements). For the UniJoystiCle, I could have avoided SpriteKit altogether, and do everything in UIKit. But SpriteKit has built-in physics (Box2d based) and that was very handy for Gyruss mode.  The SpriteKit "scene editor" is super limited, but worked for me.

**Xcode:** I've been using Xcode for the last 8 years, so I don't have any "first impression". But it was the first time for me to use Storyboard. Although Storyboard is very powerful, I needed to watch a few videos to understand how to use it. Something that didn't happen to me while using QtCreator.

**Toolchain productivity score:** Very productive

Android Studio + Java **Java:** This was my first Java project. I read Java source code many times, but this was the first time to write it. Learning it was easy, since it is very close to C++. The language is good and I like it. But two things called my attention:

- [Checked exceptions](http://www.javapractices.com/topic/TopicAction.do?Id=129): Why? Can't you just pass a closure that will get triggered if there is an error? I guess closures are a relative new feature. But catching checked exceptions feels "old", and you are forced to catch them, even if you know that no checked exceptions will be thrown.
- Directories:

I could have used [Cocos2d-x](http://cocos2d-x.org/) (I'm one of its developers) and I would have created both the iOS and Android app in a just a few days. But I wanted to learn Android SDK, the Java API. So the option of the IDE was easy: Android Studio. I didn't even consider Eclipse + ADT.

## Eagle

## cc65
