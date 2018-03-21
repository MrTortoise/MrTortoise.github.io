---
layout: post
title:  "Elixir: Notes on Agent"
date:   2017-03-25 20:00:48 +0000
categories: elixir getting-started
---
## The repo backing this code is [here](https://github.com/MrTortoise/elixir-app-minimal).
It is literally a result of me working through the docs, nothing original.

## [Agent](http://elixir-lang.org/getting-started/mix-otp/agent.html)

### Purpose
It is a wrapper around state.

### Notes

1. Introduces `Agent.start_link/0` This is the equivalent of the [process](http://elixir-lang.org/getting-started/processes.html) `spawn_link` as far as I can tell.
  > Because processes are linked, we now see a message saying the parent
  > process, which is the shell process, has received an EXIT signal from
  > another process causing the shell to terminate. IEx detects this
  > situation and starts a new shell session.

 See `Task.start_link/1`
 > Task provides convenience functions, like Task.async/1 and Task.await/1, and functionality to ease distribution ... for now it is enough to remember to use Task to get better error reports.

2. ` Agent.get(bucket, &Map.get(&1, key))` The map function gets executed in the process of the Agent. So the &1 actually refers to the bucket and hence why you have to capture it with the `&` operator. So this is important:

 ```elixir
 def delete(bucket, key) do
   Process.sleep(1000) # puts client to sleep
   Agent.get_and_update(bucket, fn dict ->
     Process.sleep(1000) # puts server to sleep
     Map.pop(dict, key)
   end)
 end
 ```
