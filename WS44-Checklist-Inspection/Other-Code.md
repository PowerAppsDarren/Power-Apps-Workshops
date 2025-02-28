# Other Code   

```yaml
- drpSingleChoice:
    Control: DropDown@0.0.44
    Properties:
      Appearance: ='DropdownCanvas.Appearance'.Outline
      Items: = galQuestions.Selected.Choices
      OnChange: =fxQuestionAnswered(galQuestions.Selected.ID, Self.Selected.Value)




- ctrToAnswer:
    Control: GroupContainer@1.3.0
    Variant: AutoLayout
    Properties:
      BorderColor: =If(ThisItem.IsSelected, App.Theme.Colors.Darker20, Color.Transparent)
      BorderStyle: =BorderStyle.Dotted
      BorderThickness: =1
      DropShadow: =If(ThisItem.IsSelected, DropShadow.Regular, DropShadow.None)
      Fill: '=If(ThisItem.IsSelected, fxTheme.Colors.LightGray, Color.Transparent)   '
      Height: =fxConstants.Control.Height * 2
      LayoutAlignItems: =LayoutAlignItems.Stretch
      LayoutDirection: =LayoutDirection.Vertical
      Visible: =galQuestions_2.Selected.AnswerTypeID = 7
      Width: =galQuestions01.TemplateWidth - Self.X * 2
      X: =fxConstants.Container.PaddingMd
      Y: =lblFullQuestionText.Height
    Children:
      - lblAnswerLabel:
          Control: Text@0.0.50
          Properties:
            FontColor: =fxTheme.Colors.Dark
            PaddingBottom: =2
            PaddingLeft: =2
            Text: ="Answer"
            VerticalAlign: =VerticalAlign.Bottom
      - drpAnswerSingleChoice:
          Control: DropDown@0.0.44
          Properties:
            Appearance: ='DropdownCanvas.Appearance'.Outline
            Items: = galQuestions_2.Selected.Choices
            OnChange: =fxQuestionAnswered(galQuestions_2.Selected.ID, Self.Selected.Value)
```