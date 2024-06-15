---- SETTING -----
_G.autofarme = true

while _G.autofarme == true do
	---- SETTING HUMANOIDROOTPART -----
	local human = game.Players.LocalPlayer.Character.HumanoidRootPart
	human.CanCollide = false
	human.CanTouch = false
	---- ANTI AFK -----
	for i,v in pairs(getconnections(game:GetService("Players").LocalPlayer.Idled)) do
    	v:Disable()
	end
	---- DELETE PART DAMAGE -----
	local ForestStage = game['Workspace']['BoatStages']['NormalStages']['ForestStage']:GetChildren()
	for i,v in pairs(ForestStage) do
		if v.Name ~= "TerrainWall1" and v.Name ~= "Sand" and v.Name ~= "SpawnRocks" and v.Name ~= "CaveMasks" and v.Name ~= "" and v.Name ~= "DarknessPart" and v.Name ~= "Wall1" and v.Name ~= "Wall2" and v.Name ~= "TerrainWall2" and v.Name ~= "Traces" then
			v:Destroy()
		end
	end
	local Other = game['Workspace']['BoatStages']['OtherStages']:GetChildren()
	for x,y in pairs(Other) do
		if y then
			local in_m = y:GetChildren()
			for i,v in pairs(in_m) do
				if v.Name ~= "TerrainWall1" and v.Name ~= "Sand" and v.Name ~= "SpawnRocks" and v.Name ~= "CaveMasks" and v.Name ~= "" and v.Name ~= "DarknessPart" and v.Name ~= "Wall1" and v.Name ~= "Wall2" and v.Name ~= "TerrainWall2" and v.Name ~= "Traces" then
					v:Destroy()				end
			end
		end
	end
	local TheEnd = game['Workspace']['BoatStages']['NormalStages']['TheEnd']:GetChildren()
	for i,v in pairs(TheEnd) do
		if v.Name ~= "WaterfallEnd" and v.Name ~= "GoldenChest" and v.Name ~= "Sand" and  v.Name ~= "TerrainWall1" and v.Name ~= "SpawnRocks" and v.Name ~= "CaveMasks" and v.Name ~= "" and v.Name ~= "DarknessPart" and v.Name ~= "Wall1" and v.Name ~= "Wall2" and v.Name ~= "TerrainWall2" and v.Name ~= "Traces" then
			v:Destroy()
		end
	end
	---- TELEPORT TO POINT -----
	local list = game['Workspace']['BoatStages']['NormalStages']:GetChildren()
	for i,v in pairs(list) do
		if v then
			if game['Workspace']['BoatStages']['NormalStages']:FindFirstChild("CaveStage"..i) then
				local wall = game['Workspace']['BoatStages']['NormalStages']["CaveStage"..i]:FindFirstChild("DarknessPart")
				if wall then
					game.TweenService:Create(human, TweenInfo.new(1.8), {CFrame = wall.CFrame}):Play()
					wait(1.8)
				end
				
			end
		end
	end
	---- GO TO CHEST -----
	game.TweenService:Create(human, TweenInfo.new(1), {CFrame = game['Workspace']['BoatStages']['NormalStages']['TheEnd']['GoldenChest']['Trigger'].CFrame}):Play()
	wait(1)
	---- Jump END-----
	for i = 0,3 do
		game.Players.LocalPlayer.Character.Humanoid.Jump = true
		wait(0.3)
	end
	wait(17)
end
