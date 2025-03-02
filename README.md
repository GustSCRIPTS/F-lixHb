--// UI Library (Criando a interface)
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/UI-Libraries/main/AstroLib.txt"))()
local Window = Library:CreateWindow("Félix Hub", "Blox Fruits", 13046415340) -- ID da tua imagem

--// Criando Tabs
local MainTab = Window:CreateTab("Principal")
local MiscTab = Window:CreateTab("Misc")

--// Variáveis
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:FindFirstChildOfClass("Humanoid")

--// Função para pegar missões corretas baseado no nível
function GetQuest()
    local level = player.Data.Level.Value
    if level <= 10 then
        return {quest = "BanditQuest1", enemy = "Bandit", position = CFrame.new(1059, 15, 1550)}
    elseif level <= 20 then
        return {quest = "MonkeyQuest", enemy = "Monkey", position = CFrame.new(-1598, 35, 155)}
    else
        return {quest = "PirateQuest", enemy = "Pirate", position = CFrame.new(-1200, 30, 200)}
    end
end

--// Auto Farm
local autoFarm = false
MainTab:CreateToggle("Auto Farm", false, function(value)
    autoFarm = value
    while autoFarm do
        task.wait(math.random(0.5, 1)) -- Delay aleatório para evitar bans
        local quest = GetQuest()
        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = quest.position
        print("Atacando " .. quest.enemy)
    end
end)

--// Auto Quest
local autoQuest = false
MainTab:CreateToggle("Auto Quest", false, function(value)
    autoQuest = value
    while autoQuest do
        task.wait(math.random(1, 2))
        local quest = GetQuest()
        print("Pegando missão: " .. quest.quest)
    end
end)

--// Speed Hack
MiscTab:CreateSlider("Velocidade", 16, 100, 16, function(value)
    humanoid.WalkSpeed = value
end)

--// Jump Hack
MiscTab:CreateSlider("Altura do Salto", 50, 200, 50, function(value)
    humano