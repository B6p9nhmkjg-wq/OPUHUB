
if not game:IsLoaded() then
    game.Loaded:wait(0.1)
end

local plrs = game:GetService("Players")
local lp = plrs.LocalPlayer
local mouse = lp:GetMouse()
local ws = game:GetService("Workspace")
local cg = game:GetService("CoreGui")
local pg = lp:FindFirstChildOfClass("PlayerGui")
local rs = game:GetService("RunService")
local uis = game:GetService("UserInputService")
local stepped = rs.Stepped
local renderstepped = rs.RenderStepped
local heartbeat = rs.Heartbeat
local guiname = tostring((game.PlaceId - lp.UserId) / 2)
local currentplayer = lp
local shp = sethiddenproperty or set_hidden_property or sethiddenprop or set_hidden_prop
local ssr = setsimulationradius or setsimradius or set_simulation_radius
local v3 = Vector3.new
local v3_0 = v3(0, 0, 0)
local cf = CFrame.new
local flycf = false

local function gp(parent, name, className)
    local ret = nil
    pcall(function()
        for i, v in pairs(parent:GetChildren()) do
            if (v.Name == name) and v:IsA(className) then
                ret = v
                break
            end
        end
    end)
    return ret
end

local gui = gp(cg, guiname, "ScreenGui") or gp(pg, guiname, "ScreenGui")
if gui then
    gui:Destroy()
end

gui = Instance.new("ScreenGui")
gui.Name = guiname
gui.ResetOnSpawn = false
gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
gui.Enabled = false
gui.IgnoreGuiInset = true
pcall(function()
    gui.Parent = cg
end)
if gui.Parent ~= cg then
    gui.Parent = pg
end
gui:GetPropertyChangedSignal("Parent"):Connect(function()
    if not (gui and gui.Parent) then
        gui = false
    end
end)
local mainFrame = Instance.new("Frame")
mainFrame.Name = "mainFrame"
mainFrame.Parent = gui
mainFrame.BackgroundColor3 = Color3.fromRGB(21, 21, 21)
mainFrame.BorderSizePixel = 0
mainFrame.Position = UDim2.new(0, 0, 1, -200)
mainFrame.Size = UDim2.new(1, 0, 0, 200)
local mf = Instance.new("Frame")
mf.Name = "mf"
mf.Parent = mainFrame
mf.BackgroundColor3 = mainFrame.BackgroundColor3
mf.BorderSizePixel = 0
mf.Position = UDim2.new(0, 0, 1, 0)
mf.Size = UDim2.new(1, 0, 1, 0)
local scriptName = Instance.new("TextLabel")
scriptName.Name = "scriptName"
scriptName.Parent = mainFrame
scriptName.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
scriptName.BackgroundTransparency = 1.000
scriptName.BorderSizePixel = 0
scriptName.Size = UDim2.new(1, 0, 0, 20)
scriptName.Font = Enum.Font.SourceSans
scriptName.Text = "OPU26.07.05:2.9"
scriptName.TextColor3 = Color3.fromRGB(255, 255, 255)
scriptName.TextSize = 20.000
scriptName.TextWrapped = true
local line = Instance.new("Frame")
line.Name = "line"
line.Parent = scriptName
line.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
line.BackgroundTransparency = 0.700
line.BorderSizePixel = 0
line.Position = UDim2.new(0, 5, 1, 0)
line.Size = UDim2.new(1, -10, 0, 1)
local showhide = Instance.new("TextButton")
showhide.Name = "showhide"
showhide.Parent = mainFrame
showhide.BackgroundColor3 = Color3.fromRGB(21, 21, 21)
showhide.BorderSizePixel = 0
showhide.Position = UDim2.new(0.5, -25, 0, -30)
showhide.Size = UDim2.new(0, 50, 0, 30)
showhide.Font = Enum.Font.SourceSans
showhide.Text = "\\/"
showhide.TextColor3 = Color3.fromRGB(255, 255, 255)
showhide.TextSize = 20.000
local scrollingFrame = Instance.new("ScrollingFrame")
scrollingFrame.Name = "scrollingFrame"
scrollingFrame.Parent = mainFrame
scrollingFrame.Active = true
scrollingFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
scrollingFrame.BackgroundTransparency = 1.000
scrollingFrame.BorderSizePixel = 0
scrollingFrame.ClipsDescendants = false
scrollingFrame.Position = UDim2.new(0, 5, 0, 30)
scrollingFrame.Size = UDim2.new(1, -10, 1, -35)
scrollingFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
scrollingFrame.ScrollBarThickness = 10
scrollingFrame.AutomaticCanvasSize = Enum.AutomaticSize.X
local UIListLayout = Instance.new("UIListLayout")
UIListLayout.Parent = scrollingFrame
UIListLayout.FillDirection = Enum.FillDirection.Horizontal
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayout.Padding = UDim.new(0, 10)

local event = Instance.new("BindableEvent", gui)
local fps = 60
fps = 1 / fps
local tf = 0
local con = nil
con = renderstepped:Connect(function(s)
    if not gui then
        con:Disconnect()
        return
    end
    tf += s
    if tf >= fps then
        for i=1, math.floor(tf / fps) do
            event:Fire(true)
        end
        tf = 0
    end
end)
local event = event.Event

local sn = scriptName.Text
local function notify(msg)
    spawn(function()
        local msg1 = sn .. " - " .. msg
        scriptName.Text = msg1
        wait(3)
        if scriptName.Text == msg1 then
            scriptName.Text = sn
        end
    end)
end

if gui.Parent == pg then
    notify("gui in playerGui")
end

local ancprt = nil
local function weldtp(part, cfr)
    if not (part and part.Parent and part:IsA("BasePart") and (not part:IsGrounded())) then
        return nil
    end
    if not (ancprt and ancprt.Parent and ancprt:IsA("BasePart") and ancprt:IsGrounded() and ancprt:IsDescendantOf(ws)) then
        for i, v in pairs(ws:GetDescendants()) do
            if v and v.Parent and v:IsA("BasePart") and v:IsGrounded() then
                ancprt = v
                break
            end
        end
    end
    if not ancprt then
        ancprt = Instance.new("Part", ws)
        ancprt.Anchored = true
        ancprt.Transparency = 1
        ancprt.CanCollide = false
        ancprt.Name = "weldtp part"
    end
    local weld = Instance.new("Weld")
    weld.Part0 = part
    weld.C0 = cfr:Inverse()
    weld.Part1 = ancprt
    weld.C1 = ancprt.CFrame:Inverse()
    weld.Parent = ws
    stepped:wait(0.1)
    pcall(function()
        weld:Destroy()
    end)
end

local function makeFrame(parent, text, color)
    local frame = Instance.new("Frame")
    frame.Name = "frame_" .. text
    frame.Parent = parent
    frame.BackgroundColor3 = color
    frame.Size = UDim2.new(0, 300, 0, 145)
    frame.BorderSizePixel = 0
    local framelabel = Instance.new("TextLabel")
    framelabel.Name = "framelabel"
    framelabel.Parent = frame
    framelabel.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
    framelabel.BackgroundTransparency = 1.000
    framelabel.BorderSizePixel = 0
    framelabel.Size = UDim2.new(1, 0, 0, 20)
    framelabel.Font = Enum.Font.SourceSans
    framelabel.Text = text
    framelabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    framelabel.TextSize = 14.000
    local line = Instance.new("Frame")
    line.Name = "line"
    line.Parent = framelabel
    line.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
    line.BackgroundTransparency = 0.700
    line.BorderSizePixel = 0
    line.Position = UDim2.new(0, 5, 1, 0)
    line.Size = UDim2.new(1, -10, 0, 1)
    local ScrollingFrame = Instance.new("ScrollingFrame")
    ScrollingFrame.Parent = frame
    ScrollingFrame.Active = true
    ScrollingFrame.Name = "ScrollingFrame"
    ScrollingFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
    ScrollingFrame.BackgroundTransparency = 1.000
    ScrollingFrame.BorderSizePixel = 0
    ScrollingFrame.Position = UDim2.new(0, 5, 0, 25)
    ScrollingFrame.Size = UDim2.new(1, -5, 1, -30)
    ScrollingFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
    ScrollingFrame.ScrollBarThickness = 7
    ScrollingFrame.AutomaticCanvasSize = Enum.AutomaticSize.Y
    local UIListLayout = Instance.new("UIListLayout")
    UIListLayout.Parent = ScrollingFrame
    UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
    UIListLayout.Padding = UDim.new(0, 5)
    return frame
end

showhide.MouseButton1Click:Connect(function()
    if showhide.Text == "/\\" then
        showhide.Text = "\\/"
        mainFrame:TweenPosition(UDim2.new(0, 0, 1, -200), "Out", "Elastic", 1)
    else
        showhide.Text = "/\\"
        mainFrame:TweenPosition(UDim2.new(0, 0, 1, -5), "Out", "Elastic", 1)
    end
end)

local controllable = {}
local lastc = nil
local con = nil
con = lp.CharacterAdded:Connect(function(c)
    if not gui then
        con:Disconnect()
        return
    end
    if lastc == c then
        return
    end
    if c and c.Parent then
        lastc = c
        controllable = {}
        for i, v in pairs(plrs:GetPlayers()) do
            local c = v.Character
            if c and c.Parent then
                table.insert(controllable, c)
            end
        end
    end
end)

local viewedPlayer = nil
local viewConnection = nil

local playersframe = makeFrame(scrollingFrame, "玩家", Color3.fromRGB(10, 10, 10))
local playercframe = makeFrame(playersframe, "playerscontrol", Color3.fromRGB(10, 10, 10))
playercframe.BorderSizePixel = 1.000
playercframe.BorderColor3 = Color3.fromRGB(27, 42, 53)
playercframe.Position = UDim2.new(0, 10, -1, -40)
playercframe.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
playercframe.Visible = true
local playerframef = makeFrame(playercframe, "friends", Color3.fromRGB(10, 10, 10))
playerframef.Position = UDim2.new(1, 10, 0, 5)

local function addbtn(parent, plr)
    local playerbutton = Instance.new("TextButton")
    playerbutton.Name = plr.Name
    playerbutton.Parent = parent
    if plr == lp then
        playerbutton.BackgroundColor3 = Color3.fromRGB(100, 50, 50)
    else
        playerbutton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    end
    playerbutton.BorderSizePixel = 0
    playerbutton.Size = UDim2.new(1, -10, 0, 20)
    playerbutton.Font = Enum.Font.SourceSans
    playerbutton.Text = plr.Name
    if plr.Name ~= plr.DisplayName then
        playerbutton.Text = "昵称：" .. plr.DisplayName .. "  ID：" .. playerbutton.Text
    end
    playerbutton.TextColor3 = Color3.fromRGB(255, 255, 255)
    playerbutton.TextSize = 15.000
    playerbutton.MouseButton1Click:Connect(function()
        playercframe.framelabel.Text = "" .. playerbutton.Text
        currentplayer = plr
        playercframe.Visible = true
        playerframef.Visible = false
        viewbutton.Text = ((viewedPlayer == plr) and "退出监视") or "进入监视"
    end)
end

local function unview()
    viewedPlayer = nil
    if viewConnection then
        viewConnection:Disconnect()
        viewConnection = nil
    end
    viewbutton.Text = "进入监视"
    local c = lp.Character
    if c and c.Parent then
        local subject = c:FindFirstChildOfClass("Humanoid") or c:FindFirstChildWhichIsA("BasePart")
        if subject then
            ws.CurrentCamera.CameraType = Enum.CameraType.Custom
            ws.CurrentCamera.CameraSubject = subject
        else
            notify("error-214:对象不存在")
        end
    else
        notify("error-534:传送目标不存在")
    end
end

local playersScroll = playersframe.ScrollingFrame

for i, v in pairs(plrs:GetPlayers()) do
    addbtn(playersScroll, v)
end
local reset = function() end
local con = nil
con = plrs.PlayerAdded:Connect(function(plr)
    if gui then
        addbtn(playersScroll, plr)
    else
        con:Disconnect()
    end
end)
local con = nil
con = plrs.PlayerRemoving:Connect(function(plr)
    if gui then
        local playerbutton = gp(playersScroll, plr.Name, "TextButton")
        if playerbutton then
            playerbutton:Destroy()
        end
        if plr == currentplayer then
            playercframe.Visible = false
        end
        if plr == viewedPlayer then
            unview()
        end
    else
        con:Disconnect()
    end
end)
local hideplayerc = Instance.new("TextButton")
hideplayerc.Name = "addpositionbutton"
hideplayerc.Parent = playercframe.framelabel
hideplayerc.BackgroundColor3 = Color3.fromRGB(59, 59, 59)
hideplayerc.BorderSizePixel = 0
hideplayerc.Position = UDim2.new(1, -17, 0, 2)
hideplayerc.Size = UDim2.new(0, 15, 0, 15)
hideplayerc.Font = Enum.Font.SourceSans
hideplayerc.Text = "×"
hideplayerc.TextColor3 = Color3.fromRGB(255, 255, 255)
hideplayerc.TextSize = 14.000
hideplayerc.MouseButton1Click:Connect(function()
    playercframe.Visible = false
end)
local function makeplrbutton(buttontext)
    local button = Instance.new("TextButton")
    button.Name = "plrButton"
    button.Parent = playercframe.ScrollingFrame
    button.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    button.BorderSizePixel = 0
    button.Size = UDim2.new(1, -10, 0, 20)
    button.Font = Enum.Font.SourceSans
    button.Text = buttontext
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.TextSize = 15.000
    return button
end
makeplrbutton("传送（快捷T键）").MouseButton1Click:Connect(function()

        local c = lp.Character
        local UserInputService = game:GetService("UserInputService")

        UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
            if input.KeyCode == Enum.KeyCode.T then
                if c and c.Parent then
                    local tp = gp(c, "HumanoidRootPart", "BasePart") or gp(c, "Head", "BasePart") or c:FindFirstChildWhichIsA("BasePart")
                    if tp then
                        local c1 = currentplayer.Character
                        if c1 and c1.Parent then
                            local to = gp(c1, "HumanoidRootPart", "BasePart") or gp(c1, "Head", "BasePart") or c1:FindFirstChildWhichIsA("BasePart")
                            if to then
                                if flycf then
                                    flycf = to.CFrame
                                else
                                    weldtp(tp, to.CFrame)
                                end
                                notify("传送至-玩家：" .. currentplayer.Name)
                            else
                                notify("error-214:对象不存在")
                            end
                        else
                            notify("error-534:传送目标不存在")
                        end
                    else
                        notify("error-214:对象不存在")
                    end
                else
                    notify("error-534:传送目标不存在")
                end
            end
        end)
        if c and c.Parent then
            local tp = gp(c, "HumanoidRootPart", "BasePart") or gp(c, "Head", "BasePart") or c:FindFirstChildWhichIsA("BasePart")
            if tp then
                local c1 = currentplayer.Character
                if c1 and c1.Parent then
                    local to = gp(c1, "HumanoidRootPart", "BasePart") or gp(c1, "Head", "BasePart") or c1:FindFirstChildWhichIsA("BasePart")
                    if to then
                        if flycf then
                            flycf = to.CFrame
                        else
                            weldtp(tp, to.CFrame)
                        end
                        notify("传送至-玩家：" .. currentplayer.Name)
                    else
                        notify("error-214:对象不存在")
                    end
                else
                    notify("error-534:传送目标不存在")
                end
            else
                notify("error-214:对象不存在")
            end
        else
            notify("error-534:传送目标不存在")
        end
    end)
viewbutton = makeplrbutton("进入监视")
viewbutton.MouseButton1Click:Connect(function()
    if viewedPlayer == currentplayer then
        unview()
    else
        viewedPlayer = currentplayer
        viewbutton.Text = "退出监视"
        
        if viewConnection then
            viewConnection:Disconnect()
        end
        
        viewConnection = renderstepped:Connect(function()
            if not viewedPlayer then
                unview()
                return
            end
            
            local char = viewedPlayer.Character
            if not char then return end
            
            local hum = char:FindFirstChildOfClass("Humanoid")
            if not hum or hum.Health <= -1 then
                unview()
                return
            end
            
            ws.CurrentCamera.CameraSubject = hum
            ws.CurrentCamera.CameraType = Enum.CameraType.Custom
        end)
    end
end)

local cbringb = makeplrbutton("生成受击框")

local function noanimations()
    local c = lp.Character
    if c and c.Parent then
        local hum = c:FindFirstChildOfClass("Humanoid")
        if hum then
            local animate = gp(c, "Animate", "LocalScript")
            if animate then
                animate.Disabled = true
            end
            for i, v in pairs(hum:GetPlayingAnimationTracks()) do
                v:Stop()
            end
        else
            notify("humanoid not found")
        end
    else
        notify("character not found")
    end
end

local function isConnected(part0, part1, tested)
    if not ((typeof(part0) == "Instance") and part0:IsA("BasePart")) then
        return false
    end
    if not ((typeof(part1) == "Instance") and part1:IsA("BasePart")) then
        return false
    end
    if not tested then
        tested = {}
    end
    local ret = false
    table.insert(tested, part0)
    for i, v in pairs(part0:GetConnectedParts()) do
        if part1 == v then
            return true
        elseif not table.find(tested, v) then
            ret = ret or isConnected(v, part1, tested)
        end
    end
    return ret
end

local function attach(c1)
    local bck = lp:FindFirstChildOfClass("Backpack")
    local c = lp.Character
    if not (c and c.Parent) then
        notify("character not found")
        return false
    end
    local hum = c:FindFirstChildOfClass("Humanoid")
    if not hum then
        notify("humanoid not found")
        return false
    end 
    local arm = gp(c, "Right Arm", "BasePart") or gp(c, "RightHand", "BasePart")
    if not arm then
        notify("arm not found")
        return false
    end
    local torso = gp(c, "Torso", "BasePart") or gp(c, "UpperTorso", "BasePart")
    if not torso then
        notify("torso not found")
        return
    end
    if torso:IsGrounded() then
        notify("torso is grounded")
        return
    end
    if not isConnected(arm, torso) then
        notify("arm and toso not connected")
        return
    end
    local tool = c:FindFirstChildOfClass("Tool")
    if (not tool) and bck then
        tool = bck:FindFirstChildOfClass("Tool")
    end
    if not tool then
        notify("no tool found")
        return false
    end
    local handle = gp(tool, "Handle", "BasePart")
    if not handle then
        notify("tool handle not found")
        return
    end
    if not (c1 and c1.Parent) then
        notify("target character not found")
        return false
    end
    local hum1 = c1:FindFirstChildOfClass("Humanoid")
    if not hum1 then
        notify("target humanoid not found")
        return false
    end
    local arm1 = gp(c1, "Right Arm", "BasePart") or gp(c1, "RightHand", "BasePart")
    if not arm1 then
        notify("target arm not found")
        return false
    end
    local torso1 = gp(c1, "Torso", "BasePart") or gp(c1, "UpperTorso", "BasePart")
    if not torso1 then
        notify("target torso not found")
        return
    end
    if torso1:IsGrounded() then
        notify("target torso is grounded")
        return
    end
    if not isConnected(arm1, torso1) then
        notify("target arm and toso not connected")
        return
    end
    if bck then
        for i, v in pairs(c:GetChildren()) do
            if v:IsA("Tool") then
                v.Parent = bck
            end
        end
    end
    local nhum = hum:Clone()
    hum:Destroy()
    hum = nhum
    hum.Parent = c
    hum:EquipTool(tool)
    for i, v in pairs(c1:GetDescendants()) do
        if v and v.Parent and v:IsA("BasePart") then
            v.Massless = true
        end
    end
    while stepped:wait(0.1) do
        if not (c and c.Parent) then
            notify("character removed")
            return false
        end
        if (not hum and hum.Parent) then
            notify("humanoid removed")
            return false
        end
        if not (arm and arm.Parent) then
            notify("arm removed")
            return false
        end
        if not (torso and torso.Parent) then
            notify("torso removed")
            return false
        end
        if torso:IsGrounded() then
            notify("torso got grounded")
            return
        end
        if not isConnected(arm, torso) then
            notify("arm and toso connection removed")
            return
        end
        if not (c1 and c1.Parent) then
            notify("target character removed")
            return false
        end
        if not (hum1 and hum1.Parent) then
            notify("target humanoid removed")
            return false
        end
        if not (arm1 and arm1.Parent) then
            notify("target arm removed")
            return false
        end
        if not (torso1 and torso1.Parent) then
            notify("target torso removed")
            return false
        end
        if torso:IsGrounded() then
            notify("target torso got grounded")
            return
        end
        if not isConnected(arm1, torso1) then
            notify("target arm and toso connection removed")
            return
        end
        if not (tool and tool.Parent) then
            notify("tool removed")
            return false
        end
        if not (handle and handle.Parent) then
            notify("tool handle removed")
            return false
        end
        if (tool.Parent ~= c) and (tool.Parent ~= c1) and (tool.Parent ~= bck) then
            notify("unexpected tool parent")
            return false
        end
        if (tool.Parent == c1) then
            break
        end
        tool.Parent = c
        weldtp(arm1, handle.CFrame)
        if (tool.Parent == c1) then
            break
        end
    end
    return handle
end

makeplrbutton("查看本服好友").MouseButton1Click:Connect(function()
    playerframef.Visible = not playerframef.Visible
    if not playerframef.Visible then
        return
    end
    playerframef.framelabel.Text = "查看本服好友：" .. currentplayer.Name
    local scroll = playerframef.ScrollingFrame
    for i, v in pairs(scroll:GetChildren()) do
        if v and v.Parent and v:IsA("TextButton") then
            v:Destroy()
        end
    end
    for i, v in pairs(plrs:GetPlayers()) do
        spawn(function()
            if v and v.Parent and currentplayer:IsFriendsWith(v.UserId) then
                addbtn(playerframef.ScrollingFrame, v)
            end
        end)
    end
end)

local positionsframe = makeFrame(scrollingFrame, "飞雷神标记", Color3.fromRGB(10, 10, 10))
local addpositionbutton = Instance.new("TextButton")
addpositionbutton.Name = "addpositionbutton"
addpositionbutton.Parent = positionsframe.framelabel
addpositionbutton.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
addpositionbutton.BorderSizePixel = 0
addpositionbutton.Position = UDim2.new(1, -77, 0, 2)
addpositionbutton.Size = UDim2.new(0, 75, 1, -4)
addpositionbutton.Font = Enum.Font.SourceSans
addpositionbutton.Text = "插标"
addpositionbutton.TextColor3 = Color3.fromRGB(255, 255, 255)
addpositionbutton.TextSize = 14.000
addpositionbutton.MouseButton1Click:Connect(function()
    local c = lp.Character
    if c and c.Parent then
        local hrp = gp(c, "HumanoidRootPart", "BasePart") or gp(c, "Head", "BasePart") or c:FindFirstChildWhichIsA("BasePart")
        if hrp then
            local cfr = hrp.CFrame
            local positionframe = Instance.new("Frame")
            local loadposbutton = Instance.new("TextButton")
            local removeposbutton = Instance.new("TextButton")
            local positionName = Instance.new("TextBox")
            positionframe.Name = "positionframe"
            positionframe.Parent = positionsframe.ScrollingFrame
            positionframe.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
            positionframe.BorderSizePixel = 0
            positionframe.Size = UDim2.new(1, -10, 0, 30)
            loadposbutton.Name = "loadposbutton"
            loadposbutton.Parent = positionframe
            loadposbutton.BackgroundColor3 = Color3.fromRGB(47, 47, 47)
            loadposbutton.BorderSizePixel = 0
            loadposbutton.Position = UDim2.new(1, -70, 0, 5)
            loadposbutton.Size = UDim2.new(0, 40, 1, -10)
            loadposbutton.Font = Enum.Font.SourceSans
            loadposbutton.Text = "瞬身"
            loadposbutton.TextColor3 = Color3.fromRGB(255, 255, 255)
            loadposbutton.TextSize = 16.000
            removeposbutton.Name = "removeposbutton"
            removeposbutton.Parent = positionframe
            removeposbutton.BackgroundColor3 = Color3.fromRGB(47, 47, 47)
            removeposbutton.BorderSizePixel = 0
            removeposbutton.Position = UDim2.new(1, -25, 0, 5)
            removeposbutton.Size = UDim2.new(0, 20, 1, -10)
            removeposbutton.Font = Enum.Font.SourceSans
            removeposbutton.Text = "×"
            removeposbutton.TextColor3 = Color3.fromRGB(255, 255, 255)
            removeposbutton.TextSize = 16.000
            positionName.Name = "positionName"
            positionName.Parent = positionframe
            positionName.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
            positionName.BackgroundTransparency = 1.000
            positionName.BorderSizePixel = 0
            positionName.Position = UDim2.new(0, 5, 0, 5)
            positionName.Size = UDim2.new(1, -80, 1, -10)
            positionName.Font = Enum.Font.SourceSans
            positionName.Text = "忍爱之剑"
            positionName.ClearTextOnFocus = false
            positionName.TextColor3 = Color3.fromRGB(255, 255, 255)
            positionName.TextSize = 25.000
            positionName.TextXAlignment = Enum.TextXAlignment.Left
            loadposbutton.MouseButton1Click:Connect(function()
                c = lp.Character
                if c and c.Parent then
                    hrp = gp(c, "HumanoidRootPart", "BasePart") or gp(c, "Head", "BasePart") or c:FindFirstChildWhichIsA("BasePart")
                    if hrp then
                        if flycf then
                            flycf = cfr
                        else
                            weldtp(hrp, cfr)
                        end
                    else
                        notify("part not found")
                    end
                else
                    notify("character not found")
                end
            end)
            removeposbutton.MouseButton1Click:Connect(function()
                positionframe:Destroy()
            end)
        end
    end
end)

local charframe = makeFrame(scrollingFrame, "功能", Color3.fromRGB(10, 10, 10))
local function makecharbutton(buttontext)
    local button = Instance.new("TextButton")
    button.Name = "charButton"
    button.Parent = charframe.ScrollingFrame
    button.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    button.BorderSizePixel = 0
    button.Size = UDim2.new(1, -10, 0, 20)
    button.Font = Enum.Font.SourceSans
    button.Text = buttontext
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.TextSize = 15.000
    return button
end
local function respawnRequest()
    local ccfr = ws.CurrentCamera.CFrame
    local c = lp.Character
    lp.Character = nil
    lp.Character = c
    ws.CurrentCamera:GetPropertyChangedSignal("CFrame"):wait(0.1)
    ws.CurrentCamera.CFrame = ccfr
end
local loopr = false
local fakevoidp = nil
reset = function(respawn)
    if fakevoidp then
        fakevoidp = nil
        wait(0.3)
    end
    local c = lp.Character
    local partName, cfr, ccfr = nil, nil, nil
    if not (c and c.Parent) then
        respawnRequest()
        if not loopr then
            notify("character not found, trying to respawn")
        end
        return
    end
    local part = gp(c, "HumanoidRootPart", "BasePart") or gp(c, "Head", "BasePart") or c:FindFirstChildWhichIsA("BasePart")
    if not part then
        respawnRequest()
        if not loopr then
            notify("no part found in the character, trying to respawn")
        end
        return
    end
    partName, cfr, ccfr = part.Name, part.CFrame, ws.CurrentCamera.CFrame
    spawn(function()
        local c, part = c, nil
        while c and c.Parent do
            stepped:wait(0.1)
        end
        while not (c and c.Parent) do
            stepped:wait(0.1)
            c = lp.Character
        end
        while stepped:wait(0.1) and c and c.Parent and (not part) do
            part = gp(c, partName, "BasePart")
        end
        if not part then
            if not loopr then
                notify("failed to tp back")
            end
            return
        end
        weldtp(part, cfr)
        ws.CurrentCamera.CFrame = ccfr
        cfr = false
        if not loopr then
            notify("respawned")
        end
    end)
    if respawn and (not loopr) then
        notify("respawning...")
    end
    if respawn and (plrs.RespawnTime > 0.5) then
        spawn(function()
            while c and c.Parent do
                if part and part.Parent then
                    cfr = part.CFrame
                end
                ccfr = ws.CurrentCamera.CFrame
                stepped:wait(0.1)
            end
        end)
        local spamrequest = true
        spawn(function()
            while wait(0.1) and spamrequest and c and c.Parent do
                respawnRequest()
            end
        end)
        wait(0.3)
        spamrequest = false
        wait(plrs.RespawnTime - 0.5)
        part = nil
    end
    if c and c.Parent then
        if respawn then
            local hum = c:FindFirstChildOfClass("Humanoid")
            if hum then
                hum:Destroy()
            end
        end
        c:BreakJoints()
        while respawn and gui and cfr do
            stepped:wait(0.1)
        end
    end
