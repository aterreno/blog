---
title: "The Practice of Continuous Testing"
description: "On my last project at Equal Experts I came up with the idea of continuously testing our client production systems: the aim is, on top of…"
date: "2017-06-23T13:58:04.199Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/the-practice-of-continuous-testing-95a37f77ffd8
redirect_from:
  - /the-practice-of-continuous-testing-95a37f77ffd8
---

On my last project at [Equal Experts](https://www.equalexperts.com/) I came up with the idea of continuously testing our client production systems: the aim is, on top of the usual classic agile testing techniques, to test in production that a new software replacing a legacy system behaves similarly.

We built a set of APIs which gather data from the legacy, on-premises system in an asynchronous fashion: queues, workers: a quite classic way to replicate data from old to new systems.

When data flows like that and consistency diminishes it’s very easy to loose track of what is working and what not.

Plus, the reality is that you can unit test as much as you like but you will know only with daily, fresh, real production data how the new software will behave.

In my experience, when data has been hidden for years in ‘obscure’ system and finally sees the light thanks to monitoring and logging people start worrying, the new system gets blamed for serving the wrong data, while actually, the problem might be at the source.

We had no visibility whatsoever of our source data, the on-premises legacy system (which will run in parallel with the new system for years) is a complete black box.

My solution was to implement a script, to run on a regular basis (ideally I’d run that continuously, 24/7) to check new vs old: we do scrape a website and compare some key values with what we return from the newly created API.

Discrepancies should be tolerated, but only up to a certain point and what is more important is to check that the percentage of failures doesn’t rise, the trend needs to be monitored, not the absolute numbers.

Often these test can’t be fully comprehensive because of the size of the dataset, so a random subset of it should be cut out, again, it’s all about trends and to make sure the new system is improving the consistency and the correctness of data.

A report can be as simple as this:

Products Found on Internal API: 6779   
Products Not Found on Internal API: 105   
Prices which are not found: 27   
Prices which didn’t match: 4   
Etc.

Our implementation runs every day on Jenkins, producing an HTML report, checking everyday something like 50k products.
