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
First, it is a pattern I see everywhere (i have built some, worked on some and even fixed one) - odds are you have an almost functional ones and have some rebels in your business frustrating you already. It is a very natural pattern that comes from a very natural and successful tendancy - taking the cheaper faster option. Unfortunatley the realities of running a company are that you often have to make this choice or the very real alternative is your company will die because you start on a shoestring then you over promise to win business and then pull a rabbit out of a hat to deliver. That is *reality*.

{% include youtubePlayer.html id=0oBx7Jg4m-o %}

spacer

![Reality](https://www.youtube.com/watch?v=0oBx7Jg4m-o)

The result of taking this appraoch is that you will end up with one big database at the core of your business. All these different processes hanging off it, dipping in and modifying state for other unconnected processes to do more work with.

The cost of this pattern is you have 1-2 emporers that know the system, evil sith lord(s) that act as hippos and lots of underlings that will shoot themselves in the foot - or get asphixiated through use of the force - when they get frustrated and then try and fail to modify the system. Its a classic co-dependance on gatekeeper releationships that is caused by ever and probably non-linear increasing complexity of the single system.

The problem is that the pace of busineses development and vaue add drops off a cliff. Rather than develop more stuff to add value to a proposition you start to look for clients to sell the existing stuff to. This is where the real death star gets built. The technical debt incurred to get something out for one client gets duplicated as clients go up. Because the business profits who can say its wrong?

Now because nobody can change anything without breaking something you decide you have a quality problem - the existing stuff works and so survivor bias makes everyone point to the new work as being the problem and Hero Complex means the gatekeepers are essential. The solution to this is to slow down, implement scrum, soem heavy handed issue tracking, delays, wait times and then you still need QA delaying releases in order to build confidence. Like that will help?

The criminal part is that because the business never slowed down it is literally impossible to meet the current businesses needs as development is now several months behind and now key parts will get oursourced - because now the business percieves development as being the bad guys. This is reasonable - dev is the bad guy here.

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