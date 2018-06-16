---
title: 'Anatomy of microservices'
slug: 'anatomy-of-microservices'
date: '2017-05-09T00:00:00'
description: 'Core parts explained'
---

This has been earlier published in [Medium](https://medium.com/@varjoinen/anatomy-of-microservices-129eb543c3e0)

# Anatomy of Microservices

Structuring complex systems is an interesting challenge that we often face.
That, combined with the need for fast time to market leads us searching for
ways to decompose large projects to more manageable pieces providing value as
soon as possible. There are multiple ways to approach this but one of the
trendiest is microservices architecture. [Microservices](https://en.wikipedia.org/wiki/Microservices)
themselves are small, independent and composable services that have defined set
of responsibilities. They provide a way to decompose large systems to smaller
manageable pieces that are easier to understand, develop and especially
maintain. However they are not a silver bullet as with multiple services comes
all the challenges of distributed systems. More detailed information about
good and bad sides of microservices can be found from Martin Fowler’s
[great article](https://martinfowler.com/articles/microservices.html). Also
some ideas on integration in complex microservices environments can be read
from [my older blog post](/posts/orchestration-vs-choreography/).

In this blog I’ll describe the essential parts of a microservice.

## Building Blocks of Microservice

![alt text](/images/building_blocks_microservices.png "Building blocks of microservices")

Essence of a microservice reduced to bare minimum

I like to decompose microservices to three separate pieces: interface, logic
and data. Breaking things down this way allows us to separate concerns related
to different parts and make it easier to focus specific challenges on design,
implementation and maintenance.

I’ll next describe these three pieces.

### Interface

Interface is an important and unfortunately many times neglected part of a
service. It describes the interactions a microservice enables with surrounding
systems.

With RESTful programming being popular nowadays, [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)
API is a good example of an interface that a microservice can have. RESTful
interface exposes access to resources (data) which the microservice manages. We
could eg. have a pricing microservice that has an API providing pricing
information and ways to manage that information.

On the other hand there could be an asynchronous batch interface implemented
with a message format and queues.

Challenges of interfaces are usually related to interface design: making
interface intuitive and usable for target audience can be hard.

### Logic

Application logic implements given set of functionality, usually related to
some business process or supporting function. Most of software architecture
related decisions are tied to logic of a microservice, for example is control
flow synchronous/asynchronous, what programming language is used or how an
application is composed.

Logic is also the section that intersect the most with business requirements.
Requirements are build into application logic to implement given business
processes and provide value.

Challenges of application logic are usually developer centric: making simple
and performant solutions for complex problems, producing understandable and
brilliant code and making sure with proper automatic tests that logic works as
intended.

### Data

Data is the new oil of digital world and core part of microservices and it can
be itself a valuable asset. Services provide access and functionality related
to specific dataset, eg. product data. Usually data is stored into a relational
or non relational database for persistence.

Data related challenges in microservices consist of modelling data and
maintaining the state of dataset. In complex systems it might be hard to create
a data model that conforms to all given requirements from different data
consuming parties. However there are several frameworks that help with data
modelling, eg. [Domain driven design](https://martinfowler.com/bliki/BoundedContext.html).

Maintaining the state of dataset is a whole issue itself. Data tends to become
inconsistent and invalid if active measures are not taken to keep it consistent
and valid. Without proper application design it is easy to let data drift to an
invalid state.