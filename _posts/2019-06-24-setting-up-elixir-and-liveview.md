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

The entire ecosystem and deployment pipeline from writing and javascript, html and css has become very very complex. The rate at which it is changing is highly significant and as a result developers with more than 2 years of experience in any given front end framework are exceptional.

This is a terrible state of affairs - it means that front end development has to follow a 'slash and burn' architectural pattern that assumes all code will be retired in a couple of years. These projects should not be designed to last more than 5 years because in 5 years time the landscape of front end development will be totally different. Being able to accommodate this change is key.

### So how to progress?

The generalised strategy of isolating a system from a part that changes is called an adapter or in the parlance of DDD an `anti-corruption layer`. If this is a viable strategy then using something that wraps up the entire JS ecosystem and abstracts away from it could be highly valuable.

This is what phoenix and live view is offering.

#### Is there another way?

Yes, come in underneath the javascript - this is hopefully what things like web assembly and Blazor are going to offer. I will be writing something on an investigation on that shortly.

## Install Elixir and Phoenix

[Install Elixir](https://elixir-lang.org/install.html)

[Install Phoenix](https://hexdocs.pm/phoenix/installation.html)

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
