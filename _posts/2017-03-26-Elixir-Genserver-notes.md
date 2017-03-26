---
layout: post
title:  "Elixir: GenServer"
date:   2017-03-26 20:00:48 +0000
categories: elixir getting-started gen-server
---

## [GenServer](http://elixir-lang.org/getting-started/mix-otp/genserver.html)
1. Separate client api and server callbacks.
  - server callbacks: `init/1`, `handle_cast/2` and `handle_call/2`
2. `start_link/3` calls `GenServer.start_link(__MODULE__, :ok, [])`
  - interesting as it passes the current module as the name. But also initialisation arguments (`:ok`) and options
3. callbacks
  - `init/1` takes the argument from `GenServer.start_link, return s{:ok, state}`.

  wip
