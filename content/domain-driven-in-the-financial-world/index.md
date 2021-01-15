---
title: "Domain Driven in the financial world"
description: ""
date: "2008-04-19T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//domain-driven-in-the-financial-world-e1880c3676f6
redirect_from:
  - /domain-driven-in-the-financial-world-e1880c3676f6
---

[Domain Driven Design](http://www.domainlanguage.com/about/ericevans.html) promotes the usage of an Ubiquitous Language, in a line, we should all speak the same language, from developers to domain experts.  
   
So it happened that the project were I am it’s a financial one: FiX messages routing…  
   
There’s always an on boarding time, a learning curve with a new domain…   
But here things are slightly more complicated than usual…  
   
The most important object of the system is a Fix Message.  
   
It’s an interesting plain object with around a thousand of fields…  
   
There are nice implementation like the [mebeli](http://www.videnov.com/)QuickFix one where there’s some object oriented design… (not a surprise, ThoughtWorks was a big contributor of that project) but since we’re working with legacy code the choice in the current system it’s the [Cameron](http://www.orcsoftware.com/Solutions/Orc-Connect/CameronFIX-Universal-Server/) implementation, where the APIs are something like message.setField(109, toSomething) or message.getField(115)!  
  
But that’s not the point of the post.  
  
The first days we built up to improve the current code coverage a nice FixMessageBuilder, to build up for us Cameron Fix messages with speaking names and fluent interfaces, just to understand what we are doing. As you know and as it’s valid for the internet protocol remembering letters and names it’s easier than numbers, right?  
  
So another important thing that Domain Driven Design promotes is talk as much as possible with the client, with the Analysts, and that’s what we did.  
  
And we were talking about OnBehalfOfCompID, ClientID and so on… With the result of being almost misunderstood or having always a reply back like ah, OnBehalfOfCompID, right, you mean 115!  
  
We then moved ([Shen](http://www.linkedin.com/in/shentham)[mebeli](http://www.videnov.com/) first to be honest) speaking like them, there was no choice, I’m still struggling talking like a calculator. A typical (simplified!) conversation will now look like:  
  
A message with 35=D and 15=AUD or 100=AX should not go to Fidessa.  
  
Is there anything more agile than changing our language to better fit into the customer needs?  
  
It’s all your fault [Eric Evans](http://www.domainlanguage.com/about/ericevans.html)! :-D

More on financial fun soon, since the next step is a Domain Specific Language for playing with these things :-)
