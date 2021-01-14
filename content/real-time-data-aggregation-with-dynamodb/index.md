---
title: "Real-time Data Aggregation with DynamoDB"
description: "One of the first things we had to address at Labrador was the data ingestion from our CADs (Consumer Access Devices), those devices, paired…"
date: "2018-07-09T10:43:55.793Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/real-time-aggregation-with-dynamodb-1d4c525a4154
redirect_from:
  - /real-time-aggregation-with-dynamodb-1d4c525a4154
---

One of the first things we had to address at [Labrador](https://www.thelabrador.co.uk/) was the data ingestion from our CADs (Consumer Access Devices), those devices, paired with a Smart Meter send instant energy consumption data every 10 seconds, it’s 24/7, and it just grows as our connected CADs userbase grows.

When designing a NoSQL data store I always start from the ‘_how will I want to read this data_’ question, so this is how our energy dashboard looks like:

Our Energy Dashboard

We wanted to be able to retrieve easily and fast the consumption for a day (hourly aggregation), for a month (daily aggregation), and yearly (monthly aggregation), we also wanted to show the user their instant power consumption, that data is not aggregated at all, and it’s the 10 seconds data I mentioned earlier.

After a few iterations and spikes, we ended up picking up what then became our ‘Swiss Knife’, DynamoDB.

The first idea was to use DynamoDB as I would use Redis, storing those data series in a key-value format, where the key is the index and it’s derived from the timestamp of the energy reading.

Then we figured out that streams would help, so what we did was creating a set of DynamoDB tables where data would just land pre-aggregated.

We don’t do any aggregation on the frontend, nor on the API, the data is pre-aggregated inside Dynamo after arriving from the IOT devices.

Data Waterfall using DynamoDB, DynamoDB Streams and Lambdas

The code is actually pretty trivial, we use [DynamoDB AWS client](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/DynamoDB/DocumentClient.html), it probably took more time to figure out the queries than to write the actual code, one of the major benefits of this approach is that Dynamo would dedupe redundant data at source, and the duplication of data won’t be propagated down in the ‘data waterfall’.

A few simple functions decide the key, we just use [moment.js](https://momentjs.com/) for formatting the indexes, once a document is saved on a table, the event gets propagated to the next aggregation level table, applying a function to calculate the index key.

Other parts of the UI, the ones at the top, require no aggregation at all, those UI Blocks are just a real-time view of what your Smart Meter would show, we have a separate Stream for that and the data gets overwritten every ten seconds on a separate Dynamo Table, in this case, the index is just the unique identifier of the IOT device.

### What did we learn

-   With IOT you should aggregate as close as possible to the device, at edge, sending data over and over it’s a waste of bandwidth/money, if we will ever implement a new solution for our CADs I’d aggregate at least half an hour of data there, at source, and then batch save to our cloud services
-   [Dynamo Streams](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html): it’s rare nowadays that we don’t write a lambda function that doesn’t listen to a stream
-   Dynamo never fails, and takes off a lot of the work that otherwise would be in code, in DevOps work, we didn’t have a single problem so far and the running costs are pretty low
