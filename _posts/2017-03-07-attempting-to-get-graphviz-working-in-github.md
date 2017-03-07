---
layout: post
title: "Getting graphviz working in github"
date: 2017-03-07 19:39:48 +0000
categories: github markdown graphviz
---

Just playing around seeing what kind of diagramming i can get working without
having to resort to something that will force me to have images rather than
text editable documents.

I was looking for something like graphviz but found this [graphvizo]. Looks great
if it works in github!

The stuff below is copied directly from here: [github-graphviz]
The exmaple is also one of the ones that can be found at the previous link also.


![Alt text](https://g.gravizo.com/g?
  digraph G {
    aize ="4,4";
    main [shape=box];
    main -> parse [weight=8];
    parse -> execute;
    main -> init [style=dotted];
    main -> cleanup;
    execute -> { make_string; printf};
    init -> make_string;
    edge [color=red];
    main -> printf [style=bold,label="100 times"];
    make_string [label="make a string"];
    node [shape=box,style=filled,color=".7 .3 1.0"];
    execute -> compare;
  }
)

[graphvizo]: [https://g.gravizo.com/]
[github-graphvizo]:[https://github.com/TLmaK0/gravizo]
