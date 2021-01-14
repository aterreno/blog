---
title: "The way we design our software these days"
description: ""
date: "2010-12-06T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/the-way-we-design-our-software-these-days-d3aa6179c02e
redirect_from:
  - /the-way-we-design-our-software-these-days-d3aa6179c02e
---

[Rory Gibson](http://twitter.com/rorygibson) wrote [a nice write up of Fred’s open space talk](http://rorygibson.wordpress.com/2010/12/01/xpday-2010-moving-forward-or-backward/) that did happen last Monday at the [10th XPDay](http://www.xpday.org/) in London.

[Jamie](http://www.financialagile.com/) wrote a comment on that post that deserves a reply.

He says:

> You won’t know it works until later… What debt are they now in? What happens when complexity grows? How do they resolve conflict? Many start ups work because debt is hidden. If peer pressure is their number 1 hr strategy they will stagnate and _not_ be able to respond to changes in their business.

The comment was mainly on our philosophy, another commenter on the blog post describes it as [JFDI](http://www.urbandictionary.com/define.php?term=JFDI).

[During my talk](http://www.agilemovement.it/video/piu-agili-senza-schema) at the Agile Day I’ve got a comment that I forgot to mention in my [post-talk write up](http://www.the-arm.com/2010/11/agiler-at-forward-and-successful-at-the-iad10/).  
One guy on the audience said, well you guys just design your software with a Unix Philosophy.

Oh man, this is so true.  
[It’s even on wikipedia](http://en.wikipedia.org/wiki/Unix_philosophy).

I particularly like the[Mike Gancarz](http://www.amazon.co.uk/UNIX-Philosophy-Mike-Gancarz/dp/1555581234/ref=sr_1_1?ie=UTF8&qid=1291633401&sr=8-1) check list of the Unix Philosophy:

-   _Small is beautiful._
-   _Make each program do one thing well._
-   _Build a prototype as soon as possible._
-   _Choose portability over efficiency._
-   _Store data in flat_ [_text files_](http://en.wikipedia.org/wiki/Text_file "Text file")_._
-   _Use software leverage to your advantage._
-   _Use_ [_shell scripts_](http://en.wikipedia.org/wiki/Shell_script "Shell script") _to increase leverage and portability._
-   _Avoid captive user interfaces._
-   _Make every program a filter._

Then let me paste here also the golden rules from [Eric Raymond](http://www.amazon.co.uk/Unix-Programming-Addison-Wesley-Professional-Computing/dp/0131429019/ref=sr_1_2?s=books&ie=UTF8&qid=1291633470&sr=1-2):

-   Rule of [Modularity](http://en.wikipedia.org/wiki/Modularity_%28programming%29 "Modularity (programming)"): Write simple parts connected by clean interfaces.
-   Rule of Clarity: Clarity is better than cleverness.
-   Rule of Composition: Design programs to be connected to other programs.
-   Rule of Separation: Separate policy from mechanism; separate interfaces from engines.
-   Rule of Simplicity: Design for simplicity; add complexity only where you must.
-   Rule of Parsimony: Write a big program only when it is clear by demonstration that nothing else will do.
-   Rule of Transparency: Design for visibility to make inspection and debugging easier.
-   Rule of Robustness: Robustness is the child of transparency and simplicity.
-   Rule of Representation: Fold knowledge into data so program logic can be stupid and robust.
-   Rule of Least Surprise: In interface design, always do the least surprising thing.
-   Rule of Silence: When a program has nothing surprising to say, it should say nothing.
-   Rule of Repair: When you must fail, fail noisily and as soon as possible.
-   Rule of Economy: Programmer time is expensive; conserve it in preference to machine time.
-   Rule of [Generation](http://en.wikipedia.org/wiki/Code_generation "Code generation"): Avoid hand-hacking; write programs to write programs when you can.
-   Rule of [Optimization](http://en.wikipedia.org/wiki/Optimization_%28computer_science%29 "Optimization (computer science)"): [Prototype](http://en.wikipedia.org/wiki/Prototype "Prototype") before polishing. Get it working before you optimize it.
-   Rule of Diversity: Distrust all claims for "one true way".
-   Rule of Extensibility: Design for the future, because it will be here sooner than you think.

Now believe or not but you can trash away lots of books just following these rules.   
Unix is, IMO, the most stable software humanity ever wrote (think about unix, linux, macos and so on)

This is the way we work.   
We do have technical debt and we have plans to rewrite our small applications, we do that continuously, since they are small, modular, with a single responsibility (think about cat, ack, grep, etc… do) it’s never a big deal.
