swatui/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── .gitignore
├── src/
│   ├── init.lua
│   └── SwatUI.lua
├── examples/
│   ├── basic.lua
│   ├── script.lua
│   └── full_menu.lua
└── docs/
    ├── API.md
    ├── THEMES.md
    └── ICONS.md
    |
    |
_______
local Unload = {}
Unload.__index = Unload

local TrackedInstances = {}
local TrackedConnections = {}
local TrackedThreads = {}
local OriginalProperties = {}

function Unload.TrackInstance(inst)
    if inst and typeof(inst) == "Instance" then
        table.insert(TrackedInstances, inst)
    end
    return inst
end

function Unload.TrackConnection(conn)
    if conn then
        table.insert(TrackedConnections, conn)
    end
    return conn
end

function Unload.TrackThread(thread)
    if thread then
        table.insert(TrackedThreads, thread)
    end
    return thread
end

function Unload.SaveProperty(inst, prop, value)
    if not OriginalProperties[inst] then
        OriginalProperties[inst] = {}
    end
    OriginalProperties[inst][prop] = value
end

function Unload.All()
    local success, err = pcall(function()
        for _, thread in ipairs(TrackedThreads) do
            pcall(function()
                if thread and coroutine.status(thread) ~= "dead" then
                    task.cancel(thread)
                end
            end)
        end
        TrackedThreads = {}

        for _, conn in ipairs(TrackedConnections) do
            pcall(function()
                if conn and typeof(conn) == "RBXScriptConnection" then
                    conn:Disconnect()
                end
            end)
        end
        TrackedConnections = {}

        for _, inst in ipairs(TrackedInstances) do
            pcall(function()
                if inst and inst.Parent then
                    inst:Destroy()
                end
            end)
        end
        TrackedInstances = {}

        for inst, props in pairs(OriginalProperties) do
            pcall(function()
                if inst and inst.Parent then
                    for prop, value in pairs(props) do
                        inst[prop] = value
                    end
                end
            end)
        end
        OriginalProperties = {}

        local playerGui = game:GetService("Players").LocalPlayer:FindFirstChild("PlayerGui")
        if playerGui then
            for _, gui in ipairs(playerGui:GetChildren()) do
                if gui:IsA("ScreenGui") and (gui.Name == "SwatUI" or gui.Name == "SwatUI_Overlay") then
                    gui:Destroy()
                end
            end
        end

        local coreGui = game:GetService("CoreGui")
        if coreGui then
            pcall(function()
                for _, gui in ipairs(coreGui:GetChildren()) do
                    if gui:IsA("ScreenGui") and (gui.Name == "SwatUI" or gui.Name == "SwatUI_Overlay") then
                        gui:Destroy()
                    end
                end
            end)
        end

        pcall(function()
            local renderSettings = settings():GetService("RenderSettings")
            if renderSettings then
                renderSettings.ShowBoundingBoxes = false
            end
        end)

        if getgenv then
            pcall(function()
                local env = getgenv()
                env.SwatUI = nil
                env.SwatUILoaded = nil
                env.SwatUIWindow = nil
            end)
        end
        _G.SwatUI = nil
        _G.SwatUILoaded = nil
        _G.SwatUIWindow = nil
    end)

    if not success then
        warn("[SwatUI Unload] Erro: " .. tostring(err))
        return false
    end

    print("[SwatUI Unload] OK")
    return true
end

function Unload.Execute()
    return Unload.All()
end

if _G.SwatUIUnload then
    pcall(_G.SwatUIUnload)
end
_G.SwatUIUnload = Unload.All

return Unload
