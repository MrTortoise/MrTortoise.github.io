---
layout: post
title: "Elixir: How To Write An App You Can Deploy"
date: 2017-03-09 21:27:48 +0000
categories: elixir getting-started
---


## Disclaimer
I have no idea how to actually deploy anything yet. This is all taken from
[Getting Started](http://elixir-lang.org/getting-started), read that to make sense of this.
This is really just meant to be notes as a kind of a quick start.

## The point:

So I have been dicking around with Elixir for a while. Really enjoying it. However
I have never taken the time to actually attempt to build a service that is deployable.
So have decided to build up a minimum app that demonstrates a service that has the
basics that a deployable app would have.

The goal is to have a service that
1. can restart a part if it fails (supervisor hierarchy)
2. has logging
3. is testable
4. can be deployed
5. can demonstrate distributed processing with location transparency.
6. Has a way to communicate with external world.


## Steps to build
1. `mix new kv_umbrella --umbrella` - creates the umbrella project
2. build the service and the client projects
```
$ cd kv_umbrella/apps
$ mix new kv_server --module KVServer --sup
$ mix new kv --module KV
```
3. `mix test` - all should compile tests should run.
4. ...
5. wip
6. profit
