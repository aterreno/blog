---
title: "Things about serverless I wish I used from the start"
description: "This list comes from the time ‘wasted’ going through multiple git repositories, changing, pushing, one by one all the serverless.yml file…"
date: "2019-02-22T16:57:22.988Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//things-about-serverless-i-wish-i-used-from-the-start-edd3841d6a95
redirect_from:
  - /things-about-serverless-i-wish-i-used-from-the-start-edd3841d6a95
---

This list comes from the time ‘wasted’ going through multiple git repositories, changing, pushing, one by one all the serverless.yml file, making ‘horizontal change’ across all functions: if I knew these things existed when I started, I would have saved myself quite some time

```
${ssm:variable}
```

You can use [SSM Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html) and it’s dead easy to use, no more hardcoded variables or secrets, those variables get expanded at build time by Serverless, we started to use them also for not-so-secret stuff, it’s nice to have a versioned, auditable repository with all those values in AWS.

```
versionFunctions: false
```

After a few months, we ran out of space on the [Function and layer storage](https://docs.aws.amazon.com/lambda/latest/dg/limits.html), which is by default 75 GB. I ended up writing a Janitor lambda function to remove all the non-live lambda deployments, but I much rather work with a always roll forward policy, so all our functions now are basically not versioned, something less to worry about.

```
logRetentionInDays: 30
```

Another parameter that you probably want to specify is the logging retention policy, this will avoid over cluttering (and overpaying) your Cloudwatch bill. 30 days is still probably too much, as we tend to fix whatever is wrong in less than 24 hours.

```
deploymentBucket:
    name: your-serverless-lambdas-deployments-bucket
```

Without setting this parameter things get a bit out of control with randomly generated buckets names, with this, all the deployments will end up in S3 in a nice and tidy structure such as serverless/{service-name}/{stage}.

```
plugins:
  - serverless-log-forwarding
```

We recently introduced centralised logging, Cloudwatch is far from being usable as logging system, we use [this plugin](https://www.npmjs.com/package/serverless-log-forwarding) and forward our logs to a lambda that forwards then the logs to [Papertrail](https://papertrailapp.com/).

```
custom:
  iopipeToken: ${file(${opt:stage}.yml):iopipeToken}
```

I always mention [IOPipe](https://www.iopipe.com/) and we used this since the very early days, but what I didn’t realise until recently is that the free plan offers two projects, so you can actually split your monitoring in prod and non-prod environments and set up what they call ‘global’ alerts: no need to set up a new alert every time you introduce a new lambda.

A last thought: we implemented our lambdas in multiple git repositories, every repository might have from one to fourteen functions each, but what if we were doing a mono repo? We could have one single serverless.yml file, with the common configuration and then many other yml files containing function specific configuration. I think it might work really well, the serverless framework development moves really fast and to fully leverage the plugins system I think it would be easier to embrace a mono-repo structure.

I’d love to hear what are your favourite, must-have plugins and some war stories on serverless and mono-repos.
