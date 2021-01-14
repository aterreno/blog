---
title: "Embrace Quality, use Sonar"
description: ""
date: "2009-04-08T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/embrace-quality-use-sonar-2bd0a12daa81
redirect_from:
  - /embrace-quality-use-sonar-2bd0a12daa81
---

> [Sonar](http://sonar.codehaus.org/#) is a code quality management platform, it enables to collect, analyse and report metrics on source code. Sonar not only offers consolidated reporting on and across projects throughout time, but it becomes the central place to manage code quality.

I’ve been using Sonar for the last couple of months and I’m positively impressed with it.

It’s very easy and quick to setup (I use Sonar from an [Hudson](https://hudson.dev.java.net/%20) build, in a Maven 2 project) and it offers a very clear and attractive overview of the project code.

The time machine feature tracks the metrics of the project, enabling the team to track progress and improvments.

It’s a separate server, so your build doesn’t slow down to produce the reports, Maven launches it transparently.

It hogs quite a lot of memory (around 300Mb) and we had an out of memory recently (after upgrading to the latest version) but it’s really a must have tool on your project.
