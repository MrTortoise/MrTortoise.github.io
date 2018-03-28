---
layout: post
title:  "SVG + elm: Getting started: P2 Playing with SVG"
date:   2018-03-24 08:00:48 +0000
categories: svg tutorial drawing animation elm
---
# So Lets build some SVG stuff in elm

The goal here is to explore some ways of doing graphics in elm, html, css and - by proxy -  javascript. I know things can be rendered using divs, absolute layout and some animation libraries. What I don't like doing is taking on lots of dependencies (so I use a language framework in js ... yeah i know ...) and because if I did that i'd just use React. This is also a good opportunity to really understand the alternatives before I go back into vue / react and start playing with some mobile native coding.

## Goal

1. Be able to render the board for a game and the pieces
1. Figure out how to put text where I want to, spaced and sized appropriately
1. Keep all the code as clean as I can
1. Explore animation
1. Figure out how to do animation on demand
1. Investigate whether I need an event loop or can rely on user input to trigger everything

## Caveat

There are quite a few goals there. This might need to be split into multiple posts.

## First a basic elm page to frame all this

```elm
import Html exposing (Html, program)
import Svg exposing (..)
import Svg.Attributes exposing(..)


main : Program Never Model Msg
main =
    Html.program
        { init = init
        , view = view
        , update = update
        , subscriptions = subscriptions
    }

type alias Model =
    {     }

type Msg
    = Msg1

update : Msg -> Model -> (Model, Cmd Msg)
update msg model =
  case msg of
    Msg1 ->
      (model, Cmd.none)

view : Model -> Html Msg
view model =
  svg
  [ ]
  [
  ]

subscriptions : Model -> Sub Msg
subscriptions model =
    Sub.none

init : (Model, Cmd Msg)
init =
    (Model , Cmd.none)
```

From here we can populate the Svg element in the view and see what we can do.

So some observations

## The Svg viewport seems to be flexible

- can use negative origin and oversize the boundary. This enables you to introduce a border.
- by using width and height attributes the viewport can be scaled relative to the window.
- combining the above enables a resizable space with a well defined resolution.

```elm
  svg  [ viewBox "-10 -10 110 110", width "100%", height "100%"]
```

## So time to play with rectangles

```elm
  rect [x "0", y "0", width "100", height "100", stroke "black", strokeWidth "0.1", fill "none" ][],
  rect [x "0", y "0", width "25", height "25", fill "#edaabc"][]
```

- positions a rectangle at 0,0 which is 10,10 relative to the viewport. I love that
- the size of the rectangle is 100 x 100
- really complex ...
- you can also fill the rectangles
- what doesn't work so well is nesting SVG objects. They need to appear in sequence

## So what about text

### elm has 2 text SVG elements

- text: which turns out to print out a literal string
- text_: this is the actual svg element that you can read about on tinterweb

```elm
Svg.text_ [x "1", y "22", textLength "23", preserveAspectRatio "xMaxyMax meet", lengthAdjust "spacingAndGlyphs", fontSize "30"][Svg.text "256"]
```

- because you cannot nest elements x and y need to be set carefully. These values take into account padding.
- the lengthAdjust setting stretches the text horizontally to fit the text length. This particular setting keeps it more in shape and space.
- fontsize in this scenario mainly defines the height of the text. Note however the height of the rectangle it appears in is 25 yet this is 30 and it still has padding space. I need to figure out how to sort that out later.

## Cool resource

I found this whilst writing this post. It is a very good read. Was hoping for insight into animation sadly it doesn't help with that

[SVGPocketGuide](http://svgpocketguide.com/book/)

## Animation

I have no had much success with this yet. However this is what I came up with. Pursuing this is probably going to require yet-another-dependency.

```elm
rect [x "0", y "0", width "25", height "25", fill "#edaabc"]
      [
        animateTransform [ attributeType "XML", type_ "translate", attributeName "transform", from "0 0", to "0 50", dur "1s", repeatCount "1"][]
      ]
```