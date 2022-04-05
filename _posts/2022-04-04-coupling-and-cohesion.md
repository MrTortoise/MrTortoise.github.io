---
layout: post
title:  "Coupling and Cohesion: Fundemental Information Model"
date:   2022-04-04
categories: architecture coupling cohesion
---

WIP

# What is 'Coupling and Cohesion' and why you should care

We want to really understand the predictability of systems because that allows us to know whether we have a system that we can test against reality and when we do test it what we expect to happen.  In businesses we call this making money, in product it is knowing your customer, in code it is getting the bloody thing to firstly compile and secondly do what we want. These are 2 fundemental concepts because everything is an information model and these concepts are descriptors of it.

These are 2 concepts that work together in 2 very interesting and useful dimensions.

I have been finding recently that I think in ways that frustrate a lot of people. When trying to explain something and understnad something (like the 2 concepts here) I understand them through their many different connections to other ideas. I will connect them with different ways of using them. By enumerating those different ways I think I am adding to either existing contexts or adding new contexts (or games).

The act of doing this reduces the cohesion of the origional thing I was talking about because as you couple that idea to an increasing number of other ideas that seem to be coherent with one another it gets harder and harder for the victim to keep clean walls around the origional idea. But this is a thing we grapple with every day - the concept of the 'product' a business sells is completley different in each different department of an organisation. In ecom product for people managing client accounts is all about market, availability and margin wheras product for a site team is data to be shown on a site and getting it to edges quickly. Product for a warehouse is about uunpacking, shelving, completing orders, packing and distribution - and less about the indiviual items. Nobody is more correct than anybody else - its just different but additive to a full understanding. Provided we keep the different conceptualisations seperate (and cohesive) we can couple these different meanings together - and by exploiting this we have a functional cohesive company.

The complaint I get is that my way of thinking and understanding has become too complicated. The ideas are too complex because they cannot be applied predictably because information overload.

Coupling and Cohesion are 2 concepts that work together to give us tools to describe the connections, globbyness and uniformity of information models. This matters because doing this well has a large impact on the predictability of systems.

When we are talking about predictablity of systems in my brain we are in the realm of Cynefin and its analysis of complexity.

For instance, systems with extremley low cohesion (eg a perfect gas) are also chaotic systems that can be exploited as they are also statistical systems because their parts are independant. Therefor if we can manipulate coupling and cohesion then we can convert at least parts of systems into states upon which we can use statistical tools.  

System with very high cohesion and well understood and mapped coupling tend towards simple from being complicated. 



## Cohesion

### What is Cohesion?
Cohesion doesn't seem to have a good example of a metric. Therefor I am going to have to get more figurative and illustrative.
Systems that have low cohesion have uniformity. The cannonical example in my mind would be a perfect gas upon which PV = nRT would apply to. It is a system which may have an effectivley infinite number of parts because the parts are so homogenous, indecipherable and interchangable that they are effectivley one glob. As a result the glob of a system as a whole could be described as a cohesive lump if it had boundaries. As such a container around this could be said to have high cohesion. This then leads into the ancient question of 'if you have a vase with nothing in it and take away the vase - where is the nothing?' - anyway, I will leave you to ponder on that and its relation to the concept of self.

