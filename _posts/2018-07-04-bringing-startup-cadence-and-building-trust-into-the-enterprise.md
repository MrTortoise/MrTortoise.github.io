---
layout: post
title:  "bringing-startup-cadence-and-building-trust-into-the-enterprise"
date:   2018-07-01 22:00:48 +0000
categories: waffle talk
---
# How to be Leeroy Jenkins in a risk averse environment

## The Problem

You spend about 36% of your waking time at work. It needs to be purposeful and fun. If you want to - and many people do want this - sit at a desk with headphones on, really enjoy performing one role and don't really want to engage outside of that. Brilliant, many modern environments are perfectly built for you. But if you get a feeling of emptiness or being shut out then maybe it is you I am talking to here.

## Who and what is Leeroy Jenkins

- Go google it ...

So Leeroy Driven Development could be characterized as committing stuff 6-7 times a day without much fear. Getting that stuff live with little or no QA oversight and acting in a very self-autominous manner, wandering around and talking to people within a team of probably about 50 people and a wider business of a few hundred.
He doesn't branch, he doesn't really check emails and when he do its usually to delete a load, he says things like 'I don't care about that', 'Is that really important?', 'Do I really need to be in this meeting?', 'Hey, do you want to go and have a chat for 5 mins?'. It's the kind of behavior that can really frustrate someone who is just trying to do their job and keep a low profile.

Leeroy is a free spirit who just rushes into hell and back. Then does it again, because really - deep down - it was kind of fun.

It sounds like total utter chaos until the reasons why start coming out.

Commits because complete faith in the build, little or no QA oversight because they paired with you early on and also trust the build and the tiny iterations have no risk. Walking around talking to stake holders - people that others are talking to via email / slack and waiting on responses. Taking time to build personal relationships whilst going is good to have the capital for when it goes bad. Not checking emails because pairing, difficult questions due to questioning the assumptions and wanting to connect back to real value. Not wanting to increase the count in meetings because when it is time to make decisions rather than expand possibilities then decisions best come from the few essential people and trusted proxies.

It is all perfectly rational and positive behavior. Moreover getting out, building relationships with the people you are delivering value for and to feels good - the real trick is how to get from 'process and ceremony hell' into it.

## The original Leeroy failed hard

To 'Leeroy' well at work you have to bring others with you. So the reality is that this kind of development is nothing like Leeroy - sadly (Click Bait) - unless you are an outside observer. Leeroy is a bit of a dick and messed up their game. What I am about to advocate is all about caring, empathy and most importantly choosing what to care a lot about whilst letting the rest run over you. 

Its about building a very specific space to positively effect whilst conceding everything else in order to give other roles the same space. It is about bringing people in to work alongside you and encouraging being pulled out to work alongside others. It is about encouraging people to stand up and support people when they want to try and excel.

All of this depends on one thing:

### Trust

Trust is important because with trust people can tolerate a level of fear. Fear is important because if you are not pushing yourself and the team around you then nobody is learning anything and wasted time is high. It is good to be slightly afraid it is better to have that fear more than balanced by all the other emotions available.

#### Being able to have trust requires a safe space

Bringing people who are usually (and correctly) risk averse requires building a space that is safe to operate within. This is not only a safe space in the soft sense but an environment that is responsive to change. By this I mean one that will respond when you change something that counters a previous specification. If you do not take the time to build the foundation of a place that is safe to make changes without harming the business you are dead in the water. This means conversations to understand how what is being delivered solves problems, feedback to ensure work is of value, TDD, CI/CD it means testing outside in, it means writing tests to reproduce defects and fix them.

#### Building trust takes time and energy - trust is not faith

If you do not have a relationship with someone you have no trust. Build trust through one to ones - practice on people, they will be happy you care. Do them with everyone you work directly with - 'rank' is irrelevant. Leeroy doesn't respect rank. To Leeroy everyLeeroy is Leeroy.

Trust is a really tricky and nuanced problem. It is better framed against common practices and looking at why they happen, and reframing the fear that causes them into a solution to the problem that caused it.

Trust is different everywhere - but the central problem in all this is that *nobody can be told* and worst people seem to do violence to themselves and prostrate themselves before assumed authority - even when it is subconscious. You can sit and explain as much as you like but visceral understanding comes from experience.

Basically trust is borne out of a sustained lack of fear and empathy in a relationship with someone.

### Fear

Depending on where you stand Leeroy is either too dumb or enlightened to know fear.

#### Process as a response to fear

Enterprise level process is nearly always driven by fear because it is a form of risk management. The problem is that if process was the antidote to fear of failure then to fix future failures the options are

1. More Process
2. Process Better

Oddly, it is never Process Less. And so we are still over processed.

Process local optima

This isn't to say process is bad - its the output of learning. But like learning and anything time based its fundamental property should be that it changes over time. But when there is nothing that can make a group change their mind about something - ie that process is required - then that group is operating under faith. Do not ever argue with faith, it only reinforces.

If we abandon the idea that process and methodology are a priori good then  we can start from nothing and introduce formalization's as experiments with clearly defined conceptions of the customer focussed value they will provide.

