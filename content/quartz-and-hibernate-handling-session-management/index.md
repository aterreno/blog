---
title: "Quartz and Hibernate — Handling Session Management?"
description: ""
date: "2006-05-06T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/quartz-and-hibernate-handling-session-management-cd3d773d1b15
redirect_from:
  - /quartz-and-hibernate-handling-session-management-cd3d773d1b15
---

How to manage the Hibernate session for the duration of the quartz job execution?  
Quartz/cron jobs by default have their own start-up times which doesn’t always match the application workflow.

If you are using lazy-init entities inside your Quartz Job then you have to initialize them eagerly either through a FETCH or using Hibernate.initialize().
