# Notes on converting to Html from Graphics Element

## Using a Spacer
```
spacer : Int -> Int -> Html
spacer w h =
  Html.div [ width w, height h ] []
```


## Creating a Title

### Graphics Element And Text
```
import Text exposing (style)

headerStyle : Style
headerStyle = { defaultStyle | height <- Just 50 }

titleFromString : String -> Element
titleFromString string = leftAligned
  (Text.fromString string
    |> style headerStyle)
```

### Html
```
import Html.Attributes exposing (style)

titleSize : String
titleSize = "50px"

titleFromString : String -> Html
titleFromString string = 
  Html.div [ style [( "font-size", titleSize )] ] [Html.text string]
```

## Clickable

```
someElement
|> clickable (Signal.message someMailbox.address CustomAction),
```

Changed to
```
Html.div [ onClick someMailbox.address CustomAction ] [ someElementAsHtml ]
```