So we want to build trust without directly engaging with the idea of process in order to reduce fear.

But we cannot tell anyone anything and we definitely cannot tell them that their process sucks.

Well we can always build on empathy and strong relationships with people and demonstrate what we are talking about by delivering value to that person.

So here starts with a series of experiments that I found make the normal sets of processes look a bit silly and overly simplistic in how they approach delivery of value.

But who?

#### Find the person who suffers most and help

WRT fear this is almost certainly the QA. That poor individual (usually part of one to be fair) who is probably running batches of manual tests (with a job title of automation engineer) gets blamed whenever the deployment process (built by someone else) takes ages to redeploy because some shonky code written a week ago finally went live. Probably not what the job description was right? So talk to them, emphasize and figure out some work to help them out. Bring their job into your job.

I think it was Leaders Eat Last where he talks about finding the shittiest job and doing it, then doing every other job. That is basically what we are going to do here. Connect with everyone and help them with their problems - build up an understanding of them and the system.

I did a talk last year about being a caring automaton, rules for engaging when you think you are terrible at this stuff. It basically boiled down to asking

1. What is important? What is important to you? what is important to you now?
1. What do you want me to do?
1. What can i do differently?
1. What are you going to do?

It really helped me (notice they are what, not how).

You get this triangle of empathy and relatipnship building against the friction of delivering value fast right now against sitting down and showing people things

Anyway. By bringing QA into a development job you are then able to do something wonderful. You can make them do their job first, but with you. Work side by side not only to 3 amigos and lob over into dev but really sit down and pair on the problem. Agree and build something together and own it together. 

Congratulations you just got rid of at least 1 column in jira. I mean this literally as if the QA owns the work that was done as it was done then why do we need QA in its current guise? (IE running regression tests and just the right air of mystery for the upper levels to be happy)

#### Find a greenfield project and automate deployment all the way to production

Failure only costs due to the cost of delay of other delivering alternate customer value. A new project can fail deployment and not be the end of the world precisely because there is no connection to customer value yet - it is the perfect place to experiment. When you get push back as 'What is the harm?' The questions about the work become focussed on 'whats' instead of someones handwavey fear. Add 'for you' onto the end of questions to focus the question because about soling their specific fears.

So step one is to automate deployment of pretty much nothing all the way to prod.
Then tell the QA who will freak out because you didn't tell her.

Beg forgiveness whilst talking about harm. Then *listen* take anything that is said and turn it into automated tests. Be very attentive for concerns that indicate that this is not a project where qa automation is really going to cost more than it will protect. Consider that the automation will itself yield new information about the system.

#### Start to write tests that exercise the whole system

Because you are engaging a QA who probably is reticent about deployment you will start to cover tests that really matter. The tests that exercise the whole system but also protect the ability to deliver existing value to the customer.

Eg maybe you want to offer gurantee on being able to perform an action (such as a return) despite data or prices being iahrd to calculate. Maybe you want to protect the ability to calculate prices because this is a system about charging the customer.

Really these are simply tests that are designed to assert on the side effects of the system. When it starts up it should check its ability to effect these external dependencies, make sure all is happy and report on this. The tests simply assert against this. The purpose of the tests is to establish and disprove the areas of the codebase that could prove harm are capable of proving harm and halting the deployment as soon as possible.

This requires outside in approach

#### Fix the deployment process

The other thing making the QA sad is the deployment process. It probably takes too long. Whilst trying to automate your little green island you will discover just how bad your build, test and deploy system is. Network problems, broken build agents, blocked ports, non existent nuget packages from internal builds. Prelive environment that is nothing like live, UAT that has never has a user look at it - but is mandatory for every deploy.

Don't let this slide. It is apathy. Twitter keeps talking about things like 'Our job is to deploy'. Well if that is true then start there and work backwards unblocking everything that stops you doing that. That is what purposeful means - knowing where you want to be.

Teleology is a very powerful idea when you are creating something. Hackers joked about ys admins liking god as a password. That always amused me because programmers we are constantly developing and testing ontologies and building crazy living systems. If there ever was a domain where the causal principle of telos applies it is here. The point is the end causes the actions.

Or if you like phenomenology we walk forwards through time facing backwards. Or another way of looking at ist is we project ourselves forwards through time by moving backward through it. It is all about purpose.

The goal is to be able to pull the repo, run one command and have it run through all environments, run all tests against each environment and promote all the way to live with as little external dependencies as possible. Eg Octopus deploy is awesome, it adds a ton of value but i'd still question why you want configuration in it that is not already in your repo.

If you can deploy from your machine reliably and have integration tests run automatically after then something new is unlocked.

EveryLeroy can deploy from their own machines, they have a reliable deploy process, they have reliable tests to support that process and they have confidence in their relationships with their colleagues to be able to now crank code out into it.

#### Now you can deploy BEFORE you push

WTF?!

Yeah.

