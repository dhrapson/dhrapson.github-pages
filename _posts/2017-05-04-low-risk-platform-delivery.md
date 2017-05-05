---
layout: post
title: Platform delivery - part II - low risk
date: 2017-05-03 06:30:21.000000000 +01:00
type: post
published: true
status: publish
categories:
- cloud
tags:
- cloud
- disruptive innovation
- shared platform
- paas
- caas
---
![Low Risk level](/assets/high-low-risk.jpg){:class="img-responsive"}<br /><br />
There are many ways to fail when delivering shared IT platforms, and in [part 1]({{ site.baseurl }}{% link _posts/2017-05-04-high-risk-platform-delivery.md %}) I described a typical high-risk delivery strategy often chosen by default. In this post I propose a better, low-risk way.<br />
### TL;DR
* work with a small number of app teams with clear requirements, to define a [mission statement]({{ site.baseurl }}{% link _posts/2016-11-22-paas-mission-control.md %})
* work with technology providers to define service level / cost options
* follow Lean Startup techniques for service level selection & PoC
* validate mission is met & measure service levels
* keep job

### Approach

IT departments often choose to deliver their own shared platform for app teams, rather than opting for cloud-based alternatives. This might be for shared logging, monitoring, platform-as-a-service, container-as-a-service, function-as-a-service, etc.

The process starts with some pushing for the introduction of a new technology from technical resources within IT and application teams. It is clear the industry is moving in a certain direction & online material suggests the technology will definitely improve app time-to-market.

A small platform delivery team is formed to define a strategy.

### App teams

The platform delivery team should work with a small number (max. 3) app teams, ideally with slightly differing requirements, to define a clear business benefit. A definition of the business benefit that suits this small sample should be formed as a [mission statement]({{ site.baseurl }}{% link _posts/2016-11-22-paas-mission-control.md %}).

Using Platform-as-a-Service (PaaS) as an example, a number of the examples below might apply:

* take an app from idea to production within 1 day
* provide existing developers a low barrier-to-entry developer prod-like deployment environment
* give developers an environment to try out deployment of apps on new languages / frameworks
* isolate app teams from deployment environment details
* provide an environment on which high-change apps can continuously deliver
* reduce operating system licensing costs

### Risks

The risks are the same as I highlighted in [part 1 of this blog post]({{ site.baseurl }}{% link _posts/2017-05-04-high-risk-platform-delivery.md %}), copied below for reference.

There will be a variety of permutations for delivering the platform, not least: technology provider; technology capabilities/options; hardware/software dependencies; redundancy / failover; load-balancing; statefulness; HA deployment pattern; clustering / distribution support; and especially cost.

The biggest risk is providing a platform that does not suit user requirements. This is mostly likely to happen due to:

* missing functional requirements e.g. support for specific technologies on the platform
* missing non-functional requirements e.g. data retention period, request latency maximums
* platform design choices e.g. specific technology dependency on Docker, platform feature turned off
* mis-judging service level e.g. meeting the functional/availability/performance/cost requirements of a small number of very demanding users whilst missing a lower-level service that would suit everyone else
* introducing unsuitable process e.g. placing a ticket-based on-boarding with a 5 day SLA for a platform aimed at having a low barrier-to-entry

### Provider Service Definitions

