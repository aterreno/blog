---
title: "Problem in WebSphere 6.0 ejbdeploy"
description: ""
date: "2007-03-13T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/problem-in-websphere-6-0-ejbdeploy-31ad300fc6e9
redirect_from:
  - /problem-in-websphere-6-0-ejbdeploy-31ad300fc6e9
---

> [JavaRanch Big Moose Saloon: Problem in WebSphere 6.0 ejbdeploy](http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=get_topic&f=46&t=007716)  
> Unable to parse setupCmdLine: nullbinsetupCmdLine.bat (The system cannot find the path specified)

I was trying to avoid to call bat files from ant. I hate that. First cos are platform (and what a platform…) dependent, second cos you can always have problems with error codes and the build can be successful even if something bad happens there…

There are 2 correct responses in this thread:

> I had the same problem last month, and struggled for a while. I found the point is, we have to use profilesAppSrv01binws\_ant.bat to call ant, instead of calling ant directly. By using ws\_ant.bat, it will initialize some env variables, and using IBM’s JVM to do the job. Another thing is, in build script, I need to define property "wasinstall" as websphere install home. This property will be used as ejb deploy task’s attribute "wasHome"’s value.

The first is this, so I’ll roll back my changes. The .bat file is plenty of SET blabla=blabla/bla so I have no choice.

The second is the best one but unfortunately I can’t do that:

> There is one fix, delete WAS and never install it :-P.

Indeed, WAS is an antipattern.
