# the-sparrow
간단해요. 이걸 스크립트 실행기에 넣으면 되요.
간단하죠?

```
    --CLIENT SIDED ONLY, THANK U :)


    local Lighting = game:GetService("Lighting")
    local Terrain = game:GetService('Workspace'):WaitForChild("Terrain")
    local Weather = {}

    Weather.ClockTime = {
        Night = function() 
    Lighting.Ambient = Color3.new(0.258823, 0.411764, 0.407843)
        Lighting.OutdoorAmbient = Color3.fromRGB(120, 120, 120)
    Lighting.GeographicLatitude = 17
    Lighting.Brightness = 5
    Lighting.ClockTime = 0
    Weather:Atmosphere({
    Color = Color3.fromRGB(50, 50, 50),
    Decay = Color3.fromRGB(50, 50, 50),
    Glare = 5,
    Haze = 1,
    Density = 0.55,
    Offset = 1
    })
    end,
    Day = function() 
    Lighting.Ambient = Color3.fromRGB(128, 128, 128)
        Lighting.OutdoorAmbient = Color3.fromRGB(130, 130, 130)
    Lighting.GeographicLatitude = 17
    Lighting.Brightness = 3
    Lighting.ClockTime = 1
    end
    }
    function Weather:ReplaceMaterial(s, e, c)
    print("looping")
    for i,v in pairs(workspace.Level.Geometry:GetDescendants()) do
    if v:IsA("BasePart") then if v.Material == s then
    v.Material =e
    v.BrickColor = c
    end
        end
        end
        for i,v in pairs(workspace.Level.Exterior:GetDescendants()) do
    if v:IsA("BasePart") then if v.Material == s then
    v.Material =e
    v.BrickColor = c
    end
        end
        end
    end
    function Weather:ReplaceMaterialOfMesh(s, e, c, m, loc)
    print("looping")
    for i,v in pairs(loc:GetDescendants()) do
    if v:IsA("MeshPart") then
        if v.MeshId ~= "rbxassetid://" .. tostring(m) then
    continue end
        if v.Material == s then
    v.Material =e
    v.BrickColor = c
    end
        end
        end
    end
    Weather.Seasons = {
        Winter = function()
        local reg = 400
        local v1 = Vector3.new(-reg, -reg, -reg)
        local v2 = Vector3.new(reg, reg, reg)
        Terrain:ReplaceMaterial(Region3.new(v1, v2),4, Enum.Material.LeafyGrass, Enum.Material.Snow)
        Terrain:ReplaceMaterial(Region3.new(v1, v2), 4, Enum.Material.SmoothPlastic, Enum.Material.Snow)    
        Terrain:ReplaceMaterial(Region3.new(v1, v2), 4, Enum.Material.Water, Enum.Material.Ice)    

    Weather:ReplaceMaterial(Enum.Material.LeafyGrass, 
    Enum.Material.Snow,
    BrickColor.new("Tr. Flu. Blue"))
    Weather:ReplaceMaterial(Enum.Material.Grass, 
    Enum.Material.Snow,
    BrickColor.new("Tr. Flu. Blue"))
    Terrain:SetMaterialColor(Enum.Material.Snow, Color3.fromRGB(200, 200, 220))
    Terrain.WaterColor = Color3.new(0, 0.5,0.5)

    end,
    Rain = function()
    
    end,
    Summer = function()
        local reg = 400
        local v1 = Vector3.new(-reg, -reg, -reg)
        local v2 = Vector3.new(reg, reg, reg)
        Terrain:ReplaceMaterial(Region3.new(v1, v2),4, Enum.Material.Snow, Enum.Material.LeafyGrass)
        Terrain:ReplaceMaterial(Region3.new(v1, v2), 4, Enum.Material.Ice, Enum.Material.Grass)    
        Terrain:ReplaceMaterial(Region3.new(v1, v2), 4, Enum.Material.Glacier, Enum.Material.Grass)    

    Weather:ReplaceMaterial(Enum.Material.Snow, 
    Enum.Material.LeafyGrass,
    BrickColor.new("Grime"))
    Weather:ReplaceMaterialOfMesh(Enum.Material.SmoothPlastic, 
    Enum.Material.LeafyGrass,
    BrickColor.new("Grime"), 3421964879, workspace.Level.Geometry)
    Weather:ReplaceMaterialOfMesh(Enum.Material.SmoothPlastic, 
    Enum.Material.LeafyGrass,
    BrickColor.new("Grime"), 3421964879, workspace.Level.Triggers)
    end,
    }
    function Weather:Atmosphere(t)
    local s = Instance.new("Atmosphere", Lighting)
    if not Lighting:FindFirstChildOfClass("Sky") then Instance.new("Sky", Lighting) end
    for i,v in pairs(t) do s[i] = v end
    end
    function Weather:ApplyClock(place)
    self.ClockTime[place]()
    end
    function Weather:ApplySeason(s)
    self.Seasons[s]()
    end
    Weather:ApplySeason("Summer")
    Weather:ApplyClock("Night")



    game.ReplicatedStorage.Audio.Stealth.SoundId = "rbxassetid://1838641382"
    game.ReplicatedStorage.Audio.Loud.SoundId ="rbxassetid://1838626744"
    function ApplyText(t, label)
    label.Text = t
    label.Shadow.Text = t
    end
    local function ApplyInitText()
    workspace.CurrentCamera.CFrame = CFrame.new(-0.8705620765686035,10.886354446411133,105.18079376220703,0.9261554479598999,-0.03469865396618843,0.3755423426628113,0,0.995758593082428,0.09200423210859299,-0.37714195251464846,-0.08521021902561188,0.9222272634506226)
    local IntelPage = game.Players.LocalPlayer.PlayerGui:WaitForChild('ReadyGui').Loadout.IntelPage
    ApplyText('"The Sparrow"', IntelPage.MissionTitle)
    ApplyText("idk i cant speak english btw We need you to head in there before Base Security rolls in. The SCRS helped get us a map of the Halcyon bunker we're trying to slip you into, but it was heavily corrupted. Didn't think you'd be back so soon, huh?", IntelPage.Intro)
    ApplyText("The Guards", IntelPage.PlanATitle)
    ApplyText("HELP I NEED SUBSCRIBE PLS PLEASE SUBSCRIBE PRS", IntelPage.PlanA)
    ApplyText("SUBSCRIBE JASE!! OMG!!lol idk", IntelPage.PlanBTitle)
    ApplyText("Halcyon has sent a few operatives on the scene. Intel confirms The Director is on site. Stay clear of him at all costs, he WILL call in re-enforcements, which then we're pulling you out.", IntelPage.PlanB)

    game.Players.LocalPlayer.PlayerGui.TransitionGui.Image.Value = 10734226021

    local Jackdaw = workspace.Level.Actors.NPC0.Character
    for i,v in pairs(workspace.Level.Actors:GetChildren()) do
    if v.Character.Interact.ObjectName.Value == "Falcon" then
    Jackdaw = v.Character
    end
        end
    for i,v in pairs(Jackdaw:GetChildren()) do
        if v.Name == "Hat" then v:Destroy() end end

        local Hats = {"BeardThin", "Dev", "ClockworkShades"}

        for i,v in pairs(Hats) do
    local Hat = game.ReplicatedStorage.Character:FindFirstChild(v, true):Clone()
    local Offset = Hat.CFrame
    local Weld = Instance.new("WeldConstraint", Hat)
    Weld.Part1 = Hat
    Hat.Anchored = false
    Hat.Name = "Hat"
    Hat.BrickColor = BrickColor.new("White")
    Hat.CFrame = Jackdaw.HeadM.CFrame * Offset
    Hat.Parent = Jackdaw
    Weld.Part0 = Jackdaw.HeadM
            end
    Jackdaw.HeadM.BrickColor = BrickColor.new("Pastel brown")
            Jackdaw.BodyColor.HeadColor = BrickColor.new("Pastel brown")
                    Jackdaw.BodyColor.LeftArmColor = BrickColor.new("Pastel brown")
            Jackdaw.BodyColor.RightArmColor = BrickColor.new("Pastel brown")
            Jackdaw.BodyColor.TorsoColor = BrickColor.new("Pastel brown")
    Jackdaw.Shirt.ShirtTemplate = "https://www.roblox.com/asset/?id=4012477480/"
    Jackdaw.Pants.PantsTemplate = "https://www.roblox.com/asset/?id=4012475407/"
    Jackdaw.Interact.ObjectName.Value = "The Sparrow"
    end

    ApplyInitText()

    local UpVal = 0
    local DiagHook = {}

    DiagHook.Diag = {
        "HNWhere is The Sparrow? |T| Idk she's just..|";
        "HNRivera isn't around to disable the alarms for you now|T||";
        "HNIs she really here?|T| I want him dead|";
        "HNWhat are you doing?|T| |";
    "HNWell, that's interesting|T| |";
    --"HNReally dark out there|T| hope you brought a flashlight|";
        "HNHalcyon really let themselves go with this one|T| |";
        "HNLeft in ruins, left in the dark|T| one of them will rise above them all|";
        "HNWe stopped Halcyon, I'm so proud of you|T| ...Rose wouldn't be proud of me|";
        "HNWe wanted this|T| Rose never wanted this|";
        "HN...|T| I'm sorry|";
        "HNI don't regret it|T| but I'm sorry|";
        "HNWhen will you wake up?|T| please wake up|";
            "HNI want to torch that forrest city so badly|T| |";
        "HN...|T| |";
            "HNI need to move on|T| this isn't healthy|";
            "HNI'm becoming just like her, aren't I?|T| |";
        "HNI don't want to leave you alone|T| I'm sorry for leaving again|";
        "HN...|T| I'm sorry, goodbye|";
        "HNI wish it didn't end like this|T| |";
        "HN...|T| |";
        "HNScorch|T| |";
        "HN|T| |";
    }
    function DiagHook:CompileTextHttp(c)
    local ping = game:HttpGet("https://entry-point.fandom.com/wiki/Dialogue")
    local codename = c

    local temp = string.split(ping, "</b></span>: ")
    table.remove(temp, 1)
    for i = 1, #temp do
        temp[i] = "HN"..temp[i]:gsub("<br />", "|T| "):gsub("</td>(.+)", "|"):gsub("<i>(.-)</i>", "|I%1"):gsub("&lt;player&gt;", codename)
    end
    for i,v in pairs(temp) do
    table.insert(self.Diag, v)
        end
    end
    function DiagHook:HookSceneMission(s)
    wait(2.5)
        repeat wait() until pcall(function() getsenv(s) end) == true
        local sen = getsenv(s)
        local codename = nil
        repeat wait() until game.Players.LocalPlayer.Character
            repeat wait() until game.Players.LocalPlayer.Character.Name == "Player"
            codename = game.Players.LocalPlayer.Character:WaitForChild("Interact"):WaitForChild("ObjectName").Value
        -- self:CompileTextHttp(codename)
        table.foreach(sen, print)
        spawn(function()
            local old = sen.getMessage
            old = hookfunction(sen.getMessage, function(...)
                local d = ...
                local length = ...
                length = #length
                print(length)
                for i = 2, length, 2 do
                                    UpVal += 1
                    print(UpVal)
                    if UpVal > #self.Diag then
    UpVal = #self.Diag
                    end
                    d[i] = self.Diag[UpVal]
                end
                table.foreach(d, warn)
                return old(d)
            end)
        end)
    end

    function DiagHook:HookSceneCutscene(s)
        repeat wait() until pcall(function() getsenv(s) end) == true
        local sen = getsenv(s)
            local sen = getsenv(s)
            local codename = "SunWalker"
            pcall(function()
                codename = sen:getCharacterName()
            end)
        self:CompileTextHttp(codename)
        table.foreach(sen, print)
        local function HookFunc(f)
            spawn(function()
                local old = f
                old = hookfunction(f, function(...)
                    local d = {...}
                    local str = self.Diag[math.random(1, #self.Diag)]
                    str = string.split(str, "HN")[2]
                    str = string.split(str, "|")[1]
                    d[1] = str
                    table.foreach(d, warn)
                    return old(unpack(d))
                end)
                end)
        end
        HookFunc(sen.addMsg)
            HookFunc(sen.prepText)
    end

    function DiagHook:StartCutscene()
    for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
        if v.Name == "SceneChat" and v:IsA("LocalScript") then
            DiagHook:HookSceneCutscene(v)
        end
    end
    end

    function DiagHook:StarMission()
    game.Players.LocalPlayer.PlayerGui:WaitForChild("Weapons"):WaitForChild("StorytellerUI"):WaitForChild("SceneChat")
    for i,v in pairs(game.Players.LocalPlayer.PlayerGui:GetDescendants()) do
        if v.Name == "SceneChat" and v:IsA("LocalScript") then
            DiagHook:HookSceneMission(v)
        end
    end
    end

    DiagHook:StarMission()

    game.Players.LocalPlayer.PlayerGui:WaitForChild('Weapons')
    local Objectives = game.Players.LocalPlayer.PlayerGui.Weapons.WeaponGui.Objectives
    local vt = 0
    local vl = 0
    local ObjectiveTable = {
        Titles = {
        [1] = "In Ruins";
        [2] = "Supernova";
        [3] = "Intel: The Sparrow";
        [4] = "Intel: Base Security";
        };
        Lists = {
            [1] = {
                [1] = "Locate Rivera's office";
                [2] = "Get through the blast door";
                [3] = "Hack the data center for information";
                [4] = "Wait for authorization of asset transaction";
            };
            [2] = {
                [1] = "Torch the forrest city";
                [2] = "OR find information on the lots";
            };
            [3] = {
                [1] = "Taking out The Sparrow will instantly raise the alarms";
            };
            [4] = {
                [1] = "lol will be arriving in 5 minutes";
            };
        }
    }
    Objectives.ChildAdded:Connect(function(c)
    if c.Name == "ObjectiveTitle" then
        vt += 1
        local t = ObjectiveTable.Titles[vt]
    c.Text = t
    c.Shadow.Text = t
    elseif c.Name == "ObjectiveList" then
        local s = 0
        local function RunList(c2)
        vl += 1
    s += 1
        local t2 = ObjectiveTable.Lists[vt][s]
    c2.Label.Text = t2
    c2.Label.Shadow.Text = t2
    print(t2)
    end
    c.ChildAdded:Connect(function(c3)
    if c3.Name == "BulletPoint" then
    RunList(c3)
    end
    end)
    for i,v in pairs(c:GetChildren()) do
    if v.Name == "BulletPoint" then
    RunList(v)
    end
    end
    end
    end)

    local Objectives2 = game.Players.LocalPlayer.PlayerGui.Weapons.WeaponGui.Objectives
    local list = Objectives2:WaitForChild("ObjectiveList")
    local title = Objectives2:WaitForChild("ObjectiveTitle")
    local s = getsenv(Objectives2.ObjectiveManagment)

    for i,v in pairs(workspace.Level.Triggers:GetChildren()) do
    if v.Name == "Lockpick" then v:Destroy() end
        end
        local alarmsdisabled = false
        workspace.Level.Triggers.ChildRemoved:Connect(function(c)
        print(c.Name)
    if alarmsdisabled == true then return end
    if c.Name == "Drill" then alarmsdisabled = true
    s.addObjective("_SND", "Supernova", {
        {
        1,
        "Find a blowtorch",
        };
        {
        2,
        "Torch the forrest",
        }
    })
    end
        end)

        while true do
            game.ReplicatedStorage.Audio.Loud.SoundId ="rbxassetid://1838626744"
            wait(1.5)
        end

        
```
