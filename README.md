The Swatui UI system is there, how to code it; this system is easy to implement.  
Warning
swatui qualquer bugs encontrado é só falar no server do Discord
• https://discord.gg/G8J3k2nB34


não Copy esse code ele não vai funcionar 

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
/
    ## HOW TO USE


    1. Load the library:
        local SwatUI = loadstring(game:HttpGet("https://gist.githubusercontent.com/swat07script77/7fbf1e4f7e502565a34396878f9a1dbb/raw/e61324627588f43c647fb838bf2bef2bbe65c1e7/Swatui%2520V2"))()

    2. Create the window:
        local Window = SwatUI:CreateWindow("My Menu")

    3. Create a tab:
        local Tab = Window:CreateTab("Name", "home")
/
    4. Add elements inside the tab
/
    ## AVAILABLE ELEMENTS

    ### SECTION

        Tab:CreateSection("Title")

    ### LABEL

        Tab:CreateLabel("Text")

    ### BUTTON

        Tab:CreateButton({
            Title = "Name",
            Callback = function()
                print("clicked")
            end,
        })

    ### TOGGLE

        Tab:CreateToggle({
            Title = "Name",
            Default = false,
            Callback = function(state)
                print(state)
            end,
        })

    ### SLIDER

        Tab:CreateSlider({
            Title = "Name",
            Min = 0,
            Max = 100,
            Default = 50,
            Callback = function(value)
                print(value)
            end,
        })

    ### DROPDOWN

        Tab:CreateDropdown({
            Title = "Name",
            Options = {"A", "B", "C"},
            Default = "A",
            Callback = function(selected)
                print(selected)
            end,
        })

    ### TEXTBOX

        Tab:CreateTextBox({
            Title = "Name",
            Placeholder = "Type here...",
            Default = "",
            Callback = function(text)
                print(text)
            end,
        })

    ### KEYBIND

        Tab:CreateKeybind({
            Title = "Name",
            Default = "K",
            Callback = function(key)
                print(key)
            end,
        })

    ### COLOR PICKER

        Tab:CreateColorPicker({
            Title = "Name",
            Default = Color3.fromRGB(255, 0, 0),
            Callback = function(color)
                print(color)
            end,
        })

    ### NOTIFY

        Window:Notify({
            Title = "Title",
            Description = "Description",
            Duration = 3,
            Type = "info",
        })

        Type: "info" | "success" | "warning" | "error"


    Callback = function(s) print("Toggle 3:", s) end,

