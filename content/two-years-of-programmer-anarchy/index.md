---
title: "Two years of programmer anarchy"
description: ""
date: "2012-08-20T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/two-years-of-programmer-anarchy-7f8a85ec4717
redirect_from:
  - /two-years-of-programmer-anarchy-7f8a85ec4717
---

Two years passed since [Fred George](http://www.linkedin.com/pub/fred-george/0/5b5/596) and I wrote the [Programmer Anarchy paper](https://www.dropbox.com/s/omqe86y4nu0z6uy/Leaner%20Programmer%20Anarchy%20v2.pdf?dl=0), in those two years Fred [went all around the world](http://www.infoq.com/presentations/Leaner-Programmer-Anarchy) explaining what was happening here at [Forward](http://www.forward.co.uk/) and meanwhile I was here experiencing the Anarchy. This blog post is a writeup of this last two years experience, what worked well, what worked less well. To start with, let’s call it with a different name, which doesn’t implies chaos and confusion, Anarchy is not a new thing in the agile world, many people refer at it as self-organising teams.

**When does it work well?**

It works well when the manager is absent or fully trusting the team. One of the main selling point of Fred Anarchy was the lack of managers in the picture. Well, some sort of business owner, idea creator still needs to be present. That person needs to fully trust the team, ideally needs to be an ex-developer. I never seen in my life a manager without a past in developing software that can trust and understand their team. I truly believe that the most performing teams have developers to lead them and drive the business, google apparently is one of those example. Brandon Keeper recently wrote about [Github anarchy](http://opensoul.org/blog/archives/2012/06/05/whats-it-like-to-work-at-github/).

**It works well with small teams**

I always loved the magic number of 5 developers per team and believed that is enough to build anything in the world. Sometimes you need to increase the WIP and have more developers, without some sort of leadership the team will lack focus and direction. Selforganising team it’s one of the facets of Agile. It’s not an arrving point, it’s not a silver bullet. It’s something to try as any other practise. I did found however that it requires experience and time to glue the team up together. If I go back in time with my memories, back in 2007, [the FM team was self organizing](http://db.tt/XsgLyEGe), but it took us few months before reaching that level of maturity when everybody knew what to do and how. We did reach at that level of self organisation leveraging pair programming, a solid, team owned code base, a kanban wall. We had a great agile project manager to help us focus and a great [tech leader](http://www.thekua.com/atwork/) who rather than leading was just coordinating us and helping us to climb the ladder of self organization.

**What I didn’t like / What didn’t work well.**

**Not Pairing.**

Assuming that you are a mature, highly skilled and performing team the code quality won’t fall down. What will feel down will be the knowledge sharing, you will need to introduce weekly showcases, increase artificially the communication inside the team.

**Polyglot anarchy.**

When I used to be a consultant I always suffered the lack of polyglotism in big enterprise companies. I had to be part of Forward to understand what full polyglot anarchy means. If you write your software in a new funky language, using a new funky application server in a new funky infrastructure you will have not only to maintain it but also to support it. And if the system has to be up and running 24/7 that may lead to some issues. Assuming that your sysadmins on support know everything from clojure to node.js, from golang to asyncronous javascript this choice is still pretty risky. The team should take responsability of keeping the system up and running, but on the long term having a whole team on call at night, day and holidays is not really feasable. I still don’t have a solution to this, I guess that the sysadmin should pair with the team, learn the caveats of any system built by the team itself. I also start to believe that fixing some constraints in the infrastructure is not such a big deal: let’s say everything will be built on the jvm, that would still give a decent choice to the teams, leaving some sort of consistency around the deployment and the live real time troubleshooting issues.

**No Iterations.**

I am not a big fan of Scrum and generally time boxed iterations, however, the human brain tends to forget the passing of the time, that’s why we have cuckoo clocks, bells towers and so on. Having iterations while releasing software helps you to realise that time is passing, helps you being more self conscious of the passing of the time. Having iterations creates a safe environment for other rituals such as: team dinners, retrospectives, one2ones with team members, feedback sessions. Most senior developers probably would have the concept of time passing always in the back of their mind, but again, why stopping having iterations if we will have, again, artificially set some dates on a calendar for having agile rituals? Without iterations it’s also hard to plan for slack, or [Golden Cards](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.23.2798&amp;rep=rep1&amp;type=pdf).

**No Estimations and no stories.**

I realised that moving a user story on the cardwall is a ritual that causes happiness, sense of completion. If Fred is right when he talks about the story tyranny it’s also true that without users stories (see [INVEST in Good Stories and SMART tasks](http://xp123.com/articles/invest-in-good-stories-and-smart-tasks/)) and doing continuous deployment the risk of having continuous requirements is pretty high. As a developer you are never done because there will be always something more to do, as a product owner you will never see the end, you will always add new features. People work in contexts and a context can be long as much as one year. When is the end of the context? Unknown. It’s hard to define done, impossible to estimate, adds way too much uncertainty to the work in progress.

**Standups.**

Knowing what the team is doing and if the team needs help is a well established right and duty of any team (not only in IT). If you walk in the morning at Forward these days between 9 and 10 you will see almost every single team standing up. Unless you are a team of 2 people the standup is a must have, and it’s such a little effort.

**No Tests.**

Well [Dan](http://dannorth.net/2011/01/15/on-craftsmanship/) wrote quite a bit around this area, the spike and stabilize and Liz replied to that blog post [here](http://lizkeogh.com/2012/06/24/beyond-test-driven-development/). Of all the practices I’ve abandoned in these last years tests is probably the one I missed the least. It’s still very dangerous to preach for stopping writing tests. Writing a lot of tests makes you become a better developer. Writing tests in most contexts is a must have.

**No Refactoring/Rewrite and write in micro services**

Without tests, writing the code in a dynamic language forced us to write small components and rewrite them instead of refactoring them. What in the past was a module in an enterprise application became a separate codebase talking with other components mainly in json. A part from obvious performance (if performance is important in your context) issues, I found this approach a little wasteful as well. Rewrite comes from lack of analysis (lack of user stories) and lack of correct design in the first place (lack of test driven development). I found more satisfying (and probably more effective) writing my software the first time “good enough” and then improving it step by step with refactoring. My brain works that way not only for coding. Imagine finding the optimal walking path from home to work, optimizing different things, sightseeing, traffic, pedestrian paths, shops you want to pass by. Refactoring is improving it every day. Rewriting is like coming back once every 3/6 months, for the first 3 months you will walk a shitty path, the next 3 months something better and so on. Rewriting it’s kaikaku while kaizen is refactoring. Again it all depends on the contexts, but, at least in my experience continuous refactoring is a pleasant activity while continuous rewriting is rather frustrating.
