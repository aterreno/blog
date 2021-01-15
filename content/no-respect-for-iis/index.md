---
title: "no respect for IIS"
description: ""
date: "2010-03-28T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//no-respect-for-iis-4b3857741ace
redirect_from:
  - /no-respect-for-iis-4b3857741ace
---

I never liked [IIS](http://www.iis.net/), internet information services… Already the name sounds quite wrong.

Coming from a Java/\*nix background, these are the things I’m missing the most:

**\- A web UI**  
Seriously, every application/web server I ever used had one, from the very basic and almost useless of the early versions of tomcat (didn’t check it for quite a while now) to the super complex and unusable of websfear (Google says: Did you mean: [websphere](http://www-01.ibm.com/software/websphere/)?).  
I hate the fact that I’ve to remote desktop onto the machine, and the rich client UI seems a bit simplistic, it doesn’t look geek/professional enough, it seems just yet another silly tool from Microsoft like regedit or notepad, it’s ridiculous and also quite hard to use (all those "Advanced settings" and "Basic settings" menus).  
My impression is that at Microsoft they don’t have any idea on how to write something that looks enterprise, they always try to make happy the people that don’t know how to use a computer…

**\- Efficient/Proper/Decent Logging**  
Last week we were trying some rules on [Netscaler](http://www.citrix.com/English/ps2/products/product.asp?contentID=21679), in order to balance traffic depending on user agents and other parameters: the IIS log sucks. After some googleing I’ve found out that I had to download and install the "Advanced Logging Module for IIS" in order to have decent, real-time logging, as they call it. What? Logging has to be real-time always! And it is on any other server!  
I believe that the "standard" installation of IIS doesn’t have "the advanced logging" feature just because the windows filesystem sucks but if you know any better reason to take off such an extremely basic feature off from IIS please let me know.  
I had to install on all our cluster instances [cygwin](http://www.cygwin.com/) to get a proper tail, but I can’t blame IIS for this, it’s off topic.

**\- Rewrite module**  
Well, apparently it’s [another](http://www.iis.net/expand/URLRewrite) "advanced module", I kind of see that they wanted to have something like a plugin architecture (unfortunately you can’t just drop all these modules somewhere, you have to go through a bloody wizard!) but this module… It’s again something very basic, I don’t understand what is advanced in it.

**\- Configuration**  
In all the other application servers I know you setup/change once and then you are done with all the others: the configuration is on a readable format (and if you’re a cool dude you are not using the UI anyway!), you can copy it across all your servers, done.

Some .net folk may argue that you can do the same cloning the whole machine, good point. Unfortunately we went in some unknown and crazy IIS errors cloning one machine from one domain (QA) to another one (LIVE).

I’ve no respect for IIS, and it’s a shame, .net 3.5 and 4.0 are quite nice languages that are evolving not being stuck as Java.

Other modules that you can get from the IIS site and I haven’t tried yet:

-   [http://www.iis.net/expand/webdeploy](http://www.iis.net/expand/webdeploy) : web deployment… another basic one totally missing  
     — [http://www.iis.net/expand/ApplicationRequestRouting](http://www.iis.net/expand/ApplicationRequestRouting) … application based routing, quite basic and needed
-   [http://www.iis.net/expand/ApplicationWarmUp](http://www.iis.net/expand/ApplicationWarmUp) … application warm up? what? yeah, right, apps in IIS take ages to start… how sad!
-   [http://www.iis.net/expand/IISManager](http://www.iis.net/expand/IISManager) … remote management… No Web UI unfortunately…
-   [http://www.iis.net/expand/PowerShell#mce\_temp\_url#](http://www.iis.net/expand/PowerShell) … scripting… like bash? not really, but scripting…

Other findings on IIS in my last 9 months:

-   **Application pools "recycle" every 20 minutes by default**! It’s like saying, you are such a shitty developer, I bet you got plenty of memory leaks, let’s restart your stuff every twenty minutes! Since starting an application in IIS is not really fast and since you’ll have probably to reconnect to the DB, reinitialize your application/NHibernate cache, your IOC container you may get some troubles here!
-   **Applications tends to take ages to start up**, as mentioned above, I really don’t know why, the WarmUP Module may help (sad lol)

No respect, not for Microsoft tools not for IIS, end of the story.