There is usually an early debate between the top 2 technology provider options (e.g. Kubernetes vs. Mesos, Cloud Foundry vs. OpenShift). Rather than relying on 'religious' fervour of its team members, or general provider popularity, the platform delivery team should work with the contenders to define target Service Levels for the platform, given the recommended platform architecture. Use the [Google SRE Service Level](https://landing.google.com/sre/book/chapters/service-level-objectives.html) concepts to support your Service Definition:
* Service Level Indicator (SLI) - a carefully defined quantitative measure of some aspect of the level of service that is provided
* Service Level Objective (SLO) - a target value or range of values for a service level that is measured by an SLI

Come up with 2 Service Level options per provider. Be sure to use the same Service Level Indicators &  method of measurement across providers. All of the options should be cost-neutral to IT in that the various license, subscription, hardware, shared service (e.g. storage, network) & human resources costs should be bundled in for each option, for recharge to consumers of the platform. This opens the door for customer preference alone to drive the decision.

### Example SLI / SLO Options

| Service Level Indicator | Service Level Objective (option 1) | Service Level Objective (option 2) |
|---|---|---|
| Uptime measured via 1 request per second from an off-platform client | 99.9% | 99.99% |
| Planned Outage requirement & frequency | 2h/week | 1h/year |
| Platform API Uptime measured via a user login request every 5s |  99% | 99.5%  |
| Request Latency - e.g. 99th percentile platform response time of HTTP requests | <1s  |  <0.5s |
| Error / Loss rate e.g. log loss | 5% | 1% |
| Cost | $0.05/hour | $0.50 |
{:.mbtablestyle}

### Service Definitions

Create a Service Definition for each Service Level option. This Service Definition should define at a high level how users will interact with the platform and operational team, which will differ between options.

Within each definition, state that you intend to use the [Google SRE](https://landing.google.com/sre/book/chapters/introduction.html) concept of an Error Budget. At a high level this concept acknowledges that platform stability is generally inversely proportional to the level of platform change & allows the platform owner the ability to continue updating the platform, perhaps causing minor outages, and hence 'spending' the Error Budget up until the point SLOs are not being met. At that point the only changes allowed are to make the platform more stable. A fairly short service metric timeframe should be set to avoid complete lock-up of platform fixes (e.g. 1 week).

## Service Selection

At this point the wider app team community can be presented with the Service Definitions and requested to provide feedback or vote on the various options. A 'None of these suits me' option should also be provided to differentiate teams uninterested in contributing, from those uninterested in the options.

Expect some spread here, for example: high-importance, high-change apps may be happy to pay a high price for highly available, flexible platform; whilst low-importance, low-change apps may not. Select option(s) that provide the highest business value.

This information-gathering process is based on the [Lean Startup validated learning concept](http://theleanstartup.com/principles) & frees up IT management from making career-altering service delivery choices, risky technology provider decisions or being forced to use *gut feel*.

## Platform Validation

Having chosen a service definition & underlying provider, the platform delivery team can go ahead and deploy the smallest PoC copy of the platform software. The next step should be to validate that the [mission statement]({{ site.baseurl }}{% link _posts/2016-11-22-paas-mission-control.md %}) is met by the platform _within the deployed environment_ using scripted automation. Pre-existing infrastructure and/or security standards are the factors most likely to affect this result.

In the instance that the platform validation fails, it should be possible to push back on the platform provider for changes, or switch to a PoC of the second favourite option amongst app teams. PoCs are not a new concept, however running them to validate the service definition rather than obtain user feedback does provide specific [validated learning](http://theleanstartup.com/principles) about the platform.

With mission validated, a small set of platform consumers could use the PoC environment in order to provide validated learning around platform clients & tooling, if required, or the infrastructure scaled to validate distributed deployment.

## Indicator Monitoring

Once the PoC environment has passed validation, a full copy of the platform infrastructure can be deployed. SLI monitoring must be introduced & dashboards should be introduced that display RAG status against SLIs, to make it clear to customers when the Error Budget has been spent. This can be developed in parallel with the platform infrastructure delivery and even initial application on-boarding, provided that the first customers accept this lack of metering.

## Success?

Since we now have SLIs, we can judge the operational success of the platform on its history of meeting the service SLOs. The underlying platform technology provider can be assessed by the same metrics in conjunction feedback from the platform delivery/support team; alternative technology providers might be considered if the provider tools caused SLOs to be missed or had a high operational overhead.

Platform take-up is an indicator of technology popularity, useability, or suitability to the company, rather than on technology decision-making.

The platform service decision, made in support of providing high perceived business value, and the technology decision, made gradually & with user support, should no longer adversely affect IT career progression having been made in a lean, low-risk way.
