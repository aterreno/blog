---
title: "Some (N)Hibernate Learnings"
description: ""
date: "2008-02-12T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/some-n-hibernate-learnings-7d83fe88df2c
redirect_from:
  - /some-n-hibernate-learnings-7d83fe88df2c
---

After at least two years of Hibernate and NHibernate experience I can say that I know what’s going on, I can’t still say that I know very well (N)Hibernate but I wanna share some learnings.

-   The logger is your best friend:  
    When sometimes goes wrong, the logger (or at least a profiler) will help you, it’s awesome to play with a database like we play with objects but I have the feeling that sometimes we forget that on a couple of layers below we are doing some good old SQL!
-   (N)Hibernate is not meant for:
-   Bulk data manipulations: use [sqlBulkCopy](http://msdn2.microsoft.com/en-us/library/system.data.sqlclient.sqlbulkcopy.aspx) in (.net) or upgrade to a version > 3.1.1 on Java Hibernate
-   Free developers from understanding the database: it’s nice to hide the DB structure but the DB is there, and it’s not OO!
-   Free developers from understanding (N)Hibernate.   
     I sow many times in developers this approach: entusiasm followed by criticism followed by hate :-) It’s very easy to do simple things and terrible then to fix bugs or understand some stack traces. It’s a great library and it’s not easy to use. A copy of [hibernate in action](http://books.google.com/books?q=hibernate+in+action&btnG=Search+Books) or of [nhibernate in action](http://books.google.com/books?q=nhibernate+in+action&btnG=Search+Books) should be always present in a team playing with it.
-   Let you forget the profiler: as mentioned before it’s the best way to understand the complexity of your queries, it’s easy to end up with a cartesian product result from a query or execute unuseful queries, especially when playing with multiple joins and criteria queries.
-   Do not generate queries using dynamic strings: queries compilations are cached (similar to query plans), it’s a nice and useful feature, especially talking about performances. Use parameters to allow reuse of query plans.
-   Lazy loading: if you don’t use lazy loading (default now) you’ll end up having all the DB in Memory, if you use lazy loading you might have the select N+1 problem…
-   Usage patterns: session per request (good for webpages, opening the session on request start, dispose on request end) Vs the session per conversation, good for rich client application. I’ve the impression that in this second case you loose a lot of the hibernate power…
-   Bags, lists, sets… : choice is yours but keep in mind that especially in a domain driven design you could have some problems having methods playing with (lazy) collections in the POJO/POCO objects. And the cost of changing from one mapping strategy to a different one can be high.
-   Optimization: you’ll have performance problems, it’s sure, you’ll have it, I don’t believe in preemptive optimization but an eye on the profiler and one on the integration tests timings could help you to find earlier problems that you’ll see otherwise when it’s too late (i.e. in production!)
