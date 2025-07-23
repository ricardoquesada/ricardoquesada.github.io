---
author: ricardoquesada
category: cocos2d
date: "2014-04-04T07:25:26+00:00"
guid: http://riq64.wordpress.com/?p=14
tag:
  - windows-8.1
title: Use Windows 8.1
url: /2014/04/04/use-windows-8-1/

---
You need Windows 8 in order to develop for Windows Phone 8. Windows 7 won’t work.

But avoid Windows 8, [it is confusing](https://www.google.com/search?q=windows+8+confusing). Use Windows 8.1 instead. And [boot directly into the “Desktop”](http://www.pcworld.com/article/2043243/how-to-boot-to-desktop-mode-in-windows-8-1.html). Avoid the annoying “Start” thing.  Good news: the upgrade from 8 to 8.1 is [free](http://windows.microsoft.com/en-us/windows-8/update-from-windows-8-tutorial).

You should  know that [there are many “flavors” of Windows](http://www.microsoft.com/en-us/windows/enterprise/products-and-technologies/windows-8-1/compare/default.aspx): “RT”, “Regular”, “Pro”, “Enterprise”… just get the “Pro”.  _RT_ (Runtime) is the new name for _[Metro](http://www.theverge.com/2012/8/2/3216545/microsoft-metro-branding-memo-european-partner)_.

Windows 8 (Regular, Pro,Enterprise) has both shells: the desktop shell (win32 API); plus the new RT shell... but you should not confuse Windows RT with Windows Phone. They have the same shell (Metro), they have very similar APIs, but they are slightly different Operating Systems. Remember: You are going to develop games for Windows Phone (using the C++ API), and not for Windows RT.

Was that confusing? Don't worry, it is still confusing for me. As a summary:

- Your host operating system will be Windows 8.1 Pro (and not Windows RT)
- Your target operating system will be Windows Phone 8 (and not Windows RT)
