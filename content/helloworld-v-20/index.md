---
title: "HelloWorld v 2.0"
description: ""
date: "2008-11-08T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/helloworld-v-2-0-c16a8d82916d
redirect_from:
  - /helloworld-v-2-0-c16a8d82916d
---

Once upon a time we used to write:

```
public static void main(String[] args) {
   System.out.println(”Hello World”);
}
```

Now I prefer:

```
@Test
public void shouldSayHelloToTheGivenName() throws Exception {
        // given
        PrintStream mockStream = mock(PrintStream.class);      

        Greeter greeter = new Greeter(mockStream);

// when
    greeter.helloworld(”toni”);

// then
    verify(mockStream).println(”Hello world, toni”);

}
```

The test is of course using the beautiful [test double](http://xunitpatterns.com/Test%20Double.html) framework [Mockito](http://mockito.org/)
