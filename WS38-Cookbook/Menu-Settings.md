


```
    Properties:
      BackgroundColor: =Color.White
      BorderColor: =ColorValue("#cccccc")
      BorderStyle: =BorderStyle.Solid
      BorderThickness: =0
      CollapsedWidth: |-
        =compMainScreen_FlyOutMenu_2.MenuItemSize 
        + compMainScreen_FlyOutMenu_2.MenuItemPadding * 2
        + compMainScreen_FlyOutMenu_2.MenuPadding * 2
      ExpandedWidth: |-
        =If(   
            compMainScreen_FlyOutMenu_2.IsLandscapeOriented,    
            350,  
            App.DesignWidth
        )
      Font: =App.Theme.Font
      FontSize: =15
      ForegroundColor: =App.Theme.Colors.Primary
      HighlightColor: =Color.LightYellow
      IconPadding: =10
      IsLandscapeOriented: =App.ActiveScreen.Orientation = "horizontal"
      MenuDropShadow: =Text(DropShadow.Light)
      MenuItemDropShadow: =Text(DropShadow.None)
      MenuItemPadding: =6
      MenuItemRoundedCornerRadius: =0
      MenuItemSize: =50
      MenuItems: =fxMenuItems
      MenuPadding: =1
      MenuRoundedCornerRadius: =5
      ScreenTransition: =ScreenTransition.Fade
      SelectedBarColor: =App.Theme.Colors.Primary
      SelectorBarHeight: =compMainScreen_FlyOutMenu_2.MenuItemSize
      SelectorBarWidth: =2
      SelectorBarX: =compMainScreen_FlyOutMenu_2.MenuItemRoundedCornerRadius
      SelectorBarY: =compMainScreen_FlyOutMenu_2.MenuItemRoundedCornerRadius
      ShowDebuggingInfo: =false
      ShowEmojiInMenuText: =true
      Fill: =compMainScreen_FlyOutMenu_2.BackgroundColor
      Height: =Parent.Height - Self.Y
      Width: |-
        =If(
            compMainScreen_FlyOutMenu_2.IsExpanded,  
            compMainScreen_FlyOutMenu_2.ExpandedWidth,
            compMainScreen_FlyOutMenu_2.CollapsedWidth
        )
```