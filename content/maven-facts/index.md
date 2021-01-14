---
title: "Maven Facts"
description: ""
date: "2009-04-16T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/maven-facts-3e2e37f7110c
redirect_from:
  - /maven-facts-3e2e37f7110c
---

1.  [Maven](http://maven.apache.org/) will never tell you which phases or goals are available in the pom, you have to guess or check the [on-line documentation](http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)
2.  Maven by default uses text files to dump the test execution results, if you want to see what’s happening on the console you have to call it with -Dsurefire.useFile=false
3.  Maven can skip the executions of the tests (sometimes might be useful!) call it with [\-Dmaven.test.skip=true](http://maven.apache.org/plugins/maven-surefire-plugin/examples/skipping-test.html)
4.  Maven knows what inheritance is (and therefore claims that it’s object oriented… grrr…) so if you can’t find where some property is defined [have a look up on the parent](http://mavenize.blogspot.com/2007/06/pom-inheritance.html)
5.  Maven is based on XML but you won’t write as much XML as with Ant
6.  Maven can create Eclipse project files and even download the sources for you ([mvn eclipse:eclipse -DdownloadSources=true](http://maven.apache.org/guides/mini/guide-ide-eclipse.html))
7.  Maven downloads stuff from the internet (#1 failure reason for 99% Maven presentations) but can be run in offline mode (if you had a sucessfull install previously), try mvn -o
8.  Maven uses repositories, but since not all the libs in the world are in repositories you should setup a local repository ([Archiva](http://archiva.apache.org/) works well)
9.  Maven uses repositories, but since you don’t want to hog all your company bandwith you should setup a local repository
10.  Maven goes great with stuff like [Hudson](https://hudson.dev.java.net/), [Sonar](http://sonar.codehaus.org/)
11.  Maven [build profiles](http://maven.apache.org/guides/introduction/introduction-to-profiles.html) are really cool
12.  Maven is not [silver bullet](http://en.wikipedia.org/wiki/Silver_bullet) but I’ll never go back to [Ant](http://ant.apache.org/)
