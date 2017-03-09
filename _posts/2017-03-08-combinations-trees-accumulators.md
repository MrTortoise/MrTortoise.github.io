---
layout: post
title:  "Fun with Elixir: TDD and functional code"
date:   2017-03-08 13:27:48 +0000
categories: elixir code-challenge
---

# So problem 26, Permutations of 5P3 or something similar:

This has been a lot of fun. I have deliberately not gone looking for an answer
for this because I have been genuinely stumped. I could not see a way to iterate
towards it. I did not understand enough about the language to make progress - yet
all the problems before this were completely trivial.

## What have I learnt?

### TDD and functional programming is an interesting experience.
 I started by trying to start with base cases and then gradually increasing complexity. It
is interesting because you get to the 'now i need an algorithm, how on earth do
i gradually do it?' I.E. you don't get away with inside out. Outside in is almost a requirement - and also generally is the way that you should approach tdd (in my experience).

### You really need to figure out how to do whatever it is you are doing up front.
Personally i find things like c# generally very easy to solve any problem in. I think
this is simply because ive been doing it for a while i have already solved most
problems like the ones in the prolog test many times. This means i know i can vaguley
iterate and just recognise bad ideas, chuck em and try something else really quickly.
It took me far longer than I would of liked to realise that I could not only pass an
accumulator around but also pass functions that return the accumulator around. As a result
I figured out how to start with a root, navigate to all the leaves and add the path to the accumulator.

I wrote a the function behind this test:

`permute([1,2,3]) == [[1, [2, [3]], [3, [2]]], [2, [1, [3]], [3, [1]]], [3, [1, [2]], [2, [1]]]]`

I realised that this was basically a tree structure and then wrote something to expand the tree by starting from simple examples.

```
test "asserts expand 1 item" do
  assert FindPermutationsInList.expandTree([1]) == [[1]]
end

test "assert expand 2 item" do
  assert FindPermutationsInList.expandTree([1,[2]]) == [[1,2]]
end

test "assert expand 3 items" do
  assert FindPermutationsInList.expandTree([1,[2,[3]]]) == [[1,2,3]]
end

test "assert expand 2 items, second list" do
  assert FindPermutationsInList.expandTree([1,[2,3]]) == [[1,2],[1,3]]
end
```

The hope was that this would let me iterate to something without having to solve a big problem all at once.

However the examples above do not make it easy to get to the point where you can expand the output of the permute function above. Moreover that final test is not a valid example of what i am trying to solve - in fact it screwed me up badly as i then created another test in which not every node was a new sub list which threw me off even further. Lack of focus on delivering the solution to the problem. Big mistake.  I then ended up writing a function to return the next item that is also a sublist and not just another node.

The code that makes the above tests pass looks like this
```
def expandTree(list), do: expandTree([],[],list)

defp expandTree(acc, parents, []), do: acc ++ [parents]
defp expandTree(acc, parents, [item]) when not is_list(item), do: acc ++ [parents ++ [item]]
defp expandTree(acc, parents, [h|[t]]) when is_list(t), do: expandTree(acc, parents++[h],t)
defp expandTree(acc, parents, [h|t]) do
  expandTree(
  expandTree(acc,parents,t),
  parents++[h], getStartOfNextList(t))
  |> Enum.reverse
end

def getStartOfNextList([]), do: []
def getStartOfNextList([_|[t]]) when is_list(t), do: t
def getStartOfNextList([_|t]), do: getStartOfNextList(t)
```

The problem is that it utterly fails to deal with the output of permute. I failed to characterise a key quality (every node is a sublist), and introduced characteristics that are not in the real data.

Back to the drawing board ...
