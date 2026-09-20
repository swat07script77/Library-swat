# SwatUI

> ⚠️ **WARNING:** Any bugs found — just report them on the Discord server.
> 🔗 https://discord.gg/G8J3k2nB34

---

**SwatUI** is a lightweight UI system — here's how to code with it. This system is easy to implement.

---

## 📁 Project Structure

> **Do not copy this code — it will not work.**

```
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

## 🚀 How to Use

**1. Load the library:**

```lua
local SwatUI = loadstring(game:HttpGet("https://gist.githubusercontent.com/swat07script77/7fbf1e4f7e502565a34396878f9a1dbb/raw/e61324627588f43c647fb838bf2bef2bbe65c1e7/Swatui%2520V2"))()
```

**2. Create the window:**

```lua
local Window = SwatUI:CreateWindow("My Menu")
```

**3. Create a tab:**

```lua
local Tab = Window:CreateTab("Name", "home")
```

**4. Add elements inside the tab.**

---

## 🧩 Available Elements

### Section

```lua
Tab:CreateSection("Title")
```

### Label

```lua
Tab:CreateLabel("Text")
```

### Button

```lua
Tab:CreateButton({
    Title = "Name",
    Callback = function()
        print("clicked")
    end,
})
```

### Toggle

```lua
Tab:CreateToggle({
    Title = "Name",
    Default = false,
    Callback = function(state)
        print(state)
    end,
})
```

### Slider

```lua
Tab:CreateSlider({
    Title = "Name",
    Min = 0,
    Max = 100,
    Default = 50,
    Callback = function(value)
        print(value)
    end,
})
```

### Dropdown

```lua
Tab:CreateDropdown({
    Title = "Name",
    Options = {"A", "B", "C"},
    Default = "A",
    Callback = function(selected)
        print(selected)
    end,
})
```

### Textbox

```lua
Tab:CreateTextBox({
    Title = "Name",
    Placeholder = "Type here...",
    Default = "",
    Callback = function(text)
        print(text)
    end,
})
```

### Keybind

```lua
Tab:CreateKeybind({
    Title = "Name",
    Default = "K",
    Callback = function(key)
        print(key)
    end,
})
```

### Color Picker

```lua
Tab:CreateColorPicker({
    Title = "Name",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(color)
        print(color)
    end,
})
```

### Notify

```lua
Window:Notify({
    Title = "Title",
    Description = "Description",
    Duration = 3,
    Type = "info",
})
```

**Available types:** `"info"` · `"success"` · `"warning"` · `"error"`

---

## 📄 License

See the [LICENSE](LICENSE) file for details.
