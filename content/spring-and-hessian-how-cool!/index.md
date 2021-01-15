---
title: "Spring & Hessian, how cool!"
description: ""
date: "2009-03-31T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//spring-hessian-how-cool-b45af3d22f24
redirect_from:
  - /spring-hessian-how-cool-b45af3d22f24
---

I’ve tried today to expose some of our services in our application service layer.

All those classes are simple POJOs, autowired with Spring.

I’ve chosen [Hessian](http://hessian.caucho.com/) for few reasons:

-   I never liked xml, soap, etc…
-   we need web services over http (so no RMI)
-   it’s very fast
-   we might need different type of clients connecting to the application (Hessian apparently supports not only plain old Java but also JavaFX, Flex, almost every decent popular programming language)

Well the modification to the code (I’ve changed a couple of xml files) took less than an hour.

You can find the instructions [here](http://static.springframework.org/spring/docs/2.5.x/reference/remoting.html#remoting-caucho-protocols), there’s nothing else I can add to that document, it just works.

Many people says that Java is death or will die soon but what Spring gives "to the masses" is still incredibly valuable and I found always very quick to implement a change in the code or make a big redesign of the codebase.

Lately I’ve been impressed by the [autowiring](http://wheelersoftware.com/articles/spring-autowiring-annotations.html) features and the [java config](http://www.springsource.org/javaconfig) new stuff.

Have a look, java is perhaps struggling but still not death.
