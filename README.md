--// UI Library (Criando a interface)
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/UI-Libraries/main/AstroLib.txt"))()
local Window = Library:CreateWindow("Félix Hub", "Blox Fruits", 13046415340) -- ID da tua imagem

--// Criando Tabs
local MainTab = Window:CreateTab("Principal")
local MiscTab = Window:CreateTab("Misc")

--// Variáveis
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

--// Auto Farm (Placeholder - código real vem depois)
local autoFarm = false
MainTab:CreateToggle("Auto Farm", false, function(value)
    autoFarm = value
    while autoFarm do
        task.wait()
        print("Auto Farm ativado!") -- Aqui vai o código real depois
    end
end)

--// Auto Quest (Placeholder)
local autoQuest = false
MainTab:CreateToggle("Auto Quest", false, function(value)
    autoQuest = value
    while autoQuest do
        task.wait()
        print("Auto Quest ativado!") -- Código real vem depois
    end
end)

--// Speed Hack
local speedMultiplier = 1
MiscTab:CreateSlider("Velocidade", 16, 100, 16, function(value)
    speedMultiplier = value
    character.Humanoid.WalkSpeed = speedMultiplier
end)

--// Jump Hack
local jumpMultiplier = 50
MiscTab:CreateSlider("Altura do Salto", 50, 200, 50, function(value)
    jumpMultiplier = value
    character.Humanoid.JumpPower = jumpMultiplier
end)

--// Remove Fog
MiscTab:CreateButton("Remover Neblina", function()
    game.Lighting.FogEnd = 100000
    print("Neblina removida!")
end)# F-lixHb
