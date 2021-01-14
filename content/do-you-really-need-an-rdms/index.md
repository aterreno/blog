---
title: "Do you really need an RDMS?"
description: ""
date: "2009-03-26T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/do-you-really-need-an-rdms-ac5af5f67a40
redirect_from:
  - /do-you-really-need-an-rdms-ac5af5f67a40
---

In the project where I’m working we are in the process of deciding for which tecnologies to go for, from the UI to the persistence layer.

Yesterday we had an interesting meeting about the persistence layer.

It ended up having a chart of three available tecnologies for storing our data:

-   [Triple Store](http://en.wikipedia.org/wiki/Triple_Store)
-   [Object Database](http://en.wikipedia.org/wiki/Object_database)
-   [Hibernate](http://www.hibernate.org/) / JPA

I never heard of triple store before and I found it quite interesting, apparently there’s an [Oracle 11g RDF](http://www.oracle.com/technology/tech/semantic_technologies/index.html) version to store triple stores, looking at the Oracle Web Site it seems like you need few patches and some hacks in order to "install" the stored procedures to enable the RDMS to perform RDF queries.

I’ve already had a look to [db4o](http://www.db4o.com/), but I’ve been impressed on the [whitepapers](http://www.versant.com/developer/resources/objectdatabase/whitepapers) from [Versant](http://www.versant.com/) (that owns db4o).

Hibernate and JPA are the default option, with their benefits and their well know cons.

Now, the point is not which tecnology is better than the others but which one is best for your project and having such a conversation/investigation at the start of a project it’s something I never done before.

We have some particular non functional requirments, like HA (five nines system), low latency, geografical clustering, complex computations and deep objects graphs so we a common stack probably might lead to big risks.

My current preference goes to Objects Databases but I’ll keep posting my findings on this blog depending on how the investigations are going.
