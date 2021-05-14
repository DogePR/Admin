
	local library = loadstring(game:HttpGet(('https://pastebin.com/raw/FsJak6AT')))() -- It's obfuscated, I won't let you see my ugly coding skills. =)

	local w = library:CreateWindow("Murder X")

	local b = w:CreateFolder("Functions")

	b:Label("Made By                           Delux#5586   Gangster#3614 ",Color3.fromRGB(38,38,38),Color3.fromRGB(0,216,111)) --BgColor,TextColor

	b:Button("Fly",function()
		repeat wait() 
		until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Head") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
		local mouse = game.Players.LocalPlayer:GetMouse() 
		repeat wait() until mouse
		local plr = game.Players.LocalPlayer 
		local torso = plr.Character.Head 
		local flying = false
		local deb = true 
		local ctrl = {f = 0, b = 0, l = 0, r = 0} 
		local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		local maxspeed = 400 
		local speed = 5000 

		function Fly() 
			local bg = Instance.new("BodyGyro", torso) 
			bg.P = 9e4 
			bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
			bg.cframe = torso.CFrame 
			local bv = Instance.new("BodyVelocity", torso) 
			bv.velocity = Vector3.new(0,0.1,0) 
			bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
			repeat wait() 
				plr.Character.Humanoid.PlatformStand = true 
				if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then 
					speed = speed+.5+(speed/maxspeed) 
					if speed > maxspeed then 
						speed = maxspeed 
					end 
				elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then 
					speed = speed-1 
					if speed < 0 then 
						speed = 0 
					end 
				end 
				if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
					lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
				elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
				else 
					bv.velocity = Vector3.new(0,0.1,0) 
				end 
				bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
			until not flying 
			ctrl = {f = 0, b = 0, l = 0, r = 0} 
			lastctrl = {f = 0, b = 0, l = 0, r = 0} 
			speed = 0 
			bg:Destroy() 
			bv:Destroy() 
			plr.Character.Humanoid.PlatformStand = false 
		end 
		mouse.KeyDown:connect(function(key) 
			if key:lower() == "h" then 
				if flying then flying = false 
				else 
					flying = true 
					Fly() 
				end 
			elseif key:lower() == "w" then 
				ctrl.f = 1 
			elseif key:lower() == "s" then 
				ctrl.b = -1 
			elseif key:lower() == "a" then 
				ctrl.l = -1 
			elseif key:lower() == "d" then 
				ctrl.r = 1 
			end 
		end) 
		mouse.KeyUp:connect(function(key) 
			if key:lower() == "w" then 
				ctrl.f = 0 
			elseif key:lower() == "s" then 
				ctrl.b = 0 
			elseif key:lower() == "a" then 
				ctrl.l = 0 
			elseif key:lower() == "d" then 
				ctrl.r = 0 
			end 
		end)
		Fly()
	end)

	b:Slider("Speed",1,100,true,function(value) --MinValue,MaxValue,Precise
		player = game.Players.LocalPlayer
		player.Character.Humanoid.WalkSpeed = value
	end)



	b:Slider("Jump",1,100,true,function(value) --MinValue,MaxValue,Precise
		player = game.Players.LocalPlayer
		player.Character.Humanoid.JumpPower = value
	end)


	b:Slider("Gravity",-100,1000,true,function(value) --MinValue,MaxValue,Precise
		game.workspace.Gravity = value
	end)

	b:Button("M&S ESP",function()
		loadstring(game:HttpGet("https://pastebin.com/raw/NjzcBZXC"))()
	end)

	b:Button("Coinfarm",function()
		loadstring(game:HttpGet('https://raw.githubusercontent.com/Sumithebestak/MM2/main/MM2PathWalkFarm'))()

	end)

b:Button("Noclip",function()
	noclip = false
	game:GetService('RunService').Stepped:connect(function()
		if noclip then
			game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
		end
	end)
	plr = game.Players.LocalPlayer
	mouse = plr:GetMouse()
	mouse.KeyDown:connect(function(key)

		if key == "b" then
			noclip = not noclip
			game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
		end
	end)
end)

b:Button("Emotes",function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/Sumithebestak/MM2/main/MM2PathWalkFarm'))()

end)

b:Button("Guns",function()
	local WeaponOwnRange = {
		min=1,
		max=5
	}

	local DataBase, PlayerData = getrenv()._G.Database, getrenv()._G.PlayerData

	local newOwned = {}

	for i,v in next, DataBase.Item do
		newOwned[i] = math.random(WeaponOwnRange.min, WeaponOwnRange.max) -- newOwned[Weapon]: ItemCount
	end

	local PlayerWeapons = PlayerData.Weapons

	game:GetService("RunService"):BindToRenderStep("InventoryUpdate", 0, function()
		PlayerWeapons.Owned = newOwned
	end)

	game.Players.LocalPlayer.Character.Humanoid.Health = 0
end)

b:Button("Esp",function()
	loadstring(game:HttpGet("https://pastebin.com/raw/kvr0AuWz"))()
end)
	b:DestroyGUI()


	--Example of refresh

	    --[[local label = b:Label("Hi",Color3.fromRGB(255,0,0),Color3.fromRGB(0,255,0))
	    
	    label:Refresh("Not epic")
	    
	    local dropdown = b:Dropdown("Hi",{"A","B"})
	    
	    dropdown:Refresh({"A","B","C"})
	    ]]



local WeaponOwnRange = {
	min=1,
	max=5
}


