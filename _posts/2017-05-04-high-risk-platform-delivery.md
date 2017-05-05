---
layout: post
title: Platform delivery - part I - high risk
date: 2017-05-03 06:30:21.000000000 +01:00
type: post
published: true
status: publish
categories:
- cloud
tags:
- cloud
- shared platform
- paas
- caas
- high risk
---
![Risks ahead](/assets/risks-ahead.jpg){:class="img-responsive"}<br /><br />
IT departments often choose to deliver their own shared platform for app teams, rather than opting for cloud-based alternatives. This might be for shared logging, monitoring, platform-as-a-service, container-as-a-service, functions-as-a-service, etc. This post describes some common mistakes...<br />
### TL;DR
The biggest risk is in delivering the 'wrong thing'. The most likely way to do this is:
* make platform choice based on platform provider marketing or gut feel
* fail to define a clear service level
* define platform success based on app team take-up

Its all too tempting for Enterprise IT management to use a high risk approach to selection and delivery of  shared IT platforms without realising there is a better way.

[Part 2 of this blog]({{ site.baseurl }}{% link _posts/2017-05-04-low-risk-platform-delivery.md %}) proposes a low-risk approach to the same challenge.

### Approach

The process starts with some pushing for the introduction of a new technology from technical resources within IT and application teams. Requirements are vague, however its clear the industry is moving in a certain direction & online material suggests the technology will definitely improve app time-to-market.

IT management initially resists, however supported by some *gut feel* (e.g. do we really need this many Linux engineers?), and after a sufficient amount of pushing from The Business, IT management succumbs and decides to deliver a shared platform that meets user requirements.

A small team is formed to define a strategy, lets call this the platform delivery team.

### Risks

There will be a variety of permutations for delivering the platform, not least: technology provider; technology capabilities/options; hardware/software dependencies; redundancy / failover; load-balancing; statefulness; HA deployment pattern; clustering / distribution support; and especially cost.

The biggest risk is providing a platform that does not suit user requirements. This is mostly likely to happen due to:

* missing functional requirements e.g. support for specific technologies on the platform
* missing non-functional requirements e.g. data retention period, request latency maximums
* platform design choices e.g. platform feature turned off, only runs on vSphere
* mis-judging service level e.g. meeting the functional/availability/performance/cost requirements of a small number of very demanding users whilst missing a lower-level service that would suit everyone else
* introducing unsuitable process e.g. placing a ticket-based on-boarding with a 5 day SLA for a platform aimed at having a low barrier-to-entry

### Provider Selection

One easy, early route to failure is to consult on technical requirements with every potential app team customer & treat each requirement as gospel, in which case the team gets caught in an analysis paralysis & fails to deliver the platform completely.

To avoid this the IT management checks for market positioning of the major technology providers with 3rd party technology analysis, perhaps reading material from, or contacting, Gartner / Forrester.

At this point there is usually some inward debate between the top 2 technology options (e.g. Kubernetes vs. Mesos, Cloud Foundry vs. OpenShift), which is decided by the provider with the best marketing material, the highest number of Meetups, or the best representation from 3rd party analysis firms.

The requirements across all the Enterprise's apps seem too various to collate & prioritise. So a technology provider is 'picked' based on strength 'religious' fervour & crucially, necks & careers are often placed on the block based on this best-guess decision.

### We did it!

A full platform is designed and built. The platform delivery team agonises over the *right* choice on a myriad of implementation details, with the aim of matching up to the marketing material on the provider website.

The shared platform is made available to some early customers and they on-board. They begin to use the platform to support development / test and proclaim success. Backslappings all around.

### Improvement Cycle

After a short while cracks start to appear:
* the platform has to be upgraded for security & functionality reasons
* there is no suitable time that suits *all* the platform customers
* uptime is not 100%
* the underlying platform infrastructure maintenance results in apps on-platform getting unexpectedly affected (e.g. restarted)
* performance drops slightly as more apps are on-boarded
* the true platform service level becomes clear
* the true cost using the platform becomes clear

In the absence of an explicit service level definition, the app teams have naturally translated their prior experiences with other similar environments as assumptions over the new shared platform behaviour.
The marketing material on the technology provider website uses phrases like 'zero-downtime' and 'always-on', supporting potentially unrealistic user expectations.

Without an availability target users expect 100% uptime; app owners would prefer to retain the performance levels they first experienced when the platform was virtually empty; app ops teams have to run more app instances to meet their availability targets - the perceived cost of running on the platform as gone up!

### Fix it!

Pressure builds on the platform delivery team to _do better_ in ways that are incompatible with platform maintenance. This constrains their ability to manage the platform well, since most management activities require some minimal disruption. High levels of change management are placed around the platform, which raises the cost & reduces the frequency of platform change. The platform design moves away from the provider roadmap or specific customisations are made in order to increase uptime/performance/value & the cost of platform change goes up further. The platform technology version begins to lag behind the provider roadmap & support costs go up.

### Success?

Remember the neck-on-the-block IT strategy decision earlier? Well soon enough a natural time comes to assess the success of the shared platform. Without any explicit service metrics, the platform is judged on the take-up by app teams & a *gut feel* for the business benefit realised versus the amount of headache that has been caused.

At this point take-up may have begun to drop because the platform & delivery team are seen as difficult to get on with & not living up to expectations. Other technology providers are suggested as better alternatives. Earlier technology decisions are revisited with the benefit of hindsight. Expertise is called into question.

Most importantly the suitability of the decision to use the specific technology cannot be analysed separately from the success in meeting the platform requirements because there was no specific platform service detail captured up front.

There must be a better way!

In [part 2 of this blog]({{ site.baseurl }}{% link _posts/2017-05-04-low-risk-platform-delivery.md %}) I propose a lower-risk approach shared platform provision, based on lean methodologies.
