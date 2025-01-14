---
author: ricardoquesada
category:
  - cocos2d
date: "2017-04-17T04:38:08+00:00"
guid: http://retro.moe/?p=1903
summary: |-
  ## Cocos2d (Python)

  ![](https://lh3.googleusercontent.com/ZXpO9qBoRfmnSsiDZYWjM_SqUhyzJQe6NT3mFDIyo1qeIZbHncgH9SA-RC-TuL8cT92zqP0kTb1JXcb4BLMg3ir_5IssEqEILVxf5xHTCGiBtzpyUaRBVyPcTHDmZJj-hPkxh8w=-no)

  In February 2008, at Los Cocos, Córdoba, Argentina, we started the "Los Cocos" Python game engine. We later renamed it Cocos2d. The idea was to create a game engine for the games we were creating for [PyWeek](https://pyweek.org/).

  \[caption id="" align="alignnone" width="512"\]![](https://lh3.googleusercontent.com/vhpMrsnv9CAOcbB_ZSSFIxOgP-Soh8FoACuQkQBAk5XU9MN84oekftn9Ai4uvaHTAQBzY4FH0LeDubielKw-iseyHkyv75Z-UmeV_PnzMgsh4WYRqCz9LIBIx0duYzsVpicyCLU=-no) PyCamp 2008. Centro Allen Gardiner, Los Cocos, Córdoba, Argentina\[/caption\]

  We started the game engine with Lucio Torre, Daniel Moisset, Rayentray Tappa, and I, with the help of Alejandro Cura and other members of [PyAr](http://www.python.org.ar/).
title: The history of Cocos2d in a glimpse
url: /2017/04/16/cocos2d-in-a-glimpse/

---
## Cocos2d (Python)

![](https://lh3.googleusercontent.com/ZXpO9qBoRfmnSsiDZYWjM_SqUhyzJQe6NT3mFDIyo1qeIZbHncgH9SA-RC-TuL8cT92zqP0kTb1JXcb4BLMg3ir_5IssEqEILVxf5xHTCGiBtzpyUaRBVyPcTHDmZJj-hPkxh8w=-no)

In February 2008, at Los Cocos, Córdoba, Argentina, we started the "Los Cocos" Python game engine. We later renamed it Cocos2d. The idea was to create a game engine for the games we were creating for [PyWeek](https://pyweek.org/).

\[caption id="" align="alignnone" width="512"\]![](https://lh3.googleusercontent.com/vhpMrsnv9CAOcbB_ZSSFIxOgP-Soh8FoACuQkQBAk5XU9MN84oekftn9Ai4uvaHTAQBzY4FH0LeDubielKw-iseyHkyv75Z-UmeV_PnzMgsh4WYRqCz9LIBIx0duYzsVpicyCLU=-no) PyCamp 2008. Centro Allen Gardiner, Los Cocos, Córdoba, Argentina\[/caption\]

We started the game engine with Lucio Torre, Daniel Moisset, Rayentray Tappa, and I, with the help of Alejandro Cura and other members of [PyAr](http://www.python.org.ar/).

We announced a beta (or was it alpha?) version in a lightning talk at PyCon Chicago in March 2008.

{{< figure align=alignnone width=533 src="https://lh3.googleusercontent.com/GCz9OlGCZMHuVauHqN7hoLZ5oZpKNtsJTojnjKkoz26GUGMmqM3x1Q5BVAlMijg4b%5FdD99jJT8EFfbE%5FTAfDcnlyw%5FRTY5eOqw3t-eZfRG0HiXN6wLWmKHdYolZUD%5FQ1HUnDHM8=w1024-h681-no" alt="" >}}

In July 2008, Lucio and I went to Euro Python to present Cocos2d (was it v0.3?).

\[caption id="" align="alignnone" width="512"\]![](https://lh3.googleusercontent.com/kgl7EbCPt_B-ZN44mSTblpdUN7TSNX9mnIa23QIqbfAv02pMxYoaQvZurHDot7d39bZv7Qh5WoDedxnSs7_iOg0WyXKGKRKFcgBQ_zHVZgSiRBHw5T7vI3IF2icSY-2OzXMsI80=-no) With Lucio Torre at Euro Python 2008 presenting Cocos2d. Vilnius, Lithuania, July 2008\[/caption\]

In addition, Lucio and I presented Cocos2d at [PyCon Ar](https://twitter.com/pyconar) 2008 and 2009.

In 2010 Claudio Canepa became the new Cocos2d developer/maintainer.

## Cocos2d-iPhone

![](https://lh3.googleusercontent.com/4Ou3F7RI7FCsvr3R7iFMSmpmWLZYwVJNSxE9LM4vZEt0vwnpUO20eZVDgAl5AkFtHJSaykuq7FbacZK57lTTIrEqNqkq8TLxoQvQUaAndIbTsvYoFuQKb2IjJ0w6L7ucQfrgsOg=-no)

Somewhere around the beginning of 2008, Apple announced that the iPhone would have a store. Apple would only take 30% of the revenue (back then, carriers were taking around 90%). Furthermore, the iPhone was powered by OpenGL ES and the OS was UNIX based.

Also, around that time, I wanted to create commercial games. I had previously considered the Web (Flash) and feature phones (J2ME) as possible markets. But after Apple's announcement, I decided to develop games exclusively for iPhone.

I needed a game engine for my iPhone games, so I re-wrote Cocos2d in Objective-C. The high level design remained the same, but I had to make substantial changes to make it work on the iPhone...  and that is how "cocos2d-iphone" was born. The  first cocos2d-iphone version (v0.1) was released in June 2008.

In March 2008, I applied to get my iPhone Developers license, and [finally got it in July 2008](/2008/09/18/el-largo-camino-a-la-licencia-de-iphone/) (it took me 4 months to get one, whereas today you can get one in a few minutes). It was not possible to publish games on the iPhone App without a license. While waiting for my license, I did some contract work, developing some games for 3rd parties using cocos2d-iphone.

Having gotten my iPhone Developers license, I created my first (and only) game for the iPhone: [Sapus Tongue.](https://github.com/sapusmedia/Sapus-Tongue) However, I realized that creating commercial games was not that fun for me; neither did I find it easy. Since cocos2d-iphone was already popular, I decided to work full time on it. The reason I could do this is that I was actually making a living by [selling two commercial tools](https://web-beta.archive.org/web/20110529144259/http://www.sapusmedia.com:80/products/) for cocos2d-iphone: [LevelSVG](https://github.com/sapusmedia/LevelSVG): a sort of editor + physics on top of cocos2d, and [Sapus Tongue source code](https://github.com/sapusmedia/Sapus-Tongue).

At the beginning of 2009 there were already more than 100 games using cocos2d-iphone. The first one to reach #1 at the iPhone App Store was [Stick Wars](http://www.erichartzog.com/blog/creating-stickwars).

{{< figure align=alignnone width=480 src="https://lh3.googleusercontent.com/5F8wGUMT8E3nXmVZVbLVK4kG%5FbIBbuQHa0cwI9VAZIN0dm2d8Hd6YkCZK0H2y8Zp8N%5F771QHJunbIJ8vFr5onjx7m-heWEWNdsxKmQ5w16yTJ6wSuF1o9aNlF-A71Dz86bcV4ek=-no" alt="" >}}

After that, many other cocos2d-iphone games reached #1. And most of the time, there was at least one cocos2d-iphone game in the Top #10. I believe this was the case from 2009 until the [end of 2011](http://web.archive.org/web/20130502004847/http://www.cocos2d-iphone.org/archives/1496).

Not only games were created with cocos2d-iphone, but also animated books, photo applications, and more. Some cocos2d-iphone games and applications were featured at [WWDC 2010](https://web.archive.org/web/20130502035554/http://www.cocos2d-iphone.org/archives/996). Even games that Apple proudly announced as "built using Apple libraries", were actually built with cocos2d-iphone.

{{< figure align=alignnone width=512 src="https://lh3.googleusercontent.com/0LiIWU6XLeTLX9GpSVnfciX3tVvWv4G9PXpoHISh95vq5z8MQiCBlUNtlnqB-x0tUa0CDjuP1Xp7Nw5eoPz%5Fsh7q8Xv7nR-18UUcSBJEbNUzMm3ONj1F07EpQtzpY9Tcja-hpCU=-no" alt="" >}}

Many cocos2d-iphone [forks/ports/bindings were created](https://web.archive.org/web/20111021045559/http://www.cocos2d-iphone.org/archives/1155) as well, such as:

- At least two Java ports: [cocos2d-android](https://code.google.com/archive/p/cocos2d-android/) and [cocos2d-android-1](https://github.com/ZhouWeikuan/cocos2d)
- A C++ port: [Cocos2d-x](http://www.cocos2d-x.org)
- Two JavaScript ports: [Cocos2d-HTML5](https://github.com/cocos2d/cocos2d-html5) and [Cocos2d-JavaScript](https://github.com/RyanWilliams/cocos2d-javascript/)
- Three C# ports: [CocosNet](https://web.archive.org/web/20100227225817/http://github.com/city41/cocosnet), [Cocos2d-XNA](https://github.com/Cocos2DXNA/cocos2d-xna), [CocosSharp](https://github.com/mono/CocosSharp)
- A Go port: [Gocos2d](https://code.google.com/archive/p/gocos2d/)
- Python bindings (bindings for cocos2d-iphone and [for cocos2d-x](https://github.com/seewindcn/pycocos2d)) and Python port (a new port based on cocos2d-iphone, and not on the original Cocos2d)
- Ruby bindings: [ShinyCocos](https://web.archive.org/web/20111021044117/http://www.cocos2d-iphone.org/wiki/doku.php/shinycocos:faq) and support for [RubyMotion](https://github.com/scottymac/rubymotion-cocos-tests)

In July 2011, after working on cocos2d-iphone for more than 3 years, and with the help of the community, I released [cocos2d-iphone v1.0](https://web.archive.org/web/20111007164432/http://www.cocos2d-iphone.org/archives/1528).  Some stats: [~140 contributors](https://github.com/cocos2d/cocos2d-iphone-classic/blob/v2.2/AUTHORS#L441), ~2600 commits and [63 internal releases](https://github.com/cocos2d/cocos2d-iphone-classic/blob/v2.2/CHANGELOG#L599).

{{< figure align=alignnone width=247 src="https://lh3.googleusercontent.com/REVtNKHCueWY1eyvzBgQsAHTIV7LKnU2hBy2DEAWY0XVmAZgDv8NipIuYR2cmvBZRfrvUh14f3nFuQonQW8vbFhvyUk0M3JcIlh4WkUstj0-NxYKZM3dk9trZ180vVlX0bZ82MQ=-no" alt="" >}}

The community was very healthy, with many people helping each other, opening bug reports, sending pull requests, suggesting features, etc. The ecosystem around cocos2d-iphone was also very healthy: many cocos2d-iphone books were published, and many editors/tools (both commercial and free/open source) supported cocos2d-iphone, many job positions were looking for cocos2d-iphone developers.

In May 2011, I joined Zynga. At Zynga we used cocos2d-iphone for some iOS games. To port them to Android, some of them were rewritten using [AndEngine](http://www.andengine.org/), and others were ported using [AppPortable](http://www.apportable.com/)'s Objective-C/UIKit stack.

In 2012, Android was already very strong. I wanted to support Android natively (and other platforms as well). I had three options:

1. Stop working on cocos2d-iphone, and work on Cocos2d-x (the C++ fork)
1. Keep developing cocos2d-iphone, and use 3rd party commercial Objective-C stack (like [StellaSDK](http://web.archive.org/web/20130502012020/http://www.cocos2d-iphone.org/archives/2013), [NoodleCake](http://web.archive.org/web/20130502015911/http://www.cocos2d-iphone.org/archives/1774) or [AppPortable](http://www.apportable.com/)) to port cocos2d-iphone to Android
1. Keep developing cocos2d-iphone, and develop an open source Objective-C stack to port cocos2d-iphone to Android.

I didn't want to depend on 3rd party commercial tools, and I didn't have the time to write my own Objective-C stack, and Cococs2d-x was already popular. So I decided to help the Cocos2d-x team. We started using Cocos2d-x at Zynga as well.

{{< figure align=alignnone width=512 src="https://lh3.googleusercontent.com/K05MOzKn8QE3Vn8s64X1p7CfrWuMfNaQyweNLpwMsa7E%5FJ50l-MFEXYxEV2N0XcsCbFdMQkqCl4L6%5FPDJYc0NNptx3ojm9qkVpDaSfjAN5rfqQwdc5BNwSvlxMkmHtzXvmlDH1E=-no" alt="" >}}

At Zynga, with the help of the Cocos2d-x team, we created a very attractive tooling:

- Cocos2d-x and cocos2d-iphone were feature compatible. The API was almost the same (of course, one in C++ and one in Objective-C)
- [CocosBuilder](https://github.com/cocos2d/CocosBuilder) (created by Viktor Lidholt) included many good features: Scene editor, key-frame animation editor, JavaScript scripting and more.
- Scenes exported by CocosBuilder were supported both by cocos2d-iphone and Cocos2d-x.

{{< figure align=alignnone width=512 src="https://lh3.googleusercontent.com/TCOj1fzRAc9uQVCfFWksM3BFI2SImRIUutG0kJYhJwtZAURrYRsuI0mFdOw5xF3QfMEbCca7icesfykHTIXQ1%5FGMyuY4pw%5FPl1r0JZYjC9skZQBBaBTa4Ss9f0ViTFeVU%5FgPpkA=-no" alt="" >}}

The only drawback was that keeping feature-compatibility between Cocos2d-x and cocos2d-iphone was expensive: we had to write the features twice. And also CocosBuilder was built on top of cocos2d-iphone which meant it was only available for Mac (no Windows version), and also required writing the features twice. Supporting Windows was important for many Cocos2d-x users.

I kept developing cocos2d-iphone until June 2013, and then [I passed the torch to Lars Birkemose](http://web.archive.org/web/20140208064401/http://www.cocos2d-iphone.org/welcome-birkemose-the-new-cocos2d-iphone-lead-developer-maintainer/) (who in 2016 passed it again to Andrei Volodin). In August 2013 I joined Chukong.

## Cocos2d-x

![](https://lh3.googleusercontent.com/M8T3KLjlbcbJEspL6Ye56OJiD07pAYjF-DwlVt16gYRjYxs5HhO37psec-PLSh-ewTa_PVuzNO0rVh-8Vi3oW7yMZPigAMzKBA4CIqm4nAvIMolVcUODqjnxmEpC8Rg4yaVOKv8=-no) _Note: Chukong, the company behind Cocos2d-x and Cocos Studio, is a Chinese company with its headquarters in Beijing. Cocos Studio was developed at Beijing. Cocos2d-x is being developed in Xiamen (south of China), and I joined their California office were we did a bit of everything._

Cocos2d-x was started by Zhe Wang in July 2010. It was a clone of cocos2d-iphone, but coded in C++ instead of Objective-C. His goal was to create an SDK to facilitate porting cocos2d-iphone games to the uPhone (a phone project that was later cancelled). In order to facilitate the porting, Cocos2d-x included all the Objective-C patterns that were found in cocos2d-iphone. Somewhere in 2012 (or was it 2011?) the Cocos2d-x team joined Chukong.

Chukong had the resources, the willing, and the position to make Cocos2d-x a world class game engine / tooling. Cocos2d-x, back in 2013, had about between 70%~80% of the Chinese market share.

At Chukong, we started by designing Cocos2d-x v3, which included the removal of Objective-C patterns from its code, the use of modern C++ APIs, the update of the renderer (Nite), the addition of 3d features (Tony and Harrison) and the writing of a [Programmers Guide](http://www.cocos2d-x.org/docs/programmers-guide/about/) (Jason).

But the most important thing was the editor: We needed one. Chukong had invested a lot of resources in [Cocos Studio](http://www.cocos2d-x.org/wiki/Cocos_Studio). It had many features, but its UX wasn't appealing for the US/Western market, and it was Windows only.

So, in the US office, we (Justin, Nite and Kai) started working from scratch on an editor for Cocos2d-x both for the Chinese and US/Western markets (something similar to CocosBuilder, but built on top of Cocos2d-x and compatible with Windows and Mac. [Qt](https://www.qt.io/) was used for this).

{{< figure align=alignnone width=512 src="https://lh3.googleusercontent.com/DDR2MQcx7Q1NUbubS4IliNRXrXAImRmSjDAD-5en6vPfM9-2kzy8Jq86bSlg4%5FN6Dt7xAoJ8ngrN5pKF30t8-qC1kVO7rXPfiEF6RdNVpGVSQnmpF7Qyp9eOlA-2FrjaXC2keyU=-no" alt="" >}}

Unfortunately the new editor was cancelled. As hard as we tried to improve Cocos Studio's UX, it failed to attract the US/Western market.

{{< figure align=alignnone width=512 src="https://lh3.googleusercontent.com/aTN3pClyIDTAaVbwomLmeQ5U96U0dIJfjIES8mywJBZGZLIRk-vFJq77u5EiHcxVGeAE7PtHhaFkrSvHY2Efe-Trp%5F9fuWxOloFaDZVd5pZ8AuqiErf9rRpUaVLqBnQCYZo8kL8=-no" alt="" >}}

Other projects were cancelled as well, such as Cocos2d-HTML5 v4, Cocos2d-x v4 renderer + HAL, Cocos2d-x launcher, Cocos IDE. Even Cocos Studio got cancelled.

{{< figure align=alignnone width=512 src="https://lh3.googleusercontent.com/jjFLcUgkM9VN8-%5FCsruQmdju4aBZ-HPDjYGCKQSodQa%5FXD1SsPJvx331-mBf-FrzAjLwOjGyMO1O3SmvI8T3xD49G1rIh1Cg0g8Nc0fp0heR2hr5TnEValfZiZe9gljxVR7igzU=-no" alt="" >}}

Cancelling projects, specially when they are almost ready, can be frustrating. But our main challenge was finding a good business model. We tried different things, but we couldn't find a good one.

In hindsight, this is what I think we should have done:

- Work on just one editor: the Qt editor that was supposed to be the Cocos Studio replacement.
- Offer services within the editor: [SDKBOX](http://www.cocos2d-x.org/sdkbox), and other services.
- Focus: Only work on casual/mid-core features (no VR or other distracting features). Try to be the best ones in that category.

After working 9 years on Cocos2d, [and due to the development of recent events](http://discuss.cocos2d-x.org/t/farewell-to-our-friends-chukong-u-s-office-is-closing-march-31-2017/34809), the time has come for me to work on something else. What should I do next? Some people say that the future is IoT, others say it is Machine Learning, while the rest say it is VR/AR. They are all wrong: The future is the Commodore 64. See you soon.
