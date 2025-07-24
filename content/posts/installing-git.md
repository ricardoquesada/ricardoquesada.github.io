---
author: ricardoquesada
category: cocos2d
date: "2014-04-10T19:25:10+00:00"
guid: http://towp8.com/?p=170
tag:
  - windows phone
  - git
  - mysysgit
  - sourcetree
  - tower
title: Installing git
url: /2014/04/10/installing-git/

---
So you have Windows 8.1 + Visual Studio 2013 installed. Now you need to install a git client.

My workflow on Mac is:

- I use git command line about 70% of the time.
- In the reaming 30% I'm using [Tower](http://www.git-tower.com/), [Kaleidoscope](http://www.kaleidoscopeapp.com/) and [Xcode](http://www.raywenderlich.com/51351/how-to-use-git-source-control-with-xcode-in-ios-7).

So, I was looking for something similar for Windows. And so far, this is my current setup:

- [Mysysgit](http://msysgit.github.io/), for git command line.
- [SourceTree](http://www.sourcetreeapp.com/) for GUI
- I couldn't find a good stand-alone diff-viewer, so I'm using SourceTree's

What I like about Mysysgit is that it installs a Unix-like shell, with [git auto-completion](http://code-worrier.com/blog/autocomplete-git/) and you can also see the [current branch](http://code-worrier.com/blog/git-branch-in-bash-prompt/) in the shell prompt. That is very handy.

[![windows-shell-git](/wp-content/uploads/2014/04/windows-shell-git.png?w=676)](/wp-content/uploads/2014/04/windows-shell-git.png)

SourceTree is also a pretty good, advanced GUI client for git. I used it a lot in Mac before switching to Tower.

In order to have both Mysysgit and SourceTree working at the same time with your own GitHub repositories, you have to do:

**a)** Create an ssh key from the git shell by running: ssh-keygen

[![ssh-key-gen-git](/wp-content/uploads/2014/04/ssh-key-gen-git.png?w=676)](/wp-content/uploads/2014/04/ssh-key-gen-git.png)**b)** From SourceTree -> Tools -> Options,  import the newly created key. Make sure you select the "OpenSSH" option, and not "Putty".![source-tree-key-config](/wp-content/uploads/2014/04/source-tree-key-config.png?w=676) **c)** Then, what you have to do is to add the [public key in Github](https://help.github.com/articles/generating-ssh-keys#step-3-add-your-ssh-key-to-github).

An alternative option to Mysysgit + SourceTree is to use [Github for Windows.](https://windows.github.com/) But I didn't like it, its GUI is too basic for my needs.

It is worth noting that Visual Studio 2013 Pro (not Express) comes with [built-in git support](http://msdn.microsoft.com/en-us/library/hh850437.aspx). It is similar to Xcode's git support.
