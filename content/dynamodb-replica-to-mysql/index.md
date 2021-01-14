---
title: "DynamoDB replica to MySQL"
description: "DynamoDB might not be good for everyone, but after almost six months of usage at Labrador I am so far pretty happy with it."
date: "2017-12-15T16:10:46.060Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/dynamodb-replica-to-mysql-8563cd2ac6b8
redirect_from:
  - /dynamodb-replica-to-mysql-8563cd2ac6b8
---

[DynamoDB might not be good for everyone](https://read.acloud.guru/why-amazon-dynamodb-isnt-for-everyone-and-how-to-decide-when-it-s-for-you-aefc52ea9476), but after almost six months of usage at [Labrador](https://www.thelabrador.co.uk/) I am so far pretty happy with it.

I often hear that one of the downsides of Dynamo is querying: indeed, you will need to design your keys carefully but you can also copy the data over a second store to run ‘traditional’ aggregations.

That’s what we did, we evolve constantly a dynamo NoSQL schema, but we propagate certain fields and their data(which are more stable) downstream to a MySql database.

That way we can query and run reports (we use the excellent [Redash](https://redash.io/)) on MySQL, if you can afford it you can propagate the data over to [Redshift](https://aws.amazon.com/redshift/), or now AWS made things even simpler and you can run [Aurora Serverless](https://aws.amazon.com/rds/aurora/serverless/).

The code is pretty straightforward, a Lambda listens to the DynamoDB stream and runs the necessary SQL to Create/Update/Delete the data in the MySQL database.
