---
layout: post
title:  "Elixir: Code Snippets"
date:   2017-04-01 13:30:48 +0000
categories: elixir getting-started snippets
---

## Code snippets that illustrate ideas nicley

1. take params object map to equality filter
  ``` Elixir
def​ get_by(module, params) ​do​
    Enum.find all(module), ​fn​ map ->
​    Enum.all?(params, ​fn​ {key, val} -> Map.get(map, key) == val ​end​)
​  ​end​
​end​
  ```
