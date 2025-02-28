


```
- ctrAnswerSingleLineOfText:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      DropShadow: =DropShadow.None
      FillPortions: =0
      Height: =fxConstants.Controls.InputHeight + fxConstants.Controls.LabelHeight
      LayoutAlignItems: =LayoutAlignItems.Stretch
      LayoutDirection: =LayoutDirection.Vertical
      Visible: =galQuestions_2.Selected.AnswerTypeID = 1
    Children:
      - lblLineOfTextLabel:
          Control: Text@0.0.50
          Properties:
            FontColor: =fxTheme.Colors.Dark
            Height: =fxConstants.Controls.LabelHeight
            PaddingBottom: =2
            PaddingLeft: =2
            Text: ="Answer"
            VerticalAlign: =VerticalAlign.Bottom
      - txtLineOfText_Entry:
          Control: TextInput@0.0.53
          Properties:
            Appearance: ='TextInputCanvas.Appearance'.Outline
            BorderColor: =fxTheme.Colors.ControlOutline
            Fill: =Color.White
            FontColor: =fxTheme.Colors.FontColor
            Height: =fxConstants.Controls.InputHeight
            OnChange: =fxQuestionAnswered(galQuestions_2.Selected.ID, Self.Value)
            Placeholder: =galQuestions_2.Selected.HintText
            Value: =//If(locNewRecord, "", Gallery1_5.Selected.SampleHeading)
```
