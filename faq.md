---
layout: default
title: "ISA: Independent Systems Architecture - FAQ"
description: Frequently asked questions (FAQ) about the Independent Systems Architecture (ISA)
---

Frequently Asked Questions
---

### Why the term "ISA"?

Independent Systems Architecture describes the concept quite well:
Build many small systems instead of a large monolith. Make those
systems as independent as possible, and therefore aim for decoupling.

### How is ISA different from microservices?

ISA is one possible approach to building microservices. However, there is little
agreement over what microservices actually are and how you should
build a microservices system. ISA defines some best practices that
have been working in many projects.

### How is ISA different from SCS (Self-contained Systems)?

[Self-contained Systems](http://scs-architecture-org) define a
specific type of systems because each SCS and therefore the system has
to have a UI. Also SCS should be integrated asynchronously or on the
UI level. ISA is broader because a system that just provides an API
and no UI can be a ISA, but not an SCS. Also ISA does recommend a specific
type of integration.

ISA covers topics like operations and micro / macro architecture that
are not part of SCS.

So SCS and ISA are two different concepts that might be combined.

### Is ISA finally the silver bullet we have all been waiting for?

No. Like any other architecture, ISA is a trade-off that fits some
scenarios quite well while it might not be a great fit for others.
The fundamental idea of ISA is to separate a system into
very loosely coupled modules that can be deployed and developed
individually. This works great for applications that can be deployed
frequently and fine grained, i.e. they are hosted in a private data
center or the public cloud. It might not work too well in environment
that focuses on less frequent deployments and monolithic deployment
units, e.g. mobile applications distributed via an app store or
games. Note that this is not clear cut. Also it is possible to use at
least some of the ISA ideas for these scenarios.

### How can I use this document?

This document is licensed under a Creative Commons Attribution-ShareAlike license,
i.e. you can essentially use it as you see fit, as long as you
include proper attribution and share your modifications under
the same license. We explicitly encourage you to recommend,
compare or develop frameworks according to this style, and
intend to be as open as reasonably possible while maintaining
conceptual integrity. We welcome pull requests to this site: You
can find the repository on [GitHub](https://github.com/innoq/ISA).

### Can I provide feedback?

Of course, please use [the comments](discussion.html) to
share your thoughts. We welcome criticism as well as suggestions for
improvement.
