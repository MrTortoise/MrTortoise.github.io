---
layout: post
title: "Writing a game in Elixir, Phoenix and LiveView: Part 1 Setting up elixir and live view"
date: 2019-06-24 11:40:48 +0000
categories: elixir phoenix tutorial
---

## Someone beat me to writing Go in LiveView

I applaud them, great minds think alike. However I was far too lazy. So in response to that I decided that I was going to TDD a game of Go and why not do it in Live View. I am not going to look at the solution the other person came up with because then I can look at it later. There are some fun things in go ... counting liberties to figure out if a group is captured, scoring the game is not trivial, managing interesting states such as KO. Then there is scaling it to multiple games being played concurrently.

Basically I think this platform (Elixir, Phoenix and LiveView) are going to be almost idea for reproducing something like [OGS](https://online-go.com/) which was another i thing I was going to write about 15 years ago (when KGS introduced paid subscriptions) but never got around to.

## Live view promises server side updates of deltas in pages

This is basically all the advantages of server side rendering with react on top.

Right now the only reason to use React (aside from being a JS developer) is to get client side updates of the DOM in a way that is not incredibly hard to work with and scale over time.

The entire ecosystem and deployment pipeline from writing and javascript, html and css has become very very complex. The rate at which it is changing is highly significant and as a result developers with more than 2 years of experience in any given front end framework are exceptional. Eg compare day rates of 20 years of exp .net against a 2 year dev with only react exp and they are very close. Then look at how those hires influence the choices across the entire stack.

The rate of change is a terrible state of affairs - it means that front end development has to follow a 'slash and burn' architectural pattern that assumes all code will be retired in a couple of years (This style of pattern is what leads to the [big ball of mud](https://en.wikipedia.org/wiki/Big_ball_of_mud)). These projects should not be designed to last more than 5 years because in 5 years time the landscape of front end development will be totally different. Being able to accommodate this rate of change is key - spending a year building a react app before going public for instance is completely wrong.

### Alternative 1: Encapsulate the area that is rapidly changing behind an ACL

The generalised strategy of isolating a system from a part that changes is called an adapter or in the parlance of DDD an `anti-corruption layer`. If this is a viable strategy then using something that wraps up the entire JS ecosystem and abstracts away from it could be highly valuable.

This is what phoenix and live view is offering.

### Alternative 2: Find a way to intercept and get in before the rapidly changing ecosystem

This complexity comes from there being an ever changing standard of javascript being implemented in many different ways across browsers. Its a mess - so maybe we should [create a brand new competing standard](https://xkcd.com/927/)? This is hopefully what things like web assembly and Blazor are going to offer. I will be writing something on an investigation on that shortly.

The hope with these 2 options is - much like how html5 and the evolution away from jquery led to another generation of solutions that learnt from the insanity of jquery (mainly by abstracting away from global state) - WebAssembly can learn from everything before it and come up with something uniquely more consistent across browsers. Things like Edge moving to Chromium will also help.

## In the meantime: Install Elixir and Phoenix

[Install Elixir](https://elixir-lang.org/install.html) - I use Ubuntu because windows terminals are terrible in their support for full character sets. I am hoping that [WSL2](https://devblogs.microsoft.com/commandline/wsl-2-is-now-available-in-windows-insiders/) will fix this (but im not on the insider preview builds of windows)

[Install Phoenix](https://hexdocs.pm/phoenix/installation.html)

## IDE choices

I started using Atom, then VSCode but more recently I am using IntelliJ (because I ended up with buying licenses for rider and webstorm so got the lot). I stopped using Atom 2 years ago because VSCode had better extensions (Also developers in general were moving to VSCode so I used the most common tool) - but that may not be true anymore. VSCode was then a bit slow around the time of Elixir 1.6 and 1.8 in getting things like the formatters working so when I came back IntelliJ was easy and just worked. It is worth hopping about to find one that has what you like though - I haven't found any that have any refactorings like extract method or variable yet though.

## Setup your solution and projects

To create your project and solution do the following

We are going to use mix to set things up - it is the elixir packgage manager. Type `mix help new` to find out about the commands.

1. Create an umbrella app called `go`
2. Create an application module called `game`
3. Run the tests in it to validate it compiles and the tests pass
4. Create a Phoenix project (web) without the ORM layer (we will talk to other applications) called `client`
5. run its tests to validate it compiles and tests pass
6. start a development server in the client app

```bash

mix new go --umbrella
cd go
cd apps
mix new game
cd game
mix test
cd ..
mix phx.new client --no-ecto
cd client
mix test
mix phx.server
```

When prompted install dependencies

you can now see the phoenix site at `localhost:4000`

The `--no-ecto` creates the phoenix project without ecto which is the ORM that we may use in another project if we ever get to the point where we want a relational database. I suspect because of how live view works (IE a command model) we may end up event sourcing a lot of this as its a small step from CQS anyway.

you should now be able to go into the root of the umbrella and run `mix test` the results should be tests pass.

### Install Live View

[install liveview](https://github.com/phoenixframework/phoenix_live_view)

follow the instructions above.

Some notes where I had to diverge:

- When you are altering the `package.json` then you need to refer to the `deps` folder that is in the root of the umbrella solution rather than just the phoenix project (the client project).
- The config that sets up the live reload and the file associations was already included in my version of phoenix (this makes me worry I have added a dependency that is already in) - see code snippet below for already existing example.

```elixir
config :client, ClientWeb.Endpoint,
 live_reload: [
   patterns: [
     ~r"priv/static/.*(js|css|png|jpeg|jpg|gif|svg)$",
     ~r"priv/gettext/.*(po)$",
     ~r"lib/client_web/{live,views}/.*(ex)$",
     ~r"lib/client_web/templates/.*(eex)$"
   ]
 ]
```

## Getting yourself setup for TDD

Mix is great, but I like my tests to run everytime I hit save.

[mix test watch](https://github.com/lpil/mix-test.watch) this has your back. Simply add the following into your mix.exs at the root of the solution.

```elixir
def deps do
  [{:mix_test_watch, "~> 0.8", only: :dev, runtime: false}]
end
```

now rather than typing `mix test` to run your tests you can use `mix test.watch` and it will autorun tests whenever you save a file.
