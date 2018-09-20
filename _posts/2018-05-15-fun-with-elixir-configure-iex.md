---
layout: post
title:  "Fun With: Elixir - configure iex"
date:   2018-05-15 22:00:48 +0000
categories: elixir iex funwith
---

# Fun with Elixir: Configuring Iex

## Pressing up does not show previous shell commands

This is basic bash shell functionality. Well it's turned off by default ... grr

to enable use this environment variable

``` bash
export ERL_AFLAGS="-kernel shell_history enabled"
```

you can find more info on iex configuration [here](https://hexdocs.pm/iex/IEx.html)

There is a ton of useful stuff on that page that wasn't in Elixir a year ago.

Eg breakpoints.

Other useful stuff is colours (especially if like me you cannot read red on black)