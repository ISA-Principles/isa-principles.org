---
layout: default
title: "ISA: Independent Systems Architecture - Reasoning"
description: Reasoning behind the Independent Systems Architecture (ISA) principles
---

## Introduction

ISA (Independent Systems Architecture) is a collection of best practices.
This page explains the reasoning behind each of the principles it comprises.

## Reasoning

1. *Modularization* has been recognized as an important tool for handling
     large and complex software systems for a very long time. Using
     the term "module" reuses these ideas. Modules imply e.g. high
     [cohesion](https://en.wikipedia.org/wiki/Cohesion_%28computer_science%29) and
     low [coupling](https://en.wikipedia.org/wiki/Coupling_(computer_programming))
     as goals of the architecture, or the
     [single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). Also
     [information hiding](https://en.wikipedia.org/wiki/Information_hiding)
     implies that the data and the database must not be accessed by
     any other module. So there is no need to state these ideas
     explicitly.

2. The architecture proposed here allows for a lot of
   freedom. However, all the modules still need to appear as one. 
   So some decisions need to be done on the level of the Macro
   Architecture. Once defined,
   *Macro and Micro
   Architecture* clearly state what has to be decided on which level.
   The goal is to define as little as possible on the Macro
   Architecture level so that the freedom is not 
   limited without a good reason. Not every detail should be defined
   in the Macro Architecture. Also the Macro Architecture should be
   focused on decisions that are pretty stable in the long run while
   the Micro Architecture decisions are not as stable. Macro
   Architecture influences all modules and is therefore harder to
   change. So it should not be changed too frequently.

2. Separating the modules into *processes, containers, or virtual
   machines* allows e.g. each module to be implemented in a different
   programming language on a different platform. Technical decisions
   are therefore specific to just one module.  
   Also this kind of separation means that each module can crash
   without any of the other modules crashing. This would be different
   if all modules were just part of one process. This benefits
   resilience (see below).

4. Modules are separated into processes (see 2). Therefore local
   method calls cannot be used to integrate them but a different means
   of *integration* is needed.  
   A standard means that a true system is created. If each module is
   integrated differently, it is hard to even consider the result a
   system.  
   At first sight it might seem that one way of
   integration should be enough. But in fact integration will usually
   be done on the UI layer _and_ on the logic layer. That already
   requires two different types of integration. Also there might be
   different cases in the same system where e.g. synchronous and
   asynchronous integration might be useful.
   *Communication* defines the low-level protocol that modules use to
   interact. Of course there is a relation between communication and
   integration. But e.g. REST allows for synchronous as well as
   asynchronous communication. Just as with integration, one option
   for communication might not be sufficient.
   For communication as well as integration the principles only take into
   account the communication among modules inside the
   system. Communication to other systems might be done with a
   different set of integration and communication
   technologies. Sometimes the communication and integration is
   already defined so it cannot be changed by the system. The public
   interface of the system is also different from an architectural
   point of view: It is harder to change because changes will
   influence other systems.

5. Users should not have to log in to each module but
   rather log in once to the whole system.
   So transferring *authentication* information including the
   principals and their roles is
   part of the standardization, too. 
   Authorization is so closely
   linked to the domain logic that it should be done in each module.
   Therefore it is up to each module to allow access or specific
   actions.
   Also other *metadata* besides authentication information might also
   need to be standardized. For example, to trace calls between
   microservices, a unique id for a call and all dependent calls must
   be transfered.

6. Real independence is only possible if each module can be *deployed
   by itself*. The architecture is just a prerequisite. In other
   words: If the architecture allows independent modules but they
   still need to be deployed as a whole, the approach provides only
   part of the desired independence but the major effort will still
   have to be spent.
   In some cases, there is a shared integration test stage. Each
   module is eventually propagated to this stage and tested
   exclusively i.e. all other modules have to wait until that module
   passes the integration test stage. This is an example of a
   dependency bottleneck in the deployment pipelines: The other pipelines cannot
   continue until the module passes the stage. This has to be avoided
   e.g. by using consumer-driven contract tests and mocks to test the
   interfaces  between modules, or by separated integration test
   stages.
   
7. Each module is a separate process, container, or virtual machine
   (2). *Operations* has to deal with each of them and is therefore
   facing a huge challenge. *Standardization* helps dealing with this
   complexity. However, there might still be services with special
   requirements that might use a different approach for
   operations. Also: In a "You build it - you run it" organization
   each team should be responsible for choosing the operations
   approach that fits them best. Most often that will still be a standardized
   approach because that causes less effort for the team. Note that the standard
   only covers the technology. Of course each module might have its
   own set of metrics, alerts, etc.
   ISA needs a high level of maturity concerning operations: Most
   operations procedures have to be automated. Lots of modules have to
   be handled. Lacking this level of maturity might make it impossible
   to implement ISA successfully.
   
8. In a way this is a result of the modularization: Modules might only
   be accessed though the *interface*. This should also be the case for
   any standards e.g. for *operations*. Also standards on the level of
   technology limit the free choice of technology which is a major
   benefit of
   this architecture. However, in some cases it might not be possible
   to limit the standard to the interface level. So the principle is just
   "should".
   
9. *Resilience* at the level of the modules tremendously helps to
   obtain high availability for the overall distributed system. Also a
   scheduler might choose to restart modules or move them to a
   different server. Modules must be able to handle this.
   
