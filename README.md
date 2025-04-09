-- Cria a GUI principal
local gui = Instance.new("ScreenGui", game.CoreGui)
gui.ResetOnSpawn = false

-- Botão principal (quadrado)
local menuButton = Instance.new("TextButton", gui)
menuButton.Size = UDim2.new(0, 50, 0, 50)
menuButton.Position = UDim2.new(0.1, 0, 0.1, 0)
menuButton.BackgroundColor3 = Color3.fromRGB(100, 100, 255)
menuButton.Text = "+"
menuButton.TextColor3 = Color3.new(1, 1, 1)
menuButton.Active = true
menuButton.Draggable = true

-- Menu principal (retângulo)
local menuFrame = Instance.new("Frame", gui)
menuFrame.Size = UDim2.new(0, 250, 0, 200)
menuFrame.Position = UDim2.new(0.1, 60, 0.1, 0)
menuFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
menuFrame.Visible = false
menuFrame.Active = true
menuFrame.Draggable = true

-- Criar abas
local tabs = {
    "Aimbot",
    "Visuals",
    "Configs"
}

local currentTab = nil
local sections = {}

for i, name in ipairs(tabs) do
    local tabBtn = Instance.new("TextButton", menuFrame)
    tabBtn.Size = UDim2.new(0, 70, 0, 25)
    tabBtn.Position = UDim2.new(0, (i - 1) * 75 + 5, 0, 5)
    tabBtn.Text = name
    tabBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    tabBtn.TextColor3 = Color3.new(1, 1, 1)

    -- Criar a área de conteúdo da aba
    local section = Instance.new("Frame", menuFrame)
    section.Size = UDim2.new(1, -10, 0, 130)
    section.Position = UDim2.new(0, 5, 0, 35)
    section.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    section.Visible = false
    sections[name] = section

    -- Trocar de aba ao clicar
    tabBtn.MouseButton1Click:Connect(function()
        for _, sec in pairs(sections) do
            sec.Visible = false
        end
        section.Visible = true
        currentTab = name
    end)
end

-- Aimbot tab conteúdo
local aimbotBtn = Instance.new("TextButton", sections["Aimbot"])
aimbotBtn.Size = UDim2.new(1, -20, 0, 30)
aimbotBtn.Position = UDim2.new(0, 10, 0, 10)
aimbotBtn.Text = "Ativar Aimbot"
aimbotBtn.BackgroundColor3 = Color3.fromRGB(80, 80, 80)
aimbotBtn.TextColor3 = Color3.new(1, 1, 1)
aimbotBtn.MouseButton1Click:Connect(function()
    print("Aimbot ativado")
end)

-- Visuals tab conteúdo
local visualsLabel = Instance.new("TextLabel", sections["Visuals"])
visualsLabel.Size = UDim2.new(1, -20, 0, 30)
visualsLabel.Position = UDim2.new(0, 10, 0, 10)
visualsLabel.Text = "Visuals em desenvolvimento"
visualsLabel.BackgroundTransparency = 1
visualsLabel.TextColor3 = Color3.new(1, 1, 1)

-- Configs tab conteúdo
local configLabel = Instance.new("TextLabel", sections["Configs"])
configLabel.Size = UDim2.new(1, -20, 0, 30)
configLabel.Position = UDim2.new(0, 10, 0, 10)
configLabel.Text = "Configs salvas em breve"
configLabel.BackgroundTransparency = 1
configLabel.TextColor3 = Color3.new(1, 1, 1)

-- Mostrar/ocultar menu com clique no quadrado
menuButton.MouseButton1Click:Connect(function()
    menuFrame.Visible = not menuFrame.Visible
end)
