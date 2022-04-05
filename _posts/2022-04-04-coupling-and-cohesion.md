---
layout: post
title:  "Coupling and Cohesion: Fundemental Information Model"
date:   2022-04-04
categories: architecture coupling cohesion
---

WIP

# What is 'Coupling and Cohesion' and why you should care

These are 2 concepts that work together in 2 very interesting and useful dimensions.

## Cohesion

Cohesion doesn't seem to have a good example of a metric. Therefor I am going to have to get more figurative and illustrative.
Systems that have low cohesion have uniformity. The cannonical example in my mind would be a perfect gas upon which PV = nRT would apply to. It is a system which may have an effectivley infinite number of parts because the parts are so homogenous and indecipherable they are effectivley one glob. As a result the glob of a system as a whole could be described as a cohesive lump if it had boundaries. As such a container around this could be said to have high cohesion. This then leads into the ancient question of 'if you have a vase with nothing in it and take away the vase - where is the nothing?' - anyway, I will leave you to ponder on that and its relation to the concept of self.

water molecues in a glass of water have low cohesion wheras the hexagonal cells in a honeycomb have high cohesion. Whilst both [plant cells](https://www.google.com/search?q=plant+cells&tbm=isch&ved=2ahUKEwj9kLDikfz2AhVRaPEDHR0gDZYQ2-cCegQIABAA&oq=plant+cells&gs_lcp=CgNpbWcQAzIHCAAQsQMQQzIECAAQQzIFCAAQgAQyBAgAEEMyBAgAEEMyBAgAEEMyBAgAEEMyBQgAEIAEMgUIABCABDIFCAAQgAQ6BwgjEO8DECc6CAgAEIAEELEDUM0IWNcRYP4SaABwAHgAgAE_iAGaBZIBAjEymAEAoAEBqgELZ3dzLXdpei1pbWfAAQE&sclient=img&ei=tMxLYv3mGdHQxc8PncC0sAk&bih=823&biw=1377&rlz=1C1CHBD_en-GBGB824GB824) and [animal cells](https://www.google.com/search?q=animal+cells&rlz=1C1CHBD_en-GBGB824GB824&sxsrf=APq-WBsrSfW7-JM25Zvhi_u3rlEseJsOsA:1649134765581&source=lnms&tbm=isch&sa=X&ved=2ahUKEwjnmI7fkfz2AhVOilwKHYqyDnYQ_AUoAXoECAEQAw&biw=1377&bih=823&dpr=2) are on their own cohesive I would say [collections of plant cells](https://www.pinterest.co.uk/pin/524880531566514173/) are more cohesive than [collection of animal cells](https://www.dreamstime.com/tissue-stomach-under-microscope-education-tissue-stomach-under-microscope-education-lab-image131991953). 

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