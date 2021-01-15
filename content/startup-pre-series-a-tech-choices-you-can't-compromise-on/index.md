---
title: "Startup Pre-series A tech choices you can’t compromise on"
description: "If you spent any time in an early stage startup you know what it’s like, it’s a rollercoaster of we are going to make it, we are killing…"
date: "2019-02-06T12:54:25.617Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//startup-pre-series-a-tech-choices-you-cant-compromise-on-a499a75f3f06
redirect_from:
  - /startup-pre-series-a-tech-choices-you-cant-compromise-on-a499a75f3f06
---

If you spent any time in an early stage startup you know what it’s like, it’s a rollercoaster of we are going to make it, we are killing it, oh no, we are not.

Investing time (and therefore money) into certain practices and tools might be a choice you can’t afford at this stage.

So here is what we did at [Labrador](https://thelabrador.co.uk), in my first year and a half, indeed it’s all very context based, but I think some choices are universal and so basic that you can’t get away with.

---

**Limit your infrastructure as much as you can and for the little that you’ve got to build automate it**

We embraced [serverless](https://serverless.com/) and it’s a choice that has been paying off, the learning curve it’s flat, the speed of going to production without worrying about the necessary infrastructure or service discovery beats any other technology I’ve used before, however, some third-party integrations require ‘real servers’, we used [Terraform](https://www.terraform.io/) to build those, even if we barely touched them in the last few months, it’s a must-have safety net that I would never compromise on: applying security updates, upgrading the OS, rebuilding the instances on AWS when necessary has been a piece of cake: no dramas, no panic mode because you have no time.

I’ve asked myself a few times, would we have been better off with a monolith? What if instead of 150~ lambdas we’d be working on a Rails/Django monolithic application? I think we’d probably been just as fast, but this goes into my next point

**Don’t worry too much about code quality, what is good today might be trashed tomorrow**

We copied and pasted, we didn’t write many tests, the good things about lambdas (as it’s for microservices but here we are at the ‘nano-services’ size) it’s that it’s easy to trash something and rewrite later. We limited homegrown npm packages (not enough!), architectural dependencies between lambdas.

In my consulting career, I had to deal way too many times with monolith apps which grew and grew and grew to the point it was impossible to replace areas of functionality, lambda-coding forces you to decouple.

Now you’ll think, you are a reckless cowboy, but this goes into the next two uncompromisable values: operability and architecture.

**Build operability from day zero**

> Operability is the ability to keep an equipment, a system or a whole industrial installation in a safe and reliable functioning condition, according to pre-defined operational requirements. [Wikipedia](https://en.wikipedia.org/wiki/Operability)

For us this implies using [IOPipe](https://www.iopipe.com/) on all our lambdas, implies always set up at least one alert in both non-prod and prod environment for every new lambda.

Serverless Architectures are complex, highly distributed systems, with eventual consistency baked in, I would say that there is also eventual correctness of the system: if you think that your system is behaving correctly because you wrote a bunch of tests, bless you but you are so wrong!  
Troubleshooting time is precious, investing in tracing, logging, centralised monitoring has been very valuable for us.

**Hack in the small but architect in the large**

Back at [Equal Experts](https://www.equalexperts.com/our-people/our-values/?=technical), we came up with [a value](https://www.equalexperts.com/our-people/our-values/?=technical) that still sits strongly in my head

> _We value overall simplicity over localised simplicity_

I think we did our best to design a resilient system, with lambdas loosely coupled (in fact no lambda calls another lambda in our system, it’s (or it was!) an unwritten rule. We invested in building an event-driven system, we can replay events and re-build our data if an unexpected condition happened (and trust me, it will happen, [Murphy Law](https://en.wikipedia.org/wiki/Murphy%27s_law))

As much as we value freedom and empowerment overall simplicity this also implies no polyglot, no multi-cloud: we love AWS, Node.JS and React: those are our weapons to turn business goals into software, we strive to minimise third-party tools and SaaS accounts to build, run, monitor our systems.

For everything else, I can only quote [Scout24 IT Principles](https://github.com/Scout24/scout24-it-principles), which I respect, admire and try to implement as best as I can here as well.

**What do I think it’s next?**

Hard to tell, and subject to change, but we need to invest in anomaly detection, centralised logging and potentially invest in automated tests, especially for the front-end codebase.

We recently started looking at [Puresec](https://www.puresec.io/) to secure our lambdas and we integrated into our ci/cd [this excellent library](https://github.com/Yelp/detect-secrets) from yelp to make sure ‘secrets’ don’t flood into the codebase.

We worked on an almost-no process, Trello/Kanban/Just in Time Requirements but we might need to start introducing more agile practices, we are not anymore 5 people sitting on the same desk, but growing fast, currently counting a total of 20 people.
