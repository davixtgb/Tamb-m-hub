# Tamb-m-hub-- GUI de teleporte entre ilhas (client-side)
-- Esse script deve ser usado em LocalScript e apenas com propósito educativo

local player = game.Players.LocalPlayer
local teleportLocations = {
    ["Starter Island"] = Vector3.new(50, 10, 100),
    ["Jungle"] = Vector3.new(-1500, 10, 300),
    ["Desert"] = Vector3.new(1150, 10, 450),
    ["Sky Island"] = Vector3.new(-4800, 800, -1000)
}

-- Criar a interface
local screenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
local frame = Instance.new("Frame", screenGui)
frame.Size = UDim2.new(0, 200, 0, 300)
frame.Position = UDim2.new(0, 20, 0, 100)
frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
frame.BorderSizePixel = 0

-- Criar botões para cada ilha
for islandName, position in pairs(teleportLocations) do
    local button = Instance.new("TextButton", frame)
    button.Size = UDim2.new(1, -10, 0, 40)
    button.Position = UDim2.new(0, 5, 0, (#frame:GetChildren() - 1) * 45)
    button.Text = islandName
    button.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    button.TextColor3 = Color3.new(1, 1, 1)
    button.Font = Enum.Font.SourceSansBold
    button.TextSize = 18

    button.MouseButton1Click:Connect(function()
        if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            player.Character.HumanoidRootPart.CFrame = CFrame.new(position)
        end
    end)
end
