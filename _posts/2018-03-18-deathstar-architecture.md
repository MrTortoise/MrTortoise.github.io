---
layout: post
title:  "Death Star Architecture"
date:   2018-03-18 11:40:48 +0000
categories: architecture lean design patterns ddd
---
# What is Death Star Architecture and why you should care

![Deathstar](/images/deathstar/deathstar.jpg)

A death star has a core. Around the core there is stuff. A DDD crafted death star would fall apart like a higher dimensional chocolate orange. The Death Star on the other hand might have segments - but if it does they are all heavily cross linked to aid its structural integrity. A well designed estate at enterprise scale has no such cohesion baked into it. Its survival and adaptability depends upon this and is achieved through domain events. It has isolation, a well defined structure to each part and a well defined value delivered by each part. The Death Star doesn't - it does on the other hand blow up moons. Most death star architecture on the other hand just blows up.

![Boom](/images/deathstar/boom.jpg)

> The job of an architect is to build a structure that allows decisions to be delayed as long as possible - Robert Martin

This enables large simple solutions to complex problems. However, feeling the pressure to know when to make decisions is hard.

Unlike with refactoring code (connaissance and groups that practice together help build shared consensus) refactoring large scale architecturally is still very much touchy feely about the when. Or maybe thats just my ignorance (link me up!).

Devops and 'measure the key things' are helping here. But still, it won't help with the deathstar - the death star happens earlier and gets you before you get the data to pressure change.

## How to build a Death Star

Odds are you have an almost functional ones and have some rebels in your business frustrating you already.

1. Take the cheaper faster option.
1. Take the cheaper faster option.
1. Goto 1.

That is *reality*. If you don't do this you are probably dead or already an established corporate entity in which case I am merely recounting the first 5-10 years of your life

{% include youtubePlayer.html id="0oBx7Jg4m-o" %}

## The result

### One **BIG** database at the core of your business

All these different processes hanging off it, dipping in and modifying state for other unconnected processes to do more work with. And no 'but schemas' is not adequate (but its barley better than nothing).

## The Cost

- 1-2 emperors that know the system
- Evil sith lord(s) that act as hippos
- lots of underlings that will shoot themselves in the foot - or get asphyxiated through use of the force - when they get frustrated and then try and fail to modify the system.

 Its a classic co-dependance on gatekeeper relationships that is caused by ever and probably non-linear increasing complexity of the single system.

![Keymaster](/images/deathstar/keymaster.jpg)

- **Pace of business development and value add drops off a cliff.**
Rather than develop more stuff to add value to a proposition you start to look for clients to sell the existing stuff to. This is where the real death star gets built.

- **Technical debt bought to ship gets duplicated** as more clients come on board. Finally the return on work to ship pays, but now the budgets are all about marketing and scaling out rather than consolidation. Also at this point things are small and so

- **Easier to integrate into database rather than model problems** because you can fix problems simply by updating a record here and there. It feels efficient and powerful - **This is the problem**

![MarginalDecisions](/images/deathstar/marginal-decisions.jpg)

## Congratulations you own a DEATH STAR
It looks a bit like this:

![YourVeryOwnDeathStar](/images/deathstar/sql-deathstar-1.png)

However that doesn't look so bad. There are lots of separate stacks with not too many cross dependencies all talking with the database. If you squinted at a diagram involving bounded contexts you could argue this achieves that idea. And it does *look* similar - but then a cloud of sulfuric acid also looks a bit like fog.

The problem comes when we start to talk about value streams. Take an operationally important process (say a core business process such as getting products and process into feeds) and map that value stream across these operations and you get something like this

![DeathStoreIsStronk](/images/deathstar/sql-deathstar-value-stream.png)

The problem is that every business process will look something like this qnd will overlap. Experts in one value stream / domain will potentially have no idea about the existence of others. But they will know this and so will be paralyzed by fear.

