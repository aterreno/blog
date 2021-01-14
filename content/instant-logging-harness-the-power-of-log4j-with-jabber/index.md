---
title: "Instant logging: Harness the power of log4j with Jabber"
description: ""
date: "2006-10-23T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/instant-logging-harness-the-power-of-log4j-with-jabber-b7a94af98658
redirect_from:
  - /instant-logging-harness-the-power-of-log4j-with-jabber-b7a94af98658
---

A former collegue of mine was asking me how to see the log if the deploy is on a server with strict restriction… After searching a bit (mail was not good, database neither) I found this funny way to log events… It’s really cool!

> [Instant logging: Harness the power of log4j with Jabber](http://www-128.ibm.com/developerworks/java/library/j-instlog/)  
> Writing an IM-based appender

> The code outlined in this article shows how you can extend the log4j framework to integrate IM features. It’s designed to enable a log4j-compliant application to log its output onto IM networks. The IM appender actually works as a customized IM client. However, instead of System.out, files, or TCP sockets, it takes IM networks as the underlying output device.

> To provide IM support, we don’t need to reinvent the wheel when developing ad-hoc solutions. Instead, we’re going to leverage a tool we consider the best of breed: Jabber. Jabber is an open, XML-based protocol for instant messaging and presence, developed by the Jabber community and supported by the non-profit Jabber Software Foundation.

> We chose Jabber over other IM systems because it offers a wide variety of benefits, including its:

-   Open nature: Unlike other proprietary systems, Jabber’s specifications and source code are freely available, allowing anyone to create Jabber implementations at no cost.
-   Simplicity: Jabber uses simple protocols based on XML as its standard data format, and follows the well-understood client/server architecture.
-   Interoperability with other IM systems: Jabber transport modules make it possible for Jabber users to reach other instant messaging systems such as AIM, Yahoo! Messenger, and ICQ.
-   Resource awareness: Jabber provides explicit support for multiple client access. The same user can connect simultaneously to the Jabber server with different clients (or resources), and messages will be routed properly to the best resource available.
