---
layout: post
title:  "Elm: User Input Part 3 - some movement"
date:   2018-03-20 20:40:48 +0000
categories: elm tutorial keyboard
---
# Following on from part 1+2

Before we caught keyboard input, then we found which key was being pressed.

So lets turn that into some kind of manipulation of a vector.
The goal is to increment and decrement x,y values and display them in the view on update.

## Changes to Model

```elm
type alias Model =
    { pressedKeys : Set KeyCode
    , x : Int
    , y : Int
    }
```

## Changes to View

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
            text keyString, text (toString model.x), text (toString model.y)
          ]
```

## Changes to update

This is the fun part. I am not sure i have done this in a very efficient way. But was fun to write.

```elm
handleKeyChange : Bool -> KeyCode -> Model -> Model
handleKeyChange pressed keyCode model =
  let
    fn = if pressed then Set.insert else Set.remove
    pressedKeys = fn keyCode model.pressedKeys
    (x, y) = parseDirection pressedKeys model
  in
    { model | pressedKeys = pressedKeys, x = x, y = y }

parseDirection : Set KeyCode -> Model -> (Int, Int)
parseDirection keyCodes model =
  let
    left = Set.member 37 model.pressedKeys
    up = Set.member  38 model.pressedKeys
    right = Set.member 39 model.pressedKeys
    down = Set.member 40 model.pressedKeys
  in
    (model.x, model.y)
    |> handleUp  up
    |> handleDown down
    |> handleLeft left
    |> handleRight right


handleUp:Bool -> (Int, Int) ->  (Int, Int)
handleUp  apply (x,y)=
  case apply of
    True -> (x,y+1)
    False -> (x,y)

handleDown: Bool ->  (Int, Int) -> (Int, Int)
handleDown apply (x,y)  =
  case apply of
    True -> (x,y-1)
    False -> (x,y)

handleLeft:  Bool ->(Int, Int) -> (Int, Int)
handleLeft apply (x,y)  =
  case apply of
    True -> (x-1,y)
    False -> (x,y)

handleRight: Bool ->(Int, Int) ->  (Int, Int)
handleRight apply (x,y)  =
  case apply of
    True -> (x+1,y)
    False -> (x,y)
```