The Deathstar is fully operational. The Empire now has full control over its denizens.

Now the follow is true:

1. **Because nobody can change anything without breaking something you decide you have a quality problem** - the existing stuff works and so survivor bias makes everyone point to the new work as being the problem and Hero Complex means the gatekeepers are essential.
1. **Gate keepers become the Heros** and this becomes a cultural target. People subconsciously copy people that seem to have more social status.
1. To fix 'sloppy development' development slows down, some heavy handed 'agile' implementation focus on **[Process, Documentation and Planning](http://agilemanifesto.org/)**. (too subtle?)
1. Lots of small problem solving per department ie **local optimizations rather then whole company** result in fragility.
1. The estate is now a mess of **braided knots with value streams spread across multiple solutions**. This entire approach complects the whole system. This is the nature of a death star.
1. **Just because dev stalled doesn't mean the business did!** it is literally impossible to meet the current businesses needs as development is now several months behind.
1. Confidence in development drops, other **departments solve their own problems**. Nobody stops to think that this is crazy - its so normal. At this point there is no unified movement, its noise and conflict. Sure the road map is followed but rather than a crystal lattice you get an ants nest.

{% include youtubePlayer.html id="rI8tNMsozo0" %}

# So Death Stars are bad .. Now what

If you dont know anything about [Domain Driven Design](https://www.amazon.co.uk/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/ref=tmm_pap_swatch_0?_encoding=UTF8&qid=&sr=) then that is probably a good place to start.

## What would a non-deathstar-enterprise-scale-mess look like?

1. **Think in terms of [value streams](https://en.wikipedia.org/wiki/Value_stream_mapping)**: map processes from the perspective of how they deliver value to the customer using something like [Event Storming](http://ziobrando.blogspot.co.uk/2013/11/introducing-event-storming.html).
1. Use these value streams to separate your domain into [bounded contexts](https://martinfowler.com/bliki/BoundedContext.html).
1. Build a fleet of mini death stars

## But why is this different?

1. You can blow up all your enemies at once
1. These contexts use completely isolated datastores.
1. Your DBA's probably are grateful but a little bored now
1. Most importantly the [Single Responsibility Principle](https://8thlight.com/blog/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html)

When code, modules, services, databases or whatever deployment units are being discussed are broken down with these kinds of considerations and the above approach then due to the isolation and singularity of purpose (that will be mapped end to end onto what the company actually does) you end up in a position more like this.

## What one looks like

There are many ways to get to a death star - the one under focus here is a SQL Death Star. (I like to think) A lot of companies embrace DDD and separation of contexts and thinking about aggregates. If this has not happened then you dont have a death star, you have a [big ball of mud](https://en.wikipedia.org/wiki/Big_ball_of_mud). It is a deathstar of sorts but the value of refactoring architecture away is far more obvious and the organizational problems its causes even more so.

## The enterprise Death Star

![Enterprise Death Star](/images/deathstar/deathstar-database-enterprise.png)

Take an enterprise level break down of departments and how they contribute to the business and use these boundaries to segregate pieces of software. This is crazy because it means the integration point of processes in different departments is the central part - this invariably ends up being the database.

What is really happening is that a customer driven value stream passes through many departments by necessity and so the software should model and segregate upon this instead.

### But we did that!

Yes, it starts like that.

So we have a core

To finish it off all we have to do is block communication between departments

The database of a big name vendor costs so much everything ends up hanging off it. When you draw architecture diagrams of multiple areas of the system you will see that rather than them coming off in sections they are also interconnected. It is the interconnections that kill development because nobody in those teams will fully understand them.

In DDD this is described as a big ball of mud but I dont think the reason it happens is ever really explained in terms of business decisions. It doesn't happen because of architectural choices it happens due to best choices within financial constraints.


Finally ...
Whats the worst that could happen right?

{% include youtubePlayer.html id="7jT8EkzCZaY" %}