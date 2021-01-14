---
title: "Netbeans"
description: ""
date: "2007-03-22T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/netbeans-6d72f495a0f
redirect_from:
  - /netbeans-6d72f495a0f
---

I’ve this draft and since I’ve seen that a friend is now in [the magic net beans team](http://www.netbeans.org/community/contribute/dreamteam.html) perhaps is time to publish it :-)

Maybe he can help me and telling me if I am wrong or just change somehow that tool…

I’m writing some code with netbeans and I would like to note here what I don’t like of this tool. Especially compared to Eclipse.

1.  Lack of the magic CTRL+1 code assist, this is really slowing down my productivity
2.  Crap code generation: why is generating always the empty public contructor? With also a smelly comment / **Creates a new instance of …** /
3.  The generator of code of the Mobility pack is pure crap. I had to open the MIDlet code with wordpad, delete all the crap from the code to be able to change something also inside netbeans. There were import with the star also. Now, of course, I am using netbeans as a simple text editor.
4.  Refactoring: as fair as I’ve seen the refactoring tool is very poor. You can’t for instance extract a variable as a local variable or field…
5.  Using create Method when the method is still not implemented netbeans sets the visibility to package and write a stupid UnsupportedOperationException exception.
