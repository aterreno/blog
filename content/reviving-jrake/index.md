---
title: "Reviving JRake"
description: ""
date: "2008-09-18T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//reviving-jrake-64a2478ea858
redirect_from:
  - /reviving-jrake-64a2478ea858
---

The post about [the need of a new build tool](http://www.the-arm.com/2008/09/its-time-to-write-a-better-build-tool/) had many comments and reactions so I started, before coding something brand new, to search on the web for something to solve the current, well known build tools problems.

I found out that [Gant](http://gant.codehaus.org/) is pretty cool but then I started to search for something using ruby, rake and java…

And I found that back in 2006 [Martin Fowler](http://www.martinfowler.com/bliki/JRake.html) and [Mattew Foemmel](http://blog.foemmel.com/search?q=jrake) were already talking and working on this…

So I’ve sent an email to Mattew since his svn repository wasn’t neither working, I’ve got the code of his jrake and I’ve started [a project on Google code](http://code.google.com/p/j-rake/), the name, unfortunately is j-rake (another jrake project was already there).

I’ve just did the first check in, compacting the vendor folder on all the scripts. J-Rake in fact comes out with jruby, rake and all the libraries you need to compile and test your code.

The next small step will be to upgrade all the libraries to the latest version, then some more clean up and then writing more examples on how to write J-Rake tasks.

I’ve a very bad rake/ruby knowledge so any help/suggestion is more than welcome.
