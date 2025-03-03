

```
ctrBottomContent
    x:0
    y:lblFullQuestionText.Height + fxConstants.Controls.Margin
    width: Parent.TemplateWidth - Self.X * 2
    height: ctrToAnswer.Height  + fxConstants.Controls.Margin * 4

ctrToAnswer
    x:fxConstants.Containers.PaddingMd
    y:lblFullQuestionText.Height  
    padding: 10
    Height: fxConstants.Controls.InputHeight + fxConstants.Controls.LabelHeight + fxConstants.Controls.Margin * 2
    Width: galQuestions01.TemplateWidth - Self.X * 5



- ctrTemplateAnswerContainer:
    Control: GroupContainer
    Variant: AutoLayout
    Properties:
      LayoutDirection: =LayoutDirection.Vertical

- txtTemplateAnswer_Entry:
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

- ctrAnswerSingleLineOfText:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      DropShadow: =DropShadow.None
      Height: =fxConstants.Controls.InputHeight + fxConstants.Controls.LabelHeight
      LayoutAlignItems: =LayoutAlignItems.Stretch
      LayoutDirection: =LayoutDirection.Vertical
      Visible: =true // galQuestions_2.Selected.AnswerTypeID = 1
      X: =40
      Y: =40
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
            BorderRadius: =fxConstants.Controls.BorderRadius
            Fill: =Color.White
            FontColor: =fxTheme.Colors.FontColor
            Height: =fxConstants.Controls.InputHeight
            OnChange: =fxQuestionAnswered(galQuestions_2.Selected.ID, Self.Value)
            Placeholder: =galQuestions_2.Selected.HintText
            Value: =//If(locNewRecord, "", Gallery1_5.Selected.SampleHeading)


```