---
layout: default
title: "ISA: Independent Systems Architecture - Non Principles"
description: Independent Systems Architecture (ISA) leaves some principles out - why?
---

## Introduction

ISA (Independent Systems Architecture) is a collection of best practices. However, it
does not define the complete architecture. This page explains
additional principles that are not part of ISA and why they were left out.

## Non-Principles

* ISA defines the technical aspects of modules. How the system is
  split into modules is beyond this
  website. [Domain-driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)
  and
  [Bounded Context](https://en.wikipedia.org/wiki/Domain-driven_design#Bounded_context)
  are good guidelines. But sometimes technical modules are needed and
  separation for reasons like scalability might also be
  important. Getting the right split into modules is hard and
  therefore cannot easily be put in a few principles.

* This architecture can have a huge organizational and culture
  impact. The approach allows for better separated modules which allow
  for independent, self-organized
  teams. [Conway's Law](https://en.wikipedia.org/wiki/Conway%27s_law)
  states that software architecture reflects the social boundaries in
  the team so there is strong relation between the organization and
  the architecture. However, ISA work without adjusting the
  organization so the idea is broader applicable in this way.

* The principles do not give a preference for communication protocols or
  operations technologies. The principles state principles, not
  concrete technological decisions.
  
* The principles provide benefits like independent scalability, load
  balancing and high availability. However, these are results of the
  principles and not principles by themselves. So they are not
  explicitly mentioned.
  
* The principles present problems like inconsistent data. These are
   fundamental challenges of distributed systems and need to be dealt
   with. This is beyond the definition of ISA.
