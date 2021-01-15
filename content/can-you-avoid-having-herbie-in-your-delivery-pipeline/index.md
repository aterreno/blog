---
title: "Can you avoid having Herbie in your delivery pipeline?"
description: "If you did read the Goal from Eliyahu M. Goldratt you will remember Herbie:"
date: "2018-01-01T19:01:01.507Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//can-you-avoid-having-herbie-in-your-delivery-pipeline-f3377ca21f1b
redirect_from:
  - /can-you-avoid-having-herbie-in-your-delivery-pipeline-f3377ca21f1b
---

[**The Thriller That Will Teach You How To Manage a Factory**  
_When I began to gather information for this series on operations management, I asked a few business-school professors…_www.slate.com](http://www.slate.com/articles/business/operations/2012/06/the_goal_eli_goldratt_s_gripping_thriller_about_operations_theory_.html "http://www.slate.com/articles/business/operations/2012/06/the_goal_eli_goldratt_s_gripping_thriller_about_operations_theory_.html")[](http://www.slate.com/articles/business/operations/2012/06/the_goal_eli_goldratt_s_gripping_thriller_about_operations_theory_.html)

If you did read [the Goal](https://en.wikipedia.org/wiki/The_Goal_%28novel%29) from Eliyahu M. Goldratt you will remember Herbie:

> "The fat kid is the bottleneck! The fat kid is the bottleneck!" And indeed, once Alex realises this, he sees that the group as a whole can only move as fast as poor little Herbie, the chubby scout who’s clogging things up in the middle of the line.

Can you avoid having Herbie at all in your delivery pipeline?

After moving super fast at [Labrador](https://www.thelabrador.co.uk/) for a few months, by leveraging serverless and ‘friendly’ 3rd party API integration we had to integrate with an ‘old school’ system.

Suddenly I felt all the pain of my years as a consultant: waiting weeks (in fact a month) for HTTP ports to be open on their systems, IP whitelisting, HTTPS certificates to be exchanged, conf calls talking about XML, SOAP, sftp.

It was like a sports car ending up in mud, couldn’t use serverless, so go and test the end2end integration with a server.

Everything still automated, infrastructure as code, cloud, but at the speed of a Herbie.

Would I put this piece of work at the top of the line? Hell no, it would slow down my entire pipeline.

I think that in a startup context, certain type of integrations should just be avoided.

People often talk about focus into time to market in a startup context, but I never realised that TTM is also constrained by your technical decision, the integrations that you pick.

A well designed API, a modern, cloud friendly, stateless integration makes a huge difference on your time to market, any other more antiquate integration should be picked up only if there’s no alternative and if that integration is essential for your business to strive.
