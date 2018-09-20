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
6. In event driven systems the concepts of Event, Message and Command are often blurred.

## Event Sourced

In an event sourced world the events are usually viewed as the source of truth (it may be an authority but correctness is still a problem). Event sourced systems also persist the events as a transactional side effect of carrying out some behaviour.
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

1. commands come in. Command application is often synchronous as it requires consistency. Asynchronous consistent commands are possible - and a powerful tool - but requires UX considerations.
1. The aggregate root loads in an aggregate for a command (by applying the history of events to it), applies the command through a policy and writes zero or more events

On the Query side:

1. Client requests some data by a key usually
2. Clients recieves precalculated denormalised read model for that specific use case.

### How does this happen?

A read model is a projection. Much like an aggregate is projected from its event stream as it is loaded a read model is simply a different kind of projection. It may be of one (or more) event type, could be to do with a kind of aggegate or anything inbetween.

A 'Read Model Generator' (projection) subscribes to an event stream, applies each  event to the current state of the object in the read model. This means that a caught up read model always (eventually) represents the latest state in the event store.


