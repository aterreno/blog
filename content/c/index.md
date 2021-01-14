---
title: "C#"
description: ""
date: "2007-05-23T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/c-96d31ff5ae7b
redirect_from:
  - /c-96d31ff5ae7b
---

C# is not so bad. It’s 7 weeks now that I am working with this language and I quite enjoy it.

The tool is terrible slash horrible, we are using resharper that helps a bit but it’s not comparable to any java IDE that I know. Just the UI designer is nice and pretty easy to use, Windows Forms are for sure better than Swing, that was kind of easy.

Talking about the syntax I really like the using syntax:

writing something like:

using(Session s = manager.GetSession())

{

DoSomething();

}

is equivalent to the java

Session s;  
try {

s = manager.GetSession();

doSomething();

} finally { s.dispose();}  
To put an object in the using () this object must implement IDisposable, and then implement the Dispose Method. Isn’t nice?

Then also all the event and delegate stuff, too lazy to explain, try to have a look [here](http://www.akadia.com/services/dotnet_delegates_and_events.html) or search with Google!  
Transaction to C# was kind of easy, in 2 weeks I was up to speed. I am looking forward to the next C#, it looks just [amazing](http://www.developer.com/net/csharp/article.php/3561756). Java where are you?
