---
title: "Composing html fragments with Mustache and Clojure"
description: ""
date: "2013-08-10T10:40:37.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/composing-html-fragments-with-mustache-and-clojure-62bb3e8ad935
redirect_from:
  - /composing-html-fragments-with-mustache-and-clojure-62bb3e8ad935
---

We got a fairly large code base of [mustache templates](http://mustache.github.io/) (5386 LOC in total, 964K), we are using [clojure](http://clojure.org/) with [stencil](https://github.com/davidsantiago/stencil) to transform our data from [ElasticSearch](http://www.elasticsearch.org/) documents into [html5](http://www.html5rocks.com/en/).

The two main views on the sites are article details and channel. Here’s the code responsible for the mobile article rendering.

\[code language=”clojure”\](article-channel-fns \[this article\]  
 {:head (partial head/render-for-single-mobile-article article)  
 :content (partial mobile-article/render-article article)  
 :masthead #’masthead/render-for-mobile  
 :navigation #’navigation/render-for-mobile  
 :footer #’footer/render-for-mobile})  
\[/code\]  
The head/render-for-single-mobile-article function looks like this:

\[code language=”clojure”\](defn render-for-single-mobile-article \[a channel\]  
 (musta :channel :head (article-defaults a channel)))  
\[/code\]  
The main mustache template is rather simple:

\[code language=”html”\]

<!DOCTYPE html>  
<html>

{{{head}}}  
{{> templates/mobile/channel/body.html}}  
</html>

\[/code\]  
The trick is to have mustache variables that gets resolved into function calls, so that {{head}} will be resolved at page load.

Musta is a simple macro that just loads the templates from file system or cache and calls the stencil library.

The head template looks more or less like this:

\[code language=”html”\]<head>

<title>{{page-title}}</title>

{{#meta.properties}}

<meta {{type}}=”{{name}}” content=”{{{content}}}” />  
{{/meta.properties}}

<meta name=”viewport” content=”width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no” />

{{#meta.links}}  
<link rel=”{{rel}}” href=”{{href}}” {{#title}}title=”{{.}}”{{/title}} {{#type}}type=”{{.}}”{{/type}} />  
{{/meta.links}}

<link rel=”stylesheet” type=”text/css” href=”http://{{globals.settings.fe-repo-host}}/{{globals.settings.fe-repo-version}}/css/main.css" />

</head>  
\[/code\]

#### In conclusion

It’s a pretty neat and flexible way to compose your html pages, stencil proved to be very fast and bug free.

Mustache has a rather extreme approach: no logic (a part from loops and simple if else) are allowed in the syntax: nevertheless it plays quite nicely generating html from clojure maps; whenever we need some conditions we pass special variables to the templates with naming conventions such as ‘map-name-count’ and ‘map-name-?’ to respectively indicate the size and the existance of the data.
