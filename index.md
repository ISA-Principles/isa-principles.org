---
layout: default
title: "ISA: Independent Systems Architecture"
description: Independent Systems Architecture (ISA) is a set of principles useful in microservices applications
---

## Introduction

ISA (Independent Systems Architecture) is a collection of best practices based on
experience in particular with microservices and
[Self-contained Systems](http://scs-architecture.org) and the
challenges faced in those projects.

Far too often microservices are adopted but the projects then fail to
succeed. This set of best practices ensures that common pitfalls are
avoided and the promised benefits of microservices are achieved.

However, ISA principles don't always apply - see the [FAQ](https://isa-principles.org/faq.html#is-isa-finally-the-silver-bullet-we-have-all-been-waiting-for) for details.

<script async class="speakerdeck-embed" data-id="bfc13f5bca9141668ff6fbe603137216" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

[Speaker Deck](https://speakerdeck.com/isaprinciples/isa-principles) [PowerPoint](./slidedeck/ISA.pptx)

## Terms

The principles use *"must"* for
aspects that cannot be compromised about and must be present in the
system. *"Should"* is used in principles that have a lot of benefits, but can be
left out in some cases. The principles described here talk about a
system. Usually the IT landscape of an enterprise contains many
systems. Each system might be built with a different set of principles
or maybe even a completely different approach.

## Principles

1. The system must be divided into *modules* that provide
    *interfaces*. Access to other modules is only possible through these
	interfaces. Therefore modules must not directly depend on implementation details
    of other modules, e.g. the internal data representation in a database.
	The rest of the principles define how
	modules might be implemented, and how ISA differs from other
	modularization approaches.
   
2. The system must have two clearly separated levels of architectural decisions:
   - The *Macro Architecture* comprises decisions that cover all
   modules. All further principles are part of the Macro
   Architecture. 
   - The *Micro Architecture* considers decisions which may be taken
   individually for each module.
   
3. Modules must be implemented as *separate processes, containers, or
    virtual machines* to maximize independence and enable a separation between
    Macro and Micro Architecture.

4. The choice of *integration and communication* options must be limited and standardized
   for the system. The integration might be done with synchronous or
   asynchronous communication, and/or on the UI level.
   Communication must use a limited set of protocols like RESTful HTTP or
   messaging.
   It might make sense to use just one protocol for each
   integration option.
   
5. Metadata, e.g. for *authentication*, must be
   standardized. Otherwise the user would need to log in to each microservices.
   This might be done using e.g. a token that is transferred with each call / request.
   Other examples might include a trace id to track a call and its dependent calls through the microservices.
   
6. Each module must have its own *independent continuous delivery
   pipeline*. Tests are part of the continuous delivery pipeline so the
   modules must be tested independently.
   
7. *Operations* should be standardized. This includes configuration, 
   deployment, log analysis, tracing, monitoring, and alerting. There might be
   exceptions from the standard if a module has very specific
   requirements.
   
8. *Standards* for operations, integration, or communication should be
   enforced on the interface level. For example, the communication protocol
   and data structures could be standardized to a specific JSON payload format
   exchanged using HTTP, but
   every module should be free to use a different REST library/implementation.
   
9. Modules must be *resilient*. They must compensate unavailable
   modules or communication problems. They must be able to cope with
   unexpected shutdowns without losing data or state. It must be
   possible to move them to other runtime environments (hosts,
   networks, config etc).
   
NOTE: We created a dedicated page to express the [reasoning behind these principles](/reasoning.html).


## Presentation

You can download a [presentation](./slidedeck/ISA.pptx) about
ISA. It is licensed under a [Creative Commons
Attribution-ShareAlike 3.0 Unported License](https://creativecommons.org/licenses/by-sa/3.0/) so you can use it for your
purposes.
