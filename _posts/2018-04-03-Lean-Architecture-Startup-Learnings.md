---
layout: post
title:  "Lean Architecture - Startup Learnings"
date:   2018-04-03 20:40:48 +0000
categories: architecture lean design patterns ddd
---
# Running Tech in startups has taught me a few things

So you find yourself in a startup. You have done your homework [Eric Ries - The Lean Startup](https://www.amazon.co.uk/Lean-Startup-Innovation-Successful-Businesses/dp/0670921602/ref=sr_1_1?ie=UTF8&qid=1522609380&sr=8-1&keywords=lean+startup+eric+ries).
So you are armed with ideas about how to have a really good running start.

## The goal of a startup is to get a customer

This sounds like its really obvious. But people love reasoning that attempts to achieve things indirectly. This is almost always a mistake and when it is not, it is usually right for reasons that are misunderstood.

Eg You think you can sell an app to people in order to help them do something

You have already messed up. See how complex this is:

1. You are building an app
1. to (presumably) enable you to then go out
1. and find a customer
1. to try and sell the app to them
1. in order for them to use the app
1. to solve a problem.

There are a ton of assumptions in there.

Once you have done this you might discover that you do not need an app at all. They might not need an app either.

The fun thing is that if you think the 'Eg' above is reasonable you will find something else that you need to do before you can approach a customer - maybe make a facebook page to run some advertising. The way most learn this lesson is the *hard* way - they go broke.

### Just find a customer and solve a problem

The point is that it is sometimes really hard to see what is painfully obvious - in most cases it is simply go out and find someone who you think needs the service and convince them to give you money to do it for them.

You don't need an app or a facebook page. You need a personal relationship with someone who has a problem that you can solve. Get out and talk to people - start to believe in their world and make it better.

If you cannot convince someone to give you money to solve their problem - why on earth do you think an app / facebook / twitter / tv campaign will work better? Your problem is that **you do not know how to find your customer because you do not understand what problem they have and so you do not understand how to fix it**.

But we are complex creatures and we have all kinds of beliefs and accepted practices. Giving yourself permission to and then finding people who can interrogate your reasons with the goal of finding the assumptions and challenging them is hard.

Even if you do market research before and figure out the idea has potential you will probably find that there are a ton of good ideas that you cannot afford to do ...

## This kind of business is frighteningly fast past

When in a company that is this early stage 2 things are true

1. Because you haven't found a customer you have no idea what your business is going to look like
1. You need to be able to try lots of different shit with **very short** lead times

## This leads to _Lean Architecture_

### Having literally no architecture is faster than all other options

1. If you can test a hypothesis with no code you should.
1. If you don't feel like you can talk to a customer without a demo then you need to talk to more people.
1. The fastest feedback is to talk to someone directly.

### Enabling fast - data driven - customer feedback

- The point of cutting code is to facilitate specific answers in talking to someone directly.

So the point of rapid iterations and connecting to value is that we can make decisions with a better understanding of what direction is more likely to be right (the one that adds most value for customer) and to also verify that the step we just took is in the right direction (rapid iterations)

But in this world we need to build something with very little understanding of what the end point will be. Eg one idea we seriously worked on had potential to be either a website, a mobile app or a chatbot. In fact most of the things I have worked on in the last year have been like that.

So how do you stay flexible and not make decisions that you later on wish you hadn't?

## Making architectural decisions with no regret

The biggest and best piece of advice is to make choices that enable you to defer choices.

### Making no decision is still a decision

>One of the biggest mistakes I made was to let someone build a sql schema - innocuous right? A schema for something we already had ui mockups for makes sense. They wanted to contribute and I wanted them to contribute, the work was great as it made us think but it locked us into a solution to a problem we hadn't fully unpacked. It took 30 minutes but the reverberations of the impact was felt weeks after. The schema was good - it is not the problem. But it removed the possibility of not needing a sql database and in the process brought along a ton of other implied decisions. It was a decision that was made before the pressure to make it mounted up. Far better to leave it as a pocket strat for when the right situation comes up. Making it then has far more value.

- If you make good moves in the wrong order you end up with suboptimal results.

So early on goal is not to build anything more than what is required to support a sale. The best contribution to make at this point is to try and strip everything out in order to identify the key value proposition. Test that idea. If you need to solve a to solve b to solve c are you *really* sure people want c at all or even b?

Eg a vendor does not need a non cash based way to sell product. They may however need a way to speed up purchases, to enable them to capitalise on a part of the market they are locked out from. But failing to break these propositions apart means failure to understand value which means you cannot make decisions that align with value.

This doesn't mean that your proposition isn't going to sell it means its selling for different reasons than you think and so your message is wrong. Worse it means you got lucky and so haven't learnt.

However what you are building needs to take into account a myriad of different directions.

### Build from the customer

1. What does the customer want to do?
1. What is the shortest path to that?
1. Now make it shorter.
1. Start with mockups - there are a number of free-ish ui mocking cloud based tools. Gone are the days of only having balsamiq and some guy on visio as your options. Some will even give you some html = but that is of very little value
1. Use these mockups to remove all the crap, always remove screens, remove controls, remove text. This is very early on - the goal is to find out what the customer needs. Get rid of account management, a wallet, the admin screens. Its all ancillary stuff that adds value in rare situations.
1. Prove that the absolute bare minimum is not enough - it probably will be by the way. By doing this perhaps you solve a problem that is way more general than your current business model ...
1. If anyone wants a fancy control to solve a problem you are dead - your basic idea is *way* too complex. It is a gimmick.
1. Do not write any back end services or decide what language framework they are in until someone will pay you for the piece of crap you have built. To them it is not crap, it is amazing. Everything should be client side.
1. Do you even need a backend? What does it add (apart from a bucket load of complexity). I've developed for 15 years, I love backend. I can eventsource and CQRS fizz buzz. But guess what, what you know doesn't count for anything. Minimal effort and economy of motion is everything.
1. Once you get a customer who has paid rejoice. If you do it right in some spaces it could be days, in others it can take months - the trick is to manage the runway.