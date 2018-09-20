---
layout: post
title:  "Death Star Architecture - The Domain Event Edition"
date:   2018-03-18 11:40:48 +0000
categories: architecture lean design patterns ddd
---
# Death Star Architecture - Your event source can be evil

Last time I wrote about how using a database as your integration point is a crime, will cause rebels and ultimately will lead you to the dark side.

Whilst doing that I made light of how you can take a diagram of a domain event based architecture with bounded contexts being integrated via an event source and pointed out that its essentially the same picture.

- Is integrating through an event source better?

The problems of the deathstar were

1. Value streams crossed deployed code making changes, business processes, timed jobs etc
1. Complex business logic can be triggered inside the source of record by events taking place inside
1. Business logic hidden from code base in the source of record
1. Failure to model the domain(s) and isolate them
1. Single database, rather that source of record per domain

All these problems can be replicated in an event source.

Most of these problems can be mitigated *without* an event source.