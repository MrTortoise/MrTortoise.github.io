---
layout: post
title:  "Elixir: Notes on Supervisor and Application"
date:   2017-03-26 20:30:48 +0000
categories: elixir getting-started supervisor
---
## The repo backing this code is [here](https://github.com/MrTortoise/elixir-app-minimal).
It is literally a result of me working through the docs, nothing original.

## [Supervisor and Application](http://elixir-lang.org/getting-started/mix-otp/supervisor-and-application.html)

### Supervisor code

```elixir
defmodule KV.Supervisor do
  use Supervisor

  def start_link do
    Supervisor.start_link(__MODULE__, :ok)
  end

  def init(:ok) do
    children = [
      worker(KV.Registry, [KV.Registry])
    ]

    supervise(children, strategy: :one_for_one)
  end
end
```

Key points:
1. `  worker(KV.Registry, [KV.Registry])` this calls `KV.Registry.start_link(KV.Registry)`
2. This means that the `KV.Registry` needs to take a name as an argument

We could now do this:

```elixir
iex> KV.Supervisor.start_link
{:ok, #PID<0.66.0>}
iex> KV.Registry.create(KV.Registry, "shopping")
:ok
iex> KV.Registry.lookup(KV.Registry, "shopping")
{:ok, #PID<0.70.0>}
```

But we don't, we use an application

## Application

To start iex and be able to use the observer gui you need this command line `iex --erl "-smp" -S mix`
