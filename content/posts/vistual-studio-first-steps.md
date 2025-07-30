---
author: ricardoquesada
category: towp8
date: "2014-04-11T02:50:07+00:00"
guid: http://towp8.com/?p=184
tag:
- breakpoint
- cocos2d-x
- emulator
- visual studio
- windows phone
title: 'Vistual Studio: First steps'
url: /2014/04/10/vistual-studio-first-steps/

---

### Goals

1. Compile and run cocos2d-x tests on the emulator
1. Set a breakpoint in Visual Studio.

### Running cpp-test on the Emulator

1. Download [cocos2d-x v3.0](http://www.cocos2d-x.org/download)
2. Unzip it and then go to _cocos2d-x/build_ directory

    ```shell
    $ cd cocos2d-x/build
    ```
3. Open _cocos2d-wp8.vc2012.sln_ with Visual Studio

    ```shell
    $ start cocos2d-wp8.vc2012.sln
    ```

4. Set _cpp-tests (Windows Phone Silverlight 8)_ as the default project:
    - Go to the _Solution Explorer_
    - Right click on _cpp-tests (Windows Phone Silverlight 8)_
    - Click on _Set as StartUp Project_

   [![vs_default_project](/wp-content/uploads/2014/04/vs_default_project.png?w=676)](/wp-content/uploads/2014/04/vs_default_project.png)

5. Run cpp-tests on the Emulator
    - Press the _Emulator 8.1 WVGA 4 inch button_
      ![run-emulator](/wp-content/uploads/2014/04/run-emulator.png?w=529)
    - If an Hyper-V error appears, then you have to enable Hyper-V:
        - [Enable Hyper-V on the BIOS](http://msdn.microsoft.com/en-us/library/windowsphone/develop/jj863509%28v=vs.105%29.aspx)
        - [And then enable Hyper-V on Windows 8.1 Pro](http://windows.microsoft.com/en-us/windows-8/hyper-v-run-virtual-machines) (
          it won't work on the 'Regular' edition).

6. If the following Dialog pops-up, just press _Retry_:

   [![hypervisor](/wp-content/uploads/2014/04/hypervisor.png?w=676)](/wp-content/uploads/2014/04/hypervisor.png)

And that's all. You should see the cpp-tests running on the Emulator:

[![cocos2d-emulator](/wp-content/uploads/2014/04/cocos2d-emulator.png?w=676)](/wp-content/uploads/2014/04/cocos2d-emulator.png)

### Setting a breakpoint

1. Open any file, like _ActionsTest.cpp._ Tip: Quick Open file is_Ctrl + ,_
1. Set a breakpoint in any line, by clicking on the left margin, like in Xcode
1. You should see a red dot (like in Xcode).

But if you run _cpp-tests_, you will see that the red dot is no longer red: it
is white now.

[![breakpoint-bad-visual-studio](/wp-content/uploads/2014/04/breakpoint-bad-visual-studio.png?w=676)](/wp-content/uploads/2014/04/breakpoint-bad-visual-studio.png)

The problem is that by default, cpp-tests is treated as a _Managed Task_ by the
debugger. You have to change it to _Native_:

1. Go to _Solution Explorer_
1. Right click on _cpp-tests (Windows Phone Silverlight 8)_
1. Go to _Properties -> Debug_
1. And change _UI Task_ and _Agent Task_ to _Native Only_

[![native-only-task](/wp-content/uploads/2014/04/native-only-task.png?w=676)](/wp-content/uploads/2014/04/native-only-task.png)

Done! you should be able to set breakpoints on your C++ code now!
