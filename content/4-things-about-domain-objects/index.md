---
title: "4 things about domain objects"
description: ""
date: "2007-06-13T00:00:00.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//4-things-about-domain-objects-f869df13442f
redirect_from:
  - /4-things-about-domain-objects-f869df13442f
---

**First**, please do not mock a domain object. [Stub](http://www.martinfowler.com/articles/mocksArentStubs.html) it. Thanks.

**Second**, do not write an interface for it. Neither if you want a Null Object implementation.

**Third** do not be obsessed with Null Objects, sometimes they are good, not always. If you end with a

if objectInstanceType == ObjectType.NULL in your code perhaps something is wrong in your design, a null object is to avoid that stuff and to give a "null behaviour".

**Forth**. Do not use the [ActiveRecord](http://www.martinfowler.com/eaaCatalog/activeRecord.html) pattern, seriously, you’re gonna couple the infrastructure layer with the domain layer. It’s not a pattern IMHO, kind of antiproton, try considering a [repository](http://www.martinfowler.com/eaaCatalog/repository.html).

**Fifth**. For the point one maybe you will like a [builder](http://www.martinfowler.com/bliki/ExpressionBuilder.html) pattern in order to stub objects. Here an example:  
  
class PersonBuilder  
{  
private string name = "testname";  
private int age;  
public PersonBuilder Name(string value)  
{  
name = value;  
return this;  
}  
}  
public PersonBuilder Age(int value)  
{  
age = value;  
return this;  
}  
public Person ToPerson()  
{  
return new Person(name, age);  
}  
  
Syntax then is nice, I really like it.

Person expected = new PersonBuilder().Age(29).Name("antonio").ToPerson();

and it encourages to write not mutable object like this Person:  
  
class Person  
{  
private readonly int age;  
private readonly string name;  
public Person(string name, int age){â€¦}  
public int age  
{  
get { return age; }  
}  
}

Looks like I’ve lost my code formatter… :-(
