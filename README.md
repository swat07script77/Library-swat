<!--<h1 align="center">SwatUI</h1> -->

<div align="center">

<picture>
  <source srcset="https://img.shields.io/badge/SwatUI-V2.0-ff0000?style=for-the-badge&logo=roblox&logoColor=white" media="(prefers-color-scheme: dark)">
  <img src="https://img.shields.io/badge/SwatUI-V2.0-ff0000?style=for-the-badge&logo=roblox&logoColor=white" alt="SwatUI Banner">
</picture>

[![SwatUI Status](https://img.shields.io/badge/Status-Active-ff3333?style=for-the-badge)](https://discord.gg/G8J3k2nB34)
[![Language](https://img.shields.io/badge/Language-Lua-ff6666?style=for-the-badge&logo=lua&logoColor=white)](https://luau.org)

<p align="center">
  <b>An easy-to-implement, lightweight, and modern UI library for Roblox script developers.</b>
</p>

</div>

> [!WARNING]
> **Beta Notice:** SwatUI is currently in active development. Bugs and unstable features may occur. Please report any issues on our Discord server.

> [!WARNING]
> **Important:** Do not copy or execute the file structure tree code below in your script execution environment—it is provided for reference only and will throw an error.

---

# Links

- [Discord Server](https://discord.gg/G8J3k2nB34)
- [Example Script](https://gist.githubusercontent.com/swat07script77/7fbf1e4f7e502565a34396878f9a1dbb/raw/e61324627588f43c647fb838bf2bef2bbe65c1e7/Swatui%2520V2)

---

# Project Structure

```text
swatui/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── .gitignore
├── src/
│   ├── init.lua
│   ├── SwatUI.lua
│   └── Unload.lua
├── examples/
│   ├── basic.lua
│   ├── script.lua
│   └── full_menu.lua
└── docs/
    ├── API.md
    ├── THEMES.md
    └── ICONS.md
```

---

# How to Use

**1. Load the library:**

```lua
local SwatUI = loadstring(game:HttpGet("https://gist.githubusercontent.com/swat07script77/7fbf1e4f7e502565a34396878f9a1dbb/raw/e61324627588f43c647fb838bf2bef2bbe65c1e7/Swatui%2520V2"))()
```

**2. Create the main window:**

```lua
local Window = SwatUI:CreateWindow("My Menu")
```

**3. Create the main tab:**

```lua
local Tab = Window:CreateTab("Home", "home")
```

**4. Add elements inside the tab.**

---

# Available Elements

### Section

```lua
Tab:CreateSection("Example Section")
```

### Label

```lua
Tab:CreateLabel("This is an example label")
```

### Button

```lua
Tab:CreateButton({
    Title = "Example Button",
    Callback = function()
        print("Button clicked!")
    end,
})
```

### Toggle

```lua
Tab:CreateToggle({
    Title = "Enable Feature",
    Default = false,
    Callback = function(state)
        print("Toggle state:", state)
    end,
})
```

### Slider

```lua
Tab:CreateSlider({
    Title = "Adjust Value",
    Min = 0,
    Max = 100,
    Default = 50,
    Callback = function(value)
        print("Slider value:", value)
    end,
})
```

### Dropdown

```lua
Tab:CreateDropdown({
    Title = "Select Option",
    Options = {"Option A", "Option B", "Option C"},
    Default = "Option A",
    Callback = function(selected)
        print("Selected option:", selected)
    end,
})
```

### Textbox

```lua
Tab:CreateTextBox({
    Title = "Text Field",
    Placeholder = "Type here...",
    Default = "",
    Callback = function(text)
        print("Typed text:", text)
    end,
})
```

### Keybind

```lua
Tab:CreateKeybind({
    Title = "Hotkey",
    Default = "K",
    Callback = function(key)
        print("Key pressed:", key)
    end,
})
```

### Color Picker

```lua
Tab:CreateColorPicker({
    Title = "Color Picker",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(color)
        print("Selected color:", color)
    end,
})
```

### Notify

```lua
Window:Notify({
    Title = "Notification",
    Description = "Menu loaded successfully!",
    Duration = 3,
    Type = "info", -- Options: "info" | "success" | "warning" | "error"
})
```

**Available types:** `"info"` · `"success"` · `"warning"` · `"error"`