end
local espitem = makecharbutton("透视稀有物品")
local espitemt = false
espitem.MouseButton1Click:Connect(function()
    if espitemt == false then
        espitemt = true
        espitem.Text = "透视稀有物品 ✓"
    else
        espitemt = false
        espitem.Text = "透视稀有物品"
    end
    while espitemt == true do
    wait(1)
        for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
            for i,v in pairs(l:GetChildren()) do
                 if v.ClassName == "MeshPart" or "Part" then
                    for i,e in pairs(v:GetChildren()) do
                        if e.ClassName == "ProximityPrompt" then
                            if e.ObjectText == "Military Armory Keycard" or e.ObjectText == "Airdrop Marker" or e.ObjectText == "Diamond Ring" or e.ObjectText == "Money Printer" or e.ObjectText == "Diamond" or e.ObjectText == "Void Gem" or e.ObjectText == "Dark Matter Gem" or e.ObjectText == "Gold AK-47" or e.ObjectText == "Gold Deagle" or e.ObjectText == "Police Armory Keycard" or e.ObjectText == "Electronics" or e.ObjectText == "Weapon Parts" or e.ObjectText == "Rollie" then
                                xd = Instance.new("BillboardGui")
                                xd.Parent = v
                                xd.AlwaysOnTop = true
                                xd.Size = UDim2.new(0, 100, 0, 25)
                                Frame = Instance.new("Frame")
                                Frame.Parent = xd
                                Frame.BackgroundColor3 = Color3.new(0, 255, 255)
                                Frame.Size = UDim2.new(1, 0, 1, 0)
                                Frame.BackgroundTransparency = 1
                                text = Instance.new("TextLabel")
                                text.TextScaled = true
                                text.BackgroundColor3 = Color3.new(0, 255, 255)
                                text.Parent = Frame
                                text.Text = e.ObjectText
                                text.Size = UDim2.new(1, 0, 1, 0)
                                text.BackgroundTransparency = 1
                                text.TextColor3 = Color3.new(0, 255, 255)
                            end
                        end    
                    end
                end
             end
        end
        wait(5)
        for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
            for i,v in pairs(l:GetChildren()) do
                 if v.ClassName == "MeshPart" or "Part" then
                    for i,e in pairs(v:GetChildren()) do
                        if e.ClassName == "ProximityPrompt" then
                            if e.ObjectText == "Military Armory Keycard" or e.ObjectText == "Airdrop Marker" or e.ObjectText == "Diamond Ring" or e.ObjectText == "Money Printer" or e.ObjectText == "Diamond" or e.ObjectText == "Void Gem" or e.ObjectText == "Dark Matter Gem" or e.ObjectText == "Gold AK-47" or e.ObjectText == "Gold Deagle" or e.ObjectText == "Police Armory Keycard" or e.ObjectText == "Electronics" or e.ObjectText == "Weapon Parts"then
                                xd:Remove()
                            end
                        end    
                    end
                end
             end
        end
    end
end)
makecharbutton("瞬移合金保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end
    local safe = workspace.Game.Entities.SmallSafe:FindFirstChild("SmallSafe")
    if not safe then return end
    local door = safe:FindFirstChild("Door")
    if not door then return end
    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end
    local att = mesh:FindFirstChild("Attachment")
    if not att then return end
    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end
    hrp.CFrame = mesh.CFrame
    task.wait(0.1)
    prompt.HoldDuration = 0
    prompt.MaxActivationDistance = 20
    prompt:InputHoldBegin()
    prompt:InputHoldEnd()
    local model = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if model and model:IsA("Model") then
        model.Name = "Opened"
    end
end)

makecharbutton("瞬移石英保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end
    local safe = workspace.Game.Entities.MediumSafe:FindFirstChild("MediumSafe")
    if not safe then return end
    local door = safe:FindFirstChild("Door")
    if not door then return end
    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end
    local att = mesh:FindFirstChild("Attachment")
    if not att then return end
    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end
    hrp.CFrame = mesh.CFrame
    task.wait(0.1)
    prompt.HoldDuration = 0
    prompt.MaxActivationDistance = 20
    prompt:InputHoldBegin()
    prompt:InputHoldEnd()
    local model = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if model and model:IsA("Model") then
        model.Name = "Opened"
    end
end)

makecharbutton("瞬移钛金保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end
    local safe = workspace.Game.Entities.LargeSafe:FindFirstChild("LargeSafe")
    if not safe then return end
    local door = safe:FindFirstChild("Door")
    if not door then return end
    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end
    local att = mesh:FindFirstChild("Attachment")
    if not att then return end
    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end
    hrp.CFrame = mesh.CFrame
    task.wait(0.1)
    prompt.HoldDuration = 0
    prompt.MaxActivationDistance = 20
    prompt:InputHoldBegin()
    prompt:InputHoldEnd()
    local model = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if model and model:IsA("Model") then
        model.Name = "Opened"
    end
end)

makecharbutton("瞬移黑色保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end
    local safe = workspace.Game.Entities.JewelSafe:FindFirstChild("JewelSafe")
    if not safe then return end
    local door = safe:FindFirstChild("Door")
    if not door then return end
    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end
    local att = mesh:FindFirstChild("Attachment")
    if not att then return end
    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end
    hrp.CFrame = mesh.CFrame
    task.wait(0.1)
    prompt.HoldDuration = 0
    prompt.MaxActivationDistance = 20
    prompt:InputHoldBegin()
    prompt:InputHoldEnd()
    local model = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if model and model:IsA("Model") then
        model.Name = "Opened"
    end
end)

makecharbutton("瞬移金质保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end
    local safe = workspace.Game.Entities.GoldJewelSafe:FindFirstChild("GoldJewelSafe")
    if not safe then return end
    local door = safe:FindFirstChild("Door")
    if not door then return end
    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end
    local att = mesh:FindFirstChild("Attachment")
    if not att then return end
    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end
    hrp.CFrame = mesh.CFrame
    task.wait(0.1)
    prompt.HoldDuration = 0
    prompt.MaxActivationDistance = 20
    prompt:InputHoldBegin()
    prompt:InputHoldEnd()
    local model = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if model and model:IsA("Model") then
        model.Name = "Opened"
    end
end)
makecharbutton("即取空投").MouseButton1Click:Connect(function()
    while true do
        wait(1)
        game:GetService("Workspace").Game.Airdrops.Airdrop.Airdrop.ProximityPrompt.HoldDuration = 0
        game:GetService("Workspace").Game.Airdrops.Airdrop.Airdrop.ProximityPrompt.MaxActivationDistance= 20
        game:GetService("Workspace").Game.Airdrops.Airdrop.Airdrop.Name = "airdropopen"
    end
end)
makecharbutton("即取珠宝").MouseButton1Click:Connect(function()
    local rocks = game:GetService("Workspace").GemRobbery.JewelryCases.HighYieldSpawns
    for _, obj in pairs(rocks:GetChildren()) do
        if obj.ClassName == "Model" then
            for _, innerObj in pairs(obj:GetChildren()) do
                if innerObj.ClassName == "Model" then
                    if innerObj.Name == "Case" then
                    elseif innerObj.Name == "Emerald" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Sapphire" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Amethyst" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Topaz" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end                     
                    elseif innerObj.Name == "Diamond" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Gold Bar" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Ruby" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    else
                        if innerObj:FindFirstChild("Box") and innerObj.Box:FindFirstChild("ProximityPrompt") then
                            innerObj.Box.ProximityPrompt.HoldDuration = 0
                        end
                    end
                end
            end
        end
    end
    local rocks2 = game:GetService("Workspace").GemRobbery.JewelryCases.LowYieldSpawns
    for _, obj in pairs(rocks2:GetChildren()) do
        if obj.ClassName == "Model" then
            for _, innerObj in pairs(obj:GetChildren()) do
                if innerObj.ClassName == "Model" then
                    if innerObj.Name == "Case" then
                    elseif innerObj.Name == "Emerald" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Sapphire" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Amethyst" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Topaz" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Diamond" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Gold Bar" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    elseif innerObj.Name == "Ruby" then
                        if innerObj:FindFirstChild("Handle") and innerObj.Handle:FindFirstChild("ProximityPrompt") then
                            innerObj.Handle.ProximityPrompt.HoldDuration = 0
                        end
                    else
                        if innerObj:FindFirstChild("Box") and innerObj.Box:FindFirstChild("ProximityPrompt") then
                            innerObj.Box.ProximityPrompt.HoldDuration = 0
                        end
                    end
                end
            end
        end
    end
    end)

    local Dealer1 = makecharbutton("远程黑市")
    local Dealer1t = false
    Dealer1.MouseButton1Click:Connect(function()
    if Dealer1t == false then
           Dealer1t = true
        Dealer1.Text = "远程黑市 ✓"
        game:GetService("Workspace").BlackMarket.Dealer.Dealer.ProximityPrompt.MaxActivationDistance = 100000
    else
        Dealer1t = false
        Dealer1.Text = "远程黑市"
        game:GetService("Workspace").BlackMarket.Dealer.Dealer.ProximityPrompt.MaxActivationDistance = 20
    end
end)

