---
title: "wanna go fast? reduce your feedback loops"
description: ""
date: "2010-10-29T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/wanna-go-fast-reduce-your-feedback-loops-ced8be8b8edf
redirect_from:
  - /wanna-go-fast-reduce-your-feedback-loops-ced8be8b8edf
---

I did work for years using the full XP/agile stack on a daily basis, after all that experience I can now finally judge when to use a methodology and when it’s not the case.

In the last years I had more than once the impression that all the various tools that are supposed to reduce the lead time where actually slowing me down.

Now I am lucky enough to work in an environment that doesn’t force me to use any particular methodology or technology.

So, how is that possible that here we go live in weeks and not in months? What happened?

No CI.   
Yeah, we don’t use CI.   
How does it work?

-   Hire good developers, most of the times they will not commit&push crap
-   Keep your application simple, prefer having lots of small applications collaborating rather than having a monolithic huge application
-   Deploy live rather than on CI, that’s where the system really runs, not on CI, that’s where you will really understand if it’s broken or not
-   Integrate often. The fact that the CI runs for every commit doesn’t mean that you are integrating. Pushing live your changes is real integration
-   Failover on a previous version of the code/automatic rollback on the live system if the deploy breaks the application

Test but not that much.   
Profanity?

-   Hire good developers, most of the times they will write decent code without a test
-   Hire good developers, most of the times they will test themselves the code they wrote
-   Keep your code simple, as simple as possible. If a method is 3/5 lines of code and your code base is small it will be simple enough to change/maintain/evolve
-   Write a test when you start feeling uncomfortable, most of the times a <a href=”http://en.wikipedia.org/wiki/Read-eval-[http://en.wikipedia.org/wiki/Read-eval-print\_loop](http://en.wikipedia.org/wiki/Read-eval-print_loop)">REPL will be actually good enough to prove you are writing your code in the right way

Ok, what about maintainability and refactoring?

Let me tell you, refactoring is overrated.   
Maintainability is overrated.

Write your application as prescribed above, use some dynamic language that will help you going faster and as soon as you will be fast enough you will realize that if you are not happy with your code you can actually trash it all out and write it again from scratch, it will take you less time.

I’ve seen this working here, I am not talking bullshit.

I’ve seen in the past projects that should have taken weeks taking months with huge amount of wasted time spent fixing the build, fixing the selenium tests, maintaining hundreds of tests, writing non sense mocks tests, writing non sense tests.

You may have embraced change, now it’s time to embrace courage, be a fearless dev.
