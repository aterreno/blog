---
title: "TDA, test driven analysis"
description: ""
date: "2008-06-20T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/tda-test-driven-analysis-18ac580faeda
redirect_from:
  - /tda-test-driven-analysis-18ac580faeda
---

Recently one of our clients had a big problem on production, having to restart a critical application a couple of times in two days, with few hours of service outage.We have been asked to investigate where the problem was and in order to figure it out we wrote few tests around the legacy application.The finger was pointed to a Bash script launching a Java class that has been written in the past without any test coverage, as soon as we covered the code with tests we gave the unit test reports to the client analysts.The test methods names were of course specifying how the obscure code was behaving in the very common (at least inside ThoughtWorks) way

```
Should...()  

{     

   Given...     

   When...     

   Then...  

}
```

Test driven development is important not only to drive the design but also to have an executable, up to date documentation, if there’s a lack of tests I can’t think on anything better rather that writing tests around a legacy system in order to understand it and documenting it.
