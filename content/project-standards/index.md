---
title: "Project Standards"
description: ""
date: "2009-05-08T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/project-standards-d451dec26d97
redirect_from:
  - /project-standards-d451dec26d97
---

I recently played a leadership role in a project where two of the biggest challenges where the time schedule and the team on boarding.

I hate repeating myself, so after explaining the technology, architectural choices a couple of times I decided to write some kind of document or presentation.

I’ve created a sample document containing for each of the areas of the project a paragraph explaining shortly all the decisions made so far.

The document has been then showcased to the whole team for feedback.

So, let’s see some part of the document, as example:

**Services** (A similar paragraph was written for each component of the architecture)

Why?

-   To decouple layers
-   To have isolated Transactionality

How

-   POJO configured with Spring (context-service.xml)
-   @Transactional annotation on any method call that requires Transactionality
-   @Service class annotation for Spring
-   @Autowiring constructor annotation for Spring
-   Completely stateless

References

-   Domain Driven Design

**Mock tests**  
Why

-   We want a fast feedback and test only objects interactions rather than effects
-   Test Double

How

-   Mockito framework to verify objects interactions
-   A Mock test should be written at least for
-   Services (mocking DAOs, JMS)
-   DWR Objects (mocking Services)

References

-   Mockito homepage
-   TestDouble page
-   Martin’s Mocks aren’t stubs page

And then for each major framework chosen, for **Spring** was something like:

Why

-   Lightweight solution
-   Easy to test out of the container (POJO beans)
-   Goes very well with DWR, Terracotta and Atomikos

How

-   Every bean is configured in a file called context-xxx.xml

References

-   Spring Vs EJB 3
-   New Spring 2.5 Features
-   Spring Reference Documentation

What about code conventions?

Ground rules

-   All fields private, information hiding
-   Reduce as much as possible private methods (usually the logic that sits in private methods can be extracted in another class), also a private method is not directly testable by unit tests.
-   use composition rather than private methods or utility classes, with composition every object can have isolated responsibilities and isolated own test
-   Methods, variable, package, class names should be speaking and tell to who’s reading the code what they’re there for
-   Avoid code smells, in particular:
-   DuplicatedCode
-   Methods too big
-   Classes with too many instance variables
-   Classes with too much code
-   Strikingly similar subclasses
-   An instance variable that is only set in some circumstances
-   Comparing variables to null
-   Too many private (or protected) methods
-   Many messages to the same object from the same method
-   ExcessiveOverloading
-   SameNameDifferentMeaning
-   Code not actually ever used
-   Classes with too few instance variables
-   Classes with too little code
-   Methods with no messages to self
-   Empty catch clauses
-   Explicitly setting variables to null
-   Comments
-   ExcessiveLogging
-   ContrivedInterfaces
-   LawOfDemeter Violations
-   SwitchStatements

and so on…

We got also a section on process, since everybody implements Scrum in its own way we highlighted our numbers:

For **Scrum** for example the list looked like this one:

-   Daily Stand-ups 9.30 AM
-   Two weeks long Sprints
-   End Of The Sprint Retrospective
-   Planning Game at the start of the Sprint
-   Product Backlog

References

-   Control Chaos Homepage
-   Any Mike Cohn’ presentation or article about Scrum
-   Any Mike Cohn’ presentation about estimating and planning

**Conclusions**

Documentation in Agile is often enemy number one, however, if you are planning to scale out your project you will need some help, Office tools are a bad beast, you can always write this type of ground rules on some cards and leave them on the wall (oh well, what if you offshore the project!).

This type of document helped me to do not miss anything, I kept it up to date with the code as soon as a new team member was joining it and I’ve got good feedback from the team (they liked the concise style and the references for further investigation).  
The client loved it too, finding out that we had a well defined stack of rules and process to follow, so no surprises.

Technical discussion were still allowed, the document wasn’t written in stone: every body in the team should feel free to criticise and then contribute to make the code/process better.
