-- Carregar a Rayfield Library
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

-- Criar a Janela Principal
local Window = Rayfield:CreateWindow({
   Name = "Troll Hub 🤡 | Brookhaven RP 🏡",
   LoadingTitle = "Carregando Troll Hub...",
   LoadingSubtitle = "Preparando zoeira...",
   ConfigurationSaving = {
      Enabled = true,
      FolderName = "TrollHub",
      FileName = "TrollHubSettings"
   },
   Discord = {
      Enabled = false,
      Invite = "",
      RememberJoins = true
   },
   KeySystem = false
})

-- Criar a Aba Troll
local TrollTab = Window:CreateTab("Troll", 4483362458) -- Ícone de palhaço

-----------------------------------------------------------
-- 🤡 FLING PLAYER
-----------------------------------------------------------
TrollTab:CreateSection("Fling Player")

local selectedPlayer = ""
local flingActive = false

-- Input para selecionar o jogador
TrollTab:CreateInput({
   Name = "Nome do Jogador",
   PlaceholderText = "Digite o nome do jogador",
   RemoveTextAfterFocusLost = false,
   Callback = function(value)
      selectedPlayer = value
   end
})

-- Alternar Fling
TrollTab:CreateToggle({
   Name = "Ativar Fling 🚀",
   Default = false,
   Callback = function(state)
      flingActive = state
      
      if flingActive then
         local players = game:GetService("Players")
         local target = players:FindFirstChild(selectedPlayer)

         if target and target.Character and target.Character:FindFirstChild("HumanoidRootPart") then
            local hrp = target.Character.HumanoidRootPart
            task.spawn(function()
               while flingActive do
                  hrp.Velocity = Vector3.new(0, 500, 0) -- Lança o player para cima
                  task.wait(0.2)
               end
            end)
         end
      end
   end
})

Rayfield:LoadConfiguration()
