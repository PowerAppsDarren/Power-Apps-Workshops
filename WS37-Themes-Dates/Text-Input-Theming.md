# Text-Input-Theming

I recommend that you paste this into a blank screen and then copy the JSON from the screen to your app.

```PowerFx
- txtCodeEditor:
    Control: Classic/TextInput
    Properties:
      Default: =JSON(App.Theme, JSONFormat.IndentFour)
      Clear: =true
      DisabledBorderColor: =Self.Fill
      Font: =Font.'Courier New'
      Height: =Parent.Height - Self.Y * 2
      HoverFill: =Self.Fill
      LineHeight: =1.4
      Mode: =TextMode.MultiLine
      PaddingBottom: =10
      PaddingLeft: =10
      PaddingRight: =10
      PaddingTop: =10
      Size: =18
      Width: =Parent.Width - Self.X * 2
      X: =20
      Y: =20
```