---
layout: post
title:  "Elm: User Input Part 2 - what key?"
date:   2018-03-21 20:40:48 +0000
categories: elm tutorial keyboard
---
# Following on from part 1

So we can detect keyboard events.
> Yay

now we want to:

1. to hook into some specific keys.
2. represent those keys in a way that doesn't involve horrible magic numbers

So hit the googles and find:
[Elm Character](http://package.elm-lang.org/packages/elm-lang/core/latest/Char#fromCode)

So now if we write something that can get to the char codes we should be able to translate them? Right?

So some elm ...
Lets update the view to show us some info.
Check out the horrible signature on `Set.foldr`
`(comparable -> b -> b) -> b -> Set.Set comparable -> b`

It means a function that takes a comparable function that takes 2 things of the same type (I think it operates in an order - because its a set order is undefined so you have to give it one), a thing, a set of the comparable things and then returns a thing.

```elm
view : Model -> Html Msg
view model =
  let
      keyString =
        Set.map toString model.pressedKeys
        |> Set.foldr String.append ""
  in
      div []
          [
            text keyString
          ]
```

Now we can see the character codes.
Lets convert them to something human readable.

```elm
import Char exposing(fromCode)
.
.
.
view : Model -> Html Msg
view model =
  let
      keyString =
        Set.map fromCode model.pressedKeys
        |> Set.map toString
        |> Set.foldr String.append ""
  in
      div []
          [
            text keyString
          ]
```

so its a bit messed up, but its a start.