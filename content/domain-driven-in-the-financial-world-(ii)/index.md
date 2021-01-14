---
title: "Domain Driven in the financial world (II)"
description: ""
date: "2008-06-17T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/domain-driven-in-the-financial-world-ii-767e50b3e8b4
redirect_from:
  - /domain-driven-in-the-financial-world-ii-767e50b3e8b4
---

[Josh](http://grahamis.com/blog/) was right on his [comment](http://blog.java2me.org/2008/04/19/domain-driven-in-the-financial-world/#comment-9092) on my [previous post](http://blog.java2me.org/2008/04/19/domain-driven-in-the-financial-world/) about DDD in the financial world: we had a new requirement from the client: design a market simulator.

Basically our market simulator is a tool to parse the production logs, inject them into the application and verify that the behaviour of the application is correct. (A commercial tool called [VeriFIX](http://www.greenlinetech.com/products/verifix.php) does more or less the same job, but we need more flexibility)

It will be used when upgrading to newer releases and when installing a new instance of the Fix Routing Engine.  
It is end to end black box testing, with some reports to understand if everything is still processed by the Fix engine as it’s supposed to be.

From a new joiner on the Fix support team we had the request to show in the reports not the tag values for the processed fix messages but the description and (not a surprise) even a senior developer of the client was asking the same feature.

Looking then to the full picture we are always playing with the same object, the famous Fix message, with his near to 1000 fields but we use friendly tag descriptions on tests and code, tag numbers on the DSL: concise and quicker to understand by the Fix team and finally again tag descriptions for the Fix support team in the test reports.

Every context has its own language, even inside the same division, even in the same domain.
