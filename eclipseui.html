
-- EclipseUI v1.0
-- Reusable UI library for authorized Roblox projects

local EclipseUI = {}
EclipseUI.__index = EclipseUI

local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")

local PURPLE = Color3.fromRGB(145, 85, 255)
local BACKGROUND = Color3.fromRGB(19, 18, 27)
local PANEL = Color3.fromRGB(29, 27, 40)
local TEXT = Color3.fromRGB(245, 242, 255)
local MUTED = Color3.fromRGB(165, 159, 185)

local function create(className, properties, parent)
    local object = Instance.new(className)

    for key, value in pairs(properties or {}) do
        object[key] = value
    end

    object.Parent = parent
    return object
end

local function round(object, radius)
    create("UICorner", {
        CornerRadius = UDim.new(0, radius or 8)
    }, object)
end

local function stroke(object, color, transparency)
    create("UIStroke", {
        Color = color or PURPLE,
        Transparency = transparency or 0.6,
        Thickness = 1
    }, object)
end

function EclipseUI:Notify(message, duration)
    local toast = create("TextLabel", {
        Size = UDim2.fromOffset(260, 48),
        Position = UDim2.new(1, -280, 1, -70),
        BackgroundColor3 = PANEL,
        TextColor3 = TEXT,
        Text = tostring(message),
        TextSize = 14,
        Font = Enum.Font.GothamMedium,
        TextWrapped = true,
        ZIndex = 10
    }, self.toastLayer)

    round(toast, 10)
    stroke(toast, PURPLE, 0.3)

    task.delay(duration or 3, function()
        if toast.Parent then
            toast:Destroy()
        end
    end)
end

