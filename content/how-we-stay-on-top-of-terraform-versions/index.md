---
title: "How we stay on top of terraform versions"
description: "At Labrador we have all our infrastructure in code, we use AWS and love Terraform."
date: "2017-12-01T17:55:04.524Z"
categories: []
published: true
canonical_link: https://medium.com/@javame/how-we-stay-on-top-of-terraform-versions-4987ef4abae7
redirect_from:
  - /how-we-stay-on-top-of-terraform-versions-4987ef4abae7
---

At [Labrador](https://www.thelabrador.co.uk/) we have all our infrastructure in code, we use [AWS](https://aws.amazon.com/) and love [Terraform](https://www.terraform.io/).

In my previous gig I’ve been trough the pains of upgrading Terraform and here I’ve (almost accidentally) found a way to stay on top of the versions.

We run our plan and apply continuously (git push on master) on [Concourse CI](https://concourse.ci/): we love this CI/CD tool, it’s so command line, API, configuration, container driven, it enables us to do the right thing, by default.

On Concourse we always pull the latest [hashicorp/terraform](https://hub.docker.com/r/hashicorp/terraform/) image from docker hub to run the plan/apply: that way we will fail fast the build if the new version introduces some regression bugs on our infrastructure code.

On local development we use [tfenv](http://brewformulas.org/Tfenv), and we have a _.terraform-version_ file on git, if you try to plan after the CI applied with a higher version of terraform you will get an error, that way it’s easy to keep that file and the terraform version locally up to date.

I’ve updated today my terraform to 0.11.1, what’s your version? ;)