OK this bit is a bit crazy and needs to be caveatted. 
1. We need to be able to measure activley whether our work is working.
1. When it fails it needs to drop offline and self heal
1. If you have built a safe space that insulates the businesses revenue from the impact of your changes should they fail we are ok
1. We need a deployment mechanism that can fail over
1. We need a deployment mechanism that can detect failures and roll back
1. We need a mature team that is developing code with an understanding of how it will be verified and a QA process that insists on making verification code based upon deployment
1. We need local dev, test and live environments to be basically the same (docker / k8s / taking the time to build something v similar)

This sounds like a lot - but when we were doing this it is exactly what we had in place. We were also off the critical path for customer journeys + revenue generation.



commit -> pull -> deploy -> push

It either blows up or it runs through all the environments to live - until you have a really good reason not to.

We all know we shouldn't deploy before QA (well another set of eyes - the QA is either sat with us and bought in, or got up and walked away because confidence is that high.) 

But if the latest code is deployable, you have made a small change, the stakeholders and qa have worked on it throughout iwth you and you have built tests that capture the desired behaviour - Why wouldn't you deploy it if you could?


'Oh we just need to sanity check it ...'
Well insanity is doing the same thing twice and expecting something different to happen.
Good luck with that.

Now you can grab any commit and deploy it with very low risk, very high repeatability.

Best of all deploying before commit becomes a very natural workflow. You integrate your code, establish its value and then, only then push it. You can always roll back a deploy safely (if not then FIX IT) - it isn't like im advocating go live to all your users at once if that is genuinely a thing. But you could build some kind of heuristic to automatically decide if a deployment should survive ...

Moreover having no branches also pops out as a side effect. You simply have no need for them.

#### But doesn't this slow down the rate of integration?

Absolutely - if you do not code in a way that enables continuous integration. IE your code should be behind feature flags. Combined with thin slicing, some feature flags and working from the outside in it is possible to write a load of code, deploy with tests and then push at a high cadence. It does however put a ton of pressure on getting the deploy fast and smooth - which as above is our entire job.

It takes 5 minutes to deploy the project we worked on this appraoch with through every environment, run integrations tests on everything and promote.

### Now your jira boards looks really stupid

You have something like these columns (this is taken from a mainline branching strategy - because you can string words together and they always make sense. But its a real example):
Backlog : 3 amigos : in dev : feature testing : merge pending : release pending


#### Lets make it look more stupid - Befriend the BA

Now you get access to the stakeholders. When a value based decision comes up that the BA cannot answer then get up and go on a road trip with them to the stakeholder. 

What is value for this project?
What makes up prioritize this ticket over this ticket?
Shall we apply that logic in other places and see what happens?
What does the shape of the cost of delay look like even if we cannot put figures on it for these projects?
What can we do to reduce lead time to the left of dev given that we just crushed it on the board we currently have?


Maybe given our board look like this:

Backlog : in progress : deployed : committed 
Or maybe
Backlog : all the amigos : deployed : committed

I dont think committed is a column, i just added it to make a point

### Bring customer values to the fore

Obviously the businesses customers should drive all the value streams, but perhaps less obviously your internal stakeholders are also your customers. Even less obviously and far far more important, you collegues are also your customers. They are the consumers of all your communication (in the sense of Conway's law) - the manner in  which this is delivered is of immense importance.

Every interaction could be seen as a form of negotiation. You need to understand what is personally important to each person and understand how actions and communication align to these. It is what opens up the possibility of building a really strong team by demonstrating that you care - this is where trust comes from.

1. Fear of failure - this is often fear of breaking the build or fear of breaking prod.
1. A need for people to be visibly doing their job in a recorded audited system because when things go wrong they need their backs covered. By this I don't mean legal requirements - I simply mean shit flows down.
1. Agile processes that cannot be changed (or are highly resistant to) because they are the process - and that is how we do the process
1. Disconnect of people doing work for a customer yet never having talked to one.
1. Ceremony

## What is the solution?

### Rule Number One: NEVER tell anyone anything - you have to *SHOW* them

They will figure it out, they will realise this is kind of what they wanted to do and will have a ton of great ideas to help refine and incorporate into whatever zany system you come up with. If you are pairing with people and bringing them into the decision process then they will come with you on the journey. Especially if you understand their person motivations.

### The power of Leeroy is strong - With great power comes great responsibility - and accountability

Enthusiasm, commitment, accountability and responsibility are the corner stones. If you dive in screaming Leeroy Jenkins they kind of have to follow even if their cc isn't working out they way they planned.

When you sit next to someone, work with them and then ask just before you push 'This is the build script, when you run this it will deploy onto the testing environments, run all the tests then promote it through and repeat all the way to live. Are you ready to run it?' you get *very* interesting responses.

1. But don't we want to push first? - No, because I don't want undeployable code pushed. Git is essentially an immutable record - keeping it clean would be nice. I can redeploy and I have faith in the tests and build. Moreover I can take the codebase and pull and redeploy in 2 commands at any time.
1. But what if we break something? - Well what we did is tested, maybe we should get a QA involved or a stakeholder to demo to?
1. No but what is we *really* break something? - Ok so you are afraid. Thats ok, lets roll back to where we think we are safe and work slowly forward until everyone is happy again?

