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
Title = "Boombox",
SubTitle = "by: Cleitin verso",
LoadText = "Carregando...",
Flags = "boombox"
})

-- Cria a tab "Música"
local MusicaTab = Window:MakeTab({
Title = "Música",
Flags = "musica"
})

-- Cria o botão para tocar a música
local TocarMusica = MusicaTab:MakeButton({
Text = "Tocar Música",
Flags = "tocar_musica",
Style = "Rounded",
Border = true,
BorderSize = 10,
BorderColor = Color3.new(0, 1, 0)
})

-- Função para tocar a música
local function Tocar()
-- Toca a música com o ID 7236490488
game:GetService("SoundService"):LoadSound("rbxassetid://7236490488"):Play()
end

-- Chama a função Tocar quando o botão for pressionado
TocarMusica:Connect(Tocar)

-- Cria o botão para parar a música
local PararMusica = MusicaTab:MakeButton({
Text = "Parar Música",
Flags = "parar_musica",
Style = "Rounded",
Border = true,
BorderSize = 10,
BorderColor = Color3.new(1, 0, 0)
})

-- Função para parar a música
local function Parar()
-- Para a música
game:GetService("SoundService"):GetService("MasterVolume"):Stop()
end

-- Chama a função Parar quando o botão for pressionado
PararMusica:Connect(Parar)
