---
title: "Bluetooth support on virtual machines w/ Parallels Desktop for Mac? — Parallels Support Forum"
description: ""
date: "2007-02-26T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/bluetooth-support-on-virtual-machines-w-parallels-desktop-for-mac-parallels-support-forum-cfc905a4adcc
redirect_from:
  - /bluetooth-support-on-virtual-machines-w-parallels-desktop-for-mac-parallels-support-forum-cfc905a4adcc
---

I am developing with a friend a small client server bluetooth application (an opensource project, perhaps more information here soon) and the target environment is Windows. So I’m using Parallels(\*), in coherence mode with bluetooth and so on :-)

> [Bluetooth support on virtual machines w/ Parallels Desktop for Mac? — Parallels Support Forum](http://forum.parallels.com/thread8813.html)  
> Yes, you may use built-in bluetooth adapter, but you need drivers for it.

> The easiest way to get those drivers is:  
> 1\. Download and install latest Apple Boot Camp from [http://www.apple.com/macosx/bootcamp/](http://www.apple.com/macosx/bootcamp/)  
> 2\. Browse to Macintosh HD->Applications->Utilities  
> 3\. Right-click the “Boot Camp Assistant” and select “Show Package Contents”.  
> 4\. Go to Contents->Resources and click the DiskImage.dmg to mount it.  
> 5\. Find the “Install Macintosh Drivers for Windows XP.exe” and copy inside your VM.  
> 6\. Run the file. In a short while, all necessary drivers will be installed. Reboot

> PS: We can’t redistribute Apple software, that is why you don’t have bluetooth drivers by default.

(\*) I had also some strange problems with my upgrade to 3170 RC3,Â the screen was black at startup, fortunately the [Parallels forum](http://forum.parallels.com/thread8920.html) rocks and I found that you simply have to start WinXP in “safe” mode, then reinstall the Paralllels tools, not from the menu, but mounting that from the parallels installation, then you’ll find them mounted on the D: letter of your Parallels winXP.
