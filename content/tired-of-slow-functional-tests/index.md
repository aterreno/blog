---
title: "Tired of slow functional tests?"
description: ""
date: "2008-11-12T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//tired-of-slow-functional-tests-d05fd64eee
redirect_from:
  - /tired-of-slow-functional-tests-d05fd64eee
---

If you are a good QA or just a good agile developer I’m sure you’re already testing your web applications with tools such as [Selenium](http://www.openqa.org/).(\*)

If you’re seeking for continuous improvement I’m sure that you complained at least once on the speed of those testing and on the maintainability.

You might wanna then have a look on the results that the guys of [Celerity](http://celerity.rubyforge.org/) have posted on their website, basically they migrated all their [Watir](http://wtr.rubyforge.org/) functional tests wrapping [htmlUnit](http://htmlunit.sourceforge.net/) instead of starting the browser through Watir.

First [benchmarks](http://celerity.rubyforge.org/benchmarks.html) are impressive:

ScenarioWatir (total)Celerity (total)Time reduction1316,97 s0,59 s99,81 %2278 s86 s69 %3128 s33 s74 %4185,00 s4,67 s97,48 %  
If you are using Selenium rather than Watir don’t despair, [Simon Stewart](http://www.pubbitch.org/) is working hard on [webdriver](http://code.google.com/p/webdriver/), and if you switch to the [htmlUnit driver](http://code.google.com/p/webdriver/wiki/HtmlUnitDriver) your Selenium test you’ll have comparable improvements on the speed of your tests.

(\*) many people might disagree with this sentence, if so have a look first the Simon Stewart [presentation at GTAC 2007](http://uk.youtube.com/watch?v=tGu1ud7hk5I) and then let me know your thoughts.
