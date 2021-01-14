---
title: "Fest & Mockito, aka how to test quickly and easily your swing classes"
description: ""
date: "2009-04-01T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/fest-mockito-aka-how-to-test-quickly-and-easily-your-swing-classes-8cc68648d458
redirect_from:
  - /fest-mockito-aka-how-to-test-quickly-and-easily-your-swing-classes-8cc68648d458
---

Today I’ve used for the first time [Fest](http://fest.easytesting.org/swing/wiki/pmwiki.php) and I’m impressed, usually UI tests are slow and painful, the nice syntax of FEST helps a lot and the framework seems very fast to find objects on the UI components.

To add some more speed and test really only the interactions between Services Objects and UI components I’ve mocked out the service layer with [Mockito](http://mockito.org/), injecting all my services through dependency injection and then I let FEST to drive the UI.

That’s fast, easy and highly recommended.

Another quick note, I didn’t use Swing for ages, I found out that there’s a new [Swing Application Framework](https://appframework.dev.java.net/) out.. Well it helps a little, Swing API are still too complex to use (even C# is better…)
