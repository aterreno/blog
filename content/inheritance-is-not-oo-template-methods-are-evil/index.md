---
title: "Inheritance is not OO, template methods are evil"
description: ""
date: "2007-07-21T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//inheritance-is-not-oo-template-methods-are-evil-c3a28d4902ce
redirect_from:
  - /inheritance-is-not-oo-template-methods-are-evil-c3a28d4902ce
---

My first coach [Bruno](http://bbossola.wordpress.com/) always said that Inheritance doesn’t imply Object Oriented and he’s absolutely right. An abstract class necessarily implies inheritance and I really don’t like abstract classes! I rather prefer to use dependency injection, inheritance between classes just leads to the highest level of coupling that you can introduce.

Right after the university I was abusing of it, then day by day fortunately I started to use interfaces rather than that. It’s strange, looks like that at the university they really love that kind of stuff, I was doing some code reviews in the last weeks for new graduates applying to TW, you know what: a good number of them were (ab)using of abstract classes with no sense, instead of using Interfaces.

A common usage of abstract class is for template methods pattern, [Martin](http://www.martinfowler.com) wrote [an article](http://www.martinfowler.com/bliki/CallSuper.html) about this already. I really hate any framework that forces you to call a super implementation. What about the design of Junit 3! What about Struts Actions!!! What’s doing the super class? Why do I have to call super (base) something? It just smells.

[Here](http://tech.puredanger.com/2007/07/03/pattern-hate-template/) there’s a good article by [Alex Miller](http://tech.puredanger.com/about/) on how to remove template methods and why template methods are evil, I just can’t add nothing more.

But what to do then, when you need to call something before or after? Aspects maybe, Interceptors, Annotations (Java),Â Attributes(C#).

[TestNG](http://testng.org/doc/) has some really interesting annotations like the BeforeClass:

> package example1;  
> import org.testng.annotations.\*;  
> public class SimpleTest {  
>  @BeforeClass  
>  public void setUp() {

> }  
>  @Test(groups = { "fast" })  
>  public void aFastTest() {  
>  System.out.println("Fast test");  
>  }  
>  @Test(groups = { "slow" })  
>  public void aSlowTest() {  
>  System.out.println("Slow test");  
>  }  
> }

[Aspectwerkz](http://aspectwerkz.codehaus.org/) is AOP with annotations, so, here an example:

> package testAOP;

> import org.codehaus.aspectwerkz.joinpoint.JoinPoint;  
> public class MyAspectWithAnnotations {

> /\*\*  
>  \* @Before execution(\* testAOP.HelloWorld.greet(..))  
>  \*/  
>  public void beforeGreeting(JoinPoint joinPoint) {  
>  System.out.println("before greeting…");  
>  }

> /\*\*  
>  \* @After execution(\* testAOP.HelloWorld.greet(..))  
>  \*/  
>  public void afterGreeting(JoinPoint joinPoint) {  
>  System.out.println("after greeting…");  
>  }

> }

Spring is also another well known framework that plays with this stuff, in the reference guide they say:

> So much for the pros and cons of each style then: which is best? If you are not using Java5 (or above) then  
> clearly the XML-style is the best because it is the only option available to you. If you are using Java5+, then  
> you really will have to come to your own decision as to which style suits you best. In the experience of the  
> Spring team, we advocate the use of the @AspectJ style whenever there are aspects that do more than simple  
> "configuration" of enterprise services. If you are writing, have written, or have access to an aspect that is not  
> part of the business contract of a particular class (such as a tracing aspect), then the XML-style is better.

I’m not sure about this, xml writing is voluntarily not supported by this blog syntax highlighter, so I’m not pasting any example :-D

So, finally, the tip is, _do not extend, implement_.
