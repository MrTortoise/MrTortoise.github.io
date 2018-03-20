---
layout: post
title:  "Elm: Enjoying it this time: User Input Part 1"
date:   2018-03-20 20:40:48 +0000
categories: elm tutorial
---
# Lets spike some user input in Elm

So came back to Elm. Enjoying it, something clicked. Probably the moment i started writing currying functions in c#.

For those not in the know. c# doesn't support currying, i ended up returning  lambdas that closed over the parameters of the function called CreateSomeFunction. It felt really broken ...

So too the hint, clearly a good time to go back to something functional and so back to Elm. Once again playing with the kool aid kids.

So Started to write a game (because a game is always a really smooth learning curve for a new language - I also suck at web dev ...)

So this will be fun.

## Lets set up the project

{% highlight bash %}
git init
{% endhighlight %}

Then head over to github and grab an elm .gitignore file

Next install the base elm package
{% highlight bash %}
elm package install
{% endhighlight %}

Then update the sources folder

{% highlight JavaScript %}
{
  "source-directories": [
        "./src"
    ],
}
{% endhighlight %}
