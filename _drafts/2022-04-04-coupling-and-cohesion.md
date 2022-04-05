---
layout: post
title:  "Coupling and Cohesion: Fundemental Information Model"
date:   2022-04-04
categories: architecture coupling cohesion
---

# What is 'Coupling and Cohesion' and why you should care

These are 2 concepts that work together in 2 very interesting and useful dimensions.

## Coupling

When writing code there is a concept called ![Connascence](https://connascence.io/). This is a powerful tool for analysing code and refactoring. I will write about this in future posts however here I want to draw attention to 2 particlar parts.

1. Coupling gets broken into 3 aspects. 
   - The *type* of coupling (the name) which I will again come back to immediatley below.
   - Yhe *distance* between the 2 things that are coupled
1. The breakdown and naming of the types along with the sequencing of them enables moves and direction when refactoring. Eg performing an extract method refactor to convert connascence of algorithm into connascence of name. 
