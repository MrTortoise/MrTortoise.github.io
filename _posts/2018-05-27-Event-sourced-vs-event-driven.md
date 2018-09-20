---
layout: post
title:  "What is Event Sourcing and how it differs from Event Driven"
date:   2018-05-15 22:00:48 +0000
categories: cqrs pubsub eventSourcing eventDriven
---
# The difference between Event Sourced and Event Driven systems

I have recently encountered some confusion between the terms. They represent very very different systems.

An event sourced systems goal is to place the source of truth in an event store, whereas a event driven system usually discards the events/messages once they have been processed. The only point of similarity is that they both have a pub/sub.

## Event Driven

In a world of pub sub (event driven) you would ack a message once you are done with it in order to tell the queue that it can discard the message and not take any non processed action (Eg dead letter / retry strategy).
However in this world it seems people rarely store these events and replay them later to rebuild aggregates (this moves into event sourced.)
the general pattern is

1. Messages are written to some sort of exchange. Messages are a chunk of data, often a type with a payload.
2. Consumers register routing for the exchanges to put messages into queues
3. Consumers then subscribe to those queues.
4. Messages are taken off a queue and put into a state that stops others from read by others until a timeout or an Ack message is received.
5. The consumers take some action a side effect of which is to update some source of record somewhere (usually mis labelled source of truth).

## Event Sourced

In an event sourced world the events are usually viewed as the source of truth (it may be an authority but correctness is still a problem).
The big distinction is that events are that from which state is constructed rather than be things that are applied to a record and then discarded.
This confers a number of properties to a system that can be very beneficial.
Eg

- System isn't integrated around a single database of state.
- Changes to the system are additional rather than mutating of a schema.
- The entire system can be replayed with different behavior.
- Fully audited
- Very easy to debug and see how state of an object what achieved
- Event sourced systems require command query responsibility segregation. IE the parts that produce events are independent of the parts that consume events

So in an event sourced world
On the Command side:

1. commands come in (often through pub/sub - if eventually consistent, direct call to aggregate root if consistency required)
1. The aggregate root loads in an aggregate for a command, applies the command through a policy and writes zero or more events

On the Query side:

1. A client requests some data
In an event sourced world you want to apply events one at a time to an aggregate. That is a sequential and synchronous operation, several wrappers around the .net code behave in a less than desirable way.
It seems that
1. Event store has no concept of ack, it simply has a handler callback in an event loop. This is fine if you are in .net
1. The node libraries i see efectivley say to eventstore - 'yes the message was handled properly' as soon as they pass over control into the other langauge. In langauges that are highly async Eg javascript or elixir this lend to specific kinds of problem

Eg in node, every event is tret in parallel. So error handling in one will take substantially longer than the next event and everythign goes to hell veyr quickly.

It also uses a master-slave gossip pattern for discovery. This is the same as many solutions to clustering. Akka certainly favours this and as a result so does everything amazing built off it.
*This is making the explicit assumption that consistent write orders for events accross the system are necessary and desirable*

## What could a solution look like?
The driver for some of these observations is that ESB can be an antipattern. But if we treat bounded contexts as sources of events then consistency boundaries only need to be in place at those boundaries.
Even if the sequence of events at domain event level could be recorded in a completley time correct manner you still run into collision problems due to time to reload an aggregate, apply a policy to a command and then emit the event to be written and published.

As such consumers and read models should need to be able to cope with events out of sequence.
Or do they? This is a situation that rarley happens because per aggregate the events are always in sequence because if they producer
Well if enterprise service bus can be an antipattern