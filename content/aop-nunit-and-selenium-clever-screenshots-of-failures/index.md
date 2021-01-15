---
title: "AOP, NUnit and Selenium: clever screenshots of failures"
description: ""
date: "2010-02-07T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//aop-nunit-and-selenium-clever-screenshots-of-failures-839dfed450e2
redirect_from:
  - /aop-nunit-and-selenium-clever-screenshots-of-failures-839dfed450e2
---

Last week I did struggle finding out why a test was failing only on our Cruise box, only in the Cruise build.

I wanted to get a screenshot of each failing tests, and I think I found a clever solution: aop.

We already use [PostSharp](http://www.postsharp.org/) on our code base for logging, transaction demarcation and hibernate session support, so I wrote a simple annotation for our acceptance tests:

```
using System;
using PostSharp.Laos;

namespace Web.UI.AcceptanceTests
{
        [Serializable]
        public class ScreenCaptureAttribute : OnExceptionAspect
        {
                public override void OnException(MethodExecutionEventArgs eventArgs)
                {
                        SeleniumManager.Selenium.CaptureScreenshot(string.Format("C:\{0}.jpg", eventArgs.Method.Name));
                }
        }
}
```

Every time a test will throw an Exception Selenium will take a screenshot of the screen: pretty simple.

The only caveat is that it won’t work if Cruise is running as a service, and to get a decent result you’ll probably need to maximize the web browser windows.
