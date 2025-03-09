-- Carrega a biblioteca RedzV4
local success, Library = pcall(function()
return loadstring(game:HttpGet("https://raw.githubusercontent.com/hacked-prototype/RedzLibV4/main/Source.lua"))()
end)

if not success or not Library then
warn("Falha ao carregar a biblioteca.")
return
end

if Library.SetTheme then Library:SetTheme("Dark") end
if Library.SetTransparency then Library:SetTransparency(0.1) end

-- Cria a janela
local Window = Library:MakeWindow({
Title = "REDz HUB",
SubTitle = "by: redz9999",
LoadText = "Carregando...",
Flags = "redzHub_Example"
})

-- Cria a tab "Fling"
local FlingTab = Window:MakeTab({
Title = "Fling",
Flags = "FlingTab"
})

-- Cria o campo de texto para o nome da pessoa que irá dar fling
local NomeFling = FlingTab:MakeTextBox({
Placeholder = "Nome da pessoa que irá dar fling",
Flags = "NomeFling"
})

-- Cria o botão para ligar o fling
local LigarFling = FlingTab:MakeButton({
Text = "Ligar Fling",
Flags = "LigarFling"
})

-- Cria o botão para desligar o fling
local DesligarFling = FlingTab:MakeButton({
Text = "Desligar Fling",
Flags = "DesligarFling"
})

-- Função para ligar o fling
local function Ligar()
-- Pega o nome da pessoa que irá dar fling
local nome = NomeFling:GetText()

-- Faça o jogador flingar
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 10
game.Players.LocalPlayer.Character.Humanoid.JumpPower = 20
end

-- Função para desligar o fling
local function Desligar()
-- Desfaça o jogador flingar
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
game.Players.LocalPlayer.Character.Humanoid.JumpPower = 16
end

-- Chama a função Ligar quando o botão for pressionado
LigarFling:Connect(Ligar)

-- Chama a função Desligar quando o botão for pressionado
DesligarFling:Connect(Desligar)
