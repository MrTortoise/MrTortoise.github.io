---
layout: post
title:  "Akka.net: Why might I be interested in akka.net?"
date:   2017-04-14 13:30:48 +0000
categories: akka.net
---

## Current problems

akka.net is not released for ,net core. I also believe that remoting on mono is not there.
So if you are using this, right now you are in windows, and you are probably not deploying
into docker. So that's a bit sad, but .net core is coming in 1.5 which is apparently going to happen this year. The focus right now seems to be on geting closer to the features in
the Java version.

## What is the point?

Want to describe the main uses I have gotten value from when using Akka.net.

1. Orchestration - There are several takes on this.
    1. Scaling horizontally - akka is really nice for adding more machines to a cluster,
    setting up roles on them letting the cluster start using the extra capacity.
    2. Controlling a set of resources - due to its message based nature it naturally lends   itself to writing protocols for controlling collections of things (Eg build agents or test   machines)
    3. Marshalling messages between aggregate roots / bounded contexts.

2. Concurrency
    1. Actors can only communicate via messages. Their state   is isolated - and if you use immutable patterns then no   references ot anything in the state of one actor will be   in another. The cognitive overhead and number of gotchas   is really really low.
    2. Message passing is really fast, hundreds of million per   second locally - obviously remoting has different   characteristics.
    3. It is tell based out of the box.

3. Event and Command sourcing
    1. The actor model is pretty much built for this.

4. CQRS
    1. It is tell based which in my view makes it a really   good match for the command side.

5. Deployment
    1. The configuration of the arrangement of actors - in   terms of degree of parallelism
    and the means of routing / distribution is determined by   configuration file rather
    than hard coded or some devops / cloud host specific   wizardry. Load balancing vs
    broadcast is simply a choice of router. The actor code in   a single step by step process looks the same when they fan   out or are distributed by hash over a cluster. Its all   config.

## What is the tradeoff?

1. A bit more code, An actor could be considered to be a wrapper around a normal piece of code. Juval Lowry in his book on Components described classes as services. Actors get v close to that.
2. Forces you to model the Commands and how they trigger transitions of operational states inside a system.
3. Because all actors are `IActorRef` and all handle messages you lose a bit of compile time certainty that all will be fine. But you do do TDD right?
4. Again because all actors are `IActorRef` you cannot get at the internal state. Which forces you to test against the ends of the system - or composite of actors you want to test.
