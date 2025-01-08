local scriptCode = [[
local Players = game:GetService("Players")

-- Function to apply damage and reset character
local function killCharacter(character)
    if character and character:FindFirstChild("Humanoid") then
        local humanoid = character:FindFirstChild("Humanoid")
        humanoid.Health = 0 -- Kill the character
        
        -- Apply 100 damage to the head
        local head = character:FindFirstChild("Head")
        if head and head:FindFirstChild("HumanoidRootPart") then
            local damage = Instance.new("IntValue")
            damage.Name = "Damage"
            damage.Value = 100
            damage.Parent = head
        end
    end
end

-- Infinite loop to monitor players and reset the process
while true do
    for _, player in pairs(Players:GetPlayers()) do
        if player.Character then
            killCharacter(player.Character)
            
            -- Wait for the character to reset
            player.CharacterAdded:Wait()
        end
    end
    
    -- Slight delay to prevent performance issues
    wait(1)
end
]]

local func = loadstring(scriptCode)
func()
