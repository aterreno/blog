---
title: "#monoglot architecture for the #win"
description: ""
date: "2010-03-22T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/monoglot-architecture-for-the-win-86bc010c61fb
redirect_from:
  - /monoglot-architecture-for-the-win-86bc010c61fb
---

I’ve probably spent too many nights up in North Wales recently and had way too many rants with [Mark](http://www.markhneedham.com/blog/) and [Chris](http://enginechris.wordpress.com/) , but if it’s true that initially I’ve been quite attracted by polyglotism now I can see its risks and the costs.

On the project where I am now we are using quite some different domain specific languages to build a trivial web application: C#, CSS, HTML, XML (at least in 3 different ways: nhibernate mappings, nant build, web config), ASPX, Javascript, SQL and unfortunately some TSQL store procedures.

We didn’t plug in any other fancy new thing, some F# or some [boo](http://boo.codehaus.org/), could be quite cool. Neither we write our acceptance tests using ruby and cucumber like [David](http://www.ilovemartinfowler.com/) and [Mike](http://mikewagg.blogspot.com/) are doing on their projects.

So, before starting to write this blog I did a search on google for posts taking about monoglotism vs polyglotism I’ve found a [a good one](http://blog.dhananjaynene.com/2009/09/the-best-amount-of-polyglotism-is-that-you-can-manage-successfully/) that references this other [good one](http://www.codecommit.com/blog/java/the-plague-of-polyglotism) criticizing polyglotism, so I am not going to criticize it, I want to think forward, what could be a good, general purpose language that will allow me to write an entire web application without having a pile of 7 or more books on the desk?

I’m quite intrigued by Javascript in these days.

Therefore I am trying to write something that uses only Javascript, server side and client side…

I’m looking at frameworks like [Sammy](http://code.quirkey.com/sammy/) (cheers Mark), at [Node.js](http://nodejs.org/) (Cheers [Duncan](http://duncan-cragg.org/blog/)), at [CouchDB](http://couchdb.apache.org/) for the persistence layer and at at the [JQuery haml](http://github.com/creationix/jquery-haml) plugin for the view layer (cheers Chris).

This is good seriously good stuff, the benefits on using only Javascript are enormous:

-   you can rely on a solid framework like JQuery on client side code and on server side (think about validation)
-   you can easily TDD your controller logic if JSON is the input and the output of your controllers
-   you don’t have to mess around with SQL and embrace the [NoSQL](http://nosql-database.org/) Movement
-   you can write event driven fragments of the UI leveraging node.js & on the fly generated html
-   you can easily cache JSON using any in memory cache provider and restful controller calls
