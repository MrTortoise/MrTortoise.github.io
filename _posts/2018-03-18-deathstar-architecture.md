---
layout: post
title:  "Deathstar Architecture: Don't be the empire, be the guys that go around blowing shit up!?"
date:   2018-03-18 11:40:48 +0000
categories: architecture lean design patterns ddd
---
# What is Deathstar Architecture and why should I care?

![Deathstar](/images/deathstar/deathstar.jpg)

The goal of architecture is to enable deferring decisions by encapsulating and adapting away from them - this enables large simple solutions to complex problems. However, being feeling the pressure to know when to make decisions is hard.

Mainly because unlike with refactoring code (connaissance and groups that practise together help build shared consensus)refactoring large scale architecturally is still very much touchy feely about the when. Or maybe thats just my ignorance (link me up!).

Devops and 'measure the key things' are helping here. But still, it won't help with the deathstar - the death star happens earlier and gets you before you get the data to pressure change.

## How to build one

Odds are you have an almost functional ones and have some rebels in your business frustrating you already.

1. Take the cheaper faster option.
1. Take the cheaper faster option.
1. Goto 1.

That is *reality*. You don't do this you are probably dead or already an established corporate entity in which case i am merley recounting the first 5-10 years of your life

{% include youtubePlayer.html id="0oBx7Jg4m-o" %}

## The result

### One **BIG** database at the core of your business

All these different processes hanging off it, dipping in and modifying state for other unconnected processes to do more work with.

## The Cost

- 1-2 emporers that know the system
- Evil sith lord(s) that act as hippos
- lots of underlings that will shoot themselves in the foot - or get asphixiated through use of the force - when they get frustrated and then try and fail to modify the system.

 Its a classic co-dependance on gatekeeper releationships that is caused by ever and probably non-linear increasing complexity of the single system.

![Keymaster](/images/deathstar/keymaster.jpg)

- **Pace of busineses development and vaue add drops off a cliff.**
Rather than develop more stuff to add value to a proposition you start to look for clients to sell the existing stuff to. This is where the real death star gets built.

- **Technical debt bought to ship gets duplicated** as more clients come on oard. Finally the return on work to ship pays, but now the budgets are all about marketing and scaling out rather than consolidation. Also at this point things are small and so

- **Easier to integrate into database rather than model problems** because you can fix problems simply by updating a record here and there. It feels efficient and powerful - **This is the problem**

![MarginalDecisions](/images/deathstar/marginal-decisions.jpg)

## Congratulations you own a DEATH STAR
Now the follow is true:

1. **Because nobody can change anything without breaking something you decide you have a quality problem** - the existing stuff works and so survivor bias makes everyone point to the new work as being the problem and Hero Complex means the gatekeepers are essential.
1. **Gate keepers become the Heros** and this becomes a cultural target.
1. To fix 'sloppy development' development slows down, some heavy handed 'agile' implementation focus on **[Process, Documentation and Planning](http://agilemanifesto.org/)**. (too subtle?)

1. Lots of small problem solving per department ie **local optomisations rather then whole company** result in fragility.
1. The estate is not a mess of braided knots with value streams spread accross multiple solutions. This entire approach complects the whole system.

{% include youtubePlayer.html id="rI8tNMsozo0" %}


You get Jira, you get Scrum (if you are lucky), you get Confluence / sharepoint you introduce gates and checkpoints to block value being released because the business percieves the work of developers as being risky. Well it is, because the system was designed to be

soem heavy handed issue tracking, delays, wait times and then you still need QA delaying releases in order to build confidence. Like that will help?

The criminal part is that because the business never slowed down it is literally impossible to meet the current businesses needs as development is now several months behind and now key parts will get oursourced - because now the business percieves development as being the bad guys. This is reasonable - dev is the bad guy here.

![ManualQA](/images/deathstar/qa.jpg)

## What one looks like

There are many ways to get to a death star - the one I am going to talk about here is a sql deathstar. This is because I think a lot of companies have already learnt a lot from DDD and seperation of contexts and thinking about aggregates. If this has not happened then you dont have a death star, you have a [big ball of mud](https://en.wikipedia.org/wiki/Big_ball_of_mud). It is a deathstar of sorts but the value of refactoring architecture away is far more obvious and the organisational problems its causes even more so. If in this situation don't build a deathstar.

Basically any architecture with a big name databse vendor is at huge risk of building a death star. Why? Because everything hangs off one database because the business is in way too deep - they cost too much. It's funny because nowhere else in the business would take such a big dependancy without a backup plans a,b and c. This means none of your domains / bounded contexts have isolation because any (and so all) kinds of things can (and so do) happen. For some reason DBA's dont think of themselves as developers and developers think of DBA's as either a necessary evil or wierd mystics.

## The enterprise deathstar
![Enterprise Death Star](/images/deathstar/deathstar-database-enterprise.png)
The deathstar starts here. Take an enterprise level break down of departments and how they contribute to the business and use these boundaries tosegregate pieces of software. This is crazy because it means the integration point of processes in different departments is the central part - this invariably ends up being the database. What is really happening is that a customer driven value stream passes through many departments by necessity and so the software should model and segregate upon this.

So we have a core

The database of a big name vendor costs so much everything ends up hanging off it. When you draw architecture diagrams of multiple areas of the system you will see that rather than them coming off in sections they are also interconnected. It is the interconnections that kill development because nobody in those teams will fully understand them.

In DDD this is described as a big ball of mud but i dont think the reason it happens is ever really explained in terms of business decisions. It doesn't happen because of architectural choices it happens due to best choices within financial constraints.

#