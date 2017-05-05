---
layout: post
title: PaaS Mission Control
date: 2016-11-22 09:02:24.000000000 +00:00
type: post
published: true
status: publish
categories: [cloud, paas, cloud foundry]
tags: [cloud, paas, cloud foundry, continuous delivery, mission, mission control]
---
![PaaS Mission Control](/assets/mission-control.png){:class="img-responsive"}<br /><br />
When delivering a PaaS platform it is important not to lose focus on the business value.
## TL;DR
* Create and publish a mission statement for your PaaS initiative
* Measure your success & iterate on it to improve
* Make PaaS a quantifiable Value Stream

## Why do we have a PaaS?
Platform-as-a-Service (PaaS) is an enabling technology, rather than an end goal in itself. Deploying your own PaaS can be a complex task that, like most Cloud technologies, changes the challenge from infrastructure to service management.

In amongst the on-boarding, upgrading, automating, managing & monitoring you may find yourself asking “Are things actually better for app teams now?” and not being able to answer with certainty.

## Define The Mission

I strongly advocate working with your PaaS funding provider to create and document a mission statement that defines the business value of your PaaS initiative, one that your major stakeholders sign up to, before you start on-boarding business apps. It must be measurable so that the level of success can be measured.

Example mission statement candidates include:
* provide a low-barrier-to-entry area into which developers can write apps using new technologies
* remove provision of strategic infrastructure technology from the business app delivery cycle in order to speed up time-to-market
* enable business apps to be conceived and delivered to production within the same day
* enable new developer staff to start developing business apps on their first day

The make-up of your PaaS will differ depending upon this statement, for example: if you simply want to provide a developer playground for trying new technology, your PaaS must have them all installed; or to achieve fast time-to-market, then you might choose to only deploy those technologies that are already approved for production.

Obtain backing for your mission from as high up the managerial ladder as possible. With PaaS software in place you may next need to influence a number of teams adjacent to PaaS, which were previously providing infrastructure or services manually e.g. CI / CD services, developer tooling, security, LDAP, accounting/finance. For these teams some change, automation & self-servicing will be necessary, so use your management contacts to make this happen. You should be able to clearly state where these teams are blocking the mission.

## Test The Mission

Test how well you are achieving the mission and iterate on improvement to ensure it is being more and more consistently achieved. For example, if your mission is to be able to conceive a business app and deliver to production on the same day, you could initially write a test that creates a PaaS deployment area (e.g. an Organization on Cloud Foundry), and pushes code to it. Then begin adding the initial pre-requisites into your mission test scripts as surrounding automation is made available: creating a new LDAP group for a made-up team, creating a new source control repository with team access, adding code to it, creating a CI account with code access, creating CI/CD jobs, creating test accounts, creating a team distribution list, creating a new cost centre with finance, etc.

At some point all the mission pre-requisites will be included and the mission met, at which point the continued running of the scripts ensure the stated benefit of the PaaS is realized throughout its life; and ensures that future changes in surrounding infrastructure or service do not interrupt the PaaS mission.

## Measuring Value

At Enterprises, without proof that you're providing a higher purpose than being a simple alternative to VMs, your PaaS platform will be continually compared to traditional infrastructure on unit price alone. Use the measurement of mission to quantify the benefit in monetary terms. For example, for a mission that defines saving time in waiting for traditional infrastructure delivery, if it takes 3 weeks longer elapsed time to deliver on VMs and an 6-man team costs Y per week, each new product is 3 x Y cheaper on PaaS.

Using this method, you can make PaaS a Value Stream for your mission, with a quantifiable value.

## Mission Complete

Alternatives to PaaS will arise over time, eventually as replacements to PaaS. These too can be assessed on their ability to meet the PaaS mission, or PaaS can be removed altogether if the mission itself is no longer relevant.
