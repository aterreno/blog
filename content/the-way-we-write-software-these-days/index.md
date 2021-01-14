---
title: "The way we write software these days"
description: ""
date: "2010-11-28T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/the-way-we-write-software-these-days-ea1820f3345f
redirect_from:
  - /the-way-we-write-software-these-days-ea1820f3345f
---

In [my previous blog](http://www.the-arm.com/2010/11/agiler-at-forward-and-successful-at-the-iad10/) post I did write about most of the conversations and feedbacks I’ve got after the Italian Agile Day.   
In this one I want to address the software design.

**Rewrite preferred over Refactoring**

As I said during the speech we don’t do that much refactoring anymore and we rather throw away the code and rewrite it from scratch.   
[Paolo Polce](http://twitter.com/paolopolce) said more or less something like this:

> “You guys are good and write good enough code already, that’s why you need less (or none) refactoring”

It’s probably true, he gave me a good explanation, from a scale from zero to ten we probably write code that is already a six or a seven, so there’s little need for refactoring.  
I’ve to say that we do refactor a bit, especially when a new feature comes in or when we re-open the code base after a week or more.   
The big difference is that if we don’t like it at all anymore, if there are some code smells, if the code is resistant to change we just rewrite it.   
Also, one type of refactoring we do often is to reduce the codebase size.   
I truly believe that the main goal of refactoring should be keep the codebase small.   
I had a chat with [Mike](http://michaeljon.es/) the other day and I found that he’s doing the same thing in his team, he keeps trying to keep a part of his code base under 200 lines, even if they are adding new features.   
I used to be obsessed in writing small classes and small methods. Let me tell you, that’s just nothing compared to writing small modular applications.   
Also, small classes and short methods too often imply huge codebases: it’s hard to understand the intent of a system when its intent is scattered through hundred of files.

**Bounded Contexts**

We do use bounded contexts and this helps to keep the applications simple, easy to change, to rewrite when needed.   
It does allow us to use the right tool for the job (picking up node.js or clojure or plain ruby) for the task.

**Aggregation**

Talking with ziobrando after the conference I’ve realized that we implement in most of the projects [aggregates](http://domaindrivendesign.org/node/88), as DDD defines them:

> Cluster the Entities and Value Objects into Aggregates and define boundaries around each. Choose one Entity to be the root of each Aggregate, and control all access to the objects inside the boundary through the root. Allow external objects to hold references to root only. Transient references to the internal members can be passed out for use within a single operation only.

Using noSQL helps a lot. But we implement it also with mysql.   
The key is to throw away all the frameworks and the patterns that dominated the market of the last 5/6 years: we don’t use Sequel Models, we don’t use (rails) Active Records. Most of the time we don’t even write domain objects, we just use hashes.   
In functional programming this is definitely easier to achieve, however, in ruby you can obtain pretty good results as well.

**Blue Green Deployment**

The way we deploy our code to production has been well explained by Martin Fowler in [this blog post](http://martinfowler.com/bliki/BlueGreenDeployment.html).   
I admit I didn’t know the name of this technique, I was just using it. Thanks again to [ziobrando](http://twitter.com/ziobrando) for suggesting me the name!

**DSLs preferred over Patterns**  
As I said in the presentation I can’t remember the last time in the last six month that I did introduce or use a pattern in my code.   
We do use tiny frameworks and DSLs rather than patterns. I think that this is the way to go.   
Sinatra is a brilliant dsl for writing web applications, haml is a lovely dsl for writing html, sass is a brilliant dsl to write css, capistrano, rake… It’s all about dsls.
