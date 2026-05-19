# Orion Library (Better Edition)
This documentation is for the enhanced version of Orion Library with additional features like MultiDropdown, Custom Themes, and improved UI.

## Booting the Library
```lua
local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/Scripter-Coder/Scripter-Coder/refs/heads/main/Universal/Orion%20Hub%20Library"))()
```



## Creating a Window
```lua
local Window = OrionLib:MakeWindow({
    Name = "Title of the library",
    HidePremium = false,
    SaveConfig = true,
    ConfigFolder = "OrionTest",
    IntroEnabled = true,
    IntroText = "Orion Library",
    IntroIcon = "rbxassetid://8834748103",
    Icon = "rbxassetid://8834748103",
    Version = "1.0.0",
    CloseCallback = function()
        print("Window closed")
    end
})

--[[
Name = <string> - The name of the UI.
HidePremium = <bool> - Whether or not the user details shows Premium status or not.
SaveConfig = <bool> - Toggles the config saving in the UI.
ConfigFolder = <string> - The name of the folder where the configs are saved.
IntroEnabled = <bool> - Whether or not to show the intro animation.
IntroText = <string> - Text to show in the intro animation.
IntroIcon = <string> - URL to the image you want to use in the intro animation.
Icon = <string> - URL to the image you want displayed on the window.
Version = <string> - Version text displayed at bottom of window.
CloseCallback = <function> - Function to execute when the window is closed.
]]
```



## Creating a Tab
```lua
local Tab = Window:MakeTab({
    Name = "Tab 1",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab (supports Feather Icons names like "home", "settings", etc.).
PremiumOnly = <bool> - Makes the tab accessible to Premium users only.
]]
```
## Creating a Section
```lua
local Section = Tab:AddSection({
    Name = "Section Name"
})

--[[
Name = <string> - The name of the section.
]]
```
You can add elements to sections the same way you would add them to a tab normally.

## Notifying the user
```lua
OrionLib:MakeNotification({
    Name = "Title!",
    Content = "Notification content... what will it say??",
    Image = "rbxassetid://4483345998",
    Time = 5
})

--[[
Name = <string> - The title of the notification.
Content = <string> - The content of the notification.
Image = <string> - The icon of the notification.
Time = <number> - The duration of the notification in seconds.
]]
```



## Creating a Button
```lua
local MyButton = Tab:AddButton({
    Name = "Button!",
    Callback = function()
        print("button pressed")
    end
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
```

### Changing the text name of an existing Button
```lua
MyButton:Set("New Button Text")
```


## Creating a Checkbox toggle
```lua
local MyToggle = Tab:AddToggle({
    Name = "This is a toggle!",
    Default = false,
    Callback = function(Value)
        print("Toggle is now:", Value)
    end,
    Flag = "toggleFlag",
    Save = true
})

--[[
Name = <string> - The name of the toggle.
Default = <bool> - The default value of the toggle.
Callback = <function> - The function of the toggle.
Flag = <string> - ID for config saving.
Save = <bool> - Whether to save this toggle in config.
]]
```

### Changing the value of an existing Toggle
```lua
MyToggle:Set(true)
```



## Creating a Color Picker
```lua
local ColorPicker = Tab:AddColorpicker({
    Name = "Colorpicker",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(Value)
        print("Color selected:", Value)
    end,
    Flag = "colorFlag",
    Save = true
})

--[[
Name = <string> - The name of the colorpicker.
Default = <color3> - The default value of the colorpicker.
Callback = <function> - The function of the colorpicker.
Flag = <string> - ID for config saving.
Save = <bool> - Whether to save this colorpicker in config.
]]
```

### Setting the color picker's value
```lua
ColorPicker:Set(Color3.fromRGB(255, 255, 255))
```


## Creating a Slider
```lua
local MySlider = Tab:AddSlider({
    Name = "Slider",
    Min = 0,
    Max = 20,
    Default = 5,
    Color = Color3.fromRGB(255, 255, 255),
    Increment = 1,
    ValueName = "bananas",
    Callback = function(Value)
        print("Slider value:", Value)
    end,
    Flag = "sliderFlag",
    Save = true
})

--[[
Name = <string> - The name of the slider.
Min = <number> - The minimum value of the slider.
Max = <number> - The maximum value of the slider.
Increment = <number> - How much the slider will change when dragging.
Default = <number> - The default value of the slider.
ValueName = <string> - The text after the value number.
Callback = <function> - The function of the slider.
Flag = <string> - ID for config saving.
Save = <bool> - Whether to save this slider in config.
]]
```

### Change Slider Value
```lua
MySlider:Set(10)
```
Make sure you make your slider a variable (local CoolSlider = Tab:AddSlider...) for this to work.


## Creating a Label
```lua
local MyLabel = Tab:AddLabel("Label Text")
```

### Changing the value of an existing label
```lua
MyLabel:Set("New Label Text!")
```


## Creating a Paragraph
```lua
local MyParagraph = Tab:AddParagraph("Title", "Content text here...")
```

### Changing an existing paragraph
```lua
MyParagraph:Set("New Title", "New content text!")
```


## Creating an Adaptive Input
```lua
local MyTextbox = Tab:AddTextbox({
    Name = "Textbox",
    Default = "default box input",
    TextDisappear = true,
    Callback = function(Value)
        print("User entered:", Value)
    end
})

--[[
Name = <string> - The name of the textbox.
Default = <string> - The default value of the textbox.
TextDisappear = <bool> - Clears text after losing focus.
Callback = <function> - The function of the textbox.
]]
```

### Changing an existing paragraph
```lua
local currentValue = MyTextbox:Get()
MyTextbox:Set("new value")
```


## Creating a Keybind
```lua
local MyBind = Tab:AddBind({
    Name = "Bind",
    Default = Enum.KeyCode.E,
    Hold = false,
    Callback = function()
        print("Key pressed!")
    end,
    Flag = "bindFlag",
    Save = true
})

--[[
Name = <string> - The name of the bind.
Default = <keycode> - The default key for the bind.
Hold = <bool> - If true, callback returns true while holding key.
Callback = <function> - The function of the bind.
Flag = <string> - ID for config saving.
Save = <bool> - Whether to save this bind in config.
]]
```

### Chaning the value of a bind
```lua
MyBind:Set(Enum.KeyCode.R)
```


## Creating a Dropdown menu
```lua
local MyDropdown = Tab:AddDropdown({
    Name = "Dropdown",
    Default = "1",
    Options = {"1", "2", "3"},
    Callback = function(Value)
        print("Selected:", Value)
    end,
    Flag = "dropdownFlag",
    Save = true
})

--[[
Name = <string> - The name of the dropdown.
Default = <string> - The default selected option.
Options = <table> - The options in the dropdown.
Callback = <function> - The function of the dropdown.
Flag = <string> - ID for config saving.
Save = <bool> - Whether to save this dropdown in config.
]]
```

### Adding a set of new Dropdown buttons to an existing menu
```lua
MyDropdown:Refresh({"New", "Options", "Here"}, true)
```

The above boolean value "true" is whether or not the current buttons will be deleted.
### Selecting a dropdown option
```lua
MyDropdown:Set("New")
```


## Creating a Multi Dropdown menu
```lua
local MyMultiDropdown = Tab:AddMultiDropdown({
    Name = "MultiDropdown",
    Options = {"ESP", "Aimbot", "Fly", "Speed", "Jump"},
    Default = {"ESP", "Speed"},  -- Pre-selected options
    Callback = function(Values)
        print("Selected options:", table.concat(Values, ", "))
    end,
    Flag = "multiFlag",
    Save = true
})

--[[
Name = <string> - The name of the multidropdown.
Options = <table> - The options available.
Default = <table> - The default selected options (array of strings).
Callback = <function> - Called when selection changes, passes table of selected values.
Flag = <string> - ID for config saving.
Save = <bool> - Whether to save in config.
]]
```

### Adding a set of new Multi Dropdown buttons to an existing menu
```lua
MyMultiDropdown:Refresh({"New", "Options"}, true)
```

The above boolean value "true" is whether or not the current buttons will be deleted.
### Selecting a multi dropdown option
```lua
MyMultiDropdown:Set({"ESP", "Fly"})
```

### Get current selected values from Multi Dropdown
```lua
print("Currently selected:", table.concat(MyMultiDropdown.Values, ", "))
```


## Creating a Theme Dropdown menu
```lua
local ThemeSelector = Tab:AddThemeDropdown({
    Name = "UI Theme"
})

--[[
This automatically adds:
1. A dropdown with all built-in themes (Red, Blue, Black, etc.)
2. A transparency slider for the UI
]]

-- Built-in theme options: "Red", "Orange", "Yellow", "Green", "Cyan", "Blue", "Purple", "Pink", "Brown", "Gray", "Black", "White"
```


### How flags work.
The flags feature in the ui may be confusing for some people. It serves the purpose of being the ID of an element in the config file, and makes accessing the value of an element anywhere in the code possible.
Below in an example of using flags.
```lua
Tab1:AddToggle({
    Name = "Toggle",
    Default = true,
    Save = true,
    Flag = "toggle"
})

print(OrionLib.Flags["toggle"].Value) -- prints the value of the toggle.
```
Flags only work with the toggle, slider, dropdown, bind, and colorpicker.

### Making your interface work with configs.
In order to make your interface use the configs function you first need to add the `SaveConfig` and `ConfigFolder` arguments to your window function. The explanation of these arguments in above.
Then you need to add the `Flag` and `Save` values to every toggle, slider, dropdown, bind, and colorpicker you want to include in the config file.
The `Flag = <string>` argument is the ID of an element in the config file.
The `Save = <bool>` argument includes the element in the config file.
Config files are made for every game the library is launched in.

## Destroying the Interface
```lua
OrionLib:Destroy()
```

## 3 Things Not Added Yet Are
```lua
Custom Animation Gui (When Script Loads)
Icon of face is white (Where The White Circle Is)
User is a fallback of your name incase if this code cant get your username properly it refers as User/Anonymous (Simple but its bug)
```

# Finishing your script (REQUIRED)
The below function needs to be added at the end of your code.
```lua

OrionLib:Init()
```
