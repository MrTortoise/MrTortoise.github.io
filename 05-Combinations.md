Problem 26, combinations
========================

So its 3C2, really easy to do imperitivley or by passing a reference to a list about during recursion in an imperative langauge.

Odd never been stumped like this before.

I can easily generate a tree ... well the revalation has been that it is a tree, its a list where each subsequent node is a sublist. Not sure what took so long!

Anyway the point: its like i need to turn the tree inside out.

The problem is that when starting from the source of the tree how to you add items to a list of lists. If you start from the leaves and work back though then it seems doable.

the problem with *that* is that if i could do that ... ie generate a list of leaves and also for each item of that list return what would effectivley be a tuple of that item and its parent path ... then this would be a non problem.
