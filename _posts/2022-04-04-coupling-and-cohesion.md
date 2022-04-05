---
layout: post
title:  "Coupling and Cohesion: Fundamental Information Model"
date:   2022-04-04
categories: architecture coupling cohesion
---

WIP

# What is 'Coupling and Cohesion' and why you should care

We spend most of our time changing existing systems and trying to [figure out how systems work](https://lepiter.io/feenk/developers-spend-most-of-their-time-figuri-9q25taswlbzjc5rsufndeu0py/). 
As such our ambition should be to build systems in ways that makes them easy to change - change also implies that we do not know what the system will need to do in a short period of time. As such we also need to be working in ways to learn and get to this change.

Anything we can do to make our lives simpler here will pay off monumentally because systems size often exceeds our capacity for mental models. We need to be able to forget parts of a system and use heuristics and assumptions to work effectively. This requires predictability. Predictability with low cognitive effort requires simplicity.

Coupling and Cohesion are words that describe complexity in the sense of complect - to braid parts of a system together. Rich Hickey gave a great talk on simplicity.

{% include youtubePlayer.html id="rI8tNMsozo0" %}

> 'The Agility of simplicity dominates all other forms of agility'

The more complected a system is the more of a hairball it is. But also the more parts effect other parts which makes it dramatically harder to reason about and be correct in our expectations.

Simplicity requires that separate parts of a system be as independent as possible. By not coupling these parts together we create firebreaks that limit the impact of change. 


### There is a lot of cargo culting and kool-aid

However we also have to consider the cognitive cost of introducing abstractions. A lot of software developers practice [Don't Repeat Yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) and a weird form of [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single-responsibility_principle) that cause a lot of harm. For instance the first 2 paragraphs in the SRP link contradict themselves. Is says Robert Martin made up the term and defined it in the second paragraph but only after proposing the common misunderstanding first. The danger is taking heuristics like these and blindly applying them.  

It is very possible (and common) for 2 pieces of code to be almost identical but have different owners. When you apply do not repeat yourself and extract them then you have invented work to do this, you have complected 2 parts of the system together. As a result changing the common for one breaks the other because these 2 pieces have separate owners and so change in both will happen at different times for different reasons. Applying do not repeat yourself here is not good - it is overzealous and increases complexity despite apparently increasing cohesion and lowering coupling. This happens but it should be said the heuristic is pretty good most of the time.

The common statement is insufficient as it is incoherent to the overly simplistic view people take. We can do better!

### What really matters? Predictability

We want to really understand the predictability of systems because that allows us to know whether we have a system that we can test against reality and when we do test it what we expect to happen.  In businesses we call this making money, in product it is knowing your customer, in code it is getting the bloody thing to firstly compile and secondly do what we want. These are 2 fundamental concepts because everything is an information model and these concepts are descriptors of it.

## Information Model and Context

I have been finding recently that I think in ways that frustrate a lot of people. When trying to explain something and understand something (like the 2 concepts here) I understand them through their many different connections to other ideas. I will connect them with different ways of using them. By enumerating those different ways I think I am adding to either existing contexts or adding new contexts (or games).

The act of doing this reduces the cohesion of the original thing I was talking about because as you couple that idea to an increasing number of other ideas that seem to be coherent with one another it gets harder and harder for the victim to keep clean walls around the original idea. But this is a thing we grapple with every day - the concept of the 'product' a business sells is completely different in each different department of an organization. In ecom product for people managing client accounts is all about market, availability and margin whereas product for a site team is data to be shown on a site and getting it to edges quickly. Product for a warehouse is about unpacking, shelving, completing orders, packing and distribution - and less about the individual items. Nobody is more correct than anybody else - its just different but additive to a full understanding. Provided we keep the different conceptualizations separate (and cohesive) we can couple these different meanings together - and by exploiting this we have a functional cohesive company.

## Exploiting Cynefin to build information and to deliberately identify unpredictability
The complaint I get is that my way of thinking and understanding has become too complicated. The ideas are too complex because they cannot be applied predictably because information overload.

Coupling and Cohesion are 2 concepts that work together to give us tools to describe the connections, globbyness and uniformity of information models. This matters because doing this well has a large impact on the predictability of systems.

When we are talking about predictability of systems in my brain we are in the realm of [Cynefin](https://en.wikipedia.org/wiki/Cynefin_framework) and its analysis of complexity. In software most of our systems are complex adaptive systems as they interact with people - customers. 

For instance, systems with extremely low cohesion and low coupling (eg a [perfect gas](https://www.khanacademy.org/science/ap-chemistry-beta/x2eef969c74e0d802:intermolecular-forces-and-properties/x2eef969c74e0d802:ideal-gas-law/v/ideal-gas-equation-pv-nrt)) are also chaotic systems that can be exploited as they are also [statistical systems because their parts are independent](https://en.wikipedia.org/wiki/Sampling_(statistics)). Therefor if we can manipulate and reduce coupling and cohesion then we can convert at least parts of systems into states upon which we can use statistical tools.  

Additionally, systems with badly understood coupling are going to be systems that when poked do unexpected things - a system that is partially or temporarily predictable is a complex system.

System with very high cohesion and well understood and mapped coupling tend towards simple from being complicated. By creating islands of cohesion it is possible to find islands of simplicity inside a complicated system.

This leads me to think in this sort of metaphor that moving from complex to complicated is the exercise of identifying the nature and kinds of coupling in a system. In code systems which is what is the main focus of myself a lot of complexity comes from difficulty of inspecting at compile time. Whereas some systems are very dispositional and feedback into themselves - this is I suspect very closely related to Heisenberg uncertainty - but in a system with a person if you interact with it in the same way twice it is unlikely to behave in the same say twice. This is because last interaction in some - perhaps metaphorical - way changed its starting state. These dispositional systems truly are complex - whereas some code systems are complex only because we did it badly. 

The goal here is to use some tools to get into what does bad look like? how do we detect and find it? what tools do we have to play with it once we find it?

## Cohesion

### What is Cohesion?
Cohesion doesn't seem to have a good example of a metric (entropy is possibly analogous - however that maybe more confusing!). Therefor I am going to have to get more figurative and illustrative.
Systems that have low cohesion have uniformity. The canonical example in my mind would be a perfect gas upon which PV = nRT would apply to. It is a system which may have an effectively infinite number of parts because the parts are so homogenous, indecipherable and interchangeable that they are effectively one glob. As a result the glob of a system as a whole could be described as a cohesive lump if it had boundaries. As such a container around this could be said to have high cohesion. This then leads into the ancient question of 'if you have a vase with nothing in it and take away the vase - where is the nothing?' - anyway, I will leave you to ponder on that and its relation to the concept of self.

Water molecules in a glass of water have low cohesion whereas the hexagonal cells in a honeycomb have high cohesion. Whilst both [plant cells](https://www.google.com/search?q=plant+cells&tbm=isch&ved=2ahUKEwj9kLDikfz2AhVRaPEDHR0gDZYQ2-cCegQIABAA&oq=plant+cells&gs_lcp=CgNpbWcQAzIHCAAQsQMQQzIECAAQQzIFCAAQgAQyBAgAEEMyBAgAEEMyBAgAEEMyBAgAEEMyBQgAEIAEMgUIABCABDIFCAAQgAQ6BwgjEO8DECc6CAgAEIAEELEDUM0IWNcRYP4SaABwAHgAgAE_iAGaBZIBAjEymAEAoAEBqgELZ3dzLXdpei1pbWfAAQE&sclient=img&ei=tMxLYv3mGdHQxc8PncC0sAk&bih=823&biw=1377&rlz=1C1CHBD_en-GBGB824GB824) and [animal cells](https://www.google.com/search?q=animal+cells&rlz=1C1CHBD_en-GBGB824GB824&sxsrf=APq-WBsrSfW7-JM25Zvhi_u3rlEseJsOsA:1649134765581&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjnmI7fkfz2AhVOilwKHYqyDnYQ_AUoAXoECAEQAw&biw=1377&bih=823&dpr=2) are on their own cohesive I would say [collections of plant cells](https://www.pinterest.co.uk/pin/524880531566514173/) are more cohesive than [collection of animal cells](https://www.dreamstime.com/tissue-stomach-under-microscope-education-tissue-stomach-under-microscope-education-lab-image131991953). 

I also think that contrast is a great example of how complexity can interact with coupling and cohesion. A collection of plan cell looks less complex than the animal cells - it would seem reasonable to say behavior of the different would be more uniform as they look the same. In the animal cell example (stomach lining) there is more variety of structure and purpose - combining these different functions into the same collection makes the collection less cohesive - and perhaps less predictable as to its function per sample. 

### Cohesions curious relationship with complexity
One of the definitions of complexity when you get into [Cynefin](https://en.wikipedia.org/wiki/Cynefin_framework) and playing tricks there is that a complex system is one where you do not know all the [constraints](https://cynefin.io/wiki/Constraints). The evidence for this is one where you make a change expecting one thing and a different thing happens. This is a property of a [dispositional system](https://thecynefin.co/inclinations-dispositions/) - and system involving people tend to be like this. A complex system where you cannot establish the constraints through analysis alone. When we see coupling below we will meet connascence, in that idea there are forms dynamic coupling that are only visible at run time. Therefor without the concept of connascence these systems would remain complex and unpredictable but by applying and using the language and games of connascence (such as mapping activities) it is possible for these to become complicated.

Ants marching in lines are more cohesive than a swarm of locusts. So we could try to say that by increasing the cohesiveness of something we are sucking the chaos, the entropy out of it. However it is possible to have a system that has high cohesion with a part that is chaotic - this is desirable and necessary in many cases (reality is chaotic). Eg a random number generator or the system that includes someone measuring the outside temperature.

Things with more cohesion have very different properties to things with very low cohesion. I believe this can end up being related to an idea of constraints and system complexity in [Cynefin](https://en.wikipedia.org/wiki/Cynefin_framework).

## Coupling

There is a lot of discussion between high and low levels of coupling. However this has always felt vague to me. This all changed when I found [Connascence](https://connascence.io/) as suddenly these vague ideas that were mapping more onto encapsulation and numbers of connections now had some meat.

### Low Coupling != Good

The problem with the common idea of low coupling as basically being high coupling but you put something in a box and point to the box is that it is overly simplistic. In reality there is a balance between going overboard and producing [Fizz Buzz enterprise architecture](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition). 

When you extract all these parts into something common across systems you are coupling those systems together. This in turn means are all of a sudden it is possible to break another teams work - so some activities that lower levels of coupling can introduce incredibly hard to detect problems. This is not good! There is a need for something more subtle!

### Simplicity == good



### Something less simplistic (Connascence)
When writing code there is a concept called [Connascence](https://connascence.io/). This is a powerful tool for analyzing code and refactoring. The purpose of it is to enable conversations around understanding how things are coupled together. This then helps to facilitate conversations around deliberately choosing what coupling should look like or identify situations where different forms are more or less desirable. I will write about connascence as it applies to code more in future posts, however here I want to draw attention to 2 particular components.

### Components of Coupling
#### Type 

The *type* of coupling (the name) which I will again come back to immediately below.

#### Distance

The *distance* between the 2 things that are coupled. The larger the distance the harder it is to know that the things are coupled. This is experienced as downstream systems failing unexpectedly upon change. Kent Beck gave a great example of 2 services being coupled because when one changed in a way that increased its network traffic some seemingly unrelated service in any logical sense started to fail - because they were both in a data center accessing the world via the same faulty switch. We can reduce the magnitude of this metric of coupling by bringing things that are coupled closer together. For instance a lot of refactors will take sets of code changes that would effect multiple files through a system and refactor the system so that those changes happen in the same folder or file. An example of this would be refactoring connascence of algorithm into connascence of name by taking 2 pieces of code in different parts of a system - one part encrypts and the other decrypts some data. We can refactor this by taking these 2 coupled sides and moving that into a common class which is then referred to by its name. If we then found that we had multiple ways of encrypting/serializing in different areas we could also use an extract interface refactor to convert their connascence of meaning into connascence of name. Considering connascence and distance leads to things that change together living together - and things that change at different times for different reasons naturally being allowed to drift apart. That deliberate action of pulling and pushing things apart leads to the other concept - cohesion, but more on that shortly. As an aside this is the power of javascript - because json and js are so closely related the need for serializing and deserializing into a type system does not exist which gives is a unique set of superpowers and downsides that are very exploitable in the current world. Typescript - in this conceptualization - sacrifices some of this closeness (lack of distance) away in an attempt to gain and exploit different types of coupling.

#### Degree 
The *number of things*. When something is coupled to more things it is perhaps unsurprisingly more coupled. The effect of this is that changes to something - or the things it is coupled to can effect the whole network of connections. In this network the edges are types of coupling and their strength is almost their distance. The final part that determines how hard it is to understand the effect of changing something is the number of things a node is coupled to. The reason we like to play with the type of coupling is that by tactically choosing a less severe form of coupling we can use things like compilers to detect when we have broken the contract by which we have coupled. The more things that are coupled the less non zero the changes of some unknown of horrible type of coupling. By being explicitly about the number of things we are maintaining a map of what is coupled to what that we can navigate and manipulate. I will again come back to this when writing up some stuff about architecture, event sourcing, CQRS and event modelling (and storming).
- 
1. The breakdown and naming of the types along with the sequencing of them enables moves and direction when refactoring. Eg performing an extract method refactor to convert connascence of algorithm into connascence of name. 

### Coupling in non-code contexts

Different levels in systems
(fold left)

## Bringing it all together (Making the coupled paragraphs cohesive)