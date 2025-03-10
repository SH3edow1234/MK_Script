local function CheckQuest()
    local player = game:GetService("Players").LocalPlayer
    local myLevel = player.Data.Level.Value

    -- Detecção de mundo
    local World1, World2, World3 = false, false, false
    if game.PlaceId == 2753915549 then
        World1 = true
    elseif game.PlaceId == 4442272183 then
        World2 = true
    elseif game.PlaceId == 7449423635 then
        World3 = true
    else
        player:Kick("Do not Support, Please wait...")
        return
    end

    -- Lógica de quest
    local Mon, LevelQuest, NameQuest, NameMon, CFrameQuest, CFrameMon
    if World1 then
        if myLevel >= 1 and myLevel <= 9 then
            Mon = "Bandit"
            LevelQuest = 1
            NameQuest = "BanditQuest1"
            NameMon = "Bandit"
            CFrameQuest = CFrame.new(1059.37195, 15.4495068, 1550.4231, 0.939700544, -0, -0.341998369, 0, 1, -0, 0.341998369, 0, 0.939700544)
            CFrameMon = CFrame.new(1045.962646484375, 27.00250816345215, 1560.8203125)
        -- ... (restante da lógica de quest para World1)
        elseif myLevel >= 175 and myLevel <= 189 then
            Mon = "Dark Master"
            LevelQuest = 2
            NameQuest = "SkyQuest"
            NameMon = "Dark Master"
            CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
            CFrameMon = CFrame.new(-4582.47412109375, 786.3787841796875, -2413.513427734375)
        end
    -- Adicione aqui a lógica de quest para World2 e World3, se necessário
    end

    -- Sistema anti-detecção
    if debug.getinfo(1, "S").what == "C" then
        return
    end
    local ofuscado = "ZXhlYygnbG9jYWwgYSAsIGIgPSAxMCwgMjAgcHJpbnQoYSArIGIpJyknKQ=="
    loadstring(game:GetService("HttpService"):JSONDecode(game:GetService("HttpService"):Base64Decode(ofuscado)))()
    wait(math.random(1, 3))
    local processos = game:GetService("ProcessService"):GetRunningProcesses()
    for _, processo in ipairs(processos) do
        if processo.Name == "ProcessoSuspeito.exe" then
            return
        end
    end

    -- IU de informações (opcional)
    local screenGui = Instance.new("ScreenGui")
    screenGui.Parent = player.PlayerGui
    local textLabel = Instance.new("TextLabel")
    textLabel.Parent = screenGui
    textLabel.Size = UDim2.new(0, 200, 0, 100)
    textLabel.Position = UDim2.new(0.5, -100, 0.5, -50)
    textLabel.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
    textLabel.Text = "Mon: " .. (Mon or "N/A") .. "\nLevelQuest: " .. (LevelQuest or "N/A") .. "\nNameQuest: " .. (NameQuest or "N/A") .. "\nNameMon: " .. (NameMon or "N/A")

    -- Restante do código (ações com base nas informações da quest)
    if Mon then
        print("Quest encontrada: " .. NameQuest)
        -- Adicione aqui o código para interagir com a quest e o monstro
    end
end

CheckQuest()
