---
title: "You might want to keep an eye on these four opensource project…"
description: ""
date: "2009-02-03T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/you-might-want-to-keep-an-eye-on-these-four-opensource-project-270ad9c38653
redirect_from:
  - /you-might-want-to-keep-an-eye-on-these-four-opensource-project-270ad9c38653
---

-   [Apache ODE (Orchestration Director Engine)](http://ode.apache.org/index.html) executes business processes written following the [WS-BPEL](http://ode.apache.org/ws-bpel-20.html "WS-BPEL 2.0") standard. It talks to web services, sending and receiving messages, handling data manipulation and error recovery as described by your process definition. It supports both long and short living process executions to orchestrate all the services that are part of your application.
-   [JBoss DNA](http://www.jboss.org/dna/) is a new unified repository system that is JCR-compliant and capable of federating information from a variety of systems. To client applications, JBoss DNA looks and behaves like a regular JCR repository that they search, navigate, version, and listen for changes. But under the covers, JBoss DNA gets its content by federating multiple external systems (like databases, services, other repositories, etc). This way, the unified repository content stays up-to-date and in sync, even though the external systems still own the information and existing applications still work. Plus, JBoss DNA sequences the content in the repository, extracting patterns and structured content that makes the repository more useful and effective.
-   [Convergence](http://www.openspaces.org/display/CVG/Convergence) is a project aimed at integrating Computational Grids with In-Memory Data Grids (IMDG)
-   [**SubRecord**](http://www.subrecord.org/features) **is a stack of enterprise aspects**:

> **Data repository**

-   repository for storing flexible records in Amazon SimpleDB manner
-   CRUD
-   underlying storage is HBase — distributed storage for massive data hosting — [Learn more…](http://www.subrecord.org/repo)

> **Logs repository**

-   Collecting logs from many sources/interfaces like (remote) files, JMS, HTTP and dedicated API

> **API/interface**

-   RESTful services channel — [Learn more…](http://www.subrecord.org/tutorial)

> **GUI/Console interface**

-   GUI interface with many capabilities
-   Trace/control Core module in real time

> **Tracing events (CEP/ESP)**

-   Registering logical events that can be identified and used in rules
-   Rules can trigger specifing events to alert/trigger another events on some specific circumstances

> **Metrics**

-   Measuring time of invocations — record time/context before service is invoked and after
-   Collect metrics reports for specific services

> **Processing (data)**

-   Collected data can be processed by scheduled, automatic tasks
-   Unification of models can be done using adaptive processing
-   Aggregating, normalizing,…

> **Session management**

-   Providing session token based authentication/authorization across multiple applications
-   Authenticate once and be logged to entire federation of applications, SSO

> **Application monitoring**

-   Monitoring services
-   Report failures

> **OSGI integration**

-   The application is supposed to be an OSGI bundle
