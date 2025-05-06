local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")

local player = Players.LocalPlayer
local toolName = "MyGeneratedTool"
local animationId = "rbxassetid://77727115892579"

-- Function to create the Tool completely in code
local function createTool()
	local tool = Instance.new("Tool")
	tool.Name = toolName
	tool.RequiresHandle = false
	tool.CanBeDropped = false
	return tool
end

-- Give the player the tool if not already given
local function giveTool()
	local backpack = player:WaitForChild("Backpack")
	if not backpack:FindFirstChild(toolName) then
		local tool = createTool()
		tool.Parent = backpack
	end
end

-- Re-give tool on respawn
player.CharacterAdded:Connect(function()
	giveTool()
end)

-- Give tool at start
giveTool()

-- Play animation on screen click
UserInputService.InputBegan:Connect(function(input, gameProcessed)

