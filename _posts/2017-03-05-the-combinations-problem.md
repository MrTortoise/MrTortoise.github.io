---
layout: post
title:  "The Combinations problem"
date:   2017-03-05 21:27:48 +0000
categories: elixir code-challenge
---

The background is that I was attempting to to the [99 prolog problems][99-prolog-problems]. All was going well until i hit the permutation / combination problem at question 26. [elixir repo][elixir-repo]


So its 3C2, really easy to do imperatively or by passing a reference to a list about during recursion in an imperative language. Odd never been stumped like this before. After some thought it turns out I hadn't realised I was creating a tree.

Anyway the point: its like I need to turn the tree inside out.

The problem is that when starting from the source of the tree how to you add items to a list of lists. If you start from the leaves and work back though then it seems doable - and so some kind of accumulator parameter could work.

[99-prolog-problems]: https://sites.google.com/site/prologsite/prolog-problems
[elixir-repo]: https://github.com/MrTortoise/elixir_ninety_nine_problems
