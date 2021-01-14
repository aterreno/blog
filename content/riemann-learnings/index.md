---
title: "Riemann Learnings"
description: ""
date: "2014-01-27T12:25:01.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/riemann-learnings-29466513eb5f
redirect_from:
  - /riemann-learnings-29466513eb5f
---

We’ve been using and troubleshooting [Riemann](http://riemann.io/) quite extensively in the last few months, here’s a little write up of the main learnings, with the hope that other users might find it useful and don’t repeat some of the mistakes we have done.

**A praise for Riemann**  
To start with, Riemann is a great monitoring tool, its code and the code of the clients I’ve been using is clean, readable and all our issues have been caused by misconfiguration or misunderstanding the tool. The support of Riemann itself has been great, [aphyr](https://twitter.com/aphyr) helped us in more than one occasion with quick, prompt suggestions.

**Why Riemann**  
Why would you spend time in using, configuring and learning Riemann, which comes with a Clojure DSL for configuration?

It does add value, tools like [New Relic](http://newrelic.com/) can be run together with Riemann, but they solve a subset of what can Riemann can provide.

If New Relic is a tool for monitoring and alerting at a high level the performance of an application, Riemann can be configured to monitor business logic in the code and can be finely grained configured to alert. Obviously new relic is a simple tool, drop its jar, configure your java agent and you are done, you have your monitoring/alerting solution up and running.

Riemann providing more needs more, you’ll need to read its docs, understand its goals, limitations and configure it adequately depending on your needs.

**A typical setup**  
We have a Riemann server running in production, few production applications instances (about 12 right now) send events which gets enriched, filtered and forwarded to [graphite](http://graphite.wikidot.com/), to [alerta](https://github.com/guardian/alerta) and eventually forwarded for email reporting to an smtp server.

**Deploy and ‘release’**  
Our process at the beginning was poor, a spike and learn approach, hacking the files on the server, day by day our configuration has grown and now we have a separate github project for the configuration, we copy the files over via Scp and we respect the Riemann file structure that the project has on [github](https://github.com/aphyr/riemann), this allow us to change the bash script to start the process, update and track a new version of the jar and keep the configs in the etc folder.

We test new changes locally by starting it with the exact same startup script, often we just copy the files over and reload the configuration by connecting to the Riemann Repl.

\[code language=”bash”\]  
lein repl :connect 127.0.0.1:5557  
\[/code\]

\[code language=”clojure”\]  
(riemann.bin/reload!)  
\[/code\]

**Riemann ‘good practises’**

-   Split the configuration in multiple files  
    \[code language=”clojure”\]  
    (include “util.clj”)  
    (include “mailer.clj”)  
    (include “graphite.clj”)  
    (include “alerta.clj”)  
    (include “molads.clj”)
-   \[/code\]
-   The configuration grows and we found beneficial to split in different files, each with a clear name and responsibility. We name them as Clojure files making our life easier within emacs.
-   Carefully define your functions and variables: a team on day changed a variable used by the mailer, it took quite some time to troubleshoot the problem and realise that being Riemann configuration written in Clojure everything can be redefined.
-   Leverage use of [LBQ](http://docs.oracle.com/javase/7/docs/api/java/util/concurrent/ThreadPoolExecutor.html) We are currently using LBQ both on the Riemann to graphite/Alerta side, using the function (async-queue!)\[clojure\]  
    (let \[index (default :ttl 300 (update-index (index)))  
    alert (async-queue! :alerta {:queue-size 1000} alerta)  
    graph (async-queue! :graphite {:queue-size 1000} graph)\]  
    \[/clojure\]
-   and also on the Clojure side, wrapping the event sending within this function:
-   \[code language=”clojure”\]
-   (ns clj-components.utils.bounded-executor  
    “See: [https://github.com/aphyr/riemann-clojure-client/issues/9#issuecomment-32624706](https://github.com/aphyr/riemann-clojure-client/issues/9#issuecomment-32624706) to understand what’s going on here”  
    (:import (java.util.concurrent ThreadPoolExecutor TimeUnit LinkedBlockingQueue RejectedExecutionHandler)))
-   (def reject-handler  
    “Handles a rejection on the bounded executor. i.e. when the LBQ is full.”  
    (proxy \[RejectedExecutionHandler\] \[\]  
    (rejectedExecution \[runnable executor\])))
-   (def bounded-executor  
    “Bounded Execution, current settings are calcuated thinking on the current volumes of Riemann In Production”  
    (let \[cores (.availableProcessors (Runtime/getRuntime))\]  
    (ThreadPoolExecutor. 1 cores 5 TimeUnit/SECONDS (LinkedBlockingQueue. 250) reject-handler)))
-   (defn run-bounded \[f\]  
    “Exectutes f in a bounded executor”  
    (let \[executor bounded-executor\]  
    (.execute executor (Thread. f))))
-   \[/code\]
-   For a deep explaination on why using LBQ follow the discussion on this issue on [github](https://github.com/aphyr/riemann-clojure-client/issues/9#issuecomment-32624706)
-   We had problems with TCP without LBQ, we switched to UDP but then noticed that the java client used by the Riemann client to send events swallows exceptions when the connection is closed, until this bug will be fixed, I’d recommend using TCP with LBQs as there’s no way to recognise a disconnected UDP client. More on this on the same github issue, just down on the same [thread](https://github.com/aphyr/riemann-clojure-client/issues/9#issuecomment-32971989).
-   Don’t use it as a datastore: a silly mistake: keeping data too long on the index will lead to poor performance, Riemann is designed to process events which have a short life and little state, keeping your events for more than few minutes will lead to obvious performance problems. Make sure you set a reasonable default ttl on the events in the index.
-   Don’t query the index too often This is the last finding: we were trying to set a flag for maintenance mode when deploying applications, to stop events propagation, however we were querying the index all the times to check if Riemann was set in maintenance mode for a certain application, this was growing somehow the heap allocation day by day. As it’s a recent finding/topic you might find some interesting comments in this github [issue](https://github.com/aphyr/riemann/issues/312).
-   Leverage the java toolset: we configured Riemann to run with NewRelic, Jmx and Yourkit, without these tools it would have been really hard to find out where the problems where, the java command would be enriched with something like:  
    \[code language=”bash”\]  
    JMX\_OPTS=” -Djava.rmi.server.hostname=10.250.76.85 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.port=9100 -Dcom.sun.management.jmxremote”  
    AGENT\_OPTS=”-javaagent:/opt/molsfw/newrelic/newrelic.jar -Dnewrelic.environment=production”  
    PROFILER\_OPTS=”-agentpath:/opt/molsfw/yourkit/libyjpagent.so”  
    \[/code\]
-   **In conclusion** I’ve been very positevely impressed by the tool and by the support and received, the DSL might be a little hard to remember if you don’t play with the code too often but the power of the tool is impressive. Reading the Guardian’s [Riemann config](https://github.com/guardian/riemann-config) has been a great source of inspiration and I encourage whoever can to share their Riemann configuration.
