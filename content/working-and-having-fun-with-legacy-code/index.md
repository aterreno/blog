---
title: "Working and having fun with legacy code"
description: ""
date: "2006-12-06T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/working-and-having-fun-with-legacy-code-a391f647a7ad
redirect_from:
  - /working-and-having-fun-with-legacy-code-a391f647a7ad
---

A lot of collegues and friends told me to read [Working Effectively with legacy code](http://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052) and one of these days I’ll. In the meanwhile I’ve joined a project were we work with only legacy code and I’m having fun reading huuuge classes with huuuge methods, no patterns (only a lot of crap singletons!) and of course, no code coverage.

Why fun?

Cos we setted up some ant tasks: [CheckStyle](http://checkstyle.sourceforge.net/) to find out the hotspots of the application (ie where the code smells more!), [Simian](http://www.redhillconsulting.com.au/products/simian/) to find out the copy and paste on the code, and [Abbot](http://abbot.sourceforge.net/doc/overview.shtml) to perform automated funcional tests on the Swing GUI.

All together runs on [Cruise Control](http://cruisecontrol.sourceforge.net/).

Abbot is very very nice and powerful: you can record the user operation on the GUI, the test is written in xml and then you can run it from a Junit class. You can also write some “scripts”, means that you can write some java code and then put these expressions in your xml test.
