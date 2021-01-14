---
title: "think different, think nosql"
description: ""
date: "2010-10-29T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/think-different-think-nosql-1f4ad2b1e9ec
redirect_from:
  - /think-different-think-nosql-1f4ad2b1e9ec
---

I just came across [this post](http://highscalability.com/blog/2010/10/28/nosql-took-away-the-relational-model-and-gave-nothing-back.html) from the high scalability blog.

I just want to say what the nosql movement gave me back.

We just finished writing a new application which visualizes pseudo realtime analytics information, it’s a web application, most of our analytics data is stored in hadoop, for this web app we decided to use mysql.

[Hive](http://wiki.apache.org/hadoop/Hive) wouldn’t be appropriate given its response time to execute a query (and lots of map reduce indeed), so we do get the data from hdfs on an hourly basis and store it in mysql.

After a quick spike on [hbase](http://hbase.apache.org/) we picked up mysql because we needed group by semantics, but at the same time we started using mysql in a different way, we don’t have any relations, we don’t do joins, we store our data as in a big table.   
So basically we use the best of both words: no relations but sql.

This db grows pretty fast, the application has been running fully operational live for less than a day now and the total db size (two tables) it’s 48GB.

Then, for once, I came out with a good idea, we split the big table in a dozen of other smaller tables, basically the analytics source regions, what before was a column and a where clause in our queries became just a suffix of the original table.

I’ve been strongly inspired by the way hadoop manages partitions.

In conclusion that’s what the noSQL movement gave me back: he made me think differently to common data problems.