Water molecues in a glass of water have low cohesion wheras the hexagonal cells in a honeycomb have high cohesion. Whilst both [plant cells](https://www.google.com/search?q=plant+cells&tbm=isch&ved=2ahUKEwj9kLDikfz2AhVRaPEDHR0gDZYQ2-cCegQIABAA&oq=plant+cells&gs_lcp=CgNpbWcQAzIHCAAQsQMQQzIECAAQQzIFCAAQgAQyBAgAEEMyBAgAEEMyBAgAEEMyBAgAEEMyBQgAEIAEMgUIABCABDIFCAAQgAQ6BwgjEO8DECc6CAgAEIAEELEDUM0IWNcRYP4SaABwAHgAgAE_iAGaBZIBAjEymAEAoAEBqgELZ3dzLXdpei1pbWfAAQE&sclient=img&ei=tMxLYv3mGdHQxc8PncC0sAk&bih=823&biw=1377&rlz=1C1CHBD_en-GBGB824GB824) and [animal cells](https://www.google.com/search?q=animal+cells&rlz=1C1CHBD_en-GBGB824GB824&sxsrf=APq-WBsrSfW7-JM25Zvhi_u3rlEseJsOsA:1649134765581&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjnmI7fkfz2AhVOilwKHYqyDnYQ_AUoAXoECAEQAw&biw=1377&bih=823&dpr=2) are on their own cohesive I would say [collections of plant cells](https://www.pinterest.co.uk/pin/524880531566514173/) are more cohesive than [collection of animal cells](https://www.dreamstime.com/tissue-stomach-under-microscope-education-tissue-stomach-under-microscope-education-lab-image131991953). 

I also think that contrast is a great example of how complexity can interract with coupling and cohesion. A collection of plan cell looks kess complex than the animal cells - it would seem reasonable to say behaviour of the different would be more uniform as they look the same. In the animal cell example (stomach lining) there is more variety of strucutre and purpose - combining these different functions into the same collection makes the collection less cohesive - and perhaps less predictable. 

### Cohesions curious relationship with complexity
One of the definitions of complexity when you get into Cynefin and playing tricks there is that a complex system is one where you do not know all the constraints. The evidence for this is one where you make a change expecting one thing and a different thing happens. This is a property of a dispositional system - and system involving people tend to be like this. A complex system where you cannot establish the constraints through analysis alone. When we see coupling below we will meet connascence, in that idea there are forms dynamic coupling that are only visible at run time. Therefor without the concept of connascence these systems would remain complex and unpredicable but by applying and using the langauge and games of connscence (such as mapping activities) it is possible for these to become complicated.

Ants marching in lines are more cohesive than a swarm of locusts.

Things with more cohesion have very different properties to things with very low cohesion. I believe this can end up being related to an idea of constraints and system complexity in [Cynefin](https://en.wikipedia.org/wiki/Cynefin_framework).

## Coupling

When writing code there is a concept called [Connascence](https://connascence.io/). This is a powerful tool for analysing code and refactoring. The purpose of it is to enable conversations around understanding how things are coupled together. This then helps to facilitate conversations around deliberatley choosing what coupling should look like or identify situations where different forms are more or less desirable. I will write about connascence as it applies to code more in future posts, however here I want to draw attention to 2 particlar components.

### Components of Coupling
#### Type 

The *type* of coupling (the name) which I will again come back to immediatley below.

#### Distance

The *distance* between the 2 things that are coupled. The larger the distance the harder it is to know that the things are coupled. This is experienced as downstream systems failing unexpectedly upon change. Kent Beck gave a great example of 2 services being coupled because when one changed in a way that increased its network traffic some seemingly unreleated service in any logical sense started to fail - because they were both in a data center accessing the world via the same faulty switch. We can reduce the magnitude of this metric of coupling by bringing things that are coupled closer together. For instance a lot of refactors will take sets of code changes that would effect multiple files throught a system and refactor the system so that those changes happen in the same folder or file. An example of this would be refactoring connascence of algorithm into connascence of name by taking 2 pieces of code in different parts of a system - one part encrypts and the other decrypts some data. We can refactor this by taking these 2 coupled sides and moving that into a common class which is then referred to by its name. If we then found that we had multiple ways of encrypting/serialising in different areas we could also use an extract interface refactor to convert their connascence of meaning into connascence of name. Considering connascence and distance leads to things that change together living together - and things that change at different times for different reasons naturally being allowed to drift apart. That deliberate action of pulling and pushing things apart leads to the other concept - cohesion, but more on that shortly. As an aside this is the power of javascript - because json and js are so closley related the need for serialising and deserialising into a type system does not exist which gives is a unique set of superpowers and downsides that are very exploitable in the current world. Typescript - in this conceptualisation - sacrifices some of this closeness (lack of distance) away in an attempt to gain and exploit different types of coupling.

#### Degree 
The *number of things*. When something is coupled to more things it is perhaps unsuprisingly more coupled. The effect of this is that changes to something - or the things it is coupled to can effect the whole network of connections. In this network the edges are types of coupling and their strength is almost their distance. The final part that determines how hard it is to understnad the effect of changing something is the number of things a node is coupled to. The reason we like to play with the type of coupling is that by tactically choosing a less severe form of coupling we can use things like compilers to detect when we have broken the contract by which we have coupled. The more things that are coupled the less non zero the changes of some unknown of horrible type of coupling. By being explicity about the number of things we are maintaining a map of what is coupled to what that we can navigate and manipulate. I will again come back to this when writing up some stuff about architecture, event sourcing, cqrs and event modelling (and storming).
- 
1. The breakdown and naming of the types along with the sequencing of them enables moves and direction when refactoring. Eg performing an extract method refactor to convert connascence of algorithm into connascence of name. 

### Coupling in non-code contexts

Different levels in systems
(fold left)

## Bringing it all together (Making the coupled paragraphs cohesive)