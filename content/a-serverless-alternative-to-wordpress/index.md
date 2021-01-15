---
title: "A Serverless alternative to WordPress"
description: "In all my career I always had to battle with a WordPress installation, first it was my personal blog then it was the public facing website…"
date: "2018-06-13T12:07:50.287Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//a-serverless-alternative-to-wordpress-b55c628c71e2
redirect_from:
  - /a-serverless-alternative-to-wordpress-b55c628c71e2
---

In all my career I always had to battle with a [WordPress](https://wordpress.com/) installation, first it was my personal blog then it was the public facing website of companies I worked for.   
It’s not in the scope of this post to elicit the flaws and fragility of the WordPress platform, but my main drivers as CTO of [Labrador](https://www.thelabrador.co.uk/) were:

#### Aligned Tech Stack

Everything at Labrador is done in [Node.JS](https://nodejs.org/en/) and [React.JS](https://reactjs.org/) not only, we leverage as much as possible Cloud ([AWS](https://aws.amazon.com/)), FaaS ([Lambdas](https://aws.amazon.com/lambda/)): WordPress was far from this model and nobody in the tech team had PHP or WordPress administration skills, and, to be quite frank, nobody wanted to gain those skills.

**Aligned and uniform Process  
**Sure, there are ways to do continuous delivery and integration with WordPress, but again we didn’t want to invest into this, we wanted to use our favourite tooling and model also to promote changes for the public facing website: a local dev environment, a non-production environment, a production environment, a continuous delivery pipeline powered by our [ConcourseCI](https://concourse-ci.org/) server.

#### More power and easier integration with other components

The User Journey was broken down in two: you’ll be in a slow, server side rendered page on WordPress and then taken into a sign-up journey running on React.   
We wanted to offer a more streamlined web experience and no jumps between domains or pages.   
Not only, because now we own the tech stack of our site and we are comfortable with the codebase we will be faster introducing new features, such as dynamic content powered by our own APIs.

#### So what’s the new tech stack like?

We generate our content inside [Contentful](https://www.contentful.com/), Contentful is configured to call one of our lambdas when new content gets published, [Gatsby](https://www.gatsbyjs.org/) re-builds the site from scratch, publishes to [S3](https://aws.amazon.com/s3/) and invalidates a [CloudFront](https://aws.amazon.com/cloudfront/) Distribution.   
We are also leveraging [GraphQL](https://graphql.org/) (to get the posts from Contentful) and [Styled Components](https://www.styled-components.com/) for styling the site: no more SASS or CSS, it’s all JS.   
There’s another little component: in order to serve folders we wrote a tiny Lambda that runs at [Edge](https://docs.aws.amazon.com/lambda/latest/dg/lambda-edge.html) and basically rewrites the URLs (/page/ => /page/index.html).   
As any of our other lambdas this stack is monitored with [IOPipe](https://www.iopipe.com/) and the lambdas are configured, packaged and deployed using the [Serverless Framework](https://serverless.com/).

Architecture Diagram

#### Is it going to cost us more or less?

I’ve done some maths. The current hosting from [WP-Engine](https://wpengine.co.uk/) costs about 999$ a year, that’s 2.7$ a day.   
Lambda edge costs $0.0000006 per request, in order to render the homepage we make 43 requests, it’s 1.4KB.  
CloudFront is 0.68$ a month, assuming that the current site will consume the same bandwidth (I am sure it’s smaller), S3 will be pennies as well.   
So we’ll need 4.5M requests a day, that’s about 100k unique views a day on our side before the Serverless Implementation will be as expensive.

So I think that it will cost way less, also, the older site wouldn’t cope with that traffic! And we’ll be really lucky if we really get so many visitors!

#### Was it worth it?

Well we learnt a lot around Lambda running@Edge, Styled Components and GraphQL, [Gatsby](https://www.gatsbyjs.org/) is lovely and we’ll now make the site better and better day by day without having to swear on how slow wp-admin is and we’ll just write code instead of installing plugins. We’ll also have no worries about upgrading WordPress or security and the pages are now honestly blazing fast, like 3x times faster!
