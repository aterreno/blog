---
title: "What’s really agile?"
description: ""
date: "2009-02-02T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/whats-really-agile-ae82ecb7fb31
redirect_from:
  - /whats-really-agile-ae82ecb7fb31
---

Today we ended a scrum sprint, two weeks long.

In two weeks a team of five developers managed to setup a project using state of art tecnologies such as [DRW](http://directwebremoting.org/), [ActiveMQ](http://activemq.apache.org/), [ServiceMix](http://servicemix.apache.org/home.html), Hibernate, Spring, [Atomikos XA Transactions](http://www.atomikos.com/Main/ProductsOverview).

Not only we have a use case up and running and we are able to show case it to the customer.

Now, few choices in my opinion made this “more agile”.

-   The usage of [Maven](http://maven.apache.org/), we have probably 50 dependencies, I can’t imagine how to handle this with ant.
-   The usage of [Hudson](https://hudson.dev.java.net/) as CI tool, simple UI, no need to read the manual
-   The usage of [Spring](http://www.springsource.org/), in a couple of hours we had all we need (DAOs, JMS senders and receivers especially)
-   The usage of [Hibernate3](http://www.hibernate.org/) with annotations, can’t be faster to write down your domain
-   The usage of [Jetty](http://www.mortbay.org/jetty/) to have a fast feedback locally
-   Well, ovious maybe but worth mention, we wrote tests first, we used [Junit4.5](http://www.junit.org/)
-   Flexible pair programming, we paired only when in trouble or when we felt the solution was mature enough to be showcased and shared in the team
-   Focused work, one developer on the Web UI, one on the deployment, one on the ServiceMix/ActiveMQ, one on the Transactions + Design of the system

I call this agile, hard work and good fun.
