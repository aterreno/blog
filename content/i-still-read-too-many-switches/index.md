---
title: "I still read too many switches"
description: ""
date: "2007-09-30T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/i-still-read-too-many-switches-b32a306ca4ee
redirect_from:
  - /i-still-read-too-many-switches-b32a306ca4ee
---

Yes, I still read too much code with switches inside. I hate it. There’s still also a "nice" page on the official website of Sun on how to write really nasty code, it’s [here](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/switch.html). I don’t wanna infect this blog, so I’m not pasting that example of code here. I paste only a quote, it says:

> Deciding whether to use if-then-else statements or a switch statement is sometimes a judgment call.

Yes, indeed. And the judgment call is: "should I write a long list of if then else or maybe think on some kind of polymorphism?" The switch is not an option. Switch smells of poor design, smells of "you dude, writing that code, you don’t know what object oriented is!". It’s not well testable, it’s ugly.

The web is plenty of examples on how to refactor from a switch to a decent design, just searching right now, I’ve found a good one [here](http://hanuska.blogspot.com/2006/08/swich-statement-code-smell-and.html).

There’s another one [here](http://sis36.berkeley.edu/projects/streek/agile/bad-smells-in-code.html#Switch+Statements), with strategies for getting rid of it.

So why are you writing still switches? Let me know, we can talk about this and maybe I can help you to quit.

Switch off the switches. That’s the tip. :-)

Hey, this does not allow you to write a long chain of if then else blocks! Think on polymorphism every time you write an if, ask to your pair what he thinks, maybe you can move that responsibility somewhere else, one if is still fine but when you start to have an else… Mhmmm….

I really hope that someone is reading and I’ll read less switch stuff…
