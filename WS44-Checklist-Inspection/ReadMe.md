# Workshop 44 - Checklist Inspection

This is the readme for Workshop 45, Checklist Inspection.

Every readme file for each workshop should have the following sections:

-  [ ] **Description**: A brief description of the workshop.
    - This is a continuation of the Checklist Inspection series.
    - This is part 3 of this recent series.
    - For playlist/videos previous from this series, [please go here](https://www.youtube.com/playlist?list=PLMgWds5p226khtGqT_GLO5kYRwFw66RAZ).
-  [ ] **Objectives**: The objectives of the workshop.
-  [ ] **Prerequisites**: The prerequisites for the workshop.
-  [ ] **Lab**: The lab instructions for the workshop.
-  [ ] **Summary**: A summary of the workshop.
-  [ ] **Additional Resources**: Links to additional resources.





    // ========================================================================
    //
    // App.Formulas - Move as much code from App.OnStart 
    //
    // ========================================================================

    fxUglyMode = true;
    fxFontTextColor = App.Theme.Colors.Darker20;
    fxFontSize = fxConstants.Controls.InputFontSize;

    /* ========================================================================
    
        STEP 1️⃣    Add your email address (and any other developer's emails
                    separated by semi-colins ";") into this constant. 
    
       ===================================================================== */ 

    fxDeveloperEmails = If(
        fxIsStudioMode And
        User().Email = fxDarrenEmail,   // I need to default this to me because 
        fxDarrenEmail & ";",            // I'll be in here editing this MSAPP.                                        
        fxDeveloperEmail                
    );
    //
    // Put all the dev emails in here separated by semi-colons
    //
    fxDeveloperEmail = User().Email & ";";    // "YOUR_EMAIL_ADDRESS_HERE"         // ⬅️ CHANGE ⬅️ CHANGE 🚨🚨🚨
    //
    // Related, of course. Feel free to remove this, but I need it in here
    // to develop With. - Darren
    //
    fxDarrenEmail = "darren@doaccelerator.com"; 




    /*
        ✅ Basic User (technicican)(Performs inspections)
        ✅ Manager (Approve Work or Requests)
        ✅ App Admin (application administrators)
        ✅ App Tester (experiencing bugs or problems)
        ✅ App Developer (you, the owner/creator of the app, but also those who you have set up as a co-owner)

        Keys never change
    */
    fxAppRoles = [
        {
            ID: 1,
            SortOrder: 1,
            Key: "TECHNICIAN-USER",
            VisibleOnlyToAdmins: false,
            Name: "Technician", 
            Description: "Performs inspections"
        },
        {
            ID: 2,
            SortOrder: 2,
            Key: "MANAGER-USER",
            VisibleOnlyToAdmins: false,
            Name: "Manager", 
            Description: "Review Inspections"
        },
        {
            ID: 3,
            SortOrder: 3,
            VisibleOnlyToAdmins: true,
            Name: "App Admin", 
            Description: "Performs inspections"
        },
        {
            ID: 4,
            SortOrder: 4,
            VisibleOnlyToAdmins: true,
            Name: "App Tester", 
            Description: "Experiencing bugs or problems, or helps test and troubleshoot"
        },
        {
            ID: 5,
            SortOrder: 5,
            VisibleOnlyToAdmins: true,
            Name: "App Developer", 
            Description: "Creates the App"
        }
    ];

    //
    // This boolean named formula tells us if we are 
    // in Power Apps Studio as the app maker. 
    // It will return false if it is merely "played".
    //
    fxIsStudioMode = StartsWith(Host.Version, "PowerApps-Studio");

    fxControlTypeChoices = ["Defer to App", "Modern", "Classic"];

    fxControlTypeEnum = {
        DefertoApp: "Defer to App", 
        Modern: "Modern", 
        Classic: "Classic"
    };

    //
    // Here are values we'll set here once and 
    // reference them throughout the application. 
    //
    fxConstants = {
        App: {
            //
            Name: "Ultimate JumpStart Kit LITE", 
            //
            StartScreen: 'Home Screen', 
            //
            Version: "2025.02.22", 
            //
            DefaultScreenTransition: ScreenTransition.Fade, 
            //
            ControlTypeDefault:         fxControlTypeEnum.Modern,   // DO NOT USE: "Defer to App"
                                                    // We need to not defer to anything here, unless it is from a DB
            ControlTypeDefaultChoices:  fxControlTypeChoices
        },
        //
        // Screen Defaults
        //
        Screen: {
            Fill: Color.White,
            ShowFullNavAt: 3, 
            ScreenTransition: ScreenTransition.Fade,
            Padding: 20
        },
        Colors: {
            LightGray:              ColorValue("#e5e5e5"),
            ReallyLightGray:        ColorValue("#f5f5f5"),
            LightGrayHex:           "#e5e5e5",
            MediumGray:             ColorValue("#aaaaaa"),
            MediumGrayHex:          "#aaaaaa"
        },
        //
        // These will be applied to controls in general
        //
        Controls: {
            BorderRadius: 6,
            LabelHeight: 32, 
            InputHeight: 40,
            Margin: 10, 

            InputFontSize: 18, 
            LabelFontSize: 15
        },
        //
        // These will be container defaults
        //
        Containers: {
            GapSm: 8,
            GapMd: 16, 
            GapLg: 24, 
            GapXL: 32, 
            GapForLayout: 12,
            PaddingForLayout: 2,
            PaddingSm: 2,
            PaddingMd: 10,
            PaddingLg: 15,
            PaddingXL: 20,
            DropShadowDefault: DropShadow.Regular, 
            DropShadowForLayout: DropShadow.Light, 
            BorderRadiusNone: 0,
            BorderRadiusSm: 4,
            BorderRadiusMd: 8,
            BorderRadiusLg: 12, 
            HeadingHeight: 45,
            Margin: 20
        },
        //
        // These will be applied to labels in general
        //
        Label: {
            BorderRadius: 4,
            Height: 30
        }
    };

    //
    //
    //
    fxGetMenuItemText(ScreenName:Text):Text = (
        Proper(
            Trim(
                Substitute(
                    Upper(ScreenName), 
                    " SCREEN", 
                    ""
                )
            )
        )
    );

    //
    // Reference all menu items here 
    //
    fxMenuItems = (
        If(
            fxUglyMode, 
            [
                {
                    ScreenToGoTo: 'Home Screen',
                    SortOrder: 1, 
                    MenuText: fxGetMenuItemText('Home Screen'.Name),
                    ParentScreenName: "",
                    MenuImage: SampleImage,
                    MenuIcon: Icon.Redo,
                    ShowForThisRole: "User;",
                    Visible: true,
                    LaunchLink: false,
                    LaunchURL: ""
                }, 
                {
                    ScreenToGoTo: 'App Users Management Screen',
                    SortOrder: 2, 
                    MenuText: fxGetMenuItemText("App Users"),
                    ParentScreenName: "",
                    MenuImage: SampleImage,
                    MenuIcon: Icon.Redo,
                    ShowForThisRole: "User;",
                    Visible: true,
                    LaunchLink: false,
                    LaunchURL: ""
                }
                
                ,{
                    ScreenToGoTo: App.ActiveScreen,
                    SortOrder: 999999999999999999999999999, 
                    MenuText: "Back",
                    ParentScreenName: "",
                    MenuImage: SampleImage,
                    MenuIcon: Icon.BackArrow,
                    ShowForThisRole: "User;",
                    Visible: true,
                    LaunchLink: false,
                    LaunchURL: ""
                }
            ],    
            [            
                {
                    ScreenToGoTo: 'Loading Screen',
                    SortOrder: 1, 
                    MenuText: "Start Over",
                    ParentScreenName: "",
                    MenuImage: SampleImage,
                    MenuIcon: Icon.Redo,
                    ShowForThisRole: "User;",
                    Visible: true,
                    LaunchLink: false,
                    LaunchURL: ""
                }, 
                {
                    ScreenToGoTo: 'Questionnaire Screen',
                    SortOrder: 2, 
                    MenuText: Proper(Trim(
                        Substitute(
                            Upper('Questionnaire Screen'.Name), 
                            " SCREEN", 
                            ""
                        )
                    )),
                    ParentScreenName: "",
                    MenuImage: SampleImage,
                    MenuIcon: Icon.QuestionMark,
                    ShowForThisRole: "User;",
                    Visible: true,
                    LaunchLink: false,
                    LaunchURL: ""
                }
                /*
                    {
                        ScreenToGoTo: 'Home Screen',
                        SortOrder: 1, 
                        MenuText: Trim(
                            Substitute(
                                Upper('Home Screen'.Name), 
                                " SCREEN", 
                                ""
                            )
                        ),
                        ParentScreenName: "",
                        MenuImage: SampleImage,
                        MenuIcon: Icon.Home,
                        ShowForThisRole: "User;",
                        Visible: true,
                        LaunchLink: false,
                        LaunchURL: ""
                    },
                    {
                        ScreenToGoTo: 'Another Screen',
                        SortOrder: 2, 
                        MenuText: Trim(
                            Substitute(
                                Upper('Another Screen'.Name), 
                                " SCREEN", 
                                ""
                            )
                        ),
                        ParentScreenName: "",
                        MenuImage: SampleImage,
                        MenuIcon: Icon.DetailList,
                        ShowForThisRole: "User;",
                        Visible: true,
                        LaunchLink: false,
                        LaunchURL: ""
                    },
                    {
                        ScreenToGoTo: 'Calendar Screen',
                        SortOrder: 3, 
                        MenuText: Trim(
                            Substitute(
                                Upper('Calendar Screen'.Name), 
                                " SCREEN", 
                                ""
                            )
                        ),
                        ParentScreenName: "",
                        MenuImage: SampleImage,
                        MenuIcon: Icon.DetailList,
                        ShowForThisRole: "User;",
                        Visible: true,
                        LaunchLink: false,
                        LaunchURL: ""
                    }
                */

                ,{
                    ScreenToGoTo: App.ActiveScreen,
                    SortOrder: 999999999999999999999999999, 
                    MenuText: "Back",
                    ParentScreenName: "",
                    MenuImage: SampleImage,
                    MenuIcon: Icon.BackArrow,
                    ShowForThisRole: "User;",
                    Visible: true,
                    LaunchLink: false,
                    LaunchURL: ""
                }
            ]
        )
    );

    fxGetHexFromColor(ColorValue:Color):Text = Left(
        Substitute(
            JSON(ColorValue, JSONFormat.Compact), 
            """",
            ""
        ), 
        7
    );



    //
    // fxTheme
    //
    fxTheme = With( 
        {
            my_base_theme:          App.Theme
        },
        With( 
            {
                my_main_color_hex:      fxGetHexFromColor(my_base_theme.Colors.Primary)
            },
            {
                IsBaseThemeDynamic:     true,
                BaseTheme:              my_base_theme,
                BaseColors:             my_base_theme.Colors,
                Colors: {
                    Primary:            ColorValue(my_main_color_hex), 
                    PrimaryHex:         my_main_color_hex, 

                    Dark:               my_base_theme.Colors.Darker20,
                    Light:              my_base_theme.Colors.Lighter80, //fxTheme.BaseColors.Lighter70
                    Faint:              ColorFade(my_base_theme.Colors.Lighter80, 80%),
                    GallerySelected:    ColorFade(my_base_theme.Colors.Lighter80, 40%),
                    ControlOutline:     my_base_theme.Colors.Lighter70,

                    LightGray:          ColorValue("#f5f5f5"),
                    Background:         ColorValue("#fafafa"),

                    Text:               my_base_theme.Colors.PrimaryForeground, 
                    FontColor:          my_base_theme.Colors.Darker10 
                },
                Fonts: {
                    Heading:            Font.'Open Sans',
                    Body:               Font.'Open Sans',
                    Sizes: {
                        H1:             24,
                        H2:             20,
                        H3:             17,
                        Body:           14
                    }
                },
                Branding: {
                    Logo:               graPowerAutomateStroke,
                    CompanyName:        "Contoso Inc."
                }
            }
        )
    );

    fxSpacing = {
                    Padding:            8,
                    Margin:             12
                };

    fxGetColoredSVGNoEncode(SVGText:Text, ColorToReplace:Text, DesiredColor:Text):Text =  
        Substitute(
            SVGText, 
            $"{ColorToReplace}", 
            $"{DesiredColor}"
        );

    fxSVGEncode(svgCode:Text):Text = 
        "data:image/svg+xml; utf8, " & EncodeUrl(svgCode);

    fxSpinnerSimple = fxSVGEncode(
        fxGetColoredSVGNoEncode(
            "<svg xmlns=""http://www.w3.org/2000/svg"" viewBox=""0 0 100 100"" preserveAspectRatio=""xMidYMid"" width=""200"" height=""200"" style=""shape-rendering: auto; display: block; background: transparent;"" xmlns:xlink=""http://www.w3.org/1999/xlink""><g><path stroke=""none"" fill=""#000000"" d=""M10 50A40 40 0 0 0 90 50A40 43.5 0 0 1 10 50""><animateTransform values=""0 50 51.75;360 50 51.75"" keyTimes=""0;1"" repeatCount=""indefinite"" dur=""1.1764705882352942s"" type=""rotate"" attributeName=""transform""></animateTransform></path><g></g></g></svg>", 
            "#000000", 
            fxTheme.Colors.PrimaryHex
        )
    );

    fxSpinnerImage = imgSpinnerSVG.Image;


    fxGenerateTheme(HexCode:Text, FontName:Text, ThemeName:Text):fxThemeBaseType = (
        With( 
            {
                PrimaryColor:       ColorValue(HexCode), 
                MyFontName:         If(IsBlank(FontName), Font.'Segoe UI', FontName), 
                MyThemeName:        If(
                                        IsBlank(ThemeName), 
                                        "New Theme - " & Text(Now(), "yyyy-mm-dd-hh-mm-ss"), 
                                        ThemeName
                                    )
            },
            {
                Font: MyFontName, 
                Name: MyThemeName,
                Colors: {
                        Primary: PrimaryColor,  // Input primary color as hex "#742774"
                        // Darker shades - reduce brightness while maintaining hue/saturation
                        Darker10: ColorFade(PrimaryColor, -0.1),
                        Darker20: ColorFade(PrimaryColor, -0.2),
                        Darker30: ColorFade(PrimaryColor, -0.3),
                        Darker40: ColorFade(PrimaryColor, -0.4),
                        Darker50: ColorFade(PrimaryColor, -0.5),
                        Darker60: ColorFade(PrimaryColor, -0.6),
                        Darker70: ColorFade(PrimaryColor, -0.7),
                        // Lighter shades - increase brightness and reduce saturation
                        Lighter10: ColorFade(ColorFade(PrimaryColor, 0.1), 0.05),
                        Lighter20: ColorFade(ColorFade(PrimaryColor, 0.2), 0.1),
                        Lighter30: ColorFade(ColorFade(PrimaryColor, 0.3), 0.15),
                        Lighter40: ColorFade(ColorFade(PrimaryColor, 0.4), 0.2),
                        Lighter50: ColorFade(ColorFade(PrimaryColor, 0.5), 0.25),
                        Lighter60: ColorFade(ColorFade(PrimaryColor, 0.6), 0.3),
                        Lighter70: ColorFade(ColorFade(PrimaryColor, 0.7), 0.35),
                        Lighter80: ColorFade(ColorFade(PrimaryColor, 0.8), 0.4),
                        PrimaryForeground: RGBA(255, 255, 255, 1)
                }
            }
        )
    );


    //
    // This is the type that has been defined by Microsoft for modern theming
    // We'll include this type into the fxExtendedThemeType
    // See: https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/controls/modern-controls/modern-theming
    //
    fxThemeBaseType := Type(
        {
            Font:Text, 
            Name:Text,
            Colors:fxColorPaletteType
        }
    );
    

    fxColorPaletteType := Type(  
        {          
            Darker10:Color,
            Darker20:Color,
            Darker30:Color,
            Darker40:Color,
            Darker50:Color,
            Darker60:Color,
            Darker70:Color,
            Lighter10:Color,
            Lighter20:Color,
            Lighter30:Color,
            Lighter40:Color,
            Lighter50:Color,
            Lighter60:Color,
            Lighter70:Color,
            Lighter80:Color,
            Primary:Color,
            PrimaryForeground:Color
        }
    );




    // ==========================================================
    // ==========================================================
    // ==========================================================
    // ==========================================================
    // ==========================================================



    // ==========================================================
    //
    // Are is the data and functions needed for this particular app
    //
    // ==========================================================

    //
    // Eventually we will have this in a database table
    //
    fxQuestionsToAnswer = [
        {
            ID: 1, 
            Title: "User Role", 
            //
            // Refer to fxQuestionCategories for QuestionCategoryID
            //
            QuestionCategoryID: 1, 
            SortOrder: 1, 
            FullQuestionText: "What role will you be performing while using this application?", 
            //
            // Refer to fxAnswerTypes for AnswerTypeID
            //
            AnswerTypeID: 7,         
            HintText: "Technician", 
            Choices: Distinct(Filter(fxAppRoles, VisibleOnlyToAdmins = false), Name)
        },
        {
            ID: 2, 
            Title: "User's Manager", 
            //
            // Refer to fxQuestionCategories for QuestionCategoryID
            //
            QuestionCategoryID: 1, 
            SortOrder: 2, 
            FullQuestionText: "What is your manager's email address?", 
            //
            // Refer to fxAnswerTypes for AnswerTypeID
            //
            AnswerTypeID: 1,         
            HintText: "manager_name@" & Last(Split(User().Email, "@")).Value
        }
    ];

    fxQuestionCategories = [
        //
        // Ask what role
        //
        {
            ID: 1, 
            Title: "User Information", 
            SortOrder: 1,
            ParentCategoryID: Blank()
        },
        {
            ID: 2, 
            Title: "Customer Information", 
            SortOrder: 2,
            ParentCategoryID: Blank()
        },
        {
            ID: 3, 
            Title: "Vehicle Information", 
            SortOrder: 3,
            ParentCategoryID: Blank()
        }
    ];

    // ===================================================================================================
    //
    //  fxAnswerTypes
    //
    //      ID:                 Unique Identifier (Integer / Number)
    //      TypeName:           User-friendly name (Text / String) (yes, you're a user descripbed here)
    //                          that describes the value type
    //                              EXAMPLE:  "Single Line of Text"
    //                                        "Multiple Lines of Text"
    //                                        "Date/Time"
    //                          in SharePoint or Dataverse they are called that.
    //      TypeDescription:    Spells out what the TypeName really means. 
    //                              EXAMPLE: "String value of up to 255 characters"
    //      ControlType:        What Power Apps Studio calls the control that we need to use for 
    //                          an answer of this type.
    //                         
    // ===================================================================================================
    fxAnswerTypes = [
        {
            ID: 1,
            TypeName: "Single Line of Text", 
            TypeDescription: "String value of up to 255 characters", 
            GenericControlName: "Text input", 
            DefaultControlType: fxConstants.App.ControlTypeDefault,
            ControlType: "Text Input", 

            // Not sure if we want to keep this...
            Control: txtSingleLineOfText
        },
        {
            ID: 7,
            TypeName: "Choice (single answer)", 
            TypeDescription: "User selects 1 item from a listing of choices", 
            GenericControlName: "Dropdown", 
            DefaultControlType: fxConstants.App.ControlTypeDefault // Modern
        },
        {
            ID: 2,
            TypeName: "Multiple Lines of Text", 
            TypeDescription: "String value for data over 1 line (over 255 characters)"
        },
        {
            ID: 3,
            TypeName: "Date/Time", 
            TypeDescription: "A date and time"
        },
        {
            ID: 4,
            TypeName: "Whole Numbers", 
            TypeDescription: "Integer type of numbers"
        },
        {
            ID: 5,
            TypeName: "Decimals", 
            TypeDescription: "A number with decimal places"
        },
        {
            ID: 6,
            TypeName: "Boolean", 
            TypeDescription: "Yes/No, True/False"
        },
        {
            ID: 8,
            TypeName: "Choice (multi-choice)", 
            TypeDescription: "User selects 1 item from a dropdown", 
            ControlType: "Combobox"
        }
    ];

    fxAnswerTypesEnum = {

    };

    fxPowerAppsControlCategories = {
        Recommended:    "Recommended",
        Display:        "Display",
        Input:          "Input"
    };

    fxPowerAppsControlsDefinedEnum = {
        TextInput: LookUp(fxPowerAppsControlsDefined, GenericControlName = "Text Input"),        
        DropDown: LookUp(fxPowerAppsControlsDefined, GenericControlName = "DropDown")
    };

    fxPowerAppsControlsDefined = [
        {
            Category:               fxPowerAppsControlCategories.Input,
            GenericControlName:     "Dropdown",
            ModernControlType:      "DropDown", 
            ModernControlVersion:   "@0.0.44",
            ClassicControlVersion:  "@2.3.1",
            ClassicControlType:     "Classic/DropDown"
        },
        {
            Category:               fxPowerAppsControlCategories.Input,
            GenericControlName:     "Text Input",
            ModernControlType:      "TextInput", 
            ModernControlVersion:   "@0.0.53",
            ClassicControlVersion:  "@2.3.2",
            ClassicControlType:     "Classic/TextInput"
        }
    ];

    fxAnswer_Type:= Type(
        {                    
            QuestionID:Number,
            AnswerValue:Text
        }
    );

    fxAnswerTable_Type:= Type([fxAnswer_Type]);

    fxCreateAnswser(    QuestionIDValue:Number,
                        AnswerTextValue:Text):fxAnswer_Type = (
        {
            QuestionID: QuestionIDValue,
            AnswerValue: AnswerTextValue
        }
    );

    fxAllQuestionsAnswered = colAnswers;

    fxQuestionAnswered( QuestionIDValue:Number,
                        AnswerTextValue:Text):fxAnswer_Type = {
            With(
                {
                    myAnswer: fxCreateAnswser(
                        QuestionIDValue, 
                        AnswerTextValue        
                    )
                },
                Collect(
                    colAnswers,
                    myAnswer
                );
                myAnswer;
            )
    };


    fxSearchAppUser(SearchTerm:Text):AppUser = (
        Sort(
            Filter(
                AppUser, 
                StartsWith(FirstName, txtSearchAppUser.Value)
                Or 
                StartsWith(LastName, txtSearchAppUser.Value)
            ), 
            Title, 
            SortOrder.Ascending
        )
    );

    //
    // Get the X or the Y of a control in relation to
    // its parent dimension. 
    // 
    // Understanding the parameters: 
    //   - Pass in width values to get the X value for 'Self'
    //   - Pass in height values to get the Y value for 'Self'   
    //
    fxGetCenteredDimension( ParentDimension:Number, 
                            SelfDimension:Number):Number = (
        (ParentDimension - SelfDimension) / 2
    );

    // You could simply copy/paste this for X value for centered self
    // #️⃣ fxGetCenteredDimension(Parent.Width, Self.Width) 
    // You could simply copy/paste this for Y value for centered self
    // #️⃣ fxGetCenteredDimension(Parent.Height, Self.Height) 