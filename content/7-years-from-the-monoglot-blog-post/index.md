---
title: "7 years from the #monoglot blog post"
description: "About seven years ago I wrote a blog post on how I thought that software development would benefit from using only one programming…"
date: "2017-12-24T19:01:02.315Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//7-years-from-the-monoglot-blog-post-f13d9e776b14
redirect_from:
  - /7-years-from-the-monoglot-blog-post-f13d9e776b14
---

About [seven years ago I wrote a blog post](https://the-arm.com/monoglot-architecture-for-the-win-86bc010c61fb) on how I thought that software development would benefit from using only one programming language.   
The reality is that 7 years ago neither JavaScript or the frameworks were ready but I think now that time has come.

I am far from saying that JavaScript is a superior language, its limits are quite evident, however, an engineering team might benefit by not switching a programming language between the layers and the different (micro) services / Functions implemented.

When I was at [Forward](http://www.forward.co.uk/) I remember changing from codebase to codebase and from programming language to programming language: we had fun but the context switch was expensive.

At [Labrador](https://www.thelabrador.co.uk/), we’ve inherited an MVP built with lambdas in ES 6, and even if reluctant at first, we’ve embraced JS as the programming language of choice.

ES6 is not bad at all, with [few new features](http://es6-features.org/#Constants) really improving the syntactic sugar and a lively ecosystem.

So what’s our stack like? Lambdas in AWS written in ES6 using either the [Serverless](https://serverless.com/) Framework or [Claudia.JS](https://claudiajs.com/): we favour this last one and especially the [API Builder](https://claudiajs.com/claudia-api-builder.html) for building APIs.

Our data is mainly stored in S3 or DynamoDB, in JSON so, it’s still JS!   
And the fronted is built with React.JS.

The only code that is not JS is our Terraform codebase, everything else is JS.

[Webstorm](https://www.jetbrains.com/webstorm/) is our editor of choice, with the help of [JSHint](http://jshint.com/), it might be heavier than other IDEs but the support for keeping the source clean and tidy is brilliant.

Are there any languages that you can use for a monoglot architecture? I don’t think so, there’s a constraint on the web browsers, JS if not the source code will always have to be at least the artefact [ClojureScript](https://clojurescript.org/) would be a good choice if you are into functional/Lisp-like languages, [Typescript](https://www.typescriptlang.org/) is very tempting.

[Here’s a list](https://www.sitepoint.com/10-languages-compile-javascript/) of ten of them: I think the main benefits might come from using types and embracing immutability, while others seem just an expensive attempt to circumvent JS rather than embracing it.

I think [modern JS can be easily functional and immutable](https://leanpub.com/javascriptallongesix/read), while types are definitely something that would be nice to optionally see in the language, it’s not a coincidence that as soon as a codebase grows large companies try safer paradigms: [TypeScript](https://slack.engineering/typescript-at-slack-a81307fa288d) at Slack, [Flow](https://flow.org/) at Facebook.
