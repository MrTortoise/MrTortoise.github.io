---
layout: post
title:  "Coupling and Cohesion: Fundemental Information Model"
date:   2022-04-04
categories: architecture coupling cohesion
---

# What is 'Coupling and Cohesion' and why you should care

These are 2 concepts that work together in 2 very interesting and useful dimensions.

## Coupling

When writing code there is a concept called [Connascence](https://connascence.io/). This is a powerful tool for analysing code and refactoring. The purpose of it is to enable conversations around understanding how things are coupled together. This then helps to facilitate conversations around deliberatley choosing what coupling should look like or identify situations where different forms are more or less desirable. I will write about connascence as it applies to code more in future posts, however here I want to draw attention to 2 particlar parts.

1. The 'amount' or as I like to think of it the vector of coupling gets broken into 3 aspects. 
   - The *type* of coupling (the name) which I will again come back to immediatley below.
   - Yhe *distance* between the 2 things that are coupled. The larger the distance the harder it is to know that the things are coupled. This is experienced as downstream systems failing unexpectedly upon change. Kent Beck gave a great example of 2 services being coupled because when one changed in a way that increased its network traffic some seemingly unreleated service in any logical sense started to fail - because they were both in a data center accessing the world via the same faulty switch. We can reduce the magnitude of this metric of coupling by beinging things that are coupled closer together. For instance a lot of refactors will take sets of code changes that would effect multiple files throught a system and refactor the system so that those changes happen in the same folder or file. An example of this would be refactoring connascence of algorithm into connascence of name by taking 2 pieces of code in different parts of a system - one part encrypts and the other decrypts some data. We can refactor this by and moving that into a common class which is then referred to by its name.
1. The breakdown and naming of the types along with the sequencing of them enables moves and direction when refactoring. Eg performing an extract method refactor to convert connascence of algorithm into connascence of name. 
