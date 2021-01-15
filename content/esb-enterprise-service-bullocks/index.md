---
title: "ESB = Enterprise Service Bullocks"
description: ""
date: "2009-04-29T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//esb-enterprise-service-bullocks-137b0776937f
redirect_from:
  - /esb-enterprise-service-bullocks-137b0776937f
---

As you can see from the title I’m not a big fan of Enterprises Services Buses.

I’m not the only one, [Jim Webber motivated already in these nice slides why](http://jim.webber.name/2009/02/22/c3350ec8-6342-4ed5-bea4-8be93d7f70c4.aspx), I’ll just add my impressions, as a newbie.

I’ve tried using [serviceMix](http://servicemix.apache.org/home.html) and I had a quick look to some other not OS vendors.

The first weird thing is that everybody is writing an [ESB](http://en.wikipedia.org/wiki/ESB), you got so many choices, even the Apache foundation has two ESBs: ServiceMix and [Synapse](http://synapse.apache.org/), must be an easy thing to write is so many companies are writing their own version: don’t assume knowing and writing code for one will work elsewhere!

The second very bad thing is maintenance. I had to change a little some JBI components written a couple of months ago, it has been painful, ServiceMix is all about XML configuration but you have no clue on what’s talking with who, which service is connected to what and why, you change a name and bang, nothing works anymore. Aweful.

You might buy one of those cool ESB (Oracle, Tibco, the list is long) offering a "nice UI" to drag and drop components, well I’m sceptical, never been a big fan of this type of tools (vendors too, to be honest).

Testability. Assuming that you care about testing how do you want to test this stuff? Writing long running integration tests?

I tried a little and I ended up pinging ServiceMix to understand if it’s up or not (it akes honestly ages to came up) and do some clever wait on JMS queues for messages in order to understand if the bus still works but hey… That’s not cool at all. It’s slow and breakes very easily.

Instead of an ESB you might consider the architecture proposed by Jim on the slides mentioned above, if that’s not enough (maybe you’ve got some syncronized JMS queues) you might try to have a look to [Scala](http://www.scala-lang.org/), I think (and I’ll try to write something more about it) you can write an ESB (only what YOU need, no XML, no bullshit) in a day or so with a couple of [Scala Actors](http://www.scala-lang.org/node/242).
