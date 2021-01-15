---
title: "My first six months with Clojure"
description: ""
date: "2013-09-01T10:38:33.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//my-first-six-months-with-clojure-f853b467eba6
redirect_from:
  - /my-first-six-months-with-clojure-f853b467eba6
---

Six months ago I’ve decided to join my friend [Jon](http://www.pitheringabout.com/) in rewriting what is acknowledged as [the world’s most popular news site](http://www.bbc.co.uk/news/magazine-16746785).

This blog post mainly focuses on my first impressions on the programming language we did choose to use [Clojure](http://clojure.org/).

#### Emacs, Paredit

I’ve tried few times to learn Clojure in the past and I’ve failed miserably.

Partially because I wasn’t forced to use it on any large production systems but right now I mainly blame the development environment.

The duo Emacs and Paredit in fact, even if definitely not quick and easy to learn will, on the longer term make your life as a developer very easy.

After a painful few weeks I was quickly fully in love with [Emacs](http://www.gnu.org/software/emacs/), its speed and its infinite power and extensibility, I can definitely say that it’s the best tool to write code I ever used.

[ParEdit](http://www.emacswiki.org/emacs/ParEdit) is a _minor mode for performing structured editing of S-expression data_.   
In human language that means that you will avoid going crazy when balancing parenthesis, I barely read the parenthesis these days in my code and I write only half of them.

The only trouble I am seeing with it right now it’s the team work: everybody ([including me](https://github.com/aterreno/.emacs.d)) tends to create its own emacs files and pairing becomes challenging since everything is easily configurable and customizable.

#### nREPL

The [nREPL](https://github.com/clojure/tools.nrepl) changed the way I write software, yes, I used in the past the rails console, irb, the Chrome console and even the console in Visual Studio, but the nREPL is way more powerful.   
Its power comes from Clojure, I usually move inside a namespace, write some code in the repl and yank it back into the editing buffer.

The functions result in being small, the code has not too many dependencies, everything is pretty self-contained. I am far away from being a good functional programmer but I can say that I can read easily enough my code months after I wrote, it’s a decent sign!

From the repl we also easily restart, reload and debug our applications.

Jon recently wrote about [TTD and Clojure](http://www.pitheringabout.com/?p=995), right now the nREPL is my way of doing TDD, the test gets thrown away straight after: it’s not far from what Dan North [thinks about TDD](http://dannorth.net/the-art-of-misdirection/).

#### Books, Community, Resources

Clojure is relative new, appeared in 2007, but pretty solid and stable, I love [its mailing list](https://groups.google.com/forum/#!forum/clojure): not too much traffic and high quality posts and there’s [a good amount](http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=clojure) of books available, [Programming Clojure](http://pragprog.com/book/shcloj2/programming-clojure) being my favourite so far.

#### Thoughts on Object Oriented Design

I had an argument with [Felix](http://wuetender-junger-mann.de/wordpress/) ages ago, I always thought that the language drives the coding style and the design.

Years of EJBs, Spring, IDEs that generates boiler template code for you created those big balls of mud that soon need rewrite.

But now I’ll add more, I reached a point where I think that Object Oriented Design is not suitable for the web.  
The power of Clojure is in its data (maps, lists but not only) transformation capabilities.  
A web application is nothing more than data transformation, from a storage to an html file, served on a socket.  
Nothing more than that.

OOD is also very hard to get right, loads of tests, [GOOS](http://www.growing-object-oriented-software.com/) all the way and so on.

Functional programming is hard as well, and I am probably far from being able to judge if it’s easier or not, but I can certainly say that the speed of changing/moving/refactoring code is incredible fast.  
I believe that this is happening also because of the small quantity of unit tests and because of the general decent quality of our code base but it still impress me.

#### High productivity

I rarely felt so productive with coding.

The only comparable project I can remember in my past was perhaps using Ruby, Sinatra and Mongo.   
However Emacs with ParEdit and code completion makes writing code quicker, the compilation on save makes it easier to spot trivial typing errors.

The dependency model is a very well camouflaged version of maven: it just works, it’s not great as [NPM](https://npmjs.org/) probably but it does the job very very well.

#### Quick wins

We use [Avout](http://avout.io/) for storing our application configuration, it has never been so simple and reliable: configuration changes are stored in [Zookeper](http://zookeeper.apache.org/) and pushed to the application instances asynchronously and with no restart needed. It just works.

Handling state (or avoiding to have state) in Clojure is pleasant, elegant and safe.

Check this [blog post](http://blakesmith.me/2012/05/25/understanding-clojure-concurrency-part-2.html) for more on the subject.

#### How does it compare with other languages I’ve used?

#### Java

Oh old good Java, it’s like talking about Cobol in the 90's.

I hope that with the next JDK things will improve and I’ve a lot of respect for all those folks that write rather [elegant libraries](https://code.google.com/p/totallylazy/) to solve the problems the languages is unable to solve elegantly.

The Ecosystem is broken: IDEs, Frameworks.

The Good Practices are followed by a way too limited number of people and I never had the luck to join a project and see an healthy code base, without [bloated Frameworks](http://www.springsource.org/spring-framework) wired in, without over-complex unnecessary design: Service Controller Repository anyone?

Clojure wins in conciseness and core API.

#### .net

_Left intentionally blank_

#### Ruby

I still like Ruby a lot, the performances are in most cases poor (I’ll save [Goliath](https://github.com/postrank-labs/goliath)), I don’t like where Rails is going, I don’t like that too many people call themselves developers after a few weeks of Rails crash course.

It’s a nice scripting toy language, I still use if for [deploy](https://github.com/capistrano/capistrano) (somewhere where Clojure lacks in tools maybe?) and for my [machine setup](http://brew.sh/). I don’t see the point in using it on large, performance intense projects: if it’s not your butcher website you probably should move away from it.

Clojure wins in performances and dependency management.

#### Node.js

I don’t like the dozens of way you can write javascript, there’s way too many good ways of writing good javascript code. It’s a broken language in so many way. Clojure wins in elegance.

Node.js is about 2 years younger than Clojure but it’s still crazy unstable, sure, this will make the platform evolve but I had to rewrite some code a few times just because of a node minor version update.   
I’ll sit and wait for the version 1.0, perhaps writing the code in Coffescript.

Clojure wins in platform maturity and stability.

#### Conclusions

Obviously I need more time to start feeling the pains, I reckon at least another year, I am also very intrigued by Erlang and Go. But learning Clojure is an exercise I can only recommend, it will make your code better, whatever language you have to use in your daily job.

I think that what’s harder (or more costly) to learn it’s then easier (or cheaper) to use.   
And that’s definitely the case of Clojure.
