---
layout: post
title:  "GraphQl + Greenfield Probably isn't what you need"
date:   2017-03-26 20:00:48 +0000
categories: graphql api
---

## What is the Lead here?

Our job as devs is to deliver value to the business - not to enrich the boring dross that we have allowed businesses to turn our jobs into. Maybe picking the latest greatest tech is exactly the least important part of what we should be doing. 

## What is a green field project?

1. A new project that needs everything setup (Deployment, Build, Team, Tech Stack). 
2. A proof of business value

## What is the first thing everyone with a green field project do?

`Look at all the toys!`

Lets use the latest and greatest stack

I want GraphQL, I want React/Vue, lets use some really alpha js features, lets use lots of really helpful libraries to solve all our problems (rather than right some simple sql).

Innovation and learning is great, but what is the cost?
Increased risk of failure with the potential of some extra value

## Where to spend innovation points?

A dev I have a lot of respect for once said to me (whilst I was figuring out my stack to solve some problems in a startup)

`Be aware of how much new stuff you are using, consider that you have a number of innovation points to spend on a particular problem and be aware that they represent liability`

What was awesome about this is that someone who I thought of as a shiny person who was going to totally eclipse me at some point completely dropped a truth bomb on me at a time when I *really* needed to hear it.

### What Do you hope to get out of innovation?

There are many ways to skin every cat. Hopefully you already have many tools to solve any job you encounter. In these situations you need to be asking yourself why do you want to push off from the island of certainty on a Zarathrustrian journey. What exactly are you hoping to get in return for throwing off the shackles of what you know?

- Faster Development time? (but is development time the bottleneck?)
- The ability to scale better? (but this is greenfield - its never going to be 'at scale' unless it succeeds)
- Some undefined better?
- A different abstraction (nothing wrong with different, but unknown needs to have definate value to offset it)

### Are you sure you are not simply bored and using a green field project to learn something new?

Really the fun, interesting and challenging part is figuing out how to get to market in ways that help you learn about what your customers really want.

Spend innovation points on this - its really hard and takes a *lot* of time.

## Why Name and shame GraphQL?

Because it seems to offer so much but I have yet to see anyone really get the most out of it compared to the available alternatives. Is it really powerful? Yes

What does it give you that simple rest / soap cannot?
Why not use some simple message passing protocol?

### I have never seen anyone use the promise of using a graph to select a subset of objects

- The exception is calling the facebook api's - it turns out they have a large amount of data you could select from.
- I once saw a company use .net for its services, use dynamic objects to simply pass though the domain object of another company all the way through to the front end through several api layers. The front end then used GraphQL to select the tiny part out of this object that was relevant to them. Obviously though here it isn't GraphQL thats the thing to leverage. It is the terrible decisions to be tightly coupled to third parties throughout the Apis.
- More commonly each query called represents a view in the UI. Quite often each query is only really used for one purpose and so the fields being requested dont actually change. When they do it is actually a different query that is called.
- CRUD / Repository patters are usually very anemic and tend to have UI that is centered around a page per table rather than imagining the customer journey and modelling to deliver value - this works against GraphQL, when you do model to deliver value you end up with query per usage again anyway as now your queries represent explicit user questions - or test hypothesis around what we think a user will value.
- When you compare a query to simply hitting a rest/soap endpoing with some parameters that just fires soem SQL - do you *really* gain enough form graphql fragments, queries, resolvers, orms's to justify all the extra time for every single read model you want to implement.

### Is passing mutations over GraphQL really the architecture you want?

There are alternatives such as message passing - or just firing something at REST.
`Whatever you can do the REST can do better`

## You sound like a REST fanboi ... are you sponsored?

No I hate rest. I think its ambiguous on how to use it (I have build rest interfaces for many companies - they all do it differently), how to handle errors and people use it badly and inconsistently as a result - but its very simple and does its job. I far prefer something SOAP like (there I admit it - because lots of tools will reflect and generate code), GRPC is good too. But my favourite is simply opening a socket and blasting something.