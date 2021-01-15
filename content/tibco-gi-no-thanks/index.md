---
title: "Tibco GI? No thanks"
description: ""
date: "2009-04-21T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//tibco-gi-no-thanks-ebd43b4ae61c
redirect_from:
  - /tibco-gi-no-thanks-ebd43b4ae61c
---

Recently we tried [TIBCO GI](http://developer.tibco.com/gi/), I’ve to say that I’ve not been particularly happy with it, here is my list of cons:

-   Not easy to test: impossible to test headless (is not supported by [htmlunit](http://htmlunit.sourceforge.net/)), impossible to test with [webdriver](http://code.google.com/p/webdriver/): Tibco provides a ["Test Automation Kit"](http://developer.tibco.com/gi/product_resources_gitak1.jsp), however we had to write an extension of [SeleniumServer](http://seleniumhq.org/) in order to be able to write SeleniumRC from java… Pretty bad!
-   It couples java, xml and javascript: yes it does, you write your objects in java, you configure them in xml and in the end you write some javascript that calls theirs java methods, a maintenance (and team on-boarding) mess!
-   Yet another tool: to edit the UI there’s no plugin for Eclipse, you’ve to use a TibcoGI tool to edit the UI… Pretty bad!
-   Small community: I found the community pretty small and completely unaware of the modern testing techniques (webdriver & htmlunit to start with)
-   XML, XSL and Javascript: at the end it’s all about these three technologies, all together, a scary combination.
-   Some browser are supported, some others.. No comment

Pros?

Well, you can write very quickly a pretty web interface but why not considering [flex](http://www.adobe.com/products/flex/) then?
