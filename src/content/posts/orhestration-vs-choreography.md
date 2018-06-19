---
title: 'Orchestration vs. choreography'
slug: 'orchestration-vs-choreography'
image: 'images/choreography.jpg'
date: '2015-10-11T00:00:00'
description: 'Blending microservices and integration architecture'
---
Image CC BY-SA 2.0, [hernanpc](https://www.flickr.com/photos/hernanpc/)

This has been earlier published in [Medium](https://medium.com/@varjoinen/orchestration-vs-choreography-9cec9e137910)

Technology nowadays starts to be mature enough for microservices to be adopted
by mainstream developers. Containerization, provisioning and build automation
tools make it easy to create new services quickly. Focal points for these
services are agility in transformation and manageability as microservices have
clear responsibilities.

Traditional software mixes multitude of responsibilities and features together
and makes it harder to make changes without breaking something in the process.
Microservices tackle this by separating functionality to smaller pieces that
are easy to test and manage.

What this trending shift from traditional software to microservices mean in
organisational context is more agile and faster development, simpler services
with clear responsibilities and a new way of managing and producing services.
However microservices are not a silver bullet that kills the complexity.
Actually microservices come with all the complexity that distributed systems
have.

---

Slicing software to a big set of smaller services has huge impact to
integration architecture. Traditional orchestrated ESB driven architecture
starts to slow down the agility and idea of microservices quite fast. As a
centralized solution ESB becomes a bottleneck when it tries to abstract and
connect hundreds of microservices together in a fast, changing environment.

Integration architectures with ESB based solution made it easy to manage
interactions between traditional software systems and leverage the power of
business processes. This way there is no direct connections between systems and
interfaces and communication methods can be abstracted.

However centralized integration solutions mean centralized management and
changes when there is new or changing requirements. This wouldn’t be a problem
with traditional systems but with microservices changes happen more often as
the building blocks are much smaller than with larger systems.

---

With microservices integration architecture needs a new point of view. Rapid
and lean development accompanied with automated build processes cut down costs
attached to changes.

> I think that integration architecture with microservices should also adapt to
> the idea of smart services and dump (data)pipelines.

Nic Ferrier has [a great piece of writing](http://nic.ferrier.me.uk/blog/2013_12/what-is-service-choreography)
about this.

Integration architecture with value added services would be more about
designing communication patterns with event driven messaging, aggregating and
managing events to form clear view to operative processes and providing
services like API management to support businesses.

---

It’s clear that current integration practices do not blend well with
microservice ideology but it takes time for microservices to become mainstream.
Being extreme SOA microservices require new ways of thinking to make them
manageable in long run.