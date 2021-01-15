---
title: "How to automatically create CloudWatch alerts with CloudTrail, Lambda, and Serverless"
description: "At ChargedUp, we’ve implemented last year the pattern described by Yan Cui to monitor the Lambdas Powering our APIs."
date: "2020-03-19T10:41:18.520Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//how-to-automatically-create-cloudwatch-alerts-with-cloudtrail-lambda-and-serverless-62aca7bdac5b
redirect_from:
  - /how-to-automatically-create-cloudwatch-alerts-with-cloudtrail-lambda-and-serverless-62aca7bdac5b
---

At ChargedUp, we’ve implemented last year the pattern described by [Yan Cui](https://medium.com/u/d00f1e6b06a2) to [monitor the Lambdas Powering our APIs](https://medium.com/free-code-camp/how-to-auto-create-cloudwatch-alarms-for-apis-with-cloudwatch-events-and-lambda-b128920857aa).

This week, I’ve decided to extend this to all our Lambdas, so right now we have a Lambda listening to [CloudTrail](https://aws.amazon.com/cloudtrail/) events, which gets triggered when any other lambda gets created or deployed.   
The code to achieve this is remarkably small and simple, what took the most time was to understand CloudTrail events (there’s more than a thousand of them), in order to figure which ones I should subscribe to I’ve queried the CloudTrail logs with Athena.

```
SELECT DISTINCT eventname
FROM cloudtrail_logs_chargedup_cloudtrail
```

I won’t go through how to set up CloudTrail in your account, but for instance, [the Terraform documentation is quite clear](https://www.terraform.io/docs/providers/aws/r/cloudtrail.html), check that out, for example, you can enable CloudTrail only for Lambdas with this TF code:

undefined

The events I am interested in are only: **UpdateFunctionCode20150331v2**, **CreateFunction20150331**: unfortunately, it seems like AWS uses versioning for these sorts of events, so this code might break in the future when the version will increase.

This serverless.yml code snippet would do the job:

undefined

And the handler will look like this:

undefined

The function **publishEventToSns** will publish on an SNS topic triggering a Slack message on our dedicated channel, the other function will generate a put request for CloudWatch to create an alert when an error in the lambda occurs.

Even if we are using [Epsagon](https://epsagon.com/) for our monitoring I find this a very valuable safety net, if somebody deploys from their machine a lambda we will know (vs a [CircleCI](https://circleci.com/) deploy) and if a lambda is not configured with the Epsagon plugin starts to fail we will be notified.

There are so many events including invocations and throttles, meaning that if you have some time you can actually quite cheaply implement a complete observability/monitoring solution for all your lambdas.

You can have a proper look at all of these code snippets [here](https://gist.github.com/aterreno/940c686c8fc409f39a8ec60b16d35bff).
