---
layout: post
title:  "Elixir: Notes on GenServer"
date:   2017-03-26 20:00:48 +0000
categories: elixir getting-started gen-server
---
## The reps backing this code is [here](https://github.com/MrTortoise/elixir-app-minimal).
It is literally a result of me working through the docs, nothing original.

## [GenServer](http://elixir-lang.org/getting-started/mix-otp/genserver.html)
The [Full Gen ServerDocumentaiton is here](https://hexdocs.pm/elixir/GenServer.html)

The code these notes refer to:

``` Elixir
  defmodule KV.Registry do
  use GenServer

  ## Client API

  @doc """
  Starts the registry.
  """
  def start_link do
    GenServer.start_link(__MODULE__, :ok, [])
  end

  @doc """
  Looks up the bucket pid for `name` stored in `server`.

  Returns `{:ok, pid}` if the bucket exists, `:error` otherwise.
  """
  def lookup(server, name) do
    GenServer.call(server, {:lookup, name})
  end

  @doc """
  Ensures there is a bucket associated to the given `name` in `server`.
  """
  def create(server, name) do
    GenServer.cast(server, {:create, name})
  end

  ## Server Callbacks

  def init(:ok) do
    {:ok, %{}}
  end

  def handle_call({:lookup, name}, _from, names) do
    {:reply, Map.fetch(names, name), names}
  end

  def handle_cast({:create, name}, names) do
    if Map.has_key?(names, name) do
      {:noreply, names}
    else
      {:ok, bucket} = KV.Bucket.start_link
      {:noreply, Map.put(names, name, bucket)}
    end
  end
end
```

1. Separate client api and server callbacks.
  - server callbacks: `init/1`, `handle_cast/2` and `handle_call/2`
2. `start_link/3` calls `GenServer.start_link(__MODULE__, :ok, [])`
  - interesting as it passes the current module as the name. But also initialisation arguments (`:ok`) and options
3. callbacks
  - `init/1` takes the argument from `GenServer.start_link, return s{:ok, state}`.
  - `handle_call` is hit from `GenServer.call(server, {:lookup, name})` - gotta wonder how that `_from` would get populated given the indirection.

Problem with code above is that if a  bucket process stops the name remains in the registry. So some cleanup is required.

The server side code is modified to the following

```Elixir
## Server callbacks

def init(:ok) do
  names = %{}
  refs  = %{}
  {:ok, {names, refs}}
end

def handle_call({:lookup, name}, _from, {names, _} = state) do
  {:reply, Map.fetch(names, name), state}
end

def handle_cast({:create, name}, {names, refs}) do
  if Map.has_key?(names, name) do
    {:noreply, {names, refs}}
  else
    {:ok, pid} = KV.Bucket.start_link
    ref = Process.monitor(pid)
    refs = Map.put(refs, ref, name)
    names = Map.put(names, name, pid)
    {:noreply, {names, refs}}
  end
end

def handle_info({:DOWN, ref, :process, _pid, _reason}, {names, refs}) do
  {name, refs} = Map.pop(refs, ref)
  names = Map.delete(names, name)
  {:noreply, {names, refs}}
end

def handle_info(_msg, state) do
  {:noreply, state}
end
```
1. Previously the code only had one map in the init - the names map. Now there is also a refs map. So in handle call the state is returned rather than just names.
2. The code includes the `handle_info` calls which are used here for handling the supervision related jobs. Any message sent that is not via `call` or `cast` hits this endpoint.

### Monitors or links
Final point is that with linked process if 1 dies both die. With monitoring only th emonitoring process gets info. In `handle_cast` above we do both ... this is bad.
