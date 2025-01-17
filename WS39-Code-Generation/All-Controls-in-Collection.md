# All-Controls-in-Collection

>**AI Prompt**: I am creating a canvas power apps YAML code generator. Please give me the code to create a collection that i can define in App.Formulas that will contain every single control available now (both modern and classic). Add fields in this collection that would be useful for a code generator such as if they are modern or classic, horizontal or vertical (in the case of responsive containers)

>**Perplexity Answer**: Certainly! I'll create a collection that contains all the available controls in Power Apps, including both modern and classic controls. This collection will be useful for your YAML code generator. Here's the Power Fx code to create the collection:

```PowerFx
ClearCollect(
    colControls,
    [
        {
            ControlName: "Button",
            IsModern: true,
            Category: "Input",
            SupportsItems: false,
            DefaultSize: {Width: 160, Height: 40}
        },
        {
            ControlName: "Checkbox",
            IsModern: true,
            Category: "Input",
            SupportsItems: false,
            DefaultSize: {Width: 160, Height: 40}
        },
        {
            ControlName: "Combobox",
            IsModern: true,
            Category: "Input",
            SupportsItems: true,
            DefaultSize: {Width: 280, Height: 40}
        },
        {
            ControlName: "DatePicker",
            IsModern: true,
            Category: "Input",
            SupportsItems: false,
            DefaultSize: {Width: 280, Height: 40}
        },
        {
            ControlName: "Dropdown",
            IsModern: true,
            Category: "Input",
            SupportsItems: true,
            DefaultSize: {Width: 280, Height: 40}
        },
        {
            ControlName: "NumberInput",
            IsModern: true,
            Category: "Input",
            SupportsItems: false,
            DefaultSize: {Width: 280, Height: 40}
        },
        {
            ControlName: "RadioGroup",
            IsModern: true,
            Category: "Input",
            SupportsItems: true,
            DefaultSize: {Width: 300, Height: 160}
        },
        {
            ControlName: "Slider",
            IsModern: true,
            Category: "Input",
            SupportsItems: false,
            DefaultSize: {Width: 300, Height: 40}
        },
        {
            ControlName: "TextInput",
            IsModern: true,
            Category: "Input",
            SupportsItems: false,
            DefaultSize: {Width: 280, Height: 40}
        },
        {
            ControlName: "Toggle",
            IsModern: true,
            Category: "Input",
            SupportsItems: false,
            DefaultSize: {Width: 44, Height: 24}
        },
        {
            ControlName: "Avatar",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 40, Height: 40}
        },
        {
            ControlName: "Badge",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 40, Height: 20}
        },
        {
            ControlName: "Header",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 1366, Height: 80}
        },
        {
            ControlName: "InfoButton",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 32, Height: 32}
        },
        {
            ControlName: "Link",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 100, Height: 40}
        },
        {
            ControlName: "ProgressBar",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 300, Height: 16}
        },
        {
            ControlName: "Spinner",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 40, Height: 40}
        },
        {
            ControlName: "Stream",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 640, Height: 360}
        },
        {
            ControlName: "Table",
            IsModern: true,
            Category: "Data",
            SupportsItems: true,
            DefaultSize: {Width: 600, Height: 400}
        },
        {
            ControlName: "Tabs",
            IsModern: true,
            Category: "Navigation",
            SupportsItems: true,
            DefaultSize: {Width: 600, Height: 400}
        },
        {
            ControlName: "Text",
            IsModern: true,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 100, Height: 40}
        },
        {
            ControlName: "CopilotAnswer",
            IsModern: true,
            Category: "AI",
            SupportsItems: false,
            DefaultSize: {Width: 400, Height: 300}
        },
        {
            ControlName: "Label",
            IsModern: false,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 100, Height: 40}
        },
        {
            ControlName: "Image",
            IsModern: false,
            Category: "Display",
            SupportsItems: false,
            DefaultSize: {Width: 200, Height: 200}
        },
        {
            ControlName: "Gallery",
            IsModern: false,
            Category: "Data",
            SupportsItems: true,
            DefaultSize: {Width: 320, Height: 480}
        },
        {
            ControlName: "Form",
            IsModern: false,
            Category: "Data",
            SupportsItems: true,
            DefaultSize: {Width: 400, Height: 600}
        },
        {
            ControlName: "Timer",
            IsModern: false,
            Category: "System",
            SupportsItems: false,
            DefaultSize: {Width: 40, Height: 40}
        },
        {
            ControlName: "HorizontalContainer",
            IsModern: false,
            Category: "Layout",
            SupportsItems: true,
            DefaultSize: {Width: 600, Height: 400},
            Orientation: "Horizontal"
        },
        {
            ControlName: "VerticalContainer",
            IsModern: false,
            Category: "Layout",
            SupportsItems: true,
            DefaultSize: {Width: 400, Height: 600},
            Orientation: "Vertical"
        }
    ]
);
```

This collection, named `colControls`, includes both modern and classic controls available in Power Apps. Each item in the collection has the following properties:

- **ControlName**: The name of the control as used in Power Apps.
- **IsModern**: A boolean indicating whether the control is a modern (true) or classic (false) control.
- **Category**: The category of the control (e.g., Input, Display, Data, Navigation, etc.).
- **SupportsItems**: A boolean indicating whether the control supports items/data input.
- **DefaultSize**: An object containing the default width and height of the control.
- **Orientation**: (Only for container controls) Specifies if the container is horizontal or vertical.

You can use this collection in your YAML code generator to iterate through all available controls and generate the appropriate YAML code based on their properties. The collection includes information that will be useful for generating code, such as whether the control is modern or classic, its category, and whether it supports items.

To use this collection in your app, you can add it to the App.OnStart property or call it from a button or other event as needed for your code generator.

Citations:
[1] https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/controls/modern-controls/modern-controls-reference
[2] https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/controls/modern-controls/overview-modern-controls