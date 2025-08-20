# 🌙 DarkLib V5 Documentation

> A powerful and elegant Roblox UI library for creating beautiful interfaces

---

## 📚 Table of Contents

- [Getting Started](#-getting-started)
- [Creating Your First Window](#-creating-your-first-window)
- [User Interface Components](#-user-interface-components)
  - [Tabs](#tabs)
  - [Sections](#sections)
  - [Labels & Text](#labels--text)
  - [Interactive Elements](#interactive-elements)
- [Advanced Features](#-advanced-features)
- [API Reference](#-api-reference)

---

## 🚀 Getting Started

To begin using DarkLib V5, you need to load the library using the following loadstring:

```luau
local DarkLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/Darkmoonxhubscript/DarkLibV5/refs/heads/main/source.lua", true))()
```

---

## 🖼️ Creating Your First Window

### Basic Window Setup

```luau
local Window = DarkLib:CreateWindow({
    Name = "Your Hub Name ",
    Subtitle = "Your subtitle here",
    LogoID = "10734897102",
    Size = UDim2.new(0.95, 0, 0.8, 0),
    LoadingEnabled = true,
    LoadingTitle = "DarkMoon X",
    LoadingSubtitle = "Loading...",
    
    ConfigSettings = {
        RootFolder = nil,
        ConfigFolder = "ScriptFolderName"
    },
    
    KeySystem = false,
    KeySettings = {
        Title = "Hub Name",
        Subtitle = "Key System",
        Note = "Enter the Key Obtained for the Hub Name",
        SaveInRoot = false,
        SaveKey = true,
        Key = {"YourKey"}, -- Add your key here
        SecondAction = {
            Enabled = false,
            Type = "Discord",
            Parameter = "YourDiscordInvite"
        }
    }
})
```

### Window Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `Name` | string | The title of your UI window |
| `Subtitle` | string | Subtitle text displayed below the title |
| `LogoID` | string | Roblox asset ID for the logo |
| `Size` | UDim2 | Window size (recommended: `UDim2.new(0.95, 0, 0.8, 0)`) |
| `LoadingEnabled` | boolean | Enable/disable loading screen |
| `LoadingTitle` | string | Title shown during loading |
| `LoadingSubtitle` | string | Subtitle shown during loading |
| `ConfigSettings` | table | Configuration folder settings |
| `KeySystem` | boolean | Enable/disable key system authentication |
| `KeySettings` | table | Key system configuration options |

---

## 🔔 Creating Notifications

Display beautiful notifications to your users:

```luau
local Notify = NewNotify({
    Title = "Success!",
    Description = "Operation completed successfully.",
    Time = 5
})
```

| Parameter | Type | Description |
|-----------|------|-------------|
| `Title` | string | Notification title |
| `Description` | string | Notification message |
| `Time` | number | Display duration in seconds |

---

## 🗂️ User Interface Components

### Tabs

Create organized sections for your interface:

```luau
local MainTab = Window:CreateTab({
    Name = "Main",
    Icon = "home", --Custom Use Only ID, don't put "rbxassetid://"
    ImageSource = "Material", -- "Material" or "Custom"
    ShowTitle = true
})
```

### Sections

Organize content within tabs:

```luau
MainTab:CreateSection("Player Options")
```

### Labels & Text

#### Simple Labels

```luau
MainTab:CreateLabel({
    Text = "Welcome to DarkLib V6!",
    Style = 1 -- 1: message, 2: success, 3: warning/error
})
```

#### Rich Paragraphs

```luau
MainTab:CreateParagraph({
    Title = "About This Script",
    Text = "This is a comprehensive script hub with various features and tools."
})
```

---

## ⚡ Interactive Elements

### Buttons

```luau
local ExampleButton = MainTab:CreateButton({
    Name = "Execute Function",
    Description = "Runs the main function",
    Callback = function()
        print("Button clicked!")
        -- Your code here
    end
})
```

### Toggles

```luau
local ExampleToggle = MainTab:CreateToggle({
    Name = "Auto Farm",
    Description = "Automatically farms resources",
    CurrentValue = false,
    Callback = function(Value)
        print("Toggle state:", Value)
        -- Your toggle logic here
    end
}, "AutoFarmFlag")
```

### Text Input

```luau
local TextInput = MainTab:CreateInput({
    Name = "Player Name",
    Description = "Enter target player name",
    PlaceholderText = "Username...",
    CurrentValue = "",
    Numeric = false,
    MaxCharacters = 20,
    Enter = true, -- Require Enter key to submit
    Callback = function(Text)
        print("Input received:", Text)
        -- Handle input
    end
}, "PlayerNameFlag")
```

### Sliders

```luau
local SpeedSlider = MainTab:CreateSlider({
    Name = "Walk Speed",
    Range = {16, 100},
    Increment = 1,
    CurrentValue = 16,
    Callback = function(Value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
    end
}, "WalkSpeedFlag")
```

### Dropdowns

```luau
local WeaponDropdown = MainTab:CreateDropdown({
    Name = "Select Weapon",
    Description = "Choose your preferred weapon",
    Options = {"Sword", "Bow", "Staff", "Dagger"},
    CurrentOption = {"Sword"},
    MultipleOptions = false,
    Callback = function(Option)
        print("Selected weapon:", Option)
        -- Handle selection
    end
}, "WeaponFlag")
```

---

## 🎨 Advanced Features

### Settings Tab with Themes

```luau
local SettingsTab = Window:CreateTab({
    Name = "Settings",
    Icon = "settings",
    ImageSource = "Material",
    ShowTitle = true
})

-- Add configuration section
SettingsTab:BuildConfigSection()

-- Add theme customization
SettingsTab:BuildThemeSection()
```

### Home Tab

```luau
Window:CreateHomeTab({
    SupportedExecutors = {"Synapse X", "Script-Ware", "Krnl", "Delta"},
    DiscordInvite = "yourinvitecode", --[[Don't include discord.gg/]]
    Icon = 1
})
```

---

## 📖 API Reference

### Core Functions

| Function | Parameters | Description |
|----------|------------|-------------|
| `DarkLib:CreateWindow()` | Table of window settings | Creates the main window |
| `NewNotify()` | Title, Description, Time | Creates a notification |
| `Window:CreateTab()` | Tab configuration | Creates a new tab |
| `Tab:CreateSection()` | Section name | Creates a section divider |

### Component Functions

| Function | Purpose | Returns |
|----------|---------|---------|
| `CreateButton()` | Interactive button | Button object |
| `CreateToggle()` | On/off switch | Toggle object |
| `CreateInput()` | Text input field | Input object |
| `CreateSlider()` | Numeric slider | Slider object |
| `CreateDropdown()` | Selection menu | Dropdown object |
| `CreateLabel()` | Display text | Label object |
| `CreateParagraph()` | Rich text block | Paragraph object |

---

## 🎯 Best Practices

### Naming Conventions
- Use descriptive names for tabs and components
- Keep titles concise but informative
- Add descriptions to clarify functionality

### Organization
- Group related functions in the same tab
- Use sections to separate different feature categories
- Place important functions in easily accessible locations

### User Experience
- Provide clear feedback for user actions
- Use appropriate icons for tabs
- Set reasonable default values for sliders and inputs

---

## 💡 Tips & Tricks

**Performance**: Store frequently accessed elements in variables to avoid repeated lookups.

**Flags**: Use meaningful flag names for saving/loading configurations.

**Validation**: Always validate user input, especially for numeric fields.

**Error Handling**: Wrap callbacks in pcall() for better error management.

---

## 🔗 Resources

- **GitHub Repository**: [DarkLib V5](https://github.com/Darkmoonxhubscript/DarkLibV5)
- **Discord Server**: Join for support and updates
- **Documentation Updates**: Check the repository for the latest features

---

*Made with ❤️ by the Darki & Luna Softwares team*
