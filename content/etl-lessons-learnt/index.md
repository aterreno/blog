---
title: "ETL lessons learnt"
description: ""
date: "2011-02-13T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/etl-lessons-learnt-118dc264733a
redirect_from:
  - /etl-lessons-learnt-118dc264733a
---

The search team at [forward](http://forwardtechnology.co.uk/) does a lot of [ETL](http://en.wikipedia.org/wiki/Extract,_transform,_load), data is our daily business.   
Recently I wrote a script that:

1.  Collects some data from our Hadoop cluster
2.  Calls a 3rd party API via HTTP
3.  Pools the 3rd party API waiting for the requests to be processed
4.  Downloads and stores locally the result of the 3rd party call

I want now to share what I learnt writing this script.

**Drop OOD, think functional**  
I didn’t wrote a single domain object, I used just hashes, they comes from Hive, they get used to call the external API, the xml that comes from the API becomes an hash, the data gathered from there goes straight in Mysql as CSV.

I wrote the script in ruby, but I wrote few functions, the application is **Stateless but stageful**.   
There’s no state but every single stage status is saved in mongo.   
In this way the script can fail at any point but always recover in a consistent state and start again from where it did stop.   
Nokogiri does crash for a bug every noun when parsing the API request page where I get the current status of the 3rd party processing.   
**If anything can go wrong, it will**  
I didn’t care of fixing that bug or understanding why it does crash, the script will recover and try again till the parsing is successful.   
I don’t need to be fast, cos the 3rd party server is rather slow in processing our requests. Speed is not a requirement.   
Consistency is.  
The 3rd party server went down as well quite few times, for networking issues and load.   
I just keep polling and let the script fail on timeout, it will start again in a 10 seconds and try again.

**Forget about REST, the important stuff is the rest**  
Data is the important bit, not the way you get it. The URL provided by the 3rd party is not rest, so what?   
What I care about is the Data that they give to us. Being rest or not won’t change my life, the value is in the content not in the transport.  
**RTFM**  
Read the fucking manual.   
I actually spent more time tuning/troubleshooting MySql (where I store the data) rather than writing the script, that deserves a full separate post, but the point is: read the manual, read the manual page till the end.   
**Drop frameworks**  
I use Sequel for the DB connectivity but I just use it to efficiently get the connection to the DB, I actually use plain SQL so that at least I know what’s going on, when you start having tables with 80 Millions rows you better start being careful about what’s going on.

**In conclusion, the funny bit is that web application are ETL too :-)**  
What I wrote is valid for writing web applications too.

The wikipedia page says:

The typical real-life ETL cycle consists of the following execution steps:

Cycle initiation  
Build reference data _(think about populating drop downs, static data)_  
Extract (from sources) _(user input)_  
Validate _(validate user input)_  
Transform (clean, apply business rules, check for data integrity, create aggregates or disaggregates) _(business logic)_  
Stage (load into staging tables, if used) (store)  
Audit reports (for example, on compliance with business rules. Also, in case of failure, helps to diagnose/repair) _(analytics, audit)_  
Publish (to target tables)  
Archive  
Clean up
