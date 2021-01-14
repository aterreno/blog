---
title: "Database Options"
description: ""
date: "2009-04-21T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/database-options-249a3bbc50ad
redirect_from:
  - /database-options-249a3bbc50ad
---

I’ve been an ignorant for years, I’ve used hibernate, I’ve listened to DBAs, clients, architects and I’ve ignored all the persistence options available.

[My previous post](http://www.the-arm.com/2009/03/do-you-really-need-an-rdms/) was arguing the need of an RDMS, there are another two DB types missing from that list:

-   [Column Oriented Databases](http://en.wikipedia.org/wiki/Column-oriented_DBMS)
-   [Document Oriented Databases](http://en.wikipedia.org/wiki/Document-oriented_database)

[Hadoop](http://hadoop.apache.org/) and [MonetDB](http://monetdb.cwi.nl/%20) are two "popular" Column Oriented Databases, the first one is modelled on the [Google BigTable whitepaper](http://labs.google.com/papers/bigtable.html), the second one claims to be the fastest opensource RDMS, I found throught its website a link to the [Transaction Processing Performance Council](http://www.tpc.org/) page.

With not that much surprise on almost all the test of the TCP Oracle performs quite badly!

The more interesting database at the moment IMO is [CouchDB](http://couchdb.apache.org/%20), quoting from the home page:

> Apache CouchDB is a distributed, fault-tolerant and schema-free document-oriented database accessible via a RESTful HTTP/JSON API. Among other features, it provides robust, incremental replication with bi-directional conflict detection and resolution, and is queryable and indexable using a table-oriented view engine with JavaScript acting as the default view definition language.

> CouchDB is written in [Erlang](http://erlang.org/), but can be easily accessed from any environment that provides means to make HTTP requests. There are a multitude of third-party client libraries that make this even easier for a variety of programming languages and environments.
