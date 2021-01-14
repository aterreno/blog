---
title: "How do you build your projects?"
description: ""
date: "2008-02-04T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/how-do-you-build-your-projects-b5a2dd32336
redirect_from:
  - /how-do-you-build-your-projects-b5a2dd32336
---

Recently we migrated all our build scripts from a combination of bat files + msbuild to a couple of [NAnt](http://nant.sourceforge.net/) build files.

There are some reasons for this and some nice outcomes.

#### Reasons

First of all we wanted to have the same build scripts for Development, CI, QA, UAT and production Environment.

On the Dev machines we need to build, test and install few services (ms services, a web service and a web app).   
On Cruise same as above but no installation of the services and, indeed some publishing of the artifacts.   
The QA environment is as close as possible as the UAT/Production: it just needs installation scripts and a way to get the latest artifacts published by [Cruise](http://confluence.public.thoughtworks.org/display/CCNET/Welcome+to+CruiseControl.NET).   
Using the same script gave us a great confidence when going to production: scripts were used every day by the QA, no surprises when going live.   
We got completely rid of all the .bat files for 2 main reasons: they become messy after 1 year of patches/fixes/modifications and we can’t really achieve the goal of one script for all as we wanted.

After a short investigation on alternatives to bat+msbuild ([boobs](http://www.ayende.com/Blog/archive/2007/09/22/Introducing-Boobs-Boo-Build-System.aspx) and [rake](http://blog.jayfields.com/2005/08/using-rake-for-building-and-testing.html)) we went for nant.   
We found boobs quite difficult to use and install (you need to build some libraries, install [boo](http://boo.codehaus.org/), etc…), in other words it does not came for free. Rake is a cool solution, we didn’t choose that cos 1) we were too lazy to install ruby everywhere (in production especially could be a problem) 2) our build, even if includes a client app, four services, a web app and a web services is fairly simple.

Nant is really a good translation from the Java Ant. It’s actually more than a one to one translation, it has more features and it’s somehow more powerful.

I really liked the [functions](http://nant.sourceforge.net/release/latest/help/functions/) for example. And the [contrib](http://nantcontrib.sourceforge.net/) project is plenty of nice, useful tasks ready to use.

Another important improvement on the build scripts was on the database scripts.   
Again, migrated from few bat files to one script for all the needed tasks.   
We had a lot of satisfaction using [dbdeploy.net](http://boo.codehaus.org/), it really speeds up the work, especially in the QA environment migrating the DB schema to the latest version keeping the data in.

#### Outcomes

Life easier for everybody: instead of calling a bat files with some parameters we had a file of properties (not a lot of properties, convention over configuration!) for each environment, it’s now harder to fail an installation. It’s also more clear of what’s going on thanks to the nant output log.

Maintenance it’s easier. There are only two files that you need to know. Tasks are pretty short and responsibilities isolated.   
We kept also a low lever of dependencies avoiding imports and more than two level of dependency.

Sometimes rewriting everything from scratch is much easier than refactoring / patching.   
It has been also interesting to write a build file after one year of development, usually it’s one of the first things you do in your project.

My suggestion is: if your build script causes problems, waste of time or if it just smells and it’s not clear what’s doing, try to spike out a different solution, the benefit could be enormous.
