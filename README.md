--[[
    ════════════════════════════════════════════════════════════════
        SwatUI - Roblox UI Library
    ════════════════════════════════════════════════════════════════

    STRUCTURE:

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

    HOW TO USE:

    1. Load the library:
        local SwatUI = loadstring(game:HttpGet("URL"))()

    2. Create the window:
        local Window = SwatUI:CreateWindow("My Menu")

    3. Create a tab:
        local Tab = Window:CreateTab("Name", "home")

    4. Add elements inside the tab (examples below)

    ════════════════════════════════════════════════════════════════
        AVAILABLE ELEMENTS
    ════════════════════════════════════════════════════════════════

    ▸ CreateSection(title)
    ▸ CreateLabel(text)
    ▸ CreateButton(cfg)
    ▸ CreateToggle(cfg)
    ▸ CreateSlider(cfg)
    ▸ CreateDropdown(cfg)
    ▸ CreateTextBox(cfg)
    ▸ CreateKeybind(cfg)
    ▸ CreateColorPicker(cfg)
    ▸ Window:Notify(cfg)
]]

local SwatUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/SEU_USUARIO/swatui/main/src/SwatUI.lua"))()

local Window = SwatUI:CreateWindow("All Elements")
local lp = game.Players.LocalPlayer

-- ============================================================
-- TABS
-- ============================================================
local MainTab   = Window:CreateTab("Main", "home")
local ButtonTab = Window:CreateTab("Button", "circle-play")
local ToggleTab = Window:CreateTab("Toggle", "check")
local SliderTab = Window:CreateTab("Slider", "activity")
local DropTab   = Window:CreateTab("Dropdown", "list")
local TextTab   = Window:CreateTab("TextBox", "file")
local KeyTab    = Window:CreateTab("Keybind", "key")
local ColorTab  = Window:CreateTab("ColorPicker", "palette")

-- ============================================================
-- MAIN TAB
-- ============================================================
MainTab:CreateSection("General")

MainTab:CreateLabel("Label example")

MainTab:CreateButton({
    Title = "Reset",
    Callback = function()
        if lp.Character then lp.Character:BreakJoints() end
    end,
})

MainTab:CreateButton({
    Title = "Rejoin",
    Callback = function()
        game:GetService("TeleportService"):Teleport(game.PlaceId)
    end,
})

-- ============================================================
-- BUTTON TAB
-- ============================================================
ButtonTab:CreateSection("Buttons")

ButtonTab:CreateButton({
    Title = "Button 1",
    Callback = function() print("Button 1") end,
})

ButtonTab:CreateButton({
    Title = "Button 2",
    Callback = function() print("Button 2") end,
})

ButtonTab:CreateButton({
    Title = "Button 3",
    Callback = function() print("Button 3") end,
})

-- ============================================================
-- TOGGLE TAB
-- ============================================================
ToggleTab:CreateSection("Toggles")

ToggleTab:CreateToggle({
    Title = "Toggle 1",
    Default = false,
    Callback = function(s) print("Toggle 1:", s) end,
})

ToggleTab:CreateToggle({
    Title = "Toggle 2",
    Default = true,
    Callback = function(s) print("Toggle 2:", s) end,
})

ToggleTab:CreateToggle({
    Title = "Toggle 3",
    Default = false,
    Callback = function(s) print("Toggle 3:", s) end,
})

-- ============================================================
-- SLIDER TAB
-- ============================================================
SliderTab:CreateSection("Sliders")

SliderTab:CreateSlider({
    Title = "Slider 1",
    Min = 0, Max = 100, Default = 50,
    Callback = function(v) print("Slider 1:", v) end,
})

SliderTab:CreateSlider({
    Title = "Slider 2",
    Min = 16, Max = 500, Default = 16,
    Callback = function(v) print("Slider 2:", v) end,
})

SliderTab:CreateSlider({
    Title = "Slider 3",
    Min = -100, Max = 100, Default = 0,
    Callback = function(v) print("Slider 3:", v) end,
})

-- ============================================================
-- DROPDOWN TAB
-- ============================================================
DropTab:CreateSection("Dropdowns")

DropTab:CreateDropdown({
    Title = "Dropdown 1",
    Options = {"Normal", "Fast", "Turbo"},
    Default = "Normal",
    Callback = function(s) print("Dropdown 1:", s) end,
})

DropTab:CreateDropdown({
    Title = "Dropdown 2",
    Options = {"Red", "Green", "Blue", "Yellow"},
    Default = "Red",
    Callback = function(s) print("Dropdown 2:", s) end,
})

DropTab:CreateDropdown({
    Title = "Dropdown 3",
    Options = {"Very Slow", "Slow", "Normal", "Fast", "Very Fast", "Instant"},
    Default = "Normal",
    Callback = function(s) print("Dropdown 3:", s) end,
})

-- ============================================================
-- TEXTBOX TAB
-- ============================================================
TextTab:CreateSection("TextBoxes")

TextTab:CreateTextBox({
    Title = "Name",
    Placeholder = "Type your name...",
    Default = "",
    Callback = function(t) print("Name:", t) end,
})

TextTab:CreateTextBox({
    Title = "Message",
    Placeholder = "Type a message...",
    Default = "",
    Callback = function(t) print("Message:", t) end,
})

-- ============================================================
-- KEYBIND TAB
-- ============================================================
KeyTab:CreateSection("Keybinds")

KeyTab:CreateKeybind({
    Title = "Key 1",
    Default = "K",
    Callback = function(k) print("Key 1:", k) end,
})

KeyTab:CreateKeybind({
    Title = "Key 2",
    Default = "E",
    Callback = function(k) print("Key 2:", k) end,
})

KeyTab:CreateKeybind({
    Title = "Key 3",
    Default = "F",
    Callback = function(k) print("Key 3:", k) end,
})

-- ============================================================
-- COLOR PICKER TAB
-- ============================================================
ColorTab:CreateSection("Color Pickers")

ColorTab:CreateColorPicker({
    Title = "Color 1",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(c) print("Color 1:", c) end,
})

ColorTab:CreateColorPicker({
    Title = "Color 2",
    Default = Color3.fromRGB(0, 255, 0),
    Callback = function(c) print("Color 2:", c) end,
})

ColorTab:CreateColorPicker({
    Title = "Color 3",
    Default = Color3.fromRGB(0, 0, 255),
    Callback = function(c) print("Color 3:", c) end,
})

-- ============================================================
-- NOTIFY
-- ============================================================
Window:Notify({
    Title = "Script",
    Description = "Loaded!",
    Duration = 3,
    Type = "success",
})
