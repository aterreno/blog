---
title: "Promote environments not artifacts"
description: ""
date: "2010-04-05T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/promote-environments-not-artifacts-3564d0a209ee
redirect_from:
  - /promote-environments-not-artifacts-3564d0a209ee
---

Lately I’ve been working quite a lot with environments and release issues.

On my last project we had eight environments: development, continuous integration, test, performance, pre-live and live plus a couple of demo boxes.

This over-engineered situation caused few issues but at the same time made me think and write this blog post :-)

**What we did to improve deployment**

Well, automation is the key, even if we are in a windows environment we wrote remote deployment scripts to do remote deploy in the machines using [psexec](http://technet.microsoft.com/en-us/sysinternals/bb897553.aspx) and [robocopy](http://technet.microsoft.com/en-us/library/cc733145%28WS.10%29.aspx).

We template our config files and we have one config per machine.

So far so good, old school good practices.

**What still doesn’t work**

Your software is done, finished, all the test are passing, unit and integration on the development boxes, acceptance on the CI box, the QA is happy in the testing environment and the product owners are happy on both of the demo boxes, the performance test team is happy on the performance box, the security team is happy with their tests executed on the pre live box.

But still your sofware may not work on live. Or most likely in any of those environments.

**Configuration is vital**

Your application without configuration doesn’t neither start or with a wrong configuration won’t log or work properly. There’s test coverage on all the aspects of your application but not on environment configuration. You may misspell a name of a server or simply forget that something is different from environment to environment. Your application won’t work as expected.

The configuration of the environment itself may cause serious problems. The most different your live boxes are from your test/integration/performance ones the higher is the risk that your software won’t perform as expected on the target servers.

**So, my humble recommendations**

_Move fast_

Moving fast is essential in any aspect of software development, when talking about releasing software is essential that you should be able to continuously deploy and redeploy in a repeatable stable way your application as fast as possible. Use remote scripts, even if you are not working with the cool kids in the ruby world do something similar to what [capistrano](http://www.capify.org/index.php/Capistrano) does.

Have a look on the [heroku](http://heroku.com/) website for a good example of moving fast…

_Reduce as much as possible the number of environments_

It’s clear that in the above example we have too many environments, if you have full control ask yourself why do you need them and just take them off. If an environment doesn’t produce any value it’s just a waste of time and resources. Environments can be recycled, most of the applications won’t need two demo environments and a performance environments available for the whole project life-cycle.

How would I cut down the number of environments on my previous example?

Development, continuous integration, test & performance, that’s it, four, it’s a 50% cut down!

A good rule is that your environments should be the same number of your story wall lanes:

1.  Story in dev > development environment
2.  Story dev complete > CI environment
3.  Story in test > test environment
4.  Story ready to sign off > performance environment

The performance environment can be used as stable build environment for showcases, demonstration of the software and indeed performance tests. But also for one last, more important thing, which is the whole point of this blog post:

_Promote environments not artifacts_

Imagine that you’re happy with you software, it has been signed off by the product owner and it’s performing well.

Probably you made some changes to the performance environment, maybe you started with a cluster of two machine and ended up with a cluster of four. Now you want to go live, but the live environment that you have is different, you may have some problems.

My idea is to promote the whole environment. You are probably using cloud computing or virtualization, just move this stuff to the live environment, clone it and you are done.

Promote the environment with the artifacts, all together.

Try to define your environments as executable scripts (in the \*nix world won’t be that hard) and version control these scripts with your environment configuration, the creation of the whole environment should be scriptable, repeatable and should evolve with your code.

[Mark](http://www.markhneedham.com/blog/) told me that [Chris Read](http://blog.chris-read.net/) has been talking about this stuff for years, you may want to check out his blog or his [presentations](http://www.slideshare.net/ChristopherRead/all-my-tests-are-passing-now-what), he’s anyway way much better than me explaining and making these things real.