makecharbutton("即用弹药箱").MouseButton1Click:Connect(function()
    for i = 1 , 50 do
        local Ammo = game.workspace.Game.Local.droppables["Ammo Box"]
        Ammo.Handle.ProximityPrompt.HoldDuration = 0
        Ammo.Name = "Ammo"
    end
end)
    makecharbutton("枪械连发无后座").MouseButton1Click:Connect(function()
        while true do
            wait(1)
            if game.ReplicatedStorage.Models.Items:FindFirstChild("Raygun") then
                if game.ReplicatedStorage.Models.Items.Raygun.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.Raygun.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("M1911") then
                if game.ReplicatedStorage.Models.Items.M1911.Handle.Muzzle:FindFirstChild("PointLight") then
                   game.ReplicatedStorage.Models.Items.M1911.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("Scar L") then
                if game.ReplicatedStorage.Models.Items["Scar L"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Scar L"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("Glock") then
                if game.ReplicatedStorage.Models.Items.Glock.Handle.Muzzle:FindFirstChild("PointLight") then
                game.ReplicatedStorage.Models.Items.Glock.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if 

game.ReplicatedStorage.Models.Items:FindFirstChild("P90") then
                if game.ReplicatedStorage.Models.Items["P90"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["P90"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("M249 SAW") then
                if game.ReplicatedStorage.Models.Items["M249 SAW"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["M249 SAW"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("Mossberg") then
                if game.ReplicatedStorage.Models.Items.Mossberg.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.Mossberg.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("RPG") then
                if game.ReplicatedStorage.Models.Items.RPG.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.RPG.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("USP 45") then
                if game.ReplicatedStorage.Models.Items["USP 45"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["USP 45"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("Sawn Off") then
                if game.ReplicatedStorage.Models.Items["Sawn Off"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Sawn Off"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("Minigun") then
                if game.ReplicatedStorage.Models.Items.Minigun.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.Minigun.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("Stagecoach") then
                if game.ReplicatedStorage.Models.Items.Stagecoach.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.Stagecoach.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if 
game.ReplicatedStorage.Models.Items:FindFirstChild("Dragunow") then
                if game.ReplicatedStorage.Models.Items["Dragunow"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Dragunow"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("M1 Garand") then
                if game.ReplicatedStorage.Models.Items["M1 Garand"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["M1 Garand"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("AWP") then
                if game.ReplicatedStorage.Models.Items["AWP"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["AWP"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("Barrett M107") then
                if game.ReplicatedStorage.Models.Items["Barrett M107"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Barrett M107"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("Saiga 12") then
                if game.ReplicatedStorage.Models.Items["Saiga 12"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Saiga 12"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("Deagle") then
                if game.ReplicatedStorage.Models.Items.Deagle.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.Deagle.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("RPK") then
                if game.ReplicatedStorage.Models.Items.RPK.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.RPK.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("Glock 18") then
                if game.ReplicatedStorage.Models.Items["Glock 18"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Glock 18"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("AK-47") then
                if game.ReplicatedStorage.Models.Items["AK-47"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["AK-47"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if 
game.ReplicatedStorage.Models.Items:FindFirstChild("AR-15") then
                if game.ReplicatedStorage.Models.Items["AR-15"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["AR-15"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("AUG") then
                if game.ReplicatedStorage.Models.Items["AUG"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["AUG"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("Tommy Gun") then
                if game.ReplicatedStorage.Models.Items["Tommy Gun"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Tommy Gun"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if game.ReplicatedStorage.Models.Items:FindFirstChild("M4A1") then
                if game.ReplicatedStorage.Models.Items.M4A1.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.M4A1.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if 
game.ReplicatedStorage.Models.Items:FindFirstChild("Double Barrel") then
                if game.ReplicatedStorage.Models.Items["Double Barrel"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["Double Barrel"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("Uzi") then
                if game.ReplicatedStorage.Models.Items.Uzi.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.Uzi.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if 
game.ReplicatedStorage.Models.Items:FindFirstChild("FN FAL") then
                if game.ReplicatedStorage.Models.Items["FN FAL"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["FN FAL"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("MP7") then
                if  game.ReplicatedStorage.Models.Items.MP7.Handle.Muzzle:FindFirstChild("PointLight") then
                game.ReplicatedStorage.Models.Items.MP7.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if 
game.ReplicatedStorage.Models.Items:FindFirstChild("AS Val") then
                if game.ReplicatedStorage.Models.Items["AS Val"].Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items["AS Val"].Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
            if
game.ReplicatedStorage.Models.Items:FindFirstChild("Python") then
                if  game.ReplicatedStorage.Models.Items.Python.Handle.Muzzle:FindFirstChild("PointLight") then
                    game.ReplicatedStorage.Models.Items.Python.Handle.Muzzle.PointLight.Name = "PointLight1"
                end
            end
        end
    end)
makecharbutton("储物柜背包（一次性）").MouseButton1Click:Connect(function()
    game:GetService("Players").LocalPlayer.PlayerGui.Backpack.Holder.Locker.Visible = true
end)
local isRotating = false
makecharbutton  ("撞飞空投、载具").MouseButton1Click:Connect(function()
    local Players = game:GetService("Players")
    local localPlayer = Players.LocalPlayer

    isRotating = not isRotating

    if isRotating then
        while isRotating do
            localPlayer.Character:SetPrimaryPartCFrame(localPlayer.Character:GetPrimaryPartCFrame() * CFrame.Angles(0, math.rad(45), 0))
            wait()
        end
    else
        localPlayer.Character:SetPrimaryPartCFrame(localPlayer.Character:GetPrimaryPartCFrame())
    end
end)
local hitbox123 = makecharbutton("近战范围")
local hitbox123t = false
hitbox123.MouseButton1Click:Connect(function()
    if hitbox123t == false then
        hitbox123t = true
        hitbox123.Text = "近战范围 ✓"
        _G.HeadSize = 40
        _G.Disabled = true
        game:GetService("RunService").RenderStepped:connect(function()
            if _G.Disabled then
                for i,v in next, game:GetService("Players"):GetPlayers() do
                    if v.Name ~= game:GetService("Players").LocalPlayer.Name then
                        pcall(function()
                            v.Character.HumanoidRootPart.Size = Vector3.new(_G.HeadSize,_G.HeadSize,_G.HeadSize)
                            v.Character.HumanoidRootPart.Transparency = 0.7
                            v.Character.HumanoidRootPart.BrickColor = BrickColor.new("Really blue")
                            v.Character.HumanoidRootPart.Material = "Neon"
                            v.Character.HumanoidRootPart.CanCollide = false
                        end)
                    end
                end
            end
        end)
    else
        hitbox123t = false
        hitbox123.Text = "近战范围"
        _G.HeadSize = 1
    end
end)
local killoppBtn = makecharbutton("↓子弹追踪器")
local killoppEnabled = false
local killoppHookInstalled = false
local oldRaycast
local targetDisplay, healthDisplay, usernameDisplay
local heartbeatConn

local function createDisplays()
    local Camera = workspace.CurrentCamera
    targetDisplay = Drawing.new("Text")
    targetDisplay.Visible = false
    targetDisplay.Size = 20
    targetDisplay.Center = false
    targetDisplay.Outline = true
    targetDisplay.OutlineColor = Color3.new(0, 0, 0)
    targetDisplay.Color = Color3.new(1, 1, 1)
    targetDisplay.Position = Vector2.new(Camera.ViewportSize.X - 200, 50)
    targetDisplay.Font = 2

    healthDisplay = Drawing.new("Text")
    healthDisplay.Visible = false
    healthDisplay.Size = 18
    healthDisplay.Center = true
    healthDisplay.Outline = true
    healthDisplay.OutlineColor = Color3.new(0, 0, 0)
    healthDisplay.Color = Color3.new(0, 1, 0)
    healthDisplay.Font = 2

    usernameDisplay = Drawing.new("Text")
    usernameDisplay.Visible = false
    usernameDisplay.Size = 18
    usernameDisplay.Center = true
    usernameDisplay.Outline = true
    usernameDisplay.OutlineColor = Color3.new(0, 0, 0)
    usernameDisplay.Color = Color3.new(1, 1, 1)
    usernameDisplay.Font = 2
end

local function installHook()
    if killoppHookInstalled then return end
    local Players = game:GetService("Players")
    local LocalPlayer = Players.LocalPlayer
    local Camera = workspace.CurrentCamera
    local function isFriend(player)
        if not ignoreFriendsEnabled then return false end
        local success, result = pcall(function() return LocalPlayer:IsFriendsWith(player.UserId) end)
        return success and result
    end
    local function getClosestHead()
        local closestHead, closestPlayer, closestCharacter
        local closestDist = math.huge
        local cameraPos = Camera.CFrame.Position
        for _, player in ipairs(Players:GetPlayers()) do
            if player ~= LocalPlayer and player.Character then
                if ignoreFriendsEnabled and isFriend(player) then
                else
                    local character = player.Character
                    local head = character:FindFirstChild("Head")
                    local humanoid = character:FindFirstChildOfClass("Humanoid")
                    local forcefield = character:FindFirstChild("ForceField")
                    if head and humanoid and not forcefield and humanoid.Health > 0 then
                        local dist = (head.Position - cameraPos).Magnitude
                        if dist < closestDist then
                            closestHead = head
                            closestPlayer = player
                            closestCharacter = character
                            closestDist = dist
                        end
                    end
                end
            end
        end
        return closestHead, closestPlayer, closestCharacter
    end
    oldRaycast = hookmetamethod(game, "__namecall", function(self, ...)
        if not killoppEnabled then
            return oldRaycast(self, ...)
        end
        local method = getnamecallmethod()
        local args = { ... }
        if (method == "Raycast" or method == "FindPartOnRay") and not checkcaller() and self == workspace then
            local origin, direction
            if method == "Raycast" then
                origin = args[1]
                direction = args[2]
            else
                local ray = args[1]
                if typeof(ray) == "Ray" then
                    origin = ray.Origin
                    direction = ray.Direction
                end
            end
            if origin and direction then
                local closestHead, closestPlayer = getClosestHead()
                if closestHead and closestPlayer then
                    if not (ignoreFriendsEnabled and isFriend(closestPlayer)) then
                        return {
                            Instance = closestHead,
                            Position = closestHead.Position,
                            Normal = (closestHead.Position - origin).Unit,
                            Material = Enum.Material.Plastic
                        }
                    end
                end
            end
        end
        return oldRaycast(self, ...)
    end)
    killoppHookInstalled = true
end

local function updateDisplay(character, player)
    local Camera = workspace.CurrentCamera
    local head = character and character:FindFirstChild("Head")
    local humanoid = character and character:FindFirstChildOfClass("Humanoid")
    if not head or not humanoid then
        healthDisplay.Visible = false
        usernameDisplay.Visible = false
        return
    end
    local headPos, headOnScreen = Camera:WorldToViewportPoint(head.Position)
    if not headOnScreen then
        healthDisplay.Visible = false
        usernameDisplay.Visible = false
        return
    end
    healthDisplay.Text = math.floor(humanoid.Health) .. "/" .. math.floor(humanoid.MaxHealth)
    healthDisplay.Position = Vector2.new(headPos.X, headPos.Y - 30)
    healthDisplay.Visible = true
    usernameDisplay.Text = player.Name
    usernameDisplay.Position = Vector2.new(headPos.X, headPos.Y - 50)
    usernameDisplay.Visible = true
end

killoppBtn.MouseButton1Click:Connect(function()
    if killoppEnabled == false then
        killoppEnabled = true
        killoppBtn.Text = "↓子弹追踪器 ✓"
        if not killoppHookInstalled then
            createDisplays()
            installHook()
        end
        local Players = game:GetService("Players")
        local LocalPlayer = Players.LocalPlayer
        local Camera = workspace.CurrentCamera
        local RunService = game:GetService("RunService")
        local function isFriend(player)
            if not ignoreFriendsEnabled then return false end
            local success, result = pcall(function() return LocalPlayer:IsFriendsWith(player.UserId) end)
            return success and result
        end
        heartbeatConn = RunService.Heartbeat:Connect(function()
            if not killoppEnabled then
                heartbeatConn:Disconnect()
                targetDisplay.Visible = false
                healthDisplay.Visible = false
                usernameDisplay.Visible = false
                return
            end
            local closestHead, closestPlayer, closestChar
            local closestDist = math.huge
            local cameraPos = Camera.CFrame.Position
            for _, player in ipairs(Players:GetPlayers()) do
                if player ~= LocalPlayer and player.Character then
                    if ignoreFriendsEnabled and isFriend(player) then
                    else
                        local character = player.Character
                        local head = character:FindFirstChild("Head")
                        local humanoid = character:FindFirstChildOfClass("Humanoid")
                        local forcefield = character:FindFirstChild("ForceField")
                        if head and humanoid and not forcefield and humanoid.Health > 0 then
                            local dist = (head.Position - cameraPos).Magnitude
                            if dist < closestDist then
                                closestHead = head
                                closestPlayer = player
                                closestChar = character
                                closestDist = dist
                            end
                        end
                    end
                end
            end
            if closestHead and closestPlayer then
                targetDisplay.Text = "目标: " .. closestPlayer.Name
                targetDisplay.Visible = true
                updateDisplay(closestChar, closestPlayer)
            else
                targetDisplay.Text = "目标: 暂无"
                targetDisplay.Visible = true
                healthDisplay.Visible = false
                usernameDisplay.Visible = false
            end
        end)
    else
        killoppEnabled = false
        killoppBtn.Text = "↓子弹追踪器"
        if heartbeatConn then
            heartbeatConn:Disconnect()
            heartbeatConn = nil
        end
        if targetDisplay then targetDisplay.Visible = false end
        if healthDisplay then healthDisplay.Visible = false end
        if usernameDisplay then usernameDisplay.Visible = false end
    end
end)

local ignoreFriendsBtn = makecharbutton("↑不追踪好友")
ignoreFriendsEnabled = false
ignoreFriendsBtn.MouseButton1Click:Connect(function()
    if ignoreFriendsEnabled == false then
        ignoreFriendsEnabled = true
        ignoreFriendsBtn.Text = "↑不追踪好友 ✓"
    else
        ignoreFriendsEnabled = false
        ignoreFriendsBtn.Text = "↑不追踪好友"
    end
end)
local infjumpb = makecharbutton("无限跳跃")
local infjump = false
local con = nil
con = game:GetService("UserInputService").JumpRequest:Connect(function()
    if not gui then
        con:Disconnect()
        return
    end
    if infjump then
        local c = lp.Character
        if c and c.Parent then
            local hum = c:FindFirstChildOfClass("Humanoid")
            if hum then
                hum:ChangeState("Jumping")
            end
        end
    end
end)

infjumpb.MouseButton1Click:Connect(function()
    infjump = not infjump
    infjumpb.Text = "无限跳跃" .. ((infjump and " ✓") or "")
end)

local noclipb = makecharbutton("移动穿墙")
local noclip = false
local antifling = false
noclipb.MouseButton1Click:Connect(function()
    noclip = not noclip
    noclipb.Text = "移动穿墙" .. ((noclip and " ✓") or "")
end)

local speedBtn = makecharbutton("↓ 移速修改")
local speedOn = false
local sudu = nil
local Speed = 2

local container = Instance.new("Frame")
container.Size = UDim2.new(1, 0, 0, 0)
container.AutomaticSize = Enum.AutomaticSize.Y
container.BackgroundTransparency = 1
container.Parent = speedBtn.Parent

local layout = Instance.new("UIListLayout")
layout.FillDirection = Enum.FillDirection.Horizontal
layout.HorizontalAlignment = Enum.HorizontalAlignment.Left
layout.VerticalAlignment = Enum.VerticalAlignment.Center
layout.Padding = UDim.new(0, 5)
layout.Parent = container

local lbl = Instance.new("TextLabel")
lbl.Size = UDim2.new(0, 100, 0, 20)
lbl.BackgroundTransparency = 1
lbl.Text = "<<<< 修改速度比例"
lbl.TextXAlignment = Enum.TextXAlignment.Left
lbl.Font = Enum.Font.SourceSans
lbl.TextSize = 14
lbl.TextColor3 = Color3.new(255, 255, 255)
lbl.Parent = container

local inputBox = Instance.new("TextBox")
inputBox.Size = UDim2.new(1, -110, 0, 20)
inputBox.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
inputBox.TextColor3 = Color3.fromRGB(255, 255, 255)
inputBox.PlaceholderText = "Speed"
inputBox.Text = tostring(Speed)
inputBox.ClearTextOnFocus = false
inputBox.Font = Enum.Font.SourceSans
inputBox.TextSize = 14
inputBox.Parent = container

inputBox.FocusLost:Connect(function(enterPressed)
    local num = tonumber(inputBox.Text)
    if num and num > 0 then
        Speed = num
        inputBox.Text = tostring(num)
    else
        inputBox.Text = tostring(Speed)
    end
end)

speedBtn.MouseButton1Click:Connect(function()
    speedOn = not speedOn
    speedBtn.Text = "↓ 移速修改" .. ((speedOn and " ✓") or "")
    if speedOn then
        if sudu then sudu:Disconnect() end
        sudu = game:GetService("RunService").Heartbeat:Connect(function()
            local char = game:GetService("Players").LocalPlayer.Character
            local hum = char and char:FindFirstChild("Humanoid")
            if hum and hum.MoveDirection.Magnitude > 0 then
                char:TranslateBy(hum.MoveDirection * Speed / 10)
            end
        end)
    else
        if sudu then
            sudu:Disconnect()
            sudu = nil
        end
    end
end)

aimBtn = makecharbutton("自动测速瞄准")
radiusBtn = makecharbutton("")  

aimOn = false
aimConnection = nil
radius = 20
markers = {}

stillSpeed = 3
bulletSpeed = 900
velocitySmooth = 0.2

lastPositions = {}
lastTimes = {}
smoothedVelocities = {}       

radiusBtn.Text = ""
radiusBtn.AutoButtonColor = false
radiusBtn.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
radiusBtn.BackgroundTransparency = 0
radiusBtn.BorderSizePixel = 0

if aimBtn and aimBtn.Size then
    radiusBtn.Size = aimBtn.Size
else
    radiusBtn.Size = UDim2.new(0, 160, 0, 30)
end

rowLayout = Instance.new("UIListLayout")
rowLayout.FillDirection = Enum.FillDirection.Horizontal
rowLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
rowLayout.VerticalAlignment = Enum.VerticalAlignment.Center
rowLayout.Padding = UDim.new(0, 2)
rowLayout.Parent = radiusBtn

minusBtn = Instance.new("TextButton")
minusBtn.Size = UDim2.new(0, 28, 1, 0)
minusBtn.Text = "-"
minusBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
minusBtn.BackgroundTransparency = 0
minusBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
minusBtn.Font = Enum.Font.SourceSansBold
minusBtn.TextSize = 14
minusBtn.AutoButtonColor = false
minusBtn.Parent = radiusBtn

plusBtn = Instance.new("TextButton")
plusBtn.Size = UDim2.new(0, 28, 1, 0)
plusBtn.Text = "+"
plusBtn.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
plusBtn.BackgroundTransparency = 0
plusBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
plusBtn.Font = Enum.Font.SourceSansBold
plusBtn.TextSize = 14
plusBtn.AutoButtonColor = false
plusBtn.Parent = radiusBtn

valLabel = Instance.new("TextLabel")
valLabel.Size = UDim2.new(0, 110, 1, 0)
valLabel.BackgroundTransparency = 1
valLabel.Text = "瞄准框半径值: "..tostring(radius)
valLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
valLabel.Font = Enum.Font.SourceSans
valLabel.TextSize = 14
valLabel.TextXAlignment = Enum.TextXAlignment.Right
valLabel.Parent = radiusBtn

minusBtn.MouseButton1Click:Connect(function()
    radius = math.max(radius - 20, 0)
    valLabel.Text = "瞄准框半径值: "..tostring(radius)
end)

plusBtn.MouseButton1Click:Connect(function()
    radius = math.min(radius + 20, 300)
    valLabel.Text = "瞄准框半径值: "..tostring(radius)
end)

createMarkers = function()
    left = Drawing.new("Text")
    left.Text = "→"
    left.Size = 25
    left.Center = true
    left.Outline = true
    left.Color = Color3.new(1, 1, 1)
    left.Visible = false

    right = Drawing.new("Text")
    right.Text = "←"
    right.Size = 25
    right.Center = true
    right.Outline = true
    right.Color = Color3.new(1, 1, 1)
    right.Visible = false

    markers.left = left
    markers.right = right
end

function getPredictedPosition(aimPart, targetPlayer)
    local currentPos = aimPart.Position
    local currentTime = tick()

    local rawVel = Vector3.zero
    if lastPositions[targetPlayer] and lastTimes[targetPlayer] then
        local lastPos = lastPositions[targetPlayer]
        local lastTime = lastTimes[targetPlayer]
        local dt = currentTime - lastTime
        if dt > 0.01 then
            rawVel = (currentPos - lastPos) / dt
        end
    end
    lastPositions[targetPlayer] = currentPos
    lastTimes[targetPlayer] = currentTime

    local prevSmoothed = smoothedVelocities[targetPlayer] or rawVel
    local smoothVel = prevSmoothed:Lerp(rawVel, velocitySmooth)
    smoothedVelocities[targetPlayer] = smoothVel

    if smoothVel.Magnitude < 0.5 then
        return currentPos
    end

    local distance = (Cam.CFrame.Position - currentPos).Magnitude
    local travelTime = distance / bulletSpeed
    return currentPos + smoothVel * travelTime
end

function getPlayerSpeed(plr)
    local root = plr.Character and (plr.Character:FindFirstChild("HumanoidRootPart") or plr.Character:FindFirstChild("Torso"))
    if not root then return 0 end
    local currentPos = root.Position
    local currentTime = tick()
    local key = plr.UserId .. "_root"
    local lastPos = lastPositions[key]
    local lastTime = lastTimes[key]
    lastPositions[key] = currentPos
    lastTimes[key] = currentTime
    if lastPos and lastTime then
        local dt = currentTime - lastTime
        if dt > 0.01 then
            return (currentPos - lastPos).Magnitude / dt
        end
    end
    return 0
end

aimBtn.MouseButton1Click:Connect(function()
    aimOn = not aimOn
    aimBtn.Text = "自动测速瞄准" .. ((aimOn and " ✓") or "")

    if aimOn then
        createMarkers()
        if markers.left then markers.left.Visible = true end
        if markers.right then markers.right.Visible = true end

        Cam = workspace.CurrentCamera
        Players = game:GetService("Players")
        LocalPlayer = Players.LocalPlayer

        lastPositions = {}
        lastTimes = {}
        smoothedVelocities = {}

        aimConnection = game:GetService("RunService").RenderStepped:Connect(function()
            center = Vector2.new(Cam.ViewportSize.X / 2, Cam.ViewportSize.Y / 2 - 12.4)
            if markers.left then
                markers.left.Position = center - Vector2.new(radius, 0)
                markers.right.Position = center + Vector2.new(radius, 0)
            end

            nearest = nil
            last = math.huge
            for _, plr in ipairs(Players:GetPlayers()) do
                if plr ~= LocalPlayer and plr.Character and plr.Character:FindFirstChild("Head") then
                    local head = plr.Character.Head
                    local pos, on = Cam:WorldToViewportPoint(head.Position)
                    if on then
                        local dist = (Vector2.new(pos.X, pos.Y) - center).Magnitude
                        if dist < last and dist <= radius then
                            last = dist
                            nearest = plr
                        end
                    end
                end
            end

            if nearest then
                local targetSpeed = getPlayerSpeed(nearest)
                local humanoid = nearest.Character:FindFirstChildOfClass("Humanoid")
                local isDowned = humanoid and humanoid.Health <= humanoid.MaxHealth * 0.25
                local aimPart

                if isDowned or targetSpeed <= stillSpeed then
                    aimPart = nearest.Character.Head
                else
                    aimPart = nearest.Character:FindFirstChild("HumanoidRootPart") or nearest.Character:FindFirstChild("Torso")
                    if not aimPart then
                        aimPart = nearest.Character.Head
                    end
                end

                local predictedPos = getPredictedPosition(aimPart, nearest)
                Cam.CFrame = CFrame.new(Cam.CFrame.Position, predictedPos)
            end
        end)
    else
        if aimConnection then
            aimConnection:Disconnect()
            aimConnection = nil
        end
        if markers.left then
            markers.left:Remove()
            markers.right:Remove()
            markers = {}
        end
        lastPositions = {}
        lastTimes = {}
        smoothedVelocities = {}
    end
end)
local espBtn = makecharbutton("ESP透视")
local espOn = false
local espLoop = nil
local highlights = {}
local displayNameDrawings = {}
local hpDrawings = {}
local nameDrawings = {}
local currentColors = {}
local deathAnims = {}
local LERP_SPEED = 0.15

local function cleanup()
    if espLoop then espLoop:Disconnect() espLoop = nil end
    for _, h in pairs(highlights) do if h.Parent then h:Destroy() end end
    highlights = {}
    for _, d in pairs(displayNameDrawings) do if d.Remove then d:Remove() end end
    displayNameDrawings = {}
    for _, d in pairs(hpDrawings) do if d.Remove then d:Remove() end end
    hpDrawings = {}
    for _, d in pairs(nameDrawings) do if d.Remove then d:Remove() end end
    nameDrawings = {}
    currentColors = {}
    deathAnims = {}
end

local function lerpColor(from, to, alpha)
    return Color3.new(
        from.R + (to.R - from.R) * alpha,
        from.G + (to.G - from.G) * alpha,
        from.B + (to.B - from.B) * alpha
    )
end

espBtn.MouseButton1Click:Connect(function()
    espOn = not espOn
    espBtn.Text = "ESP透视" .. (espOn and " ✓" or "")
    if espOn then
        local Players = game:GetService("Players")
        local RunService = game:GetService("RunService")
        local camera = workspace.CurrentCamera
        local localPlayer = Players.LocalPlayer

        espLoop = RunService.RenderStepped:Connect(function()
            local myChar = localPlayer.Character
            if not myChar then return end
            local myRoot = myChar:FindFirstChild("HumanoidRootPart")
            if not myRoot then return end

            for _, player in ipairs(Players:GetPlayers()) do
                if player == localPlayer then continue end
                local char = player.Character
                if not char then continue end
                local hum = char:FindFirstChildOfClass("Humanoid")
                local root = char:FindFirstChild("HumanoidRootPart")
                if not hum or not root then continue end

                local healthPercent = math.clamp(hum.Health / math.max(hum.MaxHealth, 1), 0, 1)

                if not highlights[char] then
                    local hl = Instance.new("Highlight")
                    hl.Parent = game.CoreGui
                    highlights[char] = hl
                end
                local hl = highlights[char]
                hl.Adornee = char
                hl.OutlineTransparency = 0

                local targetOutline
                local targetFill
                local targetText

                if healthPercent <= 0 then
                    if not deathAnims[char] then
                        local startCol = currentColors[char] and currentColors[char].outline or Color3.new(1,1,1)
                        deathAnims[char] = {
                            startTime = tick(),
                            startColor = startCol,
                            fadeOutStart = nil
                        }
                    end
                    local anim = deathAnims[char]
                    local elapsed = tick() - anim.startTime

                    if elapsed < 0.10 then
                        local t = elapsed / 0.10
                        local col = lerpColor(anim.startColor, Color3.new(0,0,0), t)
                        targetOutline = col
                        targetFill = col
                        targetText = col
                        hl.FillTransparency = 0
                    elseif elapsed < 1.25 then
                        local phase = elapsed - 0.10
                        local step = phase / 0.3833
                        local cycle = math.floor(step)
                        local sub = step - cycle
                        local col
                        if cycle < 3 then
                            if sub < 0.5 then
                                col = Color3.new(1,1,1)
                            else
                                col = Color3.new(0,0,0)
                            end
                        else
                            col = Color3.new(0,0,0)
                        end
                        targetOutline = col
                        targetFill = col
                        targetText = col
                        hl.FillTransparency = 0.1
                    else
                        targetOutline = Color3.new(0,0,0)
                        targetFill = Color3.new(0,0,0)
                        targetText = Color3.new(0,0,0)
                        hl.FillTransparency = 0.1

                        if not anim.fadeOutStart then
                            anim.fadeOutStart = tick()
                        end
                        if tick() - anim.fadeOutStart >= 1.5 then
                            if displayNameDrawings[char] then displayNameDrawings[char].Visible = false end
                            if hpDrawings[char] then hpDrawings[char].Visible = false end
                            if nameDrawings[char] then nameDrawings[char].Visible = false end
                        end
                    end
                else
                    deathAnims[char] = nil
                    hl.FillTransparency = 0.5

                    if healthPercent <= 0.05 then
                        targetOutline = Color3.new(1,1,1)
                        targetFill = Color3.new(1,1,1)
                        targetText = Color3.new(1,1,1)
                    else
                        local gb = 1 - healthPercent
                        targetOutline = Color3.new(1, gb, gb)
                        targetFill = Color3.new(1, gb, gb)
                        targetText = Color3.new(1, gb, gb)
                    end
                end

                if not currentColors[char] then
                    currentColors[char] = {
                        outline = targetOutline,
                        fill = targetFill,
                        text = targetText
                    }
                end

                local cur = currentColors[char]
                cur.outline = lerpColor(cur.outline, targetOutline, LERP_SPEED)
                cur.fill = lerpColor(cur.fill, targetFill, LERP_SPEED)
                cur.text = lerpColor(cur.text, targetText, LERP_SPEED)

                hl.OutlineColor = cur.outline
                hl.FillColor = cur.fill

                local centerPos = root.Position + Vector3.new(0, 2.5, 0)
                local screenPos, onScreen = camera:WorldToViewportPoint(centerPos)

                if onScreen then
                    local distance = (root.Position - myRoot.Position).Magnitude

                    if not displayNameDrawings[char] then
                        local d = Drawing.new("Text")
                        d.Center = true
                        d.Outline = true
                        d.Font = 2
                        d.Size = 14
                        displayNameDrawings[char] = d
                    end
                    local dnd = displayNameDrawings[char]
                    dnd.Visible = true
                    dnd.Position = Vector2.new(screenPos.X, screenPos.Y - 36)
                    dnd.Text = player.DisplayName
                    dnd.Color = cur.text

                    if not hpDrawings[char] then
                        local d = Drawing.new("Text")
                        d.Center = true
                        d.Outline = true
                        d.Font = 2
                        d.Size = 14
                        hpDrawings[char] = d
                    end
                    local hd = hpDrawings[char]
                    hd.Visible = true
                    hd.Position = Vector2.new(screenPos.X, screenPos.Y - 18)
                    hd.Text = hum.Health .. "/" .. hum.MaxHealth
                    hd.Color = cur.text

                    if not nameDrawings[char] then
                        local d = Drawing.new("Text")
                        d.Center = true
                        d.Outline = true
                        d.Font = 2
                        d.Size = 14
                        nameDrawings[char] = d
                    end
                    local nd = nameDrawings[char]
                    nd.Visible = true
                    nd.Position = Vector2.new(screenPos.X, screenPos.Y)
                    nd.Text = player.Name .. " [" .. math.floor(distance) .. "m]"
                    nd.Color = cur.text
                else
                    if displayNameDrawings[char] then displayNameDrawings[char].Visible = false end
                    if hpDrawings[char] then hpDrawings[char].Visible = false end
                    if nameDrawings[char] then nameDrawings[char].Visible = false end
                end
            end

            for char, hl in pairs(highlights) do
                if not char.Parent then
                    hl:Destroy()
                    highlights[char] = nil
                    currentColors[char] = nil
                    deathAnims[char] = nil
                end
            end
            for char, d in pairs(displayNameDrawings) do
                if not char.Parent then d:Remove() displayNameDrawings[char] = nil end
            end
            for char, d in pairs(hpDrawings) do
                if not char.Parent then d:Remove() hpDrawings[char] = nil end
            end
            for char, d in pairs(nameDrawings) do
                if not char.Parent then d:Remove() nameDrawings[char] = nil end
            end
        end)
    else
        cleanup()
    end
end)

ctrltp = false
clicktpbutton = makecharbutton("点击传送模式")
clicktpbutton.MouseButton1Click:Connect(function()
    ctrltp = not ctrltp
    clicktpbutton.Text = "点击传送模式" .. ((ctrltp and " ✓") or "")
end)

con = mouse.Button1Down:Connect(function()
    if not gui then
        con:Disconnect()
        return
    end
    if not ctrltp then
        return
    end

    local to = mouse.Hit.Position + v3(0, 5, 0)
    to = cf(to, to + v3(-1, 0, -1) * ws.CurrentCamera.CFrame.LookVector)

    if flycf then
        flycf = to
        return
    end

    local c = lp.Character
    if not (c and c.Parent) then
        return
    end
    local hrp = gp(c, "HumanoidRootPart", "BasePart") or gp(c, "Torso", "BasePart") or gp(c, "UpperTorso", "BasePart") or gp(c, "Head", "BasePart") or c:FindFirstChildWhichIsA("BasePart")
    if hrp then
        weldtp(hrp, to)
    end
end)
btn = makecharbutton("创建幽灵")
btn.MouseButton1Click:Connect(function()
    Transparency = true
    NoClip = false

    Player = game:GetService("Players").LocalPlayer

    if not GhostCreated then
        RealCharacter = Player.Character or Player.CharacterAdded:wait(0.1)
        IsInvisible = false
        CanInvis = true

        if not Part or not Part.Parent then
            Part = Instance.new("Part", workspace)
            Part.Anchored = true
            Part.Size = Vector3.new(200, 1, 200)
            Part.CFrame = CFrame.new(0, -500, 0)
            Part.CanCollide = true
        end

        RealCharacter.Archivable = true
        FakeCharacter = RealCharacter:Clone()
        FakeCharacter.Parent = workspace
        FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)

        for i, v in pairs(RealCharacter:GetChildren()) do
            if v:IsA("LocalScript") then
                local clone = v:Clone()
                clone.Disabled = true
                clone.Parent = FakeCharacter
            end
        end
        if Transparency then
            for i, v in pairs(FakeCharacter:GetDescendants()) do
                if v:IsA("BasePart") then
                    v.Transparency = 0.7
                end
            end
        end

        PseudoAnchor = FakeCharacter.HumanoidRootPart

        if not EventsBound then
            EventsBound = true

            game:GetService "RunService".RenderStepped:Connect(function()
                if PseudoAnchor ~= nil and Part and Part.Parent then
                    PseudoAnchor.CFrame = Part.CFrame * CFrame.new(0, 2, 0)
                end
                if NoClip and FakeCharacter and FakeCharacter:FindFirstChild("Humanoid") then
                    FakeCharacter.Humanoid:ChangeState(11)
                end
            end)

            Player.CharacterAppearanceLoaded:Connect(function()
                if GhostCreated then
                    RealCharacter = Player.Character
                    CanInvis = true
                    IsInvisible = false

                    if FakeCharacter and FakeCharacter.Parent then
                        FakeCharacter:Destroy()
                    end

                    RealCharacter.Archivable = true
                    FakeCharacter = RealCharacter:Clone()
                    FakeCharacter.Parent = workspace
                    FakeCharacter.HumanoidRootPart.CFrame = Part.CFrame * CFrame.new(0, 5, 0)

                    for i, v in pairs(RealCharacter:GetChildren()) do
                        if v:IsA("LocalScript") then
                            local clone = v:Clone()
                            clone.Disabled = true
                            clone.Parent = FakeCharacter
                        end
                    end
                    if Transparency then
                        for i, v in pairs(FakeCharacter:GetDescendants()) do
                            if v:IsA("BasePart") then
                                v.Transparency = 0.7
                            end
                        end
                    end

                    PseudoAnchor = FakeCharacter.HumanoidRootPart
                    btn.Text = "幽灵模式"

                    RealCharacter.Humanoid.Died:Connect(function()
                        if FakeCharacter and FakeCharacter.Parent then
                            FakeCharacter:Destroy()
                        end
                        GhostCreated = false
                        btn.Text = "创建幽灵"
                    end)
                end
            end)
        end

        RealCharacter.Humanoid.Died:Connect(function()
            if FakeCharacter and FakeCharacter.Parent then
                FakeCharacter:Destroy()
            end
            GhostCreated = false
            btn.Text = "创建幽灵"
        end)

        GhostCreated = true
        btn.Text = "幽灵模式"

        local Sound = Instance.new("Sound", game:GetService("SoundService"))
        Sound.SoundId = "rbxassetid://232127604"
        Sound:Play()
        game:GetService("StarterGui"):SetCore("SendNotification", {
            ["Title"] = "Opu提示",
            ["Text"] = "幽灵体已创建！点击按钮切换幽灵模式，无需重复按！",
            ["Duration"] = 10,
            ["Button1"] = "好"
        })

    else
        if CanInvis and RealCharacter and FakeCharacter
            and RealCharacter:FindFirstChild("HumanoidRootPart")
            and FakeCharacter:FindFirstChild("HumanoidRootPart") then

            if IsInvisible == false then
                local StoredCF = RealCharacter.HumanoidRootPart.CFrame
                RealCharacter.HumanoidRootPart.CFrame = FakeCharacter.HumanoidRootPart.CFrame
                FakeCharacter.HumanoidRootPart.CFrame = StoredCF
                RealCharacter.Humanoid:UnequipTools()
                Player.Character = FakeCharacter
                workspace.CurrentCamera.CameraSubject = FakeCharacter.Humanoid
                PseudoAnchor = RealCharacter.HumanoidRootPart
                for i, v in pairs(FakeCharacter:GetChildren()) do
                    if v:IsA("LocalScript") then
                        v.Disabled = false
                    end
                end
                IsInvisible = true
                btn.Text = "幽灵模式 ✓"
            else
                local StoredCF = FakeCharacter.HumanoidRootPart.CFrame
                FakeCharacter.HumanoidRootPart.CFrame = RealCharacter.HumanoidRootPart.CFrame
                RealCharacter.HumanoidRootPart.CFrame = StoredCF
                FakeCharacter.Humanoid:UnequipTools()
                Player.Character = RealCharacter
                workspace.CurrentCamera.CameraSubject = RealCharacter.Humanoid
                PseudoAnchor = FakeCharacter.HumanoidRootPart
                for i, v in pairs(FakeCharacter:GetChildren()) do
                    if v:IsA("LocalScript") then
                        v.Disabled = true
                    end
                end
                IsInvisible = false
                btn.Text = "幽灵模式"
            end
        end
    end
end)
makecharbutton("绕过高级动作").MouseButton1Click:Connect(function()
    while true do
        task.wait(1)
        pcall(function()
            local gui = game:GetService("Players").LocalPlayer.PlayerGui
            local scroll = gui:FindFirstChild("Emotes") and gui.Emotes:FindFirstChild("Frame") and gui.Emotes.Frame:FindFirstChild("ScrollingFrame")
            if scroll then
                for _, v in pairs(scroll:GetDescendants()) do
                    if v.Name == "Locked" then
                        v.Visible = false
                    end
                end
            end
        end)
    end
end)
makecharbutton("清除多余障碍（按一次就行)").MouseButton1Click:Connect(function()
    game:GetService("Workspace").InviteSigns:Destroy()
    game:GetService("Workspace").Game.Props["Trash Bag"]:Destroy()
    game:GetService("Workspace").Game.Props.Dumpster:Destroy()
    game:GetService("Workspace").Game.Props["Traffic Cone"]:Destroy()
    game:GetService("Workspace").Game.Props["Wire Fence"]:Destroy()
    game:GetService("Workspace").Game.Props["Wood Crate"]:Destroy()
    game:GetService("Workspace").Game.Props.Hydrant:Destroy()
    game:GetService("Workspace").Game.Props["Street Light"]:Destroy()
    game:GetService("Workspace").Game.Props["Power Line Pole"]:Destroy()
    game:GetService("Workspace").Game.Props["Wood Fence"]:Destroy()
    game:GetService("Workspace").Game.Props.BusStop:Destroy()
    game:GetService("Workspace").Game.Props.Roadblock:Destroy()
    game:GetService("Workspace").Game.Props.Bollard:Destroy()
    game:GetService("Workspace").Game.Props.Light:Destroy()
    game:GetService("Workspace").Game.Props.Roadblock:Destroy()
    game:GetService("Workspace").Game.Props.Glass:Destroy()
    game:GetService("Workspace").Game.Props.Bench:Destroy()
    game:GetService("Workspace").Game.Props["Trash Bin"]:Destroy()
    game:GetService("Workspace").Game.Props.Bollard:Destroy()
    game:GetService("Workspace").Game.Props["Office Chair"]:Destroy()
    game:GetService("Workspace").Game.Props.Table:Destroy()
    game:GetService("Workspace").BankRobbery.BankWalls:Destroy()
    game:GetService("Workspace").BankRobbery.AlarmLightModel:Destroy()
    game:GetService("Workspace").BankRobbery.AlarmLights:Destroy()
end)
makecharbutton("放置梯子（仅自己可见）").MouseButton1Click:Connect(function()
    local Players = game:GetService("Players")

    local function generatePartAboveHead(player)
        local character = player.Character
        if character then
            local head = character:FindFirstChild("Head")
            if head then
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 20, 0.5)
                part.Position = head.Position + Vector3.new(2.1, 5, 1)
                part.Anchored = true
                part.Parent = workspace
                part.Material = "Metal"
                part.Color = Color3.new(0,0,0)
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 20, 0.5)
                part.Position = head.Position + Vector3.new(2.1, 5, -1)
                part.Anchored = true
                part.Parent = workspace
                part.Material = "Metal"
                part.Color = Color3.new(0,0,0)
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, -3, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Material = "Wood"
                part.Color = Color3.new(0.427,0.282,0.176)
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, -1.5, 0)
                part.Anchored = true
                part.Parent = workspace            
                part.Material = "Wood"
                part.Color = Color3.new(0.427,0.282,0.176)
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 0, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Material = "Wood"
                part.Color = Color3.new(0.427,0.282,0.176)
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 1.5, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Material = "Wood"
                part.Color = Color3.new(0.427,0.282,0.176)
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 3, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 4.5, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 6, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 7.5, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 9, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 10.5, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 12, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
                local part = Instance.new("Part")
                part.Size = Vector3.new(0.5, 0.5, 4)
                part.Position = head.Position + Vector3.new(2, 13.5, 0)
                part.Anchored = true
                part.Parent = workspace
                part.Color = Color3.new(0.427,0.282,0.176)
                part.Material = "Wood"
            end
        end
    end

    generatePartAboveHead(Players.LocalPlayer)
end)
local tpframe = makeFrame(scrollingFrame, "定点传送", Color3.fromRGB(10, 10, 10))
local tpscroll = tpframe.ScrollingFrame
local function maketpbutton(buttontext)
    local button = Instance.new("TextButton")
    button.Name = "tpscroll"
    button.Parent = tpscroll
    button.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    button.BorderSizePixel = 0
    button.Size = UDim2.new(1, -10, 0, 20)
    button.Font = Enum.Font.SourceSans
    button.Text = buttontext
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.TextSize = 15.000
    return button
end
local tp = maketpbutton("传送银行>金库")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(1055.94153, 15.11950874, -344.58374)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送珠宝店>后门")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(1719.02637, 14.2831011, -714.293091)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送黑市")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(690.499, -18.949, -115.453)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送沙滩>码头")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(998.4656372070312, 15, 395.9789733886719)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送武器店>撬锁")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(660.5284423828125, 6.4081127643585205, -716.489990234375)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送警局>M4A1")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(603.4676513671875,28.662811279296875,-922.0442504882812)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送警局>蓝卡枪械库")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(594.4676513671875,27.662811279296875,-900.0442504882812)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送军事基地>军甲")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(563.4422607421875,28.502071380615234,-1472.780517578125)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送军事基地>红卡军械库")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(385.4676513671875,20.66281127929687,-1360.0442504882812)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送武器店>工作台")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(652.0,2.502071380615234,-571.0)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送咖啡店")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(1354.655, 5.7, -330.364)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送武士刀")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(175.191, 13.937, -132.69)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送钟塔>短喷")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(1179.98523,40,-436.812683)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送沙漠之鹰")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(363.341461, 27.0798492, -259.681396)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送下水道>射线枪")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(148.685471, -90, -529.280945)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送医院>担架")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(1180.700244140625,8.37138366699219,-934.25859375)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送AUG")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(1170.500244140625,48.37138366699219,-772.55859375)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送幽灵空间(需创建幽灵体)")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(0,-499,0)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送军事基地>加特林")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(364.97076416015625, 0.764974117279053, -1447.3302001953125)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送电玩厅")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(835.8676513671875,4.662811279296875,-910.0442504882812)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送防爆空间")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(1345.655,26.7, -327.364)
    tp2.CFrame = tp3
end)
local tp = maketpbutton("传送虚空")
tp.MouseButton1Click:Connect(function()
    local tp1 = game:GetService("Players")
    local tp2 = tp1.LocalPlayer.Character.HumanoidRootPart
    local tp3 = CFrame.new(-9999999999,-599,-9999999999)
    tp2.CFrame = tp3
end)

local utilframe = makeFrame(scrollingFrame, "自动化", Color3.fromRGB(10, 10, 10))
local utilscroll = utilframe.ScrollingFrame

local function makeutilbutton(buttontext)
    local button = Instance.new("TextButton")
    button.Name = "utilButton"
    button.Parent = utilscroll
    button.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    button.BorderSizePixel = 0
    button.Size = UDim2.new(1, -10, 0, 20)
    button.Font = Enum.Font.SourceSans
    button.Text = buttontext
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.TextSize = 15.000
    return button
end
local autobankb = makeutilbutton("自动银行")
local autobankbt = false
autobankb.MouseButton1Click:Connect(function()
    if autobankbt == false then
        autobankbt = true
        autobankb.Text = "自动银行 ✓"
    else
        autobankbt = false
        autobankb.Text = "自动银行"
    end
    while autobankbt == true do
    wait(0.3)
    if autobankbt == true then
        local BankDoor = game:GetService("Workspace").BankRobbery.VaultDoor
        local BankCashs = game:GetService("Workspace").BankRobbery.BankCash
        local epoh2 = game:GetService("Players")
        local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
        if BankDoor.Door.Attachment.ProximityPrompt.Enabled == true then
            BankDoor.Door.Attachment.ProximityPrompt.HoldDuration = 0
            BankDoor.Door.Attachment.ProximityPrompt.MaxActivationDistance = 20
            local epoh1 = CFrame.new(1071.955810546875, 9, -343.80816650390625)
            epoh3.CFrame = epoh1
            wait(0.3)
            BankDoor.Door.Attachment.ProximityPrompt:InputHoldBegin()
            wait(0.3)
            BankDoor.Door.Attachment.ProximityPrompt:InputHoldEnd()
        else
            if BankCashs.Cash:FindFirstChild("Bundle") then
                local epoh1 = CFrame.new(1055.94153, 15.11950874, -344.58374)
                epoh3.CFrame = epoh1
                BankCashs.Main.Attachment.ProximityPrompt.MaxActivationDistance = 20
                BankCashs.Main.Attachment.ProximityPrompt:InputHoldBegin()
            end 
            if not BankCashs.Cash:FindFirstChild("Bundle") then
                BankCashs.Main.Attachment.ProximityPrompt:InputHoldEnd()
            end
        end
    end
end
end)
local automoneyprint = makeutilbutton("自动捡印钞机")
local automoneyprintt = false
automoneyprint.MouseButton1Click:Connect(function()
    if automoneyprintt == false then
        automoneyprintt = true
        automoneyprint.Text = "自动捡印钞机 ✓"
    else
        automoneyprintt = false
        automoneyprint.Text = "自动捡印钞机"
    end
    while automoneyprintt == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Money Printer" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

local autoore = makeutilbutton("自动捡稀有珠宝")
local autooret = false
autoore.MouseButton1Click:Connect(function()
    autooret = not autooret
    autoore.Text = autooret and "自动捡稀有珠宝 ✓" or "自动捡稀有珠宝"
    if autooret then
        task.spawn(function()
            local Players = game:GetService("Players")
            local player = Players.LocalPlayer
            local itemsFolder = workspace:WaitForChild("Game"):WaitForChild("Entities"):WaitForChild("ItemPickup")
            local rareNames = {
                ["Diamond Ring"] = true,
                ["Diamond"] = true,
                ["Void Gem"] = true,
                ["Dark Matter Gem"] = true,
                ["Rollie"] = true,
            }
            while autooret do
                local character = player.Character
                local hrp = character and character:FindFirstChild("HumanoidRootPart")
                if not hrp then
                    task.wait(0.5)
                    continue
                end
                for _, item in ipairs(itemsFolder:GetChildren()) do
                    if not autooret then break end
                    for _, part in ipairs(item:GetChildren()) do
                        if part:IsA("BasePart") then
                            local prompt = part:FindFirstChildOfClass("ProximityPrompt")
                            if prompt and rareNames[prompt.ObjectText] then
                                local dist = (hrp.Position - part.Position).Magnitude
                                if dist <= 100 then
                                    hrp.CFrame = part.CFrame * CFrame.new(0, 2, 0)
                                    task.wait(0.1)
                                    prompt:InputHoldBegin()
                                    prompt:InputHoldEnd()
                                end
                                break
                            end
                        end
                    end
                end
                task.wait(0.1)
            end
        end)
    end
end)

local autoMoneyBtn = makeutilbutton("瞬移最少1K金钱")
local autoMoneyOn = false
autoMoneyBtn.MouseButton1Click:Connect(function()
    autoMoneyOn = not autoMoneyOn
    autoMoneyBtn.Text = autoMoneyOn and "瞬移最少1K金钱 ✓" or "瞬移最少1K金钱"
    if autoMoneyOn then
        task.spawn(function()
            local Players = game:GetService("Players")
            local player = Players.LocalPlayer
            local cashFolder = workspace:WaitForChild("Game"):WaitForChild("Entities"):WaitForChild("CashBundle")
            while autoMoneyOn do
                local character = player.Character
                local hrp = character and character:FindFirstChild("HumanoidRootPart")
                if not hrp then
                    task.wait(0.5)
                    continue
                end
                local foundCash = false
                local originalCFrame = hrp.CFrame
                for _, cashBundle in ipairs(cashFolder:GetChildren()) do
                    if not autoMoneyOn then break end
                    if cashBundle:IsA("Model") then
                        local intValue = cashBundle:FindFirstChildWhichIsA("IntValue")
                        if intValue and intValue.Value >= 1000 then
                            foundCash = true
                            hrp.CFrame = cashBundle:GetPivot()
                            task.wait(0.3)
                            hrp.CFrame = originalCFrame
                            task.wait(0.3)
                        end
                    end
                end
                if not foundCash then
                    task.wait(1)
                else
                    task.wait(0.3)
                end
            end
        end)
    end
end)

local automgoldgun = makeutilbutton("自动捡黄金枪")
local automgoldgunt = false
automgoldgun.MouseButton1Click:Connect(function()
    if automgoldgunt == false then
        automgoldgunt = true
        automgoldgun.Text = "自动捡黄金枪 ✓"
    else
        automgoldgunt = false
        automgoldgun.Text = "自动捡黄金枪"
    end
    while automgoldgunt == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Gold AK-47" or e.ObjectText == "Gold Deagle" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            wait(0.1)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

local autoairdrop123 = makeutilbutton("自动捡圣诞、空投、空袭")
local autoairdrop123t = false
autoairdrop123.MouseButton1Click:Connect(function()
    if autoairdrop123t == false then
        autoairdrop123t = true
        autoairdrop123.Text = "自动捡圣诞、空投、空袭 ✓"
    else
        autoairdrop123t = false
        autoairdrop123.Text = "自动捡圣诞、空投、空袭"
    end
    while autoairdrop123t == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Airdrop Marker" or e.ObjectText == "Airstrike Marker" or e.ObjectText == "Santa Signal" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            wait(0.1)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

local autoairdrop1231 = makeutilbutton("自动捡精致零件")
local autoairdrop1231t = false
autoairdrop1231.MouseButton1Click:Connect(function()
    if autoairdrop1231t == false then
        autoairdrop1231t = true
        autoairdrop1231.Text = "自动捡精致零件 ✓"
    else
        autoairdrop1231t = false
        autoairdrop1231.Text = "自动捡精致零件"
    end
    while autoairdrop1231t == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Electronics" or e.ObjectText == "Weapon Parts" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            wait(0.1)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

local autoPresent = makeutilbutton("自动捡大、中、小礼物盒")
local autoPresentt = false
autoPresent.MouseButton1Click:Connect(function()
    if autoPresentt == false then
        autoPresentt = true
        autoPresent.Text = "自动捡大、中、小礼物盒 ✓"
    else
        autoPresentt = false
        autoPresent.Text = "自动捡大、中、小礼物盒"
    end
    while autoPresentt == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Large Present" or e.ObjectText == "Medium Present" or e.ObjectText == "Small Present" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            wait(0.1)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

local autoredcrad = makeutilbutton("自动捡红卡")
local autoredcradt = false
autoredcrad.MouseButton1Click:Connect(function()
    if autoredcradt == false then
        autoredcradt = true
        autoredcrad.Text = "自动捡红卡 ✓"
    else
        autoredcradt = false
        autoredcrad.Text = "自动捡红卡"
    end
    while autoredcradt == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Military Armory Keycard" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            wait(0.1)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

local autopickballoon = makeutilbutton("自动捡气球、玫瑰")
local autopickballoont = false
autopickballoon.MouseButton1Click:Connect(function()
    if autopickballoont == false then
        autopickballoont = true
        autopickballoon.Text = "自动捡气球、玫瑰 ✓"
    else
        autopickballoont = false
        autopickballoon.Text = "自动捡气球、玫瑰"
    end
    while autopickballoont == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Gold Clover Balloon" or e.ObjectText == "Black Rose" or e.ObjectText == "Golden Rose" or e.ObjectText == "Bat Balloon" or e.ObjectText == "Bunny Balloon" or e.ObjectText == "Ghost Balloon" or e.ObjectText == "Heart Balloon" or e.ObjectText == "Clover Balloon" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            wait(0.1)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

local autopickbluecandycane = makeutilbutton("自动捡双颜色糖果棒")
local autopickbluecandycanet = false
autopickbluecandycane.MouseButton1Click:Connect(function()
    if autopickbluecandycanet == false then
        autopickbluecandycanet = true
        autopickbluecandycane.Text = "自动捡双颜色糖果棒 ✓"
    else
        autopickbluecandycanet = false
        autopickbluecandycane.Text = "自动双颜色糖果棒"
    end
    while autopickbluecandycanet == true do
    wait(0.1)
    local epoh2 = game:GetService("Players")
    local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
    for i,l in pairs(game:GetService("Workspace").Game.Entities.ItemPickup:GetChildren()) do
        for i,v in pairs(l:GetChildren()) do
            if v.ClassName == "MeshPart" or "Part" then
                for i,e in pairs(v:GetChildren()) do
                    if e.ClassName == "ProximityPrompt" then
                        if e.ObjectText == "Candy Cane" or e.ObjectText == "Blue Candy Cane" then
                            local epoh1 = v.CFrame
                            epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
                            wait(0.1)
                            e:InputHoldBegin()
                            e:InputHoldEnd()
                        end
                    end
                end       
            end
        end
    end
end
end)

makeutilbutton("瞬移金质保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local bankDoor = workspace.BankRobbery.VaultDoor
    local doorPrompt = bankDoor and bankDoor:FindFirstChild("Door") and bankDoor.Door:FindFirstChild("Attachment") and bankDoor.Door.Attachment:FindFirstChild("ProximityPrompt")

    if doorPrompt and doorPrompt.Enabled then
        hrp.CFrame = CFrame.new(1078.0809326171875, 6.246849060058594, -343.95758056640625)
        task.wait(0.5)
        doorPrompt:InputHoldBegin()
        doorPrompt:InputHoldEnd()
    else
        local safeFolder = workspace.Game.Entities.GoldJewelSafe
        local safe = safeFolder:FindFirstChild("GoldJewelSafe")
        if safe then
            local door = safe:FindFirstChild("Door")
            if door then
                local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
                if mesh then
                    local att = mesh:FindFirstChild("Attachment")
                    if att then
                        local prompt = att:FindFirstChild("ProximityPrompt")
                        if prompt then
                            hrp.CFrame = mesh.CFrame
                            task.wait(0.1)
                            local safeModel = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
                            if safeModel and safeModel:IsA("Model") then
                                safeModel.Name = "Opened"
                            end
                        end
                    end
                end
            end
        end
    end
end)
makeutilbutton("瞬移黑色保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local bankDoor = workspace.BankRobbery.VaultDoor
    local doorPrompt = bankDoor and bankDoor:FindFirstChild("Door") and bankDoor.Door:FindFirstChild("Attachment") and bankDoor.Door.Attachment:FindFirstChild("ProximityPrompt")

    if doorPrompt and doorPrompt.Enabled then
        hrp.CFrame = CFrame.new(1078.0809326171875, 6.246849060058594, -343.95758056640625)
        task.wait(0.5)
        doorPrompt:InputHoldBegin()
        doorPrompt:InputHoldEnd()
    else
        local safeFolder = workspace.Game.Entities.JewelSafe
        local safe = safeFolder:FindFirstChild("JewelSafe")
        if safe then
            local door = safe:FindFirstChild("Door")
            if door then
                local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
                if mesh then
                    local att = mesh:FindFirstChild("Attachment")
                    if att then
                        local prompt = att:FindFirstChild("ProximityPrompt")
                        if prompt then
                            hrp.CFrame = mesh.CFrame
                            task.wait(0.1)
                            local safeModel = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
                            if safeModel and safeModel:IsA("Model") then
                                safeModel.Name = "Opened"
                            end
                        end
                    end
                end
            end
        end
    end
end)
makeutilbutton("瞬移普通宝箱").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local chestFolder = workspace.Game.Entities.SmallChest
    local smallChest = chestFolder:FindFirstChild("SmallChest")
    if not smallChest then return end

    local lock = smallChest:FindFirstChild("Lock")
    if not lock then return end

    local mesh = lock:FindFirstChild("Meshes/untitled_chest.002_Material.009 (4)")
    if not mesh then return end

    local att = mesh:FindFirstChild("Attachment")
    if not att then return end

    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end

    hrp.CFrame = mesh.CFrame
    task.wait(0.1)

    local chestModel = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if chestModel and chestModel:IsA("Model") then
        chestModel.Name = "Opened"
    end
end)
makeutilbutton("瞬移大型宝箱").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local chestFolder = workspace.Game.Entities.LargeChest
    local largeChest = chestFolder:FindFirstChild("LargeChest")
    if not largeChest then return end

    local lock = largeChest:FindFirstChild("Lock")
    if not lock then return end

    local mesh = lock:FindFirstChild("Meshes/untitled_chest.002_Material.009 (4)")
    if not mesh then return end

    local att = mesh:FindFirstChild("Attachment")
    if not att then return end

    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end

    hrp.CFrame = mesh.CFrame
    task.wait(0.1)

    local chestModel = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if chestModel and chestModel:IsA("Model") then
        chestModel.Name = "Opened"
    end
end)
makeutilbutton("瞬移合金保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local safe = workspace.Game.Entities.SmallSafe:FindFirstChild("SmallSafe")
    if not safe then return end

    local door = safe:FindFirstChild("Door")
    if not door then return end

    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end

    local att = mesh:FindFirstChild("Attachment")
    if not att then return end

    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end

    hrp.CFrame = mesh.CFrame
    task.wait(0.1)

    local smallSafeModel = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if smallSafeModel and smallSafeModel:IsA("Model") then
        smallSafeModel.Name = "Opened"
    end
end)
makeutilbutton("瞬移石英保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local safe = workspace.Game.Entities.MediumSafe:FindFirstChild("MediumSafe")
    if not safe then return end

    local door = safe:FindFirstChild("Door")
    if not door then return end

    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end

    local att = mesh:FindFirstChild("Attachment")
    if not att then return end

    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end

    hrp.CFrame = mesh.CFrame
    task.wait(0.1)

    local mediumSafeModel = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if mediumSafeModel and mediumSafeModel:IsA("Model") then
        mediumSafeModel.Name = "Opened"
    end
end)
makeutilbutton("瞬移钛金保险").MouseButton1Click:Connect(function()
    local player = game:GetService("Players").LocalPlayer
    local char = player.Character
    if not char then return end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local safe = workspace.Game.Entities.LargeSafe:FindFirstChild("LargeSafe")
    if not safe then return end

    local door = safe:FindFirstChild("Door")
    if not door then return end

    local mesh = door:FindFirstChild("Meshes/LargeSafe_Cube.002_Cube.003_None (1)")
    if not mesh then return end

    local att = mesh:FindFirstChild("Attachment")
    if not att then return end

    local prompt = att:FindFirstChild("ProximityPrompt")
    if not prompt then return end

    hrp.CFrame = mesh.CFrame
    task.wait(0.1)

    local largeSafeModel = att.Parent and att.Parent.Parent and att.Parent.Parent.Parent
    if largeSafeModel and largeSafeModel:IsA("Model") then
        largeSafeModel.Name = "Opened"
    end
end)

makeutilbutton("瞬移挖宝藏(需手持藏宝图!)").MouseButton1Click:Connect(function()
    local Debri = game:GetService("Workspace").Game.Local.Debris
    if Debri.TreasureMarker then
        local epoh1 = Debri.TreasureMarker.CFrame
        local epoh2 = game:GetService("Players")
        local epoh3 = epoh2.LocalPlayer.Character.HumanoidRootPart
        epoh3.CFrame = epoh1 * CFrame.new(0, 2, 0)
        Debri.TreasureMarker.ProximityPrompt.HoldDuration = 0
        Debri.TreasureMarker.ProximityPrompt.MaxActivationDistance = 40
        wait(0.1)
        Debri.TreasureMarker.ProximityPrompt:InputHoldBegin()
        Debri.TreasureMarker.ProximityPrompt:InputHoldEnd()
    end  
end)

local cbringframe = makeFrame(scrollingFrame, "状态&受击框", Color3.fromRGB(10, 10, 10))
local cbringscroll = cbringframe.ScrollingFrame

local cbring = {}

local togglecbring = nil

local function makecbringframe(name)
    local plrcbringf = Instance.new("Frame")
    local uncbringbtn = Instance.new("TextButton")
    local cbringplrname = Instance.new("TextBox")
    plrcbringf.Name = name
    plrcbringf.BackgroundColor3 = Color3.fromRGB(106, 106, 106)
    plrcbringf.BorderSizePixel = 0
    plrcbringf.Size = UDim2.new(1, -10, 0, 30)
    plrcbringf.Parent = cbringscroll
    uncbringbtn.Name = "removeposbutton"
    uncbringbtn.Parent = plrcbringf
    uncbringbtn.BackgroundColor3 = Color3.fromRGB(47, 47, 47)
    uncbringbtn.BorderSizePixel = 0
    uncbringbtn.Position = UDim2.new(1, -25, 0, 5)
    uncbringbtn.Size = UDim2.new(0, 20, 1, -10)
    uncbringbtn.Font = Enum.Font.SourceSans
    uncbringbtn.Text = "×"
    uncbringbtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    uncbringbtn.TextSize = 16.000
    cbringplrname.Parent = plrcbringf
    cbringplrname.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
    cbringplrname.BackgroundTransparency = 1.000
    cbringplrname.BorderSizePixel = 0
    cbringplrname.Position = UDim2.new(0, 5, 0, 5)
    cbringplrname.Size = UDim2.new(1, -80, 1, -10)
    cbringplrname.Font = Enum.Font.SourceSans
    cbringplrname.Text = name
    cbringplrname.TextColor3 = Color3.fromRGB(255, 255, 255)
    cbringplrname.TextSize = 25.000
    cbringplrname.TextXAlignment = Enum.TextXAlignment.Left
    uncbringbtn.MouseButton1Click:Connect(function()
        togglecbring(name)
    end)
    return plrcbringf
end

togglecbring = function(name)
    local frame = gp(cbringscroll, name, "Frame")
    if frame then
        pcall(function()
            table.remove(cbring, table.find(cbring, name))
        end)
        frame:Destroy()
        notify("删除了-玩家：" .. name .. " 的受击框")
    else
        table.insert(cbring, name)
        makecbringframe(name)
        notify("添加了-玩家：" .. name .. " 的受击框")
    end
end

cbringb.MouseButton1Click:Connect(function()
    togglecbring(currentplayer.Name)
end)

local cbringallbtn = Instance.new("TextButton")
cbringallbtn.Name = "cbringallbtn"
cbringallbtn.Parent = cbringframe.framelabel
cbringallbtn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
cbringallbtn.BorderSizePixel = 0
cbringallbtn.Position = UDim2.new(1, -57, 0, 2)
cbringallbtn.Size = UDim2.new(0, 55, 1, -4)
cbringallbtn.Font = Enum.Font.SourceSans
cbringallbtn.Text = "添加所有"
cbringallbtn.TextColor3 = Color3.fromRGB(255, 255, 255)
cbringallbtn.TextSize = 14.000
cbringallbtn.MouseButton1Click:Connect(function()
    for i, v in pairs(plrs:GetPlayers()) do
        if (v ~= lp) and v and v.Parent and (not table.find(cbring, v.Name)) then
            togglecbring(v.Name)
        end
    end
end)

local clearallbtn = Instance.new("TextButton")
clearallbtn.Name = "clearallbtn"
clearallbtn.Parent = cbringframe.framelabel
clearallbtn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
clearallbtn.BorderSizePixel = 0
clearallbtn.Position = UDim2.new(1, -118, 0, 2)
clearallbtn.Size = UDim2.new(0, 55, 1, -4)
clearallbtn.Font = Enum.Font.SourceSans
clearallbtn.Text = "清空所有"
clearallbtn.TextColor3 = Color3.fromRGB(255, 255, 255)
clearallbtn.TextSize = 14

clearallbtn.MouseButton1Click:Connect(function()
    for _, name in ipairs(table.clone(cbring)) do
        togglecbring(name)
    end
    table.clear(cbring)
end)
spawn(function()
    while gui do
        local waited = false
        local lpc = lp.Character
        if lpc and lpc.Parent then
            local part0 = gp(lpc, "Torso", "BasePart") or gp(lpc, "HumanoidRootPart", "BasePart") or gp(lpc, "Head", "BasePart") or lpc:FindFirstChildWhichIsA("BasePart")
            if part0 then
                for i, v in pairs(plrs:GetPlayers()) do
                    if v ~= lp then
                        local c = v.Character
                        if c and c.Parent then
                            if table.find(cbring, v.Name) then
                                local part1 = gp(c, part0.Name, "BasePart") or gp(c, "Torso", "BasePart") or gp(c, "HumanoidRootPart", "BasePart") or gp(c, "Head", "BasePart") or c:FindFirstChildWhichIsA("BasePart")
                                if part1 then
                                    local p1cf = part0.CFrame
                                    waited = true
                                    weldtp(part1, p1cf + p1cf.LookVector * 2)
                                end
                            end
                        end
                    end
                end
            end
        end
        if not waited then
            stepped:wait(0.1)
        end
    end
end)

local con = nil
con = stepped:Connect(function()
    if not gui then
        con:Disconnect()
        return
    end
    local lpc = lp.Character
    if noclip and lpc and lpc.Parent then
        for i, v in pairs(lpc:GetDescendants()) do
            if v:IsA("BasePart") then
                v.CanCollide = false
            end
        end
    end
end)

local con0, con1 = nil, nil
local function antiflingF()
    if not gui then
        con0:Disconnect()
        con1:Disconnect()
        return
    end
    if antifling then
        for i, v in pairs(plrs:GetPlayers()) do
            if v ~= lp then
                local c = v.Character
                if c and c.Parent then
                    for i1, v1 in pairs(c:GetDescendants()) do
                        if v1:IsA("BasePart") then
                            v1.CanCollide = false
                            v1.Velocity = v3_0
                            v1.RotVelocity = v3_0
                        end
                    end
                end
            end
        end
    end
end
con0 = stepped:Connect(antiflingF)
con1 = heartbeat:Connect(antiflingF)

gui.Enabled = true
renderstepped:wait(0.1)
playercframe.Visible = false

game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChatChannelParentFrame.Visible = true
game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChatChannelParentFrame.Position = UDim2.new(0, 0, 0, 40)
game:GetService("Players").LocalPlayer.PlayerGui.Money.Container.premium.Shadow.Visible = false
game:GetService("Players").LocalPlayer.PlayerGui.Money.Container["2x cash"].Shadow.Visible = false
game:GetService("Players").LocalPlayer.PlayerGui.Money.Container.premium.Visible = true
game:GetService("Players").LocalPlayer.PlayerGui.Money.Container.premium.TextLabel.Text = "Opu User"
game:GetService("Players").LocalPlayer.PlayerGui.Money.Container["2x cash"].Visible = true
game:GetService("Players").LocalPlayer.PlayerGui.Money.Container["2x cash"].TextLabel.Text = "Opu By Smk"
game:GetService("Workspace").BlackMarket.Dealer.Dealer.ProximityPrompt.HoldDuration = 0
game:GetService("Workspace").BlackMarket.BlackMarketBillboard.TopLabel.Text = "黑市"
game:GetService("Workspace").BlackMarket.BlackMarketBillboard.BottomLabel.Text = "向黑商出售物品以获得钱!"
game:GetService("Workspace").OhioSign.Screen.SurfaceGui.Frame.Population.Text = "Opu User"

local Teams = game:GetService("Teams")
local newTeam = Instance.new("Team")
newTeam.Name = "Opu User"
newTeam.Parent = Teams
local player = game:GetService("Players").LocalPlayer
player.Team = newTeam

local UserInputService = game:GetService("UserInputService")
UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if input.KeyCode == Enum.KeyCode.Z then
        game:GetService("Players").LocalPlayer.PlayerGui.Backpack.Holder.Locker.Visible = true
    end
end)

UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if input.KeyCode == Enum.KeyCode.E then
        game:GetService("Workspace").BankRobbery.VaultDoor.Door.Attachment.ProximityPrompt.HoldDuration = 0
        game:GetService("Workspace").BankRobbery.VaultDoor.Door.Attachment.ProximityPrompt.MaxActivationDistance = 20
        game:GetService("Workspace").BankRobbery.BankCash.Main.Attachment.ProximityPrompt.MaxActivationDistance = 20    
    end
end)

UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if input.KeyCode == Enum.KeyCode.E then
        local safe = game:GetService("Workspace").Game.Entities.GoldJewelSafe.GoldJewelSafe
        safe.Door["Meshes/LargeSafe_Cube.002_Cube.003_None (1)"].Attachment.ProximityPrompt.HoldDuration = 0
        safe.Name = "safeopen"  
    end
end)

UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if input.KeyCode == Enum.KeyCode.E then
        local safe2 = game:GetService("Workspace").Game.Entities.JewelSafe.JewelSafe
        safe2.Door["Meshes/LargeSafe_Cube.002_Cube.003_None (1)"].Attachment.ProximityPrompt.HoldDuration = 0
        safe2.Name = "safeopen"
    end
end)

UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if input.KeyCode == Enum.KeyCode.E then
        game:GetService("Workspace").Game.Airdrops.Airdrop.Airdrop.ProximityPrompt.HoldDuration = 0
    end
end)
local function loop1()
        while true do
            wait(0.1)
            local players = game:GetService("Players"):GetPlayers()

            for _, player in pairs(players) do
                local leaderstats = Instance.new("IntValue")
                leaderstats.Name = "leaderstats"
                leaderstats.Value = player.stats.Money.Value

                local Rank = Instance.new("NumberValue")
                Rank.Name = "全服金钱"
                Rank.Value = player.stats.Money.Value

                local Health = Instance.new("NumberValue")
                Health.Name = "血量"
                Health.Value = player.Character.Humanoid.Health

                leaderstats.Parent = player
                Rank.Parent = leaderstats
                Health.Parent = leaderstats
            end
        end
    end

    for i = 1, 20 do

        if game.Workspace.ToSort:FindFirstChild('Tunnel') then
            game.workspace.ToSort.Tunnel:Destroy()
        end
    end
    local road = Instance.new("Part")
    road.Size = Vector3.new(760.364, 1.001, 46.918)
    road.Anchored = true
    road.Archivable = true
    road.Position = Vector3.new(-255.446, -9.808, -350.11)
    road.Parent = workspace
    road.Color = Color3.new(0.223529, 0.223529, 0.223529)
    road.Material = "Concrete"
    local road2 = Instance.new("Part")
    road2.Size = Vector3.new(766.188, 5.496, 16.4)
    road2.Anchored = true
    road2.Archivable = true
    road2.Position = Vector3.new(-252.73, -11.793, -379.689)
    road2.Parent = workspace
    road2.Material = "Concrete"
    road2.Color = Color3.new(0.529412, 0.529412, 0.529412)
    local road3 = Instance.new("Part")
    road3.Size = Vector3.new(563.051, 1.796, 19.772)
    road3.Anchored = true
    road3.Archivable = true
    road3.Position = Vector3.new(-354.694, -9.944, -322.653)
    road3.Parent = workspace
    road3.Material = "Concrete"
    road3.Color = Color3.new(0.529412, 0.529412, 0.529412)
    local road3 = Instance.new("Part")
    road3.Size = Vector3.new(563.051, 1.796, 19.772)
    road3.Anchored = true
    road3.Archivable = true
    road3.Position = Vector3.new(-354.694, -9.944, -322.653)
    road3.Parent = workspace
    road3.Material = "Concrete"
    road3.Color = Color3.new(0.529412, 0.529412, 0.529412)
    local road3 = Instance.new("Part")
    road3.Size = Vector3.new(19.773, 1.796, 239.333)
    road3.Anchored = true
    road3.Archivable = true
    road3.Position = Vector3.new(-83.056, -20.395, -194.468)
    road3.Orientation = Vector3.new(5, 0, 0)
    road3.Parent = workspace
    road3.Material = "Concrete"
    road3.Color = Color3.new(0.529412, 0.529412, 0.529412)
    local road3 = Instance.new("Part")
    road3.Size = Vector3.new(19.773, 1.796, 239.333)
    road3.Anchored = true
    road3.Archivable = true
    road3.Position = Vector3.new(-19.256, -20.395, -194.468)
    road3.Orientation = Vector3.new(5, 0, 0)
    road3.Parent = workspace
    road3.Material = "Concrete"
    road3.Color = Color3.new(0.529412, 0.529412, 0.529412)
    local road3 = Instance.new("Part")
    road3.Size = Vector3.new(179.456, 1.796, 19.772)
    road3.Anchored = true
    road3.Archivable = true
    road3.Position = Vector3.new(60.439, -9.944, -322.653)
    road3.Orientation = Vector3.new(0, 0, 0)
    road3.Parent = workspace
    road3.Material = "Concrete"
    road3.Color = Color3.new(0.529412, 0.529412, 0.529412)
    local road3 = Instance.new("Part")
    road3.Size = Vector3.new(47.792, 1.001, 60.939)
    road3.Anchored = true
    road3.Archivable = true
    road3.Position = Vector3.new(-51.234, -9.808, -343.099)
    road3.Orientation = Vector3.new(0, 0, 0)
    road3.Parent = workspace
    road3.Material = "Concrete"
    road3.Color = Color3.new(0.223529, 0.223529, 0.223529)
    local road3 = Instance.new("Part")
    road3.Size = Vector3.new(47.792, 1.001, 262.574)
    road3.Anchored = true
    road3.Archivable = true
    road3.Position = Vector3.new(-51.234, -21.234, -181.97)
    road3.Orientation = Vector3.new(5, 0, 0)
    road3.Parent = workspace
    road3.Material = "Concrete"
    road3.Color = Color3.new(0.223529, 0.223529, 0.223529)
    local rt = Instance.new("Part")
    rt.Size = Vector3.new(47.792, 1.001, 262.574)
    rt.Anchored = true
    rt.Archivable = true
    rt.Position = Vector3.new(-193.438, 46.016, -490.664)
    rt.Orientation = Vector3.new(25, 0, 0)
    rt.Parent = workspace
    rt.Material = "Concrete"
    rt.Color = Color3.new(0.223529, 0.223529, 0.223529)
    local rt = Instance.new("Part")
    rt.Size = Vector3.new(0.965, 4.432, 262.5)
    rt.Anchored = true
    rt.Archivable = true
    rt.Position = Vector3.new(-216.854, 48.471, -489.503)
    rt.Orientation = Vector3.new(25, 0, 0)
    rt.Parent = workspace
    rt.Material = "Concrete"
    local rt = Instance.new("Part")
    rt.Size = Vector3.new(0.965, 4.432, 262.5)
    rt.Anchored = true
    rt.Archivable = true
    rt.Position = Vector3.new(-170.157, 48.471, -489.503)
    rt.Orientation = Vector3.new(25, 0, 0)
    rt.Parent = workspace
    rt.Material = "Concrete"
    local rt = Instance.new("Part")
    rt.Size = Vector3.new(47.792, 1.001, 92.834)
    rt.Anchored = true
    rt.Archivable = true
    rt.Position = Vector3.new(-193.404, 101.593, -655.732)
    rt.Orientation = Vector3.new(0, 0, 0)
    rt.Parent = workspace
    rt.Material = "Concrete"
    rt.Color = Color3.new(0.223529, 0.223529, 0.223529)
    local rt = Instance.new("Part")
    rt.Size = Vector3.new(1853.465, 1.001, 44.169)
    rt.Anchored = true
    rt.Archivable = true
    rt.Position = Vector3.new(695.76, 254.199, -680.065)
    rt.Orientation = Vector3.new(0, 0, 10)
    rt.Parent = workspace
    rt.Material = "Concrete"
    rt.Color = Color3.new(0.223529, 0.223529, 0.223529)
    local function loop2()
        while true do
            wait(0.1)
            local players = game:GetService("Players")
            for _, player in pairs(players:GetPlayers()) do
                local character = player.Character
                if character then
                    local gta = character:FindFirstChild("grabPrompt")
                    if gta then
                        gta.ClickablePrompt = true
                        gta.MaxActivationDistance = 35
                        gta.RequiresLineOfSight = false
                        gta.HoldDuration = 0
                        gta.ActionText = "请输入文本"
                        local leaderstats = Instance.new("IntValue")
                        leaderstats.Name = "leaderstats"
                        leaderstats.Value = player.stats.Money.Value

                        local Rank = Instance.new("NumberValue")
                        Rank.Name = "全服金钱"
                        Rank.Value = player.stats.Money.Value

                        local Health = Instance.new("NumberValue")
                        Health.Name = "血量"
                        Health.Value = player.Character.Humanoid.Health

                        leaderstats.Parent = player
                        Rank.Parent = leaderstats
                        Health.Parent = leaderstats
                    end
                end
            end

        end
    end
    local thread1 = coroutine.create(loop1)
    local thread2 = coroutine.create(loop2)
    coroutine.resume(thread1)
    coroutine.resume(thread2)
