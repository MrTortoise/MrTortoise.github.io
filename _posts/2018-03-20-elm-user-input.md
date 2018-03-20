---
layout: post
title:  "Elm: User Input Part 1"
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

```bash
git init
```

Then head over to github and grab an elm .gitignore file

Next install the base elm package

```bash
elm package install
```

Then update the sources folder

```json
{
  "source-directories": [
        "./src"
    ],
}
```

Now we are going to need a keyboard library. If you google 'elm language' you will end up at [this](http://package.elm-lang.org/packages/elm-lang/keyboard/latest) page. Install it like this:

```bash
elm-package install elm-lang/keyboard
```

## The code

Below is a big blurt of code:

### Highlights

- import Set: Need a de duplicated non ordered collection of keys
- Subscription: This is what kicked my ass. A subscription is of type `Sub Msg` yet we need to sign up to both key up and key down events turns out you can create a batch.

The code for this is: (and no i dont have the foggiest how it works)

```elm
{-| When you need to subscribe to multiple things, you can create a `batch` of
subscriptions.
**Note:** `Sub.none` and `Sub.batch [ Sub.none, Sub.none ]` and
`Sub.batch []` all do the same thing.
-}
batch : List (Sub msg) -> Sub msg
batch =
Elm.Kernel.Platform.batch
```

The code for handling user input is below. Put it in `./src/` and `elm-reactor`

```elm
import Html exposing (..)
import Keyboard exposing (KeyCode)
import Set exposing (..)

main : Program Never Model Msg
main =
    Html.program
        { init = init
        , view = view
        , update = update
        , subscriptions = subscriptions
    }

type alias Model =
    { pressedKeys : Set KeyCode
    }

type Msg
    = KeyChange Bool KeyCode

update : Msg -> Model -> (Model, Cmd Msg)
update msg model =
    case msg of
        KeyChange pressed keyCode  ->
            (handleKeyChange pressed keyCode model, Cmd.none)

handleKeyChange : Bool -> KeyCode -> Model -> Model
handleKeyChange pressed keyCode model =
  let
    fn = if pressed then Set.insert else Set.remove
    pressedKeys = fn keyCode model.pressedKeys
  in
    { model | pressedKeys = pressedKeys }


view : Model -> Html Msg
view model =
    div []
        [ (Set.isEmpty model.pressedKeys)
          |> toString
          |> text
        ]

init : (Model, Cmd Msg)
init =
    (Model Set.empty  , Cmd.none)

subscriptions : Model -> Sub Msg
subscriptions model =
    let
        keys = [ Keyboard.downs (KeyChange True)
               , Keyboard.ups (KeyChange False)
               ]
    in
    keys |> Sub.batch
```