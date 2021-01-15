---
title: "One year of serverless"
description: "I’ve joined Labrador exactly a year ago, time flies when you are working in an early stage startup!"
date: "2018-07-10T10:25:12.687Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//one-year-of-serverless-61bfc475b23b
redirect_from:
  - /one-year-of-serverless-61bfc475b23b
---

I’ve joined [Labrador](https://www.thelabrador.co.uk/) exactly a year ago, time flies when you are working in an early stage startup!

#### What did we build in a year?

[A Real-time Data Aggregation with DynamoDB](https://javame.netlify.app//real-time-aggregation-with-dynamodb-1d4c525a4154), we killed [WordPress](https://javame.netlify.app//a-serverless-alternative-to-wordpress-b55c628c71e2), and we [Visualise Everything we do or what our users](https://javame.netlify.app//visualise-all-things-82adc32bcf64) do with Kibana… We also built a few internal and external frontends with React.JS and some other little things… It’s too much to list it all, but I’ll blog soon about them.

#### Would I do it again?

The short answer is yes, the more complete answer is that Serverless enabled a fairly small team (two full-time full-stack developers, a full-time DevOps and code-as-much-as-he-can CTO) to build a pretty impressive end2end stack, from collecting IOT data, to showing the same data to the end users, a signup user journey and a bunch of internal tools for operations or management.

I think Serverless enabled us to work at the speed of ‘editing the code on the server’ without encountering the issues of that style of ‘programming’.

Once you have a Lambda done and a set of patterns on how to tackle your problems, it takes minutes to build something that scales, it’s cheap to run, it requires no maintenance.

As far as I can remember, the only ‘maintenance’ on our ‘oldest’ Lambdas was to migrate from Node 6 to 8!

The granularity of the Lambdas is key too: I would struggle to write such little code and run it on a microservices, perhaps I never worked in a project where Kubernetes was adopted in the right way, or perhaps it was too early, but running a company without having to worry about the servers it’s just brilliant, and a massive relief.

I am glad we ended up using Node: the intrinsic event-driven nature of the language, the beauty of ES6 helped us build an event-driven architecture where [everything is JS](https://javame.netlify.app//7-years-from-the-monoglot-blog-post-f13d9e776b14).

According to [IOPipe](https://www.iopipe.com/) we have 58 functions running in prod, I love these sort of screenshots, where are we going to be in 3,6,9 months? How many more functions?

That slow function on the right it’s pulling reports from Google…

We have right now 54 repositories on GitHub, that means that we created on average a new repo every week, how did I let that happen? ;)

undefined

Maybe we should start thinking about how to go [monorepo](https://trunkbaseddevelopment.com/monorepos/) for the next year…

#### How are we doing cost wise?

Our costs have remained pretty much flat

That’s right, our platform is insanely cheap to run, not only the maintenance costs but also the running costs themselves are pretty low, and so far it did scale well, while the costs have remained pretty much constant, the number of users has grown averaging +33% users every month.

Half! Half of the costs are VPN, the AWS ElasticSearch Cluster, a bunch of EC2 instances, the non-serverless bits of the architecture.

Sadly we can’t get rid of those.

While our users… Well, we had a steady growth!
