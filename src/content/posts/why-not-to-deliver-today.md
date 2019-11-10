---
title: 'Why not to deliver today?'
slug: 'why-not-to-deliver-today'
date: '2019-11-10T00:00:00'
description: 'How to deliver multiple times a day'
---

Is delivering to production painfull and time consuming task that you wouldn't
want to do so often? There is always a huge risk of outage or something breaking
when applying changes to otherwise stable environment? Developers fear the day
of delivery and the sleepless nights they will need to have fixing bugs? There
are some crazy people suggesting to deliver even daily, who wants to deal with
these issues all the time?

These kind of feelings and scenarios are actually quite common in the IT
industry. The fear of delivery makes everyone from top management to developers
wanting to avoid it at any cost because it always causes so many issues. And who
wants to do so stressful thing more often?

## What makes us fear the delivery

Often delivery is feared because there is no confidence that something wouldn't
break. Bugs and other issues translate to lower user satisfaction and higher
cost of operation. There might also be strict deadlines or content set for the
deliveries which makes the work even more stressful for the development
organisation.

I have observed many cases where this has happened. Often the common nominators
for the situation include (not a definitive list, there can be many more
reasons):

* Lack of development process automation
* Lack of (automated) testing
* Lack of ownership of the end-to-end delivery process

Let's analyse these issues.

### Development process automation

Nowadays there are many examples available on how to automate development
process so that teams can focus on delivering value. However in many
organisations teams are not given time or resources to automate their build or
testing processes (or improve them), which leads to manual and error prone
practices as quality assurance and delivery will compete with new features
and other demands from customers and management.

Automated processes enable repeatable process without risk of manual errors.
They also free developers to focus on more productive work.

### (Automatic) testing

Testing the code written should be quite obvious part of the software
development practices. In some cases implementing features feels more exiting
than writing tests, however without tests there is no proof that the code works.
No tests or poor tests usually lead to issues in production environment and low
perceived quality of a service or a product.

I have written earlier an article about
[testing](/posts/crafting-quality-software-chapter-2/). Tests are the proof your
service is working as it should be and gives you confidence to further automate
the delivery process. Every feature that is implemented should include tests to
prove it works as it is designed to. Otherwise you are just hoping or silently praying
that your service works after the next deployment.

### Ownership of delivery

Ownership in general is usually an organisational issue. Many organisations are
not structured to optimise the value delivery in the digital world and teams are
not empowered to ensure the success of the service or product that they are
developing. The path from idea to production might include multiple hand overs
in the organisation, from one silo to another. When there is no collaboration or
ownership of the end-to-end process of delivery every silo (sub)optimises its
own performance instead of the whole process.

In many cases organisations structured around customers or value streams,
working in agile ways, perform better than siloed ones. The best results I have
seen are from organisations with multidisciplinary teams containing all the
needed capabilities for end-to-end delivery.

## From fear to continuous delivery

Analysing the issues of delivery process leads to understanding the painpoints.

In highly performing organisations the issues have been tackled by building
confidence to be part of the delivery process by automating the development
processes, adding automated testing for quality assurance and enabling teams to
succeed by giving them freedom and responsibility to deliver value.
