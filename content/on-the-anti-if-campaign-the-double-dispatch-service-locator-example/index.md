---
title: "On the anti-if campaign, the double dispatch service locator example"
description: ""
date: "2008-02-04T00:00:00.000Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/on-the-anti-if-campaign-the-double-dispatch-service-locator-example-75720bb637ef
redirect_from:
  - /on-the-anti-if-campaign-the-double-dispatch-service-locator-example-75720bb637ef
---

I had a good number of jokes and questions since the announcement of the [anti-if campaign](http://brainscrum.wordpress.com/2007/11/26/the-anti-if-campaign/).

Do you want to remove all these if? What’s wrong with the ifs?

So, it’s better to clarify something.

First of all it’s not about removing every single if, it’s about having a more flexible, maintainable and readable code.

A long case (or if then else) statement can be difficult to read and follow, maintenance can be painful.

The first category of if to get of rid of, the most immediate it’s the type based if.

There is clear: something is wrong, the responsibility is not where the if is but in the class itself.

So, an example.

On a project (in a Domain Driven Architecture) we had a fairly long "if type then, else if type then, etc…"

The if chain was on different Tasks Types in a workflow engine.

Let’s imagine that the workflow is an engine for a touch-less car wash system.

So you have, for example:

InsertCoinTask  
2-StepHeatedPreSoakTask  
HighPressureTouchFreeWashTask  
Tire&WheelCleanerTask  
HighPressureRinseTask and so on.

Every task depends on the completion of a previous one and might need a run time configuration.

So, the code was something like this:

if (task is InsertCoinTask)

{ Configure(task as InsertCoinTask) }

else if (task is StepHeatedPreSoakTask) {

Configure(task as StepHeatedPreSoakTask) }  
…  
Inside of a class called TaskServiceConfigurator, were for example a Configure method was implemented like:

private Configure(Tire&WheelCleanerTask task)  
{  
task.TirePosition = touchFreeWashTask.LastCarPosition;  
}  
The different configure methods inside that class (then private!) were setting previous tasks settings, values and so on.

So, pain points:

-   The long if: you can easily forget to configure when adding your task to the workflow to add it there
-   Private configuration methods: difficult to test, not only the configuration but also when testing the task itself
-   Public setters on the tasks: since each task is configured inside the TaskServiceConfigurator all the setting came from there

Solution to this has been a double dispatch.

We added on the Task Interface a method Configure with the ITaskServiceConfigurator as a parameter, like this:

ITask   
{  
Configure(ITaskServiceConfigurator configurator)  
}

Tire&WheelCleanerTask is an ITask and the Configure implementation might look like:

Configure(ITaskServiceConfigurator configurator)  
{  
tirePosition = configurator.LastCarPosition;  
…  
}

The above example probably is too stupid, but the key point is that the LastCarPosition depends on other task (performed or not) it’s really a run-time configuration, a real time dependency between tasks.

I found easier to test the tasks, passing a stubbed configuration and the configuration itself had a definitely better code coverage.

Any better solution to this code redesign is more than welcome.

(Task names are taken from this page: [http://www.autec-carwash.com/](http://www.autec-carwash.com/) :-))
