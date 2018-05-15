---
layout: post
title:  "Fun With: RabbitMQ and Elixir"
date:   2018-05-14 21:00:48 +0000
categories: elixir rabbitmq erlang funwith
---
## Elixir is Erlang, RabbitMQ is Erlang ZOMG this should be amazing

So to cut a fairly dull story short. This is what to do

1. Do not upgrade your ubuntu distro to latest and expect all to be funky dory - you lose 3rd party repos etc.
1. Do not go onto rabbit page and install Erlang there. Instead `apt install esl-erlang`
1. May as well finish installing Elixir from [here](https://elixir-lang.org/install.html)
1. Then install RabbitMQ-Server `apt install rabbitmq-server`
1. Follow instructions to setup the management ui plugin and start/enable the service.
1. You can now start the tutorials (and have a hope of success)

### HAHA I lied
(The tutorials will fail with the following error)

```
/deps/rabbit_common/.erlang.mk/hex/lager.tar: Cannot open: No such file or directory
```

### WTF is lager?

Lager is a logging framework for Erlang.
Add it as a dependency in you elixir project

``` elixir
  defp deps do
    [
      {:amqp, "~> 1.0"},
      {:lager, "~> 3.5"}
    ]
  end
```

### Now you can run stuff

``` bash
iex -S mix
```