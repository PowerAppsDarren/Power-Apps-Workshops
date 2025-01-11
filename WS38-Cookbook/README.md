# WS38-Cookbook

This repository contains the code for the WS38 Cookbook project.

- [Suggested Topics](https://www.skool.com/power-apps-community/workshop-today-is-on-cookbook-items-bring-your-topic)
- [Skool WS38](https://www.skool.com/power-platform-workshops/classroom/c5600251?md=172ca8d19c9b4ae5b8a6466b30a76d3e)

## Accessing and this GitHub Repo 

- This repository is public and can be accessed by anyone: 
    - [Power-Apps-Workshops](https://github.com/PowerAppsDarren/Power-Apps-Workshops)

- **Q: How do we update the files in VS Code, once we downloaded Git Desktop?**
    - Forks
    - Branches in Git 
    - Pull request 

## Configuring Complex Menus

- How to manipulate the menu  
- Different ways utilize the menu based on all the rich properties in the menu items collection

### Sample Menu Items

```PowerFx
//
// This is the collection used for any of the the menus used
//
fxMenuItems = Sort(
    AddColumns(
        [
            {
                AsciiIcon: "🏠", 
                ScreenToGoTo: 'Home Screen',
                MenuText: Substitute(
                    Upper('Home Screen'.Name), 
                    " SCREEN", 
                    ""
                ),
                ParentScreenName: "",
                ImageOrIcon: "Icon",
                MenuImage: SampleImage,
                MenuIcon: Icon.Home,
                ShowForThisRole: "User;",
                Visible: true,
                LaunchLink: false,
                LaunchURL: "", 
                SortOrder: 1
            },
            {
                AsciiIcon: "🎯", 
                ScreenToGoTo: 'TMPL - MAIN SCREEN',
                MenuText: Substitute(
                    Upper('TMPL - MAIN SCREEN'.Name), 
                    " SCREEN", 
                    ""
                ),
                ParentScreenName: "",
                ImageOrIcon: "Icon",
                MenuImage: SampleImage,
                MenuIcon: Icon.Airplane,
                ShowForThisRole: "User;",
                Visible: true,
                LaunchLink: false,
                LaunchURL: "", 
                SortOrder: 2
            },
            {
                AsciiIcon: "⭐", 
                ScreenToGoTo: 'Another Screen',
                MenuText: Substitute(
                    Upper('Another Screen'.Name), 
                    " SCREEN", 
                    ""
                ),
                ParentScreenName: "",
                ImageOrIcon: "Icon",
                MenuImage: SampleImage,
                MenuIcon: Icon.Bookmark,
                ShowForThisRole: "User;",
                Visible: true,
                LaunchLink: false,
                LaunchURL: "", 
                SortOrder: 3
            }
        ], 
        MenuTextWithEmoji, 
        AsciiIcon & " " & MenuText
    ), 
    SortOrder
);
```

## Installing & Configuring an on premise data gateway


### If you don't already have an on-premise data gateway installed

- [Download the appropriate SQL Server version](https://www.microsoft.com/en-us/sql-server/sql-server-downloads?msockid=037561927e376fdc2f14749b7f2d6eee)
    - [Express Version of MSSQL](https://go.microsoft.com/fwlink/p/?linkid=2216019&clcid=0x409&culture=en-us&country=us)


- [[https://www.lipsum.com/]]
- https://www.youtube.com/playlist?list=PLMgWds5p226lrfjfOczlHR2kX0VPq2HWx 