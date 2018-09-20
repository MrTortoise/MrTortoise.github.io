---
layout: post
title:  "Lean Architecture - aka don't build shit you don't need"
date:   2018-04-03 20:40:48 +0000
categories: architecture lean design patterns ddd
---
# Running Tech in startups has taught me that we overcomplicate and build loads of unnecessary crap - STOP IT

This post is about how the nature of finding a market / product / customer is about an approach and how the philosophy behind that approach applies at all levels. In this case I want to make a point about architecture and hopefully it falls out the the main thrust.

So you find yourself in a startup. You have done your homework [Eric Ries - The Lean Startup](https://www.amazon.co.uk/Lean-Startup-Innovation-Successful-Businesses/dp/0670921602/ref=sr_1_1?ie=UTF8&qid=1522609380&sr=8-1&keywords=lean+startup+eric+ries).
So you are armed with ideas about how to have a really good running start.

## The goal of a startup is to get a customer

This sounds really obvious however it seems most peoples reasoning loves to achieve things indirectly. This is almost always a mistake and when it is not, it is usually right for reasons that are misunderstood.

>For Example: You start to build an app because you think you can sell an app to people in order to help them do something

You have already fallen victim of 'Introduce another problem to solve a problem'. See how complex this is:

1. You are building an app
1. to (presumably) enable you to then go out
1. and find a customer
1. to try and sell the app to them
1. in order for them to use the app
1. to solve a problem.

There are a ton of assumptions in there.

Once you have done this you might discover that you do not need an app at all. They might not need an app either.

The fun thing is: If you think the example above is reasonable then you will probably find something else that you need to do before you can approach a customer - maybe make a facebook page to run some advertising. The way most learn this lesson is the *hard* way - they go broke.

It is taking a problem that one person may (or may not have) and solving it for a whole batch of people. This approach robs you of the detail and intimate connection of solving it really well for one person. Then doing it again for another and another until the pressure to automate it in a specific direction comes out.

## Just find a customer and solve a problem

It is really hard to see this: In most cases the answer to developing a new product is simply go out and find someone who you think needs the service and convince them to give you money to do it for them.

You don't need an app or a facebook page. You need a personal relationship with someone who has a problem that you can solve. Get out and talk to people - start to believe in their world and make it better.

If you cannot convince someone to give you money to solve their problem - why on earth do you think an app / facebook / twitter / tv campaign will work better? Your problem is that **you do not know how to find your customer because you do not understand what problem they have and so you do not understand how to fix it**.

>When we found our first customer my reaction was 'What? Why on earth do they want that?' - it should of been a perspective altering experience akin to 30 days in a desert. I let that learning experience pass me by.

We are complex creatures and we have all kinds of beliefs and accepted practices. Giving yourself permission to, and then finding people who can interrogate your reasons with the goal of finding the assumptions and challenging them is hard. (Hint: customers will do this)

Even if you do market research before and figure out the idea has potential you will probably find that there are a ton of good ideas that you cannot afford to do ...discover this quickly.

## This kind of business is frighteningly fast past

When in a company that is this early stage 2 things are true

1. Because you haven't found a customer you have no idea what your business is going to look like
1. You need to be able to try lots of different shit with **very short** lead times

These 2 things need to be your architectural goal.

## This leads to _Lean Architecture_

### Having literally no architecture is faster than all other options

1. If you can test a hypothesis with no code you should.
1. If you don't feel like you can talk to a customer without a demo then you need to talk to more people.
1. The fastest feedback is to talk to someone directly.

### Enabling fast - data driven - customer feedback

- The point of cutting code is to facilitate specific answers in talking to someone directly.

The purpose of rapid iterations and relentlessly connecting work to value for customers is that we can make decisions with a better understanding of what direction we expect to be right. This hopefully enables us to be more likely to be right (the one that adds most value for customer) and to also verify that the step we just took is in the right direction (rapid iterations), when this is not true we actively learn from being wrong. Knowing precisely why you were wrong is very very hard - maybe another post. Finding out quickly is over half the battle. After all, we still don't know why things fall - but we can still use it.

But in this world we need to build something with very little understanding of what the end point will be. Eg one idea we seriously worked on had potential to be either a website, a mobile app or a chatbot. In fact most of the things I have worked on in the last year have been like that.

So how do you stay flexible and not make decisions that you later on wish you hadn't?

## Making architectural decisions with no regret

The biggest and best piece of advice is to make choices that enable you to defer choices.

### Making no decision is still a decision

>One of the biggest mistakes I made was to let someone build a sql schema - innocuous right? A schema for something we already had ui mockups for makes sense. They wanted to contribute and I wanted them to contribute, the work was great as it made us think but it locked us into a solution to a problem we hadn't fully unpacked. It took 30 minutes but the reverberations of the impact was felt weeks after. The schema was good - it is not the problem. But it removed the possibility of not needing a sql database and in the process brought along a ton of other implied decisions. It was a decision that was made before the pressure to make it mounted up. Far better to leave it as a pocket strat for when the right situation comes up. Making it then has far more value.

- If you make good moves in the wrong order you end up with suboptimal results.

If there is no pressure to do something now then take it into account and work in a way that enables making the decision later. Solve the problem that adds most value now.

Early on don't build anything more than what is required to support a sale (or whatever the goal of business is). The best contribution to make at this point is to try and strip everything out in order to identify the key value proposition. Test that idea. If you need to solve a to solve b to solve c are you *really* sure people want c at all or even b? Why do they want a if they really want c?

Understand what you are doing from a customers perspective. You might think you are building a cashless transaction system. But for your clients you might be optimizing their flow at a counter and for their customers you might be simply keeping up with the times.

This doesn't mean that your proposition isn't going to sell it means its selling for different reasons than you think and so your message is wrong. Worse it means you got lucky and so haven't learnt.

However what you are building needs to take into account a myriad of different directions - and those directions will change every week. As a result not over committing and playing a very soft game until the signal you need to make a decision takes place is strong. Building a framework to enable working with speed and flexibility is key.

## Techniques

### Model Your Domain from your customers perspective

- You will be wrong about what and how customers want things. By modelling it explicitly you may find this faster and when you do it is far simpler to cut and modify because your code maps onto the businesses understanding of the process.
- If internally you cannot talk to problem through you cannot solve it
- If you cannot model it in a way that your customer understands and can shine radical insight into then its probably not interesting or valuable
- It is far easier to have multiple solutions working in parrallel as tests when everything is based around the domain rather than say a schema

### Event Storm

- By bringing everything together at different levels it becomes simple to identify the value stream that matters.
- You can start to hang UI off an event stream in a way that is very organic.
- Given an event stream and an understanding of the information required to make the decision that led to the event UI design can really be innovative in that it models the real problem and not just 'yet another shopping cart'
- Once you know what information is required to make a decision to produce an event you can start to ask really concrete questions about what information a user needs in order to provide the data to fuel the decision. Now you have your read models.

Everything else architecturally just emerges organically. Once you know what read models you know what kind of data store (and can easily change your mind - see below), once you know what kind of data store you know how you can't to process the commands that produce events. Once you know this you can decide what (if any) areas you want to event source (all of them ...)

### Encapsulate your dependancies

- This is all ports and adapters / hexagonal architecture goodness.
- Do not spend a long time integrating to sell something. Mock it out, fake it till you make it.
- By deferring decisions about implementations of dependancies you buy time to find out more information about what and why you are about to make a decision. Eg do you *really* need to store customer info on anything but their device? Do you *really* need to store it? If you just have a 'storage' adapter you can decide the detail anytime you like - and change it.

### Separate Commands from Queries

- I have heard it argued time and time again that event sourcing is expensive. **I call complete bullshit**. It might seem like its slower than just whacking an ORM on top of a schema and using CRUD, but thats because the people doing that are not rewarded based on *speed of change* and decoupling everything.
- If you employ event storming as above you can very rapidly build a prototype very quickly that uses dummy read models and internally processes commands to raise events that transition across screens.
- once you have done this you can change and react to customer feedback with no backend system having been written at all - yet all the while you are implicitly designing it and building understanding and requirements for it.
- When finally you do need to implement something the work to do so will be very clear and due to the abstractions in place be very very simple - even if the problem space is hard because this approach separates out concerns to is very resistant to attempts to complect it.

## Instead of writing code go out and find a customer
