---
title: "Spiking with spikes: what is a spike?"
description: ""
date: "2008-03-16T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/spiking-with-spikes-what-is-a-spike-83a783e09d89
redirect_from:
  - /spiking-with-spikes-what-is-a-spike-83a783e09d89
---

What is a spike?   
That question came out at the second [Hong Kong Agile](http://agilehongkong.com/) meeting, last Wednesday.   
I was surprised, a spike was something in my base knowledge, something obvious.   
I think I’ve learned first the world spike in a programming context rather than spike in [any other context](http://www.google.com/search?client=safari&rls=en-us&q=define:spike&ie=UTF-8&oe=UTF-8).  
  
Probably is not so obvious and makes sense to blog about it.

#### knowledge spikes

My first spike was quite few years ago, on my first medium size Enterprise project.  
  
The aim of the spikes was to understand a current system, from the database layer to the UI.  
  
It was pain, I still remember it. It took me almost a week, asking help many times, it wasn’t an XP project.  
  
At the end of the exercise I was able to understand very well the system, and able to contribute well on the project.  
  
The code produced was checked in. To provide context, knowledge for future joiners in the project. Code that should not run in production.  
   
Basically it was a main class, instantiating all what you need to start up the full system.  
  
I’ve to say that the codebase was definitely well designed, otherwise doing such an exercise cold be very very diffult.

#### spikes checked-in?

Conrad, while giving his presentation with Tom on Agile techniques stated that there should be no check in of the code, since that code should never go on production.  
  
I disagree on most cases, there’s always a value on the spikes.  
   
The only spikes I would not check in are my personal trials to understand what’s going on, crappy code that I would not show us to anybody, so ugly that it doesn’t deserve the honor to go on the code repository: **One shot spikes**.

#### design sets spikes

On my last project with [Pat](http://www.thekua.com/atwork/) we tried different design sets (also including technology decisions) for a big problem of redesign/refactor we had.  
  
Also in that case we put the code under version control. Why? For future joiners for instance, these was what we tried, the solution that won it’s on the trunk, the failures on a sperate trunk folder, spikes can be a good name right?  
  
I’ll take the same approach also starting a new project. Let’s pretend I’ve to start a new java project, an app with a database layer. You can spike the database access with Hibernate, with Ibatis, with EJBS, etc…  
  
It will help you in estimating future stories, in the understanding on how much the chosen solution is testable.

#### estimations?

A spike should always be estimated, a fixed amount of time can be allocated during an estimation session.  
  
A spike should always achieve a final goal.  
   
If a spike screw completely the estimation throw it away, something is wrong, probably the design, the technology you’re trying to use is too complex to play with it, don’t insist on.  
  
Throw away but check it in, even if not working, on the spikes trunk! I can’t imagine any better documentation for new joiner to justify, to explain, that’s why we didn’t use EJBs, look at that!  
  
Shall I write tests doing a spike? Why not. If you’re trying to find a design I can’t imagine anything better that some old good TDD, if you’re trying to understand the system you can write a main if you’re not familiar with tests or just some tests. A spike can be made of tests.

#### more on the web…

Take a look also on the definitions on [C2.com](http://c2.com/xp/SpikeSolution.html).  
   
[XP.org](http://www.extremeprogramming.org/rules/spike.html) has his definition as well.
