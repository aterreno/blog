---
title: "Ruby… Not so bad…"
description: ""
date: "2006-10-25T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//ruby-not-so-bad-5d9854d0b25b
redirect_from:
  - /ruby-not-so-bad-5d9854d0b25b
---

Yuppie, finally I have a project and looks nice, we have to use Ruby on Rails and Ajax, so I’m forced to study a bit this language and the framework.

I’m reading [Agile Web Development with Rails](http://www.amazon.co.uk/Agile-Development-Rails-Dave-Thomas/dp/097669400X/ref=sr_11_1/203-8945782-5143904), really a good book and after a lazy mac os intallation of [Locomotive](http://locomotive.raaum.org/) + [RadRails](http://www.radrails.org/), I’ve moved to a more "hacking" installation following the good tutorial on the blog of [James Dunkan](http://blog.duncandavidson.com/2006/04/sandboxing_rail.html).

Right now I’m blocking cos the installation, done using ports takes really ages, compliling and downloading what’s needed…

There are some "features" that I really like of Ruby, for example all member variables are private, to access it you have to write a getter, using the keyword attr, if you want only getter just write attr\_reader

[ruby]

class Blog  
def initialize(title)  
@title = title  
end  
attr\_reader :title

[/ruby]

Nice no?

Another cool thing is that Ruby does not have Multiple Inheritance by the way it has the module concept, so you can have methods for free from another class.

A stupid example can be something like this:

[ruby]

module WebPage  
def WebPage.toHtml

### …

end

class Blog  
require ‘WebPage’

[/ruby]

An you’ll be able to use that Method on the Blog class.
