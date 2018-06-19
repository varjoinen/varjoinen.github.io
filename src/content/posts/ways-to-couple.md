---
title: 'Ways to couple'
slug: 'ways-to-couple'
image: 'images/dark_hand.jpg'
date: '2016-02-10T00:00:00'
description: 'The types of interaction and what’s next for integrations'
---

Image CC-BY-NC, [Brett Sayer](https://www.flickr.com/photos/brett-sayer/4011652476)

This has been earlier published in [Medium](https://medium.com/@varjoinen/ways-to-couple-30c37a29c9c8))

In systems interaction coupling means degree of interdependence. The
relationship between two separate system, service or component.

Intrasystem coupling between components of a same system is usually very tight.
In object oriented programming classes reference each other directly or through
interfaces and changes to a component means changes to others with a high
probability. This kind of coupling can be justified and managed inside a system.

Type of interaction between systems varies case by case and different frameworks
and architectures have emerged to address this point of systems design. Older
systems tend to be tightly coupled eg. directly call each others interfaces which
usually also means changes to both systems when one’s interface changes.

---

Newer trends favour loose coupling.

By [Wikipedia definition](https://en.wikipedia.org/wiki/Loose_coupling) loose
coupling means:

> In computing and systems design a loosely coupled system is one in which each 
> of its components has, or makes use of, little or no knowledge of the
> definitions of other separate components.

The benefit of loose coupling can be decreased need to make related changes to
other connected systems when something in one system changes. One way to
achieve this is to have a proxy or mediator between system to abstract and
define the interfaces and endpoints. In large organisations this mediator tends
to be an enterprise service bus (ESB) which offers a platform to connect
systems to each other according to defined business processes.

An ESB offers centralised management of system connectivity and helps to
monitor and react to errors and anomalies in processes. As a middleware it also
helps to implement all necessary business logic that processes need.

But if you think closer this mediator pattern you might notice that while two
systems are decoupled using third one in the middle changes affecting all
systems can still happen. In the coupling point of view middleware only
abstracts interfaces and creates some buffer when dealing with errors.

---

An emerging architectural trend is event drive architecture (EDA). For example
read NGINX’s Patrick Nommensen’s [article](https://dzone.com/articles/event-driven-data-management-for-microservices-1)
about event-driven data management with micro services.

Events are natural units of information transfer. We humans react to events
also. If you are are hungry, you probably eat. “Hungry” event makes you
execute “eating”. This same formula can be used to create serial logic
implemented by services that publish and subscribe to events served by a
broker.

When architectures shift from [plain old SOA](https://en.wikipedia.org/wiki/Service-oriented_architecture)
towards event driven and distributed architecture, traditional centralised
integration solutions face a challenge of not being so distributed and agile.
Before abstracting other systems with monitoring and management capabilities
offered a flexible and robust way to accelerate organisations’ digital
transformation but agile micro-ish services can transform ESB to a burden for
quick development. As an abstraction layer between systems ESB may reduce the
speed of change.

Agile distributed architecture consisting of multitude of systems with
interaction modelled as a series of events doesn’t need a centralised 
bstraction layer. Instead it needs process modelling and visualisation, defined
schemas for events to ensure consistency and tooling to monitor event streams
and state of processes.
