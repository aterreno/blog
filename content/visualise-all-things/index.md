---
title: "Visualise all things"
description: "At Labrador, we love DynamoDB and we also love its Streams, no doubt about that, one of the most recent usage that we implemented is a sort…"
date: "2018-06-05T20:18:27.691Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/visualise-all-things-82adc32bcf64
redirect_from:
  - /visualise-all-things-82adc32bcf64
---

At [Labrador](https://www.thelabrador.co.uk/), we love [DynamoDB](https://aws.amazon.com/dynamodb/) and we also love its [Streams](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html), no doubt about that, one of the most recent usage that we implemented is a sort of replica of our ‘master user data’ into [ElasticSearch](https://www.elastic.co/).

DynamoTables to Elastic Search Indexes Via Streams

Every time a CRUD operation happens in a Dynamo Table, the stream propagates the event to a [Lambda](https://aws.amazon.com/lambda/), which consumes it pushing the data over to the Elastic Search Cluster.

The first goal of this architecture was to enable a full text search for our bespoke CRM application (a React.JS app running on S3/Cloudfront and powered by some APIs built with the [Serverless Framework](https://serverless.com/)).

Map of our Users (Taken from Kibana), at time of writing we have more than 100 visualisations and eight dashboards…

We quickly started enjoying querying and visualising our user data, in order to improve our service, CTR, CPA and LTV.

The power of aggregating data inside Elastic Search also gave us functionalities inside our CRM such as counting, fine grained filtering: it became very easy to add these features.

#### What we learnt

-   It’s dead easy to replicate 1:1 Dynamo Table to ES index, but doing aggregate objects is more tricky: we have tons of events and our architecture is rather [reactive](https://www.reactivemanifesto.org/), that makes it hard to predict race conditions: you need to build your domain objects the more immutable as possible
-   Lambdas inside a VPC work fine (for security reasons our ES cluster is inside a private VPC) but you need to watch out for outbound connectivity: we use [IOPipe](https://www.iopipe.com/) for monitoring and alerting and that needs outbound connectivity: we have use NAT gateways (we are actually in touch with them to find a workaround to this by peering our AWS account)
-   Migrations are fine now (between DynamoDB and ES) but they will be a problem sooner or later, we might have to investigate clever ways of resetting an ES cluster from scratch with production data
-   ES running on AWS might have few limitations (such as no login/security option) but it really rocks, it’s basic but despite running on the smallest size available the performances are amazing, way better than any bespoke ES cluster I’ve seen before in my career
-   NoSQL rocks: nothing new, but we are at early stage in the architecture and requirements keep changing, it would have been a nightmare using static types, a non dynamic language and not using JSON for storing our data across all data stores
-   ES and DynamoDB are great but sometimes you need SQL: we also leverage [Athena](https://aws.amazon.com/athena/) for doing some ad-hoc queries on our data stores
-   ES empowers us also to ingest data and reports from other 3rd party sources, such as Google Analytics: it really give us an holistic end to end view on how we are doing
