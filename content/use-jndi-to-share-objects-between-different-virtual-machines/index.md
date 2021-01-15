---
title: "Use JNDI to share objects between different virtual machines"
description: ""
date: "2006-05-08T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//use-jndi-to-share-objects-between-different-virtual-machines-c72e3df3d93d
redirect_from:
  - /use-jndi-to-share-objects-between-different-virtual-machines-c72e3df3d93d
---

Since I’m implementing a Bluetooth Media Sender and since I’m using the Avetana JSR 185 Implementation (with it on Windows Systems you can use two dongles, one controlled by Widcomm and one controlled by the Microsoft stack. On startup of the application you need to specify the VM Option -Davetanabt.stack=microsoft to force one application to actually use that stack. It defaults to Widcomm if both are available)

I need to share objects between different 2 virtual machines… To have running 2 instances of my BluetoothSender.  
I’ve found this cool article dated 1999:  
[Use JNDI to share objects between different virtual machines](http://www.javaworld.com/javaworld/jw-07-1999/jw-07-cooltools_p.html)  
Use JNDI to share objects between different virtual machines  
Share remote objects between different virtual machines without the need for an object request broker

Summary  
Imagine the following: Process A on machine B puts an object into a Hashtable. Now, a separate process C on a different machine D can access that object from its own local copy of the Hashtable — even after process A terminates and the virtual machine unloads! Now imagine all this is achieved without the use of RMI, and without involving an ORB, CORBA, EJB, or a database. What’s the secret? The Java Naming and Directory Interface (JNDI). This month’s tool is the JNDIHashtable — which, as its name reveals, uses JNDI to do its thing. (2,600 words)  
Well, It looks working very well. I’m using the fscontext.jar, which is not included in the JDK distribution, you have to download it [here](http://java.sun.com/products/jndi/downloads/index.html). I’ve still to try the performance on the linux box…  
I’ve found also a great article about this stuff wrote by a former collegue of mine :-) Fabrizio Giudici, it’s in italian, on theÂ [mokabyte](http://www.mokabyte.it/2002/01/jndi_1.htm) website.