function EclipseUI:CreateWindow(options)
    options = options or {}

    local playerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

    local gui = create("ScreenGui", {
        Name = "EclipseUI",
        ResetOnSpawn = false,
        ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    }, playerGui)

    local window = create("Frame", {
        Name = "Window",
        Size = UDim2.fromOffset(560, 370),
        Position = UDim2.new(0.5, -280, 0.5, -185),
        BackgroundColor3 = BACKGROUND,
        BorderSizePixel = 0,
        ClipsDescendants = true
    }, gui)

    round(window, 12)
    stroke(window, PURPLE, 0.25)

    local topbar = create("Frame", {
        Size = UDim2.new(1, 0, 0, 44),
        BackgroundColor3 = PANEL,
        BorderSizePixel = 0
    }, window)

    local title = create("TextLabel", {
        Position = UDim2.fromOffset(15, 0),
        Size = UDim2.new(1, -60, 1, 0),
        BackgroundTransparency = 1,
        Text = options.Title or "EclipseUI",
        TextColor3 = TEXT,
        TextSize = 16,
        Font = Enum.Font.GothamBold,
        TextXAlignment = Enum.TextXAlignment.Left
    }, topbar)

    local close = create("TextButton", {
        Size = UDim2.fromOffset(36, 32),
        Position = UDim2.new(1, -42, 0, 6),
        BackgroundColor3 = Color3.fromRGB(65, 37, 76),
        Text = "×",
        TextColor3 = TEXT,
        TextSize = 22,
        Font = Enum.Font.GothamBold,
        AutoButtonColor = true
    }, topbar)

    round(close, 7)

    close.Activated:Connect(function()
        gui:Destroy()
    end)

    -- Dragging the window with the top bar.
    local dragging = false
    local dragStart
    local startPosition

    topbar.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1
            or input.UserInputType == Enum.UserInputType.Touch then
            dragging = true
            dragStart = input.Position
            startPosition = window.Position
        end
    end)

    topbar.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1
            or input.UserInputType == Enum.UserInputType.Touch then
            dragging = false
        end
    end)

    game:GetService("UserInputService").InputChanged:Connect(function(input)
        if dragging and (
            input.UserInputType == Enum.UserInputType.MouseMovement
            or input.UserInputType == Enum.UserInputType.Touch
        ) then
            local delta = input.Position - dragStart
            window.Position = UDim2.new(
                startPosition.X.Scale,
                startPosition.X.Offset + delta.X,
                startPosition.Y.Scale,
                startPosition.Y.Offset + delta.Y
            )
        end
    end)

    local sidebar = create("ScrollingFrame", {
        Position = UDim2.fromOffset(0, 44),
        Size = UDim2.new(0, 145, 1, -44),
        BackgroundColor3 = Color3.fromRGB(23, 22, 33),
        BorderSizePixel = 0,
        ScrollBarThickness = 3,
        ScrollBarImageColor3 = PURPLE,
        CanvasSize = UDim2.new()
    }, window)

    create("UIListLayout", {
        Padding = UDim.new(0, 6),
        SortOrder = Enum.SortOrder.LayoutOrder
    }, sidebar)

    create("UIPadding", {
        PaddingTop = UDim.new(0, 10),
        PaddingLeft = UDim.new(0, 9),
        PaddingRight = UDim.new(0, 9)
    }, sidebar)

    local content = create("Frame", {
        Position = UDim2.fromOffset(155, 54),
        Size = UDim2.new(1, -165, 1, -64),
        BackgroundTransparency = 1
    }, window)

    local pages = create("Folder", {}, content)
    local activeTab

    local toastLayer = create("Frame", {
        Name = "Notifications",
        Size = UDim2.fromScale(1, 1),
        BackgroundTransparency = 1
    }, gui)

    local library = setmetatable({
        Gui = gui,
        Window = window,
        Content = content,
        Pages = pages,
        Sidebar = sidebar,
        ToastLayer = toastLayer
    }, EclipseUI)

    function library:CreateTab(tabName)
        local page = create("ScrollingFrame", {
            Name = tabName,
            Size = UDim2.fromScale(1, 1),
            BackgroundTransparency = 1,
            BorderSizePixel = 0,
            ScrollBarThickness = 3,
            ScrollBarImageColor3 = PURPLE,
            Visible = false,
            CanvasSize = UDim2.new()
        }, pages)

        local layout = create("UIListLayout", {
            Padding = UDim.new(0, 9),
            SortOrder = Enum.SortOrder.LayoutOrder
        }, page)

        layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
            page.CanvasSize = UDim2.fromOffset(
                0, layout.AbsoluteContentSize.Y + 12
            )
        end)

        create("UIPadding", {
            PaddingTop = UDim.new(0, 5),
            PaddingBottom = UDim.new(0, 8),
            PaddingRight = UDim.new(0, 5)
        }, page)

        local tabButton = create("TextButton", {
            Size = UDim2.new(1, 0, 0, 34),
            BackgroundColor3 = PANEL,
            Text = tabName,
            TextColor3 = MUTED,
            TextSize = 12,
            Font = Enum.Font.GothamMedium,
            TextTruncate = Enum.TextTruncate.AtEnd
        }, sidebar)

        round(tabButton, 7)

        local tab = {}

        tabButton.Activated:Connect(function()
            if activeTab then
                activeTab.Page.Visible = false
                activeTab.Button.BackgroundColor3 = PANEL
                activeTab.Button.TextColor3 = MUTED
            end

            activeTab = tab
            page.Visible = true
            tabButton.BackgroundColor3 = PURPLE
            tabButton.TextColor3 = Color3.new(1, 1, 1)
        end)

        tab.Page = page
        tab.Button = tabButton

        if not activeTab then
            tabButton:Activate()
        end

        function tab:CreateSection(sectionName)
            local section = create("Frame", {
                Size = UDim2.new(1, 0, 0, 44),
                AutomaticSize = Enum.AutomaticSize.Y,
                BackgroundColor3 = PANEL,
                BorderSizePixel = 0
            }, page)

            round(section, 9)
            stroke(section, PURPLE, 0.8)

            create("TextLabel", {
                Size = UDim2.new(1, -20, 0, 30),
                Position = UDim2.fromOffset(10, 0),
                BackgroundTransparency = 1,
                Text = sectionName,
                TextColor3 = TEXT,
                TextSize = 14,
                Font = Enum.Font.GothamBold,
                TextXAlignment = Enum.TextXAlignment.Left
            }, section)

            local body = create("Frame", {
                Position = UDim2.fromOffset(10, 32),
                Size = UDim2.new(1, -20, 0, 0),
                AutomaticSize = Enum.AutomaticSize.Y,
                BackgroundTransparency = 1
            }, section)

            local bodyLayout = create("UIListLayout", {
                Padding = UDim.new(0, 7),
                SortOrder = Enum.SortOrder.LayoutOrder
            }, body)

            create("UIPadding", {
                PaddingBottom = UDim.new(0, 10)
            }, body)

            local controls = {}

            local function addControl(height)
                local item = create("Frame", {
                    Size = UDim2.new(1, 0, 0, height),
                    BackgroundTransparency = 1
                }, body)

                return item
            end

            function controls:CreateLabel(text)
                local label = create("TextLabel", {
                    Size = UDim2.new(1, 0, 0, 25),
                    BackgroundTransparency = 1,
                    Text = tostring(text),
                    TextColor3 = MUTED,
                    TextSize = 12,
                    Font = Enum.Font.Gotham,
                    TextXAlignment = Enum.TextXAlignment.Left
                }, body)

                return {
                    SetText = function(_, value)
                        label.Text = tostring(value)
                    end
                }
            end

            function controls:CreateButton(config)
                config = config or {}
                local item = addControl(32)

                local button = create("TextButton", {
                    Size = UDim2.fromScale(1, 1),
                    BackgroundColor3 = PURPLE,
                    Text = config.Name or "Button",
                    TextColor3 = TEXT,
                    TextSize = 12,
                    Font = Enum.Font.GothamMedium
                }, item)

                round(button, 7)

                button.Activated:Connect(function()
                    if config.Callback then
                        task.spawn(config.Callback)
                    end
                end)

                return {
                    SetText = function(_, value)
                        button.Text = tostring(value)
                    end
                }
            end

            function controls:CreateToggle(config)
                config = config or {}
                local item = addControl(32)
                local enabled = config.Default or false

                local button = create("TextButton", {
                    Size = UDim2.fromScale(1, 1),
                    BackgroundColor3 = enabled and PURPLE or BACKGROUND,
                    Text = (config.Name or "Toggle") ..
                        (enabled and "  [ON]" or "  [OFF]"),
                    TextColor3 = TEXT,
                    TextSize = 12,
                    Font = Enum.Font.Gotham
                }, item)

                round(button, 7)
                stroke(button, PURPLE, 0.7)

                local function update()
                    button.Text = (config.Name or "Toggle") ..
                        (enabled and "  [ON]" or "  [OFF]")
                    button.BackgroundColor3 = enabled and PURPLE or BACKGROUND
                    if config.Callback then
                        task.spawn(config.Callback, enabled)
                    end
                end

                button.Activated:Connect(function()
                    enabled = not enabled
                    update()
                end)

                return {
                    GetValue = function()
                        return enabled
                    end,
                    SetValue = function(_, value)
                        enabled = not not value
                        update()
                    end
                }
            end

            function controls:CreateSlider(config)
                config = config or {}
                local minimum = config.Min or 0
                local maximum = config.Max or 100
                local value = math.clamp(
                    config.Default or minimum, minimum, maximum
                )

                local item = addControl(48)

                local label = create("TextLabel", {
                    Size = UDim2.new(1, 0, 0, 20),
                    BackgroundTransparency = 1,
                    Text = (config.Name or "Slider") .. ": " .. value,
                    TextColor3 = TEXT,
                    TextSize = 12,
                    Font = Enum.Font.Gotham,
                    TextXAlignment = Enum.TextXAlignment.Left
                }, item)

                local track = create("TextButton", {
                    Position = UDim2.fromOffset(0, 27),
                    Size = UDim2.new(1, 0, 0, 8),
                    BackgroundColor3 = BACKGROUND,
                    Text = "",
                    AutoButtonColor = false
                }, item)

                round(track, 5)

                local fill = create("Frame", {
                    Size = UDim2.new(
                        (value - minimum) / math.max(maximum - minimum, 1),
                        0, 1, 0
                    ),
                    BackgroundColor3 = PURPLE,
                    BorderSizePixel = 0
                }, track)

                round(fill, 5)

                local UserInputService = game:GetService("UserInputService")
                local sliding = false

                local function setFromX(x)
                    local width = math.max(track.AbsoluteSize.X, 1)
                    local alpha = math.clamp(
                        (x - track.AbsolutePosition.X) / width, 0, 1
                    )

                    value = math.floor(
                        (minimum + alpha * (maximum - minimum)) + 0.5
                    )

                    fill.Size = UDim2.fromScale(alpha, 1)
                    label.Text = (config.Name or "Slider") .. ": " .. value

                    if config.Callback then
                        task.spawn(config.Callback, value)
                    end
                end

                track.Activated:Connect(function(input)
                    setFromX(UserInputService:GetMouseLocation().X)
                end)

                track.InputBegan:Connect(function(input)
                    if input.UserInputType == Enum.UserInputType.MouseButton1
                        or input.UserInputType == Enum.UserInputType.Touch then
                        sliding = true
                        setFromX(input.Position.X)
                    end
                end)

                UserInputService.InputChanged:Connect(function(input)
                    if sliding and (
                        input.UserInputType == Enum.UserInputType.MouseMovement
                        or input.UserInputType == Enum.UserInputType.Touch
                    ) then
                        setFromX(input.Position.X)
                    end
                end)

                UserInputService.InputEnded:Connect(function(input)
                    if input.UserInputType == Enum.UserInputType.MouseButton1
                        or input.UserInputType == Enum.UserInputType.Touch then
                        sliding = false
                    end
                end)

                return {
                    GetValue = function()
                        return value
                    end
                }
            end

            bodyLayout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
                body.Size = UDim2.new(
                    1, -20, 0, bodyLayout.AbsoluteContentSize.Y + 10
                )
            end)

            return controls
        end

        return tab
    end

    return library
end

return EclipseUI
