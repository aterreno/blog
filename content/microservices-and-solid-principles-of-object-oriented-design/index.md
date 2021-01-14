---
title: "Microservices and SOLID principles of Object Oriented Design"
description: ""
date: "2013-09-30T10:39:44.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/microservices-and-solid-principles-of-object-oriented-design-fab2e0a6a2c7
redirect_from:
  - /microservices-and-solid-principles-of-object-oriented-design-fab2e0a6a2c7
---

I’ve taken the [Principles Of Object Oriented Design](http://c2.com/cgi/wiki?PrinciplesOfObjectOrientedDesign) from c2.com and tried to see how they fit describing [microservices](http://www.infoq.com/presentations/Micro-Services).

#### There are five principles of class design (aka SOLID):

1.  [Single Responsibility Principle](http://c2.com/cgi/wiki?SingleResponsibilityPrinciple)
2.  1.1. Each responsibility should be a separate microservice, because each responsibility is an axis of change.
3.  1.2. A microservice should have one, and only one, reason to change.
4.  1.3. If a change to the business rules causes a microservice to change, then a change to the database schema, GUI, report format, or any other segment of the system should not force that microservice to change.
5.  [The Open Closed Principle](http://c2.com/cgi/wiki?OpenClosedPrinciple)
6.  2.1 You should never need to change existing code or microservices: rather rewrite it.  
    This prevents you from introducing new bugs in existing code. If you never change it, you can’t break it. It also prevents you from fixing existing bugs in existing code, if taken to the extreme.
7.  [The Liskov Substitution Principle](http://c2.com/cgi/wiki?LiskovSubstitutionPrinciple)
8.  3.1 If for each microservice instance m1 of type S there is a microservice instance m2 of type T such that for all other microservices P defined in terms of T, the behavior of P is unchanged when m1 is substituted for m2 then S is a rewrite of T."
9.  [The Interface Segregation Principle](http://c2.com/cgi/wiki?InterfaceSegregationPrinciple)  
    4.1 The dependency of one microservice to another one should depend on the smallest possible interface.
10.  [The Dependency Inversion Principle](http://c2.com/cgi/wiki?DependencyInversionPrinciple)
11.  5.1 We wish to avoid designs which are:

-   Rigid (Hard to change due to dependencies. Especially since dependencies are transitive.)
-   Fragile (Changes cause unexpected bugs.)
-   Immobile (Difficult to reuse due to implicit dependence on current application code.)

#### Summarizing…

Principles 1, 4 and 5 have a direct translation, points 2 and 3 solved in OO by subclassing and extending is addressed by continuous rewrite.

#### Concerns

-   Continous Rewrite
-   Granularity of microservices
-   Maintenance
-   Monitoring
-   Deploy
-   Resilience

Stay tuned and I’ll address how to mitigate those in the next few posts.
