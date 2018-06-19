---
title: 'Crafting quality software, chapter 2'
slug: 'crafting-quality-software-chapter-2'
image: 'images/quality_puzzle.jpg'
date: '2017-02-02T00:00:00'
description: 'Making sure it works before its too late'
---

Image CC BY 2.0, [Elizabeth Hahn](https://www.flickr.com/photos/128185330@N03/)

This has been earlier published in [Medium](https://medium.com/@varjoinen/crafting-quality-software-chapter-2-37d74a3d7d64)

I started a series of writings describing some important aspects of creating
quality software. In the [first part](/posts/crafting-quality-software-chapter-1/)
I focused on one of the most important piece: people. In this second part I’ll
circle a bit around the actual software development process and talk about
testing.

---

So why testing is a topic of importance? Wouldn’t it be easier just to write
code and run it as good programmers don’t make mistakes nor create buggy code?
We do it in agile way and deploy anyway multiple times a day to production. If
there are issues, we’ll fix them fast. And by the way, we don’t need
documentation.

One could think like that until a complex time consuming issue halts critical
production process for hours and coders stay up whole night hunting the root
cause. Afterwards proof that software works and does what it is supposed to do
starts to sound a good idea.

![alt text](/images/spheres_of_dev_anxiety.png "Spheres of developer anxiety")

Spheres of coder anxiety

Based on my experience I would divide testing to six categories pictured above.
If you have ever let a bug slip through your quality assurance process, you may 
know why I have colour coded the spheres like that.

I’d argue that the sooner issues are detected the cheaper they are to fix. A
bug working its way to the utmost sphere has a potential effect to business as
it will only be noticed in production environment or worse, it won’t be noticed
and it silently causes damage.

There are multiple barriers for ensuring that applications work as expected and
I’ll next describe few of them.

## Quality code

First step in testing is developers themselves. Application logic should be
designed and design critically reviewed. After that implementation should be
done and reviewed by someone else if possible.

This way ideas and designs get challenged and developers have to rationalise
their decisions before actual code is written and after implementing a
solution. Sharing thoughts also helps to pass on knowledge from peer to peer.

## Unit tests

[Unit testing](https://en.wikipedia.org/wiki/Unit_testing) ensures that
separate units of code are tested and refactoring and adding new functionality
can be done with confidence as tests verify that nothing breaks.

Of course it is important to write tests that matter. This is usually balancing
between confidence, project resources and application criticality. Some demo
application maybe doesn’t need rigorous testing but with core banking software
there needs to be confidence that it really works as expected.

Some code analysis tools like [SonarQube](https://www.sonarqube.org/) may
complain about not writing unit tests for [POJOs’](https://en.wikipedia.org/wiki/Plain_Old_Java_Object)
getters and setters but more experienced developers will be confident enough to
not to do that.

Good unit tests tell early if something breaks because they are usually run
before even committing changes to version control (or at least should be run).
This way it is harder to let broken code spread across a project.

## Integration tests

[Integration testing](https://en.wikipedia.org/wiki/Integration_testing) or as
I also like to call it, black-box testing, assures that applications or their
components work through their defined interfaces and with systems they are
dependent on. For example [AWS](https://aws.amazon.com/) related applications
would test that their integration with various AWS managed services work as
expected. Database facing applications would check that all interactions with
database work and have anticipated results.

Inter-process testing helps noticing possible issues with application and its
dependent systems. This is especially handy when there starts to be multiple
versions of components or there is upgrades to external components like
databases or third party APIs.

## Acceptance tests

[Acceptance](https://en.wikipedia.org/wiki/Acceptance_testing) testing helps to
ensure that functional and non-functional requirements defined for an
application and/or set of applications are met. Criteria for acceptance should
give confidence that applications deliver their intended functionality with
defined constraints and performance.

Systematic acceptance tests can provide a consistent and scalable framework for
assuring operability of systems through whole business processes that create
the actual value for organisations.

There are frameworks like [Robot Framework](http://robotframework.org/) for
implementing and automating acceptance tests.

## Exploratory tests

[Exploratory testing](https://en.wikipedia.org/wiki/Exploratory_testing) is not
always part of a quality assurance process but can yield valuable input for
development team. It can be a phase in the process or culture that is followed
through a project. Committed developers and testers or clients can personally
try out software and give input to the team.

Back-end applications do not usually have exploratory testing planned but at
least in the security point of view trying to penetrate or break systems
continuously during development cycles can lead more secure software.

A dedicated tester can also bring fresh ideas to a project and in a project
containing front-end component spare a team from issues that first end-users
tend encounter if no one has tested the product outside of the development
process.

## Monitoring

I wanted to include this to the context as ways of working are shifting more
towards [DevOps](https://en.wikipedia.org/wiki/DevOps) culture. After going
live systems are monitored and “tested” in production use. Feedback is gathered
and fine-tuning is done, lessons are learned and applications are made better.

Automation and visualisation are key terms with monitoring. Data gathering from
various servers should be automated and information processed via well defined
workflows that also visualise the data for those who operate the systems. This
way there is a constant feedback loop and some issues can be prevented
proactively.

---

Testing is an important part in crafting quality software. Wise developers
write enough tests to be confident that nothing important breaks if code is
refactored or new functionality is added. Testing should also be automated as
much as possible to make it easy and seamless part of the software development
process.