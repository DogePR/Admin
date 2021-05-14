
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


FindFirstChild("Humanoid"):GetAccessories() do
				getacc:Destroy()
			end
			for i = 1,#Hats do
				repeat game:GetService("RunService").Heartbeat:wait() until Hats[i]
				firetouchinterest(Hats[i].Handle,Character:FindFirstChild("HumanoidRootPart"),0)
				repeat game:GetService("RunService").Heartbeat:wait() until Character:FindFirstChildOfClass("Accessory")
				Character:FindFirstChildOfClass("Accessory"):Destroy()
				repeat game:GetService("RunService").Heartbeat:wait() until not Character:FindFirstChildOfClass("Accessory")
			end
			Character:BreakJoints()
			Player.CharacterAdded:wait()
			for i = 1,20 do game:GetService("RunService").Heartbeat:wait()
				if Player.Character:FindFirstChild("HumanoidRootPart") then
					Player.Character:FindFirstChild("HumanoidRootPart").CFrame = Old
				end
			end
		else
			notify('Incompatible Exploit','Your exploit does not support this command (missing firetouchinterest)')
		end
	end)


	addcmd('vr',{},function(args, speaker)
		-- Full credit to Abacaxl @V3rmillion
		-- Free for all thanks to Zinnia
		loadstring(game:HttpGet('https://ghostbin.co/paste/yb288/raw'))()
	end)

	addcmd('split',{},function(args, speaker)
		if r15(speaker) then
			speaker.Character.UpperTorso.Waist:Destroy()
		else
			notify('R15 Required','This command requires the r15 rig type')
		end
	end)

	addcmd('nilchar',{},function(args, speaker)
		if speaker.Character ~= nil then
			speaker.Character.Parent = nil
		end
	end)

	addcmd('unnilchar',{'nonilchar'},function(args, speaker)
		if speaker.Character ~= nil then
			speaker.Character.Parent = workspace
		end
	end)

	addcmd('noroot',{'removeroot','rroot'},function(args, speaker)
		if speaker.Character ~= nil then
			local char = Players.LocalPlayer.Character
			char.Parent = nil
			char.HumanoidRootPart:Destroy()
			char.Parent = workspace
		end
	end)

	addcmd('replaceroot',{'replacerootpart'},function(args, speaker)
		if speaker.Character ~= nil and speaker.Character:FindFirstChild("HumanoidRootPart") then
			local Char = speaker.Character
			local OldParent = Char.Parent
			local HRP = Char and Char:FindFirstChild("HumanoidRootPart")
			local OldPos = HRP.CFrame
			Char.Parent = game
			local HRP1 = HRP:Clone()
			HRP1.Parent = Char
			HRP = HRP:Destroy()
			HRP1.CFrame = OldPos
			Char.Parent = OldParent
		end
	end)

	addcmd('clearcharappearance',{'clearchar','clrchar'},function(args, speaker)
		speaker:ClearCharacterAppearance()
	end)

	addcmd('equiptools',{},function(args, speaker)
		for i,v in pairs(speaker:FindFirstChildOfClass("Backpack"):GetChildren()) do
			if v:IsA("Tool") or v:IsA("HopperBin") then
				v.Parent = speaker.Character
			end
		end
	end)

	local function GetHandleTools(p)
		p = p or Players.LocalPlayer
		local r = {}
		for _, v in ipairs(p.Character and p.Character:GetChildren() or {}) do
			if v.IsA(v, "BackpackItem") and v.FindFirstChild(v, "Handle") then
				r[#r + 1] = v
			end
		end
		for _, v in ipairs(p.Backpack:GetChildren()) do
			if v.IsA(v, "BackpackItem") and v.FindFirstChild(v, "Handle") then
				r[#r + 1] = v
			end
		end
		return r
	end
	addcmd('dupetools', {'clonetools'}, function(args, speaker)
		local LOOP_NUM = tonumber(args[1]) or 1
		local OrigPos = speaker.Character.HumanoidRootPart.Position
		local Tools, TempPos = {}, Vector3.new(math.random(-2e5, 2e5), 2e5, math.random(-2e5, 2e5))
		for i = 1, LOOP_NUM do
			local Human = speaker.Character:WaitForChild("Humanoid")
			wait(.1, Human.Parent:MoveTo(TempPos))
			Human.RootPart.Anchored = speaker:ClearCharacterAppearance(wait(.1)) or true
			local t = GetHandleTools(speaker)
			while #t > 0 do
				for _, v in ipairs(t) do
					coroutine.wrap(function()
						for _ = 1, 25 do
							v.Parent = speaker.Character
							v.Handle.Anchored = true
						end
						for _ = 1, 5 do
							v.Parent = workspace
						end
						table.insert(Tools, v.Handle)
					end)()
				end
				t = GetHandleTools(speaker)
			end
			wait(.1)
			speaker.Character = speaker.Character:Destroy()
			speaker.CharacterAdded:Wait():WaitForChild("Humanoid").Parent:MoveTo(LOOP_NUM == i and OrigPos or TempPos, wait(.1))
			if i == LOOP_NUM or i % 5 == 0 then
				local HRP = speaker.Character.HumanoidRootPart
				if type(firetouchinterest) == "function" then
					for _, v in ipairs(Tools) do
						v.Anchored = not firetouchinterest(v, HRP, 1, firetouchinterest(v, HRP, 0)) and false or false
					end
				else
					for _, v in ipairs(Tools) do
						coroutine.wrap(function()
							local x = v.CanCollide
							v.CanCollide = false
							v.Anchored = false
							for _ = 1, 10 do
								v.CFrame = HRP.CFrame
								wait()
							end
							v.CanCollide = x
						end)()
					end
				end
				wait(.1)
				Tools = {}
			end
			TempPos = TempPos + Vector3.new(10, math.random(-5, 5), 0)
		end
	end)

	addcmd('touchinterests', {'touchinterest', 'firetouchinterests', 'firetouchinterest'}, function(args, speaker)
		local Root = getRoot(speaker.Character) or speaker.Character:FindFirstChildWhichIsA("BasePart")
		local function Touch(x)
			x = x.FindFirstAncestorWhichIsA(x, "Part")
			if x then
				if firetouchinterest then
					return spawn(function()
						firetouchinterest(x, Root, 1, wait() and firetouchinterest(x, Root, 0))
					end)
				end
				x.CFrame = Root.CFrame
			end
		end
		for _, v in ipairs(workspace:GetDescendants()) do
			if v.IsA(v, "TouchTransmitter") then
				Touch(v)
			end
		end
	end)

	addcmd('fullbright',{'fb','fullbrightness'},function(args, speaker)
		game:GetService("Lighting").Brightness = 2
		game:GetService("Lighting").ClockTime = 14
		game:GetService("Lighting").FogEnd = 100000
		game:GetService("Lighting").GlobalShadows = false
		game:GetService("Lighting").OutdoorAmbient = Color3.fromRGB(128, 128, 128)
	end)

	addcmd('loopfullbright',{'loopfb'},function(args, speaker)
		if brightLoop then
			brightLoop:Disconnect()
		end
		local function brightFunc()
			game:GetService("Lighting").Brightness = 2
			game:GetService("Lighting").ClockTime = 14
			game:GetService("Lighting").FogEnd = 100000
			game:GetService("Lighting").GlobalShadows = false
			game:GetService("Lighting").OutdoorAmbient = Color3.fromRGB(128, 128, 128)
		end

		brightLoop = game:GetService("RunService").RenderStepped:Connect(brightFunc)
	end)

	addcmd('unloopfullbright',{'unloopfb'},function(args, speaker)
		if brightLoop then
			brightLoop:Disconnect()
		end
	end)

	addcmd('ambient',{},function(args, speaker)
		game:GetService("Lighting").Ambient = Color3.new(args[1],args[2],args[3])
		game:GetService("Lighting").OutdoorAmbient = Color3.new(args[1],args[2],args[3])
	end)

	addcmd('day',{},function(args, speaker)
		game:GetService("Lighting").ClockTime = 14
	end)

	addcmd('night',{},function(args, speaker)
		game:GetService("Lighting").ClockTime = 0
	end)

	addcmd('nofog',{},function(args, speaker)
		game:GetService("Lighting").FogEnd = 100000
	end)

	addcmd('brightness',{},function(args, speaker)
		game:GetService("Lighting").Brightness = args[1]
	end)

	addcmd('globalshadows',{'gshadows'},function(args, speaker)
		game:GetService("Lighting").GlobalShadows = true
	end)

	addcmd('unglobalshadows',{'nogshadows','ungshadows','noglobalshadows'},function(args, speaker)
		game:GetService("Lighting").GlobalShadows = false
	end)

	origsettings = {abt = game:GetService("Lighting").Ambient, oabt = game:GetService("Lighting").OutdoorAmbient, brt = game:GetService("Lighting").Brightness, time = game:GetService("Lighting").ClockTime, fe = game:GetService("Lighting").FogEnd, fs = game:GetService("Lighting").FogStart, gs = game:GetService("Lighting").GlobalShadows}

	addcmd('restorelighting',{'rlighting'},function(args, speaker)
		game:GetService("Lighting").Ambient = origsettings.abt
		game:GetService("Lighting").OutdoorAmbient = origsettings.oabt
		game:GetService("Lighting").Brightness = origsettings.brt
		game:GetService("Lighting").ClockTime = origsettings.time
		game:GetService("Lighting").FogEnd = origsettings.fe
		game:GetService("Lighting").FogStart = origsettings.fs
		game:GetService("Lighting").GlobalShadows = origsettings.gs
	end)

	addcmd('stun',{'platformstand'},function(args, speaker)
		speaker.Character:FindFirstChildOfClass('Humanoid').PlatformStand = true
	end)

	addcmd('unstun',{'nostun','unplatformstand','noplatformstand'},function(args, speaker)
		speaker.Character:FindFirstChildOfClass('Humanoid').PlatformStand = false
	end)

	addcmd('norotate',{'noautorotate'},function(args, speaker)
		speaker.Character:FindFirstChildOfClass('Humanoid').AutoRotate  = false
	end)

	addcmd('unnorotate',{'autorotate'},function(args, speaker)
		speaker.Character:FindFirstChildOfClass('Humanoid').AutoRotate  = true
	end)

	addcmd('enablestate',{},function(args, speaker)
		local x = args[1]
		if not tonumber(x) then
			local x = Enum.HumanoidStateType[args[1]]
		end
		speaker.Character:FindFirstChildOfClass("Humanoid"):SetStateEnabled(x, true)
	end)

	addcmd('disablestate',{},function(args, speaker)
		local x = args[1]
		if not tonumber(x) then
			local x = Enum.HumanoidStateType[args[1]]
		end
		speaker.Character:FindFirstChildOfClass("Humanoid"):SetStateEnabled(x, false)
	end)

	addcmd('drophats',{'drophat'},function(args, speaker)
		if speaker.Character then
			for _,v in pairs(speaker.Character.Humanoid:GetAccessories()) do
				v.Parent = workspace
			end
		end
	end)

	addcmd('deletehats',{'nohats','rhats'},function(args, speaker)
		if speaker.Character then
			speaker.Character:FindFirstChildOfClass("Humanoid"):RemoveAccessories()
		end
	end)

	addcmd('droptools',{'droptool'},function(args, speaker)
		for i,v in pairs(Players.LocalPlayer.Backpack:GetChildren()) do
			if v:IsA("Tool") then
				v.Parent = Players.LocalPlayer.Character
			end
		end
		wait()
		for i,v in pairs(Players.LocalPlayer.Character:GetChildren()) do
			if v:IsA("Tool") then
				v.Parent = workspace
			end
		end
	end)

	addcmd('droppabletools',{},function(args, speaker)
		if speaker.Character then
			for _,obj in pairs(speaker.Character:GetChildren()) do
				if obj:IsA("Tool") then
					obj.CanBeDropped = true
				end
			end
		end
		if speaker:FindFirstChildOfClass("Backpack") then
			for _,obj in pairs(speaker:FindFirstChildOfClass("Backpack"):GetChildren()) do
				if obj:IsA("Tool") then
					obj.CanBeDropped = true
				end
			end
		end
	end)

	local currentToolSize = ""
	local currentGripPos = ""
	addcmd('reach',{},function(args, speaker)
		execCmd('unreach')
		wait()
		for i,v in pairs(speaker.Character:GetDescendants()) do
			if v:IsA("Tool") then
				if args[1] then
					currentToolSize = v.Handle.Size
					currentGripPos = v.GripPos
					local a = Instance.new("SelectionBox")
					a.Name = "SelectionBoxCreated"
					a.Parent = v.Handle
					a.Adornee = v.Handle
					v.Handle.Massless = true
					v.Handle.Size = Vector3.new(0.5,0.5,args[1])
					v.GripPos = Vector3.new(0,0,0)
					speaker.Character.Humanoid:UnequipTools()
				else
					currentToolSize = v.Handle.Size
					currentGripPos = v.GripPos
					local a = Instance.new("SelectionBox")
					a.Name = "SelectionBoxCreated"
					a.Parent = v.Handle
					a.Adornee = v.Handle
					v.Handle.Massless = true
					v.Handle.Size = Vector3.new(0.5,0.5,60)
					v.GripPos = Vector3.new(0,0,0)
					speaker.Character.Humanoid:UnequipTools()
				end
			end
		end
	end)

	addcmd('unreach',{'noreach'},function(args, speaker)
		for i,v in pairs(speaker.Character:GetDescendants()) do
			if v:IsA("Tool") then
				v.Handle.Size = currentToolSize
				v.GripPos = currentGripPos
				v.Handle.SelectionBoxCreated:Destroy()
			end
		end
	end)

	addcmd('grippos',{},function(args, speaker)
		for i,v in pairs(speaker.Character:GetDescendants()) do
			if v:IsA("Tool") then
				v.Parent = speaker:FindFirstChildOfClass("Backpack")
				v.GripPos = Vector3.new(args[1],args[2],args[3])
				v.Parent = speaker.Character
			end
		end
	end)

	addcmd('usetools', {}, function(args, speaker)
		local Backpack = speaker:FindFirstChildOfClass("Backpack")
		local ammount = tonumber(args[1]) or 1
		local delay_ = tonumber(args[2]) or false
		for _, v in ipairs(Backpack:GetChildren()) do
			v.Parent = speaker.Character
			coroutine.wrap(function()
				for _ = 1, ammount do
					v:Activate()
					if delay_ then
						wait(delay_)
					end
				end
				v.Parent = Backpack
			end)()
		end
	end)

	addcmd('logs',{},function(args, speaker)
		logs:TweenPosition(UDim2.new(0, 0, 1, -265), "InOut", "Quart", 0.3, true, nil)
	end)

	addcmd('chatlogs',{'clogs'},function(args, speaker)
		join.Visible = false
		chat.Visible = true
		table.remove(shade3,table.find(shade3,selectChat))
		table.remove(shade2,table.find(shade2,selectJoin))
		table.insert(shade2,selectChat)
		table.insert(shade3,selectJoin)
		selectJoin.BackgroundColor3 = currentShade3
		selectChat.BackgroundColor3 = currentShade2
		logs:TweenPosition(UDim2.new(0, 0, 1, -265), "InOut", "Quart", 0.3, true, nil)
	end)

	addcmd('joinlogs',{'jlogs'},function(args, speaker)
		chat.Visible = false
		join.Visible = true	
		table.remove(shade3,table.find(shade3,selectJoin))
		table.remove(shade2,table.find(shade2,selectChat))
		table.insert(shade2,selectJoin)
		table.insert(shade3,selectChat)
		selectChat.BackgroundColor3 = currentShade3
		selectJoin.BackgroundColor3 = currentShade2
		logs:TweenPosition(UDim2.new(0, 0, 1, -265), "InOut", "Quart", 0.3, true, nil)
	end)

	flinging = false
	addcmd('fling',{},function(args, speaker)
		for _, child in pairs(speaker.Character:GetDescendants()) do
			if child:IsA("BasePart") then
				child.CustomPhysicalProperties = PhysicalProperties.new(2, 0.3, 0.5)
			end
		end
		execCmd('noclip nonotify')
		wait(.1)
		local bambam = Instance.new("BodyAngularVelocity")
		bambam.Name = randomString()
		bambam.Parent = getRoot(speaker.Character)
		bambam.AngularVelocity = Vector3.new(0,311111,0)
		bambam.MaxTorque = Vector3.new(0,311111,0)
		bambam.P = math.huge
		local function PauseFling()
			if speaker.Character:FindFirstChildOfClass("Humanoid") then
				if speaker.Character:FindFirstChildOfClass("Humanoid").FloorMaterial == Enum.Material.Air then
					bambam.AngularVelocity = Vector3.new(0,0,0)
				else
					bambam.AngularVelocity = Vector3.new(0,311111,0)
				end
			end
		end
		if TouchingFloor then
			TouchingFloor:Disconnect()
		end
		if TouchingFloorReset then
			TouchingFloorReset:Disconnect()
		end
		TouchingFloor = speaker.Character:FindFirstChildOfClass("Humanoid"):GetPropertyChangedSignal("FloorMaterial"):Connect(PauseFling)
		flinging = true
		local function flingDied()
			execCmd('unfling')
		end
		TouchingFloorReset = speaker.Character:FindFirstChildOfClass('Humanoid').Died:Connect(flingDied)
	end)

	addcmd('unfling',{'nofling'},function(args, speaker)
		execCmd('clip nonotify')
		if TouchingFloor then
			TouchingFloor:Disconnect()
		end
		if TouchingFloorReset then
			TouchingFloorReset:Disconnect()
		end
		flinging = false
		wait(.1)
		local speakerChar = speaker.Character
		if not speakerChar or not getRoot(speakerChar) then return end
		for i,v in pairs(getRoot(speakerChar):GetChildren()) do
			if v.ClassName == 'BodyAngularVelocity' then
				v:Destroy()
			end
		end
		for _, child in pairs(speakerChar:GetDescendants()) do
			if child.ClassName == "Part" or child.ClassName == "MeshPart" then
				child.CustomPhysicalProperties = PhysicalProperties.new(0.7, 0.3, 0.5)
			end
		end
	end)

	addcmd('togglefling',{},function(args, speaker)
		if flinging then
			execCmd('unfling')
		else
			execCmd('fling')
		end
	end)

	addcmd('invisfling',{},function(args, speaker)
		local ch = speaker.Character
		local prt=Instance.new("Model")
		prt.Parent = speaker.Character
		local z1 = Instance.new("Part")
		z1.Name="Torso"
		z1.CanCollide = false
		z1.Anchored = true
		local z2 = Instance.new("Part")
		z2.Name="Head"
		z2.Parent = prt
		z2.Anchored = true
		z2.CanCollide = false
		local z3 =Instance.new("Humanoid")
		z3.Name="Humanoid"
		z3.Parent = prt
		z1.Position = Vector3.new(0,9999,0)
		speaker.Character=prt
		wait(3)
		speaker.Character=ch
		wait(3)
		local Hum = Instance.new("Humanoid")
		z2:Clone()
		Hum.Parent = speaker.Character
		local root =  getRoot(speaker.Character)
		for i,v in pairs(speaker.Character:GetChildren()) do
			if v ~= root and  v.Name ~= "Humanoid" then
				v:Destroy()
			end
		end
		root.Transparency = 0
		root.Color = Color3.new(1, 1, 1)
		local invisflingStepped
		invisflingStepped = game:GetService('RunService').Stepped:Connect(function()
			if speaker.Character and getRoot(speaker.Character) then
				getRoot(speaker.Character).CanCollide = false
			else
				invisflingStepped:Disconnect()
			end
		end)
		sFLY()
		workspace.CurrentCamera.CameraSubject = root
		local bambam = Instance.new("BodyThrust")
		bambam.Parent = getRoot(speaker.Character)
		bambam.Force = Vector3.new(99999,99999*10,99999)
		bambam.Location = getRoot(speaker.Character).Position
	end)

	function attach(speaker,target)
		if tools(speaker) then
			local char = speaker.Character
			local tchar = target.Character
			local hum = speaker.Character:FindFirstChildOfClass("Humanoid")
			local hrp = getRoot(speaker.Character)
			local hrp2 = getRoot(target.Character)
			hum.Name = "1"
			local newHum = hum:Clone()
			newHum.Parent = char
			newHum.Name = "Humanoid"
			wait()
			hum:Destroy()
			workspace.CurrentCamera.CameraSubject = char
			newHum.DisplayDistanceType = "None"
			local tool = speaker:FindFirstChildOfClass("Backpack"):FindFirstChildOfClass("Tool") or speaker.Character:FindFirstChildOfClass("Tool")
			tool.Parent = char
			hrp.CFrame = hrp2.CFrame * CFrame.new(0, 0, 0) * CFrame.new(math.random(-100, 100)/200,math.random(-100, 100)/200,math.random(-100, 100)/200)
			local n = 0
			repeat
				wait(.1)
				n = n + 1
				hrp.CFrame = hrp2.CFrame
			until (tool.Parent ~= char or not hrp or not hrp2 or not hrp.Parent or not hrp2.Parent or n > 250) and n > 2
		else
			notify('Tool Required','You need to have an item in your inventory to use this command')
		end
	end

	addcmd('attach',{},function(args, speaker)
		local players = getPlayer(args[1], speaker)
		for i,v in pairs(players) do
			attach(speaker,Players[v])
		end
	end)

	function kill(speaker,target,fast)
		if tools(speaker) then
			if target ~= nil then
				local NormPos = getRoot(speaker.Character).CFrame
				if not fast then
					refresh(speaker)
					wait()
					repeat wait() until speaker.Character ~= nil and getRoot(speaker.Character)
					wait(0.3)
				end
				local hrp = getRoot(speaker.Character)
				attach(speaker,target)
				repeat
					wait()
					hrp.CFrame = CFrame.new(999999, workspace.FallenPartsDestroyHeight + 5,999999)
				until not getRoot(target.Character) or not getRoot(speaker.Character)
				wait(1)
				speaker.CharacterAdded:Wait():WaitForChild("HumanoidRootPart").CFrame = NormPos
			end
		else
			notify('Tool Required','You need to have an item in your inventory to use this command')
		end
	end

	addcmd('kill',{'fekill'},function(args, speaker)
		local players = getPlayer(args[1], speaker)
		for i,v in pairs(players) do
			kill(speaker,Players[v])
		end
	end)

	addcmd('handlekill', {'hkill'}, function(args, speaker)
		if not firetouchinterest then
			return notify('Incompatible Exploit', 'Your exploit does not support this command (missing firetouchinterest)')
		end
		local RS = game:GetService("RunService").RenderStepped
		local Tool = speaker.Character.FindFirstChildWhichIsA(speaker.Character, "Tool")
		local Handle = Tool and Tool.FindFirstChild(Tool, "Handle")
		if not Tool or not Handle then
			return notify("Handle Kill", "You need to hold a \"Tool\" that does damage on touch. For example the default \"Sword\" tool.")
		end
		for _, v in ipairs(getPlayer(args[1], speaker)) do
			v = Players[v]
			spawn(function()
				while Tool and speaker.Character and v.Character and Tool.Parent == speaker.Character do
					local Human = v.Character.FindFirstChildWhichIsA(v.Character, "Humanoid")
					if not Human or Human.Health <= 0 then
						break
					end
					for _, v1 in ipairs(v.Character.GetChildren(v.Character)) do
						v1 = ((v1.IsA(v1, "BasePart") and firetouchinterest(Handle, v1, 1, (RS.Wait(RS) and nil) or firetouchinterest(Handle, v1, 0)) and nil) or v1) or v1
					end
				end
				notify("Handle Kill Stopped!", v.Name .. " died/left or you unequiped the tool!")
			end)
		end
	end)

	addcmd('fastkill',{'fastfekill'},function(args, speaker)
		local players = getPlayer(args[1], speaker)
		for i,v in pairs(players) do
			kill(speaker,Players[v],true)
		end
	end)

	function bring(speaker,target,fast)
		if tools(speaker) then
			if target ~= nil then
				local NormPos = getRoot(speaker.Character).CFrame
				if not fast then
					refresh(speaker)
					wait()
					repeat wait() until speaker.Character ~= nil and getRoot(speaker.Character)
					wait(0.3)
				end
				local hrp = getRoot(speaker.Character)
				attach(speaker,target)
				repeat
					wait()
					hrp.CFrame = NormPos
				until not getRoot(target.Character) or not getRoot(speaker.Character)
				wait(1)
				speaker.CharacterAdded:Wait():WaitForChild("HumanoidRootPart").CFrame = NormPos
			end
		else
			notify('Tool Required','You need to have an item in your inventory to use this command')
		end
	end

	addcmd('bring',{'febring'},function(args, speaker)
		local players = getPlayer(args[1], speaker)
		for i,v in pairs(players) do
			bring(speaker,Players[v])
		end
	end)

	addcmd('fastbring',{'fastfebring'},function(args, speaker)
		local players = getPlayer(args[1], speaker)
		for i,v in pairs(players) do
			bring(speaker,Players[v],true)
		end
	end)

	function teleport(speaker,target,target2,fast)
		if tools(speaker) then
			if target ~= nil then
				local NormPos = getRoot(speaker.Character).CFrame
				if not fast then
					refresh(speaker)
					wait()
					repeat wait() until speaker.Character ~= nil and getRoot(speaker.Character)
					wait(0.3)
				end
				local hrp = getRoot(speaker.Character)
				local hrp2 = getRoot(target2.Character)
				attach(speaker,target)
				repeat
					wait()
					hrp.CFrame = hrp2.CFrame
				until not getRoot(target.Character) or not getRoot(speaker.Character)
				wait(1)
				speaker.CharacterAdded:Wait():WaitForChild("HumanoidRootPart").CFrame = NormPos
			end
		else
			notify('Tool Required','You need to have an item in your inventory to use this command')
		end
	end

	addcmd('tp',{'teleport'},function(args, speaker)
		local players1=getPlayer(args[1], speaker)
		local players2=getPlayer(args[2], speaker)
		for i,v in pairs(players1)do
			if getRoot(Players[v].Character) and getRoot(Players[players2[1]].Character) then
				if speaker.Character:FindFirstChildOfClass('Humanoid') and speaker.Character:FindFirstChildOfClass('Humanoid').SeatPart then
					speaker.Character:FindFirstChildOfClass('Humanoid').Sit = false
					wait(.1)
				end
				teleport(speaker,Players[v],Players[players2[1]])
			end
		end
	end)

	addcmd('fasttp',{'fastteleport'},function(args, speaker)
		local players1=getPlayer(args[1], speaker)
		local players2=getPlayer(args[2], speaker)
		for i,v in pairs(players1)do
			if getRoot(Players[v].Character) and getRoot(Players[players2[1]].Character) then
				if speaker.Character:FindFirstChildOfClass('Humanoid') and speaker.Character:FindFirstChildOfClass('Humanoid').SeatPart then
					speaker.Character:FindFirstChildOfClass('Humanoid').Sit = false
					wait(.1)
				end
				teleport(speaker,Players[v],Players[players2[1]],true)
			end
		end
	end)

	addcmd('spin',{},function(args, speaker)
		local spinSpeed = 20
		if args[1] and isNumber(args[1]) then
			spinSpeed = args[1]
		end
		for i,v in pairs(getRoot(speaker.Character):GetChildren()) do
			if v.Name == "Spinning" then
				v:Destroy()
			end
		end
		local Spin = Instance.new("BodyAngularVelocity")
		Spin.Name = "Spinning"
		Spin.Parent = getRoot(speaker.Character)
		Spin.MaxTorque = Vector3.new(0, math.huge, 0)
		Spin.AngularVelocity = Vector3.new(0,spinSpeed,0)
	end)

	addcmd('unspin',{},function(args, speaker)
		for i,v in pairs(getRoot(speaker.Character):GetChildren()) do
			if v.Name == "Spinning" then
				v:Destroy()
			end
		end
	end)

	local transparent = false
	function x(v)
		if v then
			for _,i in pairs(workspace:GetDescendants()) do
				if i:IsA("BasePart") and not i.Parent:FindFirstChild("Humanoid") and not i.Parent.Parent:FindFirstChild("Humanoid") then
					i.LocalTransparencyModifier = 0.5
				end
			end
		else
			for _,i in pairs(workspace:GetDescendants()) do
				if i:IsA("BasePart") and not i.Parent:FindFirstChild("Humanoid") and not i.Parent.Parent:FindFirstChild("Humanoid") then
					i.LocalTransparencyModifier = 0
				end
			end
		end
	end

	addcmd('xray',{},function(args, speaker)
		transparent = true
		x(transparent)
	end)

	addcmd('unxray',{'noxray'},function(args, speaker)
		transparent = false
		x(transparent)
	end)

	addcmd('togglexray',{},function(args, speaker)
		transparent=not transparent
		x(transparent)
	end)

	local walltpTouch = nil
	addcmd('walltp',{},function(args, speaker)
		local torso
		if r15(speaker) then
			torso = speaker.Character.UpperTorso
		else
			torso = speaker.Character.Torso
		end
		local function touchedFunc(hit)
			local Root = getRoot(speaker.Character)
			if hit:IsA("BasePart") and hit.Position.Y > Root.Position.Y - speaker.Character.Humanoid.HipHeight then
				local hitP = getRoot(hit.Parent)
				if hitP ~= nil then
					Root.CFrame = hit.CFrame * CFrame.new(Root.CFrame.lookVector.X,hitP.Size.Z/2 + speaker.Character.Humanoid.HipHeight,Root.CFrame.lookVector.Z)
				elseif hitP == nil then
					Root.CFrame = hit.CFrame * CFrame.new(Root.CFrame.lookVector.X,hit.Size.Y/2 + speaker.Character.Humanoid.HipHeight,Root.CFrame.lookVector.Z)
				end
			end
		end
		walltpTouch = torso.Touched:Connect(touchedFunc)
	end)

	addcmd('unwalltp',{'nowalltp'},function(args, speaker)
		if walltpTouch then
			walltpTouch:Disconnect()
		end
	end)

	autoclicking = false
	addcmd('autoclick',{},function(args, speaker)
		if mouse1press and mouse1release then
			execCmd('unautoclick')
			wait()
			local clickDelay = 0.1
			local releaseDelay = 0.1
			if args[1] and isNumber(args[1]) then clickDelay = args[1] end
			if args[2] and isNumber(args[2]) then releaseDelay = args[2] end
			autoclicking = true
			cancelAutoClick = UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
				if not gameProcessedEvent then
					if (input.KeyCode == Enum.KeyCode.Backspace and UserInputService:IsKeyDown(Enum.KeyCode.Equals)) or (input.KeyCode == Enum.KeyCode.Equals and UserInputService:IsKeyDown(Enum.KeyCode.Backspace)) then
						autoclicking = false
						cancelAutoClick:Disconnect()
					end
				end
			end)
			notify('Auto Clicker',"Press [backspace] and [=] at the same time to stop")
			repeat wait(clickDelay)
				mouse1press()
				wait(releaseDelay)
				mouse1release()
			until autoclicking == false
		else
			notify('Auto Clicker',"Your exploit doesn't have the ability to use the autoclick")
		end
	end)

	addcmd('unautoclick',{'noautoclick'},function(args, speaker)
		autoclicking = false
		if cancelAutoClick then cancelAutoClick:Disconnect() end
	end)

	addcmd('mousesensitivity',{'ms'},function(args, speaker)
		UserInputService.MouseDeltaSensitivity = args[1]
	end)

	local nameBox = nil
	local nbSelection = nil
	addcmd('hovername',{},function(args, speaker)
		execCmd('unhovername')
		wait()
		nameBox = Instance.new("TextLabel")
		nameBox.Name = randomString()
		nameBox.Parent = PARENT
		nameBox.BackgroundTransparency = 1
		nameBox.Size = UDim2.new(0,200,0,30)
		nameBox.Font = Enum.Font.Code
		nameBox.TextSize = 16
		nameBox.Text = ""
		nameBox.TextColor3 = Color3.new(1, 1, 1)
		nameBox.TextStrokeTransparency = 0
		nameBox.TextXAlignment = Enum.TextXAlignment.Left
		nameBox.ZIndex = 10
		nbSelection = Instance.new('SelectionBox')
		nbSelection.Name = randomString()
		nbSelection.LineThickness = 0.03
		nbSelection.Color3 = Color3.new(1, 1, 1)
		local function updateNameBox()
			local t
			local target = IYMouse.Target

			if target then
				local humanoid = target.Parent:FindFirstChild('Humanoid') or target.Parent.Parent:FindFirstChild('Humanoid')
				if humanoid then
					t = humanoid.Parent
				end
			end

			if t ~= nil then
				local x = IYMouse.X
				local y = IYMouse.Y
				local xP
				local yP
				if IYMouse.X > 200 then
					xP = x - 205
					nameBox.TextXAlignment = Enum.TextXAlignment.Right
				else
					xP = x + 25
					nameBox.TextXAlignment = Enum.TextXAlignment.Left
				end
				nameBox.Position = UDim2.new(0, xP, 0, y)
				nameBox.Text = t.Name
				nameBox.Visible = true
				nbSelection.Parent = t
				nbSelection.Adornee = t
			else
				nameBox.Visible = false
				nbSelection.Parent = nil
				nbSelection.Adornee = nil
			end
		end
		nbUpdateFunc = IYMouse.Move:Connect(updateNameBox)
	end)

	addcmd('unhovername',{'nohovername'},function(args, speaker)
		if nbUpdateFunc then
			nbUpdateFunc:Disconnect()
			nameBox:Destroy()
			nbSelection:Destroy()
		end
	end)

	addcmd('hitbox',{},function(args, speaker)
		local players = getPlayer(args[1], speaker)
		for i,v in pairs(players) do
			if Players[v]~= speaker and Players[v].Character:FindFirstChild('Head') then
				local sizeArg = tonumber(args[2])
				local Size = Vector3.new(sizeArg,sizeArg,sizeArg)
				local Head = Players[v].Character:FindFirstChild('Head')
				if Head:IsA("BasePart") then
					if not args[2] or sizeArg == 1 then
						Head.Size = Vector3.new(2,1,1)
					else
						Head.Size = Size
					end
				end
			end
		end
	end)

	addcmd('stareat',{'stare'},function(args, speaker)
		local players = getPlayer(args[1], speaker)
		for i,v in pairs(players) do
			if stareLoop then
				stareLoop:Disconnect()
			end
			if not Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") and Players[v].Character:FindFirstChild("HumanoidRootPart") then return end
			local function stareFunc()
				if Players.LocalPlayer.Character.PrimaryPart and Players:FindFirstChild(v) and Players[v].Character ~= nil and Players[v].Character:FindFirstChild("HumanoidRootPart") then
					local chrPos=Players.LocalPlayer.Character.PrimaryPart.Position
					local tPos=Players[v].Character:FindFirstChild("HumanoidRootPart").Position
					local modTPos=Vector3.new(tPos.X,chrPos.Y,tPos.Z)
					local newCF=CFrame.new(chrPos,modTPos)
					Players.LocalPlayer.Character:SetPrimaryPartCFrame(newCF)
				elseif not Players:FindFirstChild(v) then
					stareLoop:Disconnect()
				end
			end

			stareLoop = game:GetService("RunService").RenderStepped:Connect(stareFunc)
		end
	end)

	addcmd('unstareat',{'unstare','nostare','nostareat'},function(args, speaker)
		if stareLoop then
			stareLoop:Disconnect()
		end
	end)

	addcmd('removeterrain',{'rterrain','noterrain'},function(args, speaker)
		workspace:FindFirstChildOfClass('Terrain'):Clear()
	end)

	addcmd('clearnilinstances',{'nonilinstances','cni'},function(args, speaker)
		if getnilinstances then
			for i,v in pairs(getnilinstances()) do
				v:Destroy()
			end
		else
			notify('Incompatible Exploit','Your exploit does not support this command (missing getnilinstances)')
		end
	end)

	addcmd('destroyheight',{'dh'},function(args, speaker)
		local dh = args[1] or -500
		if isNumber(dh) then
			workspace.FallenPartsDestroyHeight = dh
		end
	end)

	local freezingua = nil
	frozenParts = {}
	addcmd('freezeunanchored',{'freezeua'},function(args, speaker)
		if sethidden then
			local badnames = {
				"Head",
				"UpperTorso",
				"LowerTorso",
				"RightUpperArm",
				"LeftUpperArm",
				"RightLowerArm",
				"LeftLowerArm",
				"RightHand",
				"LeftHand",
				"RightUpperLeg",
				"LeftUpperLeg",
				"RightLowerLeg",
				"LeftLowerLeg",
				"RightFoot",
				"LeftFoot",
				"Torso",
				"Right Arm",
				"Left Arm",
				"Right Leg",
				"Left Leg",
				"HumanoidRootPart"
			}
			local function FREEZENOOB(v)
				if v:IsA("BasePart" or "UnionOperation") and v.Anchored == false then
					local BADD = false
					for i = 1,#badnames do
						if v.Name == badnames[i] then
							BADD = true
						end
					end
					if speaker.Character and v:IsDescendantOf(speaker.Character) then
						BADD = true
					end
					if BADD == false then
						for i,c in pairs(v:GetChildren()) do
							if c:IsA("BodyPosition") or c:IsA("BodyGyro") then
								c:Destroy()
							end
						end
						if not simRadius then
							execCmd('simulationradius')
						end
						local bodypos = Instance.new("BodyPosition")
						bodypos.Parent = v
						bodypos.Position = v.Position
						bodypos.MaxForce = Vector3.new(math.huge,math.huge,math.huge)
						local bodygyro = Instance.new("BodyGyro")
						bodygyro.Parent = v
						bodygyro.CFrame = v.CFrame
						bodygyro.MaxTorque = Vector3.new(math.huge,math.huge,math.huge)
						if not table.find(frozenParts,v) then
							table.insert(frozenParts,v)
						end
					end
				end
			end
			for i,v in pairs(workspace:GetDescendants()) do
				FREEZENOOB(v)
			end
			freezingua = workspace.DescendantAdded:Connect(FREEZENOOB)
		else
			notify('Incompatible Exploit','Your exploit does not support this command (missing sethiddenproperty)')
		end
	end)

	addcmd('thawunanchored',{'thawua','unfreezeunanchored','unfreezeua'},function(args, speaker)
		if sethidden then
			if freezingua then
				freezingua:Disconnect()
			end
			if not simRadius then
				execCmd('simulationradius')
			end
			for i,v in pairs(frozenParts) do
				for i,c in pairs(v:GetChildren()) do
					if c:IsA("BodyPosition") or c:IsA("BodyGyro") then
						c:Destroy()
					end
				end
			end
			frozenParts = {}
		else
			notify('Incompatible Exploit','Your exploit does not support this command (missing sethiddenproperty)')
		end
	end)

	addcmd('tpunanchored',{'tpua'},function(args, speaker)
		if sethidden then
			local players = getPlayer(args[1], speaker)
			for i,v in pairs(players) do
				local Forces = {}
				for _,part in pairs(workspace:GetDescendants()) do
					if Players[v].Character:FindFirstChild('Head') and part:IsA("BasePart" or "UnionOperation" or "Model") and part.Anchored == false and not part:IsDescendantOf(speaker.Character) and part.Name == "Torso" == false and part.Name == "Head" == false and part.Name == "Right Arm" == false and part.Name == "Left Arm" == false and part.Name == "Right Leg" == false and part.Name == "Left Leg" == false and part.Name == "HumanoidRootPart" == false then
						for i,c in pairs(part:GetChildren()) do
							if c:IsA("BodyPosition") or c:IsA("BodyGyro") then
								c:Destroy()
							end
						end
						local ForceInstance = Instance.new("BodyPosition")
						ForceInstance.Parent = part
						ForceInstance.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
						table.insert(Forces, ForceInstance)
						if not table.find(frozenParts,part) then
							table.insert(frozenParts,part)
						end
					end
				end
				if not simRadius then
					execCmd('simulationradius')
				end
				for i,c in pairs(Forces) do
					c.Position = Players[v].Character.Head.Position
				end
			end
		else
			notify('Incompatible Exploit','Your exploit does not support this command (missing sethiddenproperty)')
		end
	end)

	keycodeMap = {
		["0"] = 0x30,
		["1"] = 0x31,
		["2"] = 0x32,
		["3"] = 0x33,
		["4"] = 0x34,
		["5"] = 0x35,
		["6"] = 0x36,
		["7"] = 0x37,
		["8"] = 0x38,
		["9"] = 0x39,
		["a"] = 0x41,
		["b"] = 0x42,
		["c"] = 0x43,
		["d"] = 0x44,
		["e"] = 0x45,
		["f"] = 0x46,
		["g"] = 0x47,
		["h"] = 0x48,
		["i"] = 0x49,
		["j"] = 0x4A,
		["k"] = 0x4B,
		["l"] = 0x4C,
		["m"] = 0x4D,
		["n"] = 0x4E,
		["o"] = 0x4F,
		["p"] = 0x50,
		["q"] = 0x51,
		["r"] = 0x52,
		["s"] = 0x53,
		["t"] = 0x54,
		["u"] = 0x55,
		["v"] = 0x56,
		["w"] = 0x57,
		["x"] = 0x58,
		["y"] = 0x59,
		["z"] = 0x5A,
		["enter"] = 0x0D,
		["shift"] = 0x10,
		["ctrl"] = 0x11,
		["alt"] = 0x12,
		["pause"] = 0x13,
		["capslock"] = 0x14,
		["spacebar"] = 0x20,
		["pageup"] = 0x21,
		["pagedown"] = 0x22,
		["end"] = 0x23,
		["home"] = 0x24,
		["left"] = 0x25,
		["up"] = 0x26,
		["right"] = 0x27,
		["down"] = 0x28,
		["insert"] = 0x2D,
		["delete"] = 0x2E,
		["f1"] = 0x70,
		["f2"] = 0x71,
		["f3"] = 0x72,
		["f4"] = 0x73,
		["f5"] = 0x74,
		["f6"] = 0x75,
		["f7"] = 0x76,
		["f8"] = 0x77,
		["f9"] = 0x78,
		["f10"] = 0x79,
		["f11"] = 0x7A,
		["f12"] = 0x7B,
	}
	autoKeyPressing = false
	cancelAutoKeyPress = nil

	addcmd('autokeypress',{'keypress'},function(args, speaker)
		if keypress and keyrelease and args[1] then
			local code = keycodeMap[args[1]:lower()]
			if not code then notify('Auto Key Press',"Invalid key") return end
			execCmd('unautokeypress')
			wait()
			local clickDelay = 0.1
			local releaseDelay = 0.1
			if args[2] and isNumber(args[2]) then clickDelay = args[2] end
			if args[3] and isNumber(args[3]) then releaseDelay = args[3] end
			autoKeyPressing = true
			cancelAutoKeyPress = UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
				if not gameProcessedEvent then
					if (input.KeyCode == Enum.KeyCode.Backspace and UserInputService:IsKeyDown(Enum.KeyCode.Equals)) or (input.KeyCode == Enum.KeyCode.Equals and UserInputService:IsKeyDown(Enum.KeyCode.Backspace)) then
						autoKeyPressing = false
						cancelAutoKeyPress:Disconnect()
					end
				end
			end)
			notify('Auto Key Press',"Press [backspace] and [=] at the same time to stop")
			repeat wait(clickDelay)
				keypress(code)
				wait(releaseDelay)
				keyrelease(code)
			until autoKeyPressing == false
			if cancelAutoKeyPress then cancelAutoKeyPress:Disconnect() keyrelease(code) end
		else
			notify('Auto Key Press',"Your exploit doesn't have the ability to use auto key press")
		end
	end)

	addcmd('unautokeypress',{'noautokeypress','unkeypress','nokeypress'},function(args, speaker)
		autoKeyPressing = false
		if cancelAutoKeyPress then cancelAutoKeyPress:Disconnect() end
	end)

	addcmd('addplugin',{'plugin'},function(args, speaker)
		addPlugin(getstring(1))
	end)

	addcmd('removeplugin',{'deleteplugin'},function(args, speaker)
		deletePlugin(getstring(1))
	end)

	addcmd('reloadplugin',{},function(args, speaker)
		local pluginName = getstring(1)
		deletePlugin(pluginName)
		wait(1)
		addPlugin(pluginName)
	end)

	addcmd('removecmd',{'deletecmd'},function(args, speaker)
		removecmd(args[1])
	end)

	updateColors(currentShade1,shade1)
	updateColors(currentShade2,shade2)
	updateColors(currentShade3,shade3)
	updateColors(currentText1,text1)
	updateColors(currentText2,text2)
	updateColors(currentScroll,scroll)

	if PluginsTable ~= nil or PluginsTable ~= {} then
		FindPlugins(PluginsTable)
	end

	-- Events
	eventEditor.RegisterEvent("OnExecute")
	eventEditor.RegisterEvent("OnSpawn",{
		{Type="Player",Name="Player Filter ($1)"}
	})
	eventEditor.RegisterEvent("OnDied",{
		{Type="Player",Name="Player Filter ($1)"}
	})
	eventEditor.RegisterEvent("OnDamage",{
		{Type="Player",Name="Player Filter ($1)"},
		{Type="Number",Name="Below Health ($2)"}
	})
	eventEditor.RegisterEvent("OnKilled",{
		{Type="Player",Name="Victim Player ($1)"},
		{Type="Player",Name="Killer Player ($2)",Default = 1}
	})
	eventEditor.RegisterEvent("OnJoin",{
		{Type="Player",Name="Player Filter ($1)",Default = 1}
	})
	eventEditor.RegisterEvent("OnChatted",{
		{Type="Player",Name="Player Filter ($1)",Default = 1},
		{Type="String",Name="Message Filter ($2)"}
	})

	function hookCharEvents(plr,instant)
		spawn(function()
			local char = plr.Character
			if not char then return end

			local humanoid = char:WaitForChild("Humanoid",10)
			if not humanoid then return end

			local oldHealth = humanoid.Health
			humanoid.HealthChanged:Connect(function(health)
				local change = math.abs(oldHealth - health)
				if oldHealth > health then
					eventEditor.FireEvent("OnDamage",plr.Name,tonumber(health))
				end
				oldHealth = health
			end)

			humanoid.Died:Connect(function()
				eventEditor.FireEvent("OnDied",plr.Name)

				local killedBy = humanoid:FindFirstChild("creator")
				if killedBy and killedBy.Value and killedBy.Value.Parent then
					eventEditor.FireEvent("OnKilled",plr.Name,killedBy.Name)
				end
			end)
		end)
	end

	Players.PlayerAdded:Connect(function(plr)
		eventEditor.FireEvent("OnJoin",plr.Name)
		plr.Chatted:Connect(function(msg) eventEditor.FireEvent("OnChatted",tostring(plr),msg) end)
		plr.CharacterAdded:Connect(function() eventEditor.FireEvent("OnSpawn",tostring(plr)) hookCharEvents(plr) end)
		JoinLog(plr)
		ChatLog(plr)
		if ESPenabled then
			repeat wait(1) until plr.Character and getRoot(plr.Character)
			ESP(plr)
		end
		if CHMSenabled then
			repeat wait(1) until plr.Character and getRoot(plr.Character)
			CHMS(plr)
		end
	end)

	for _,plr in pairs(Players:GetPlayers()) do
		pcall(function()
			plr.Chatted:Connect(function(msg) eventEditor.FireEvent("OnChatted",tostring(plr),msg) end)
			plr.CharacterAdded:Connect(function() eventEditor.FireEvent("OnSpawn",tostring(plr)) hookCharEvents(plr) end)
			hookCharEvents(plr)
		end)
	end

	if spawnCmds and #spawnCmds > 0 then
		for i,v in pairs(spawnCmds) do
			eventEditor.AddCmd("OnSpawn",{v.COMMAND or "",{0},v.DELAY or 0})
		end
		updatesaves()
	end

	if loadedEventData then eventEditor.LoadData(loadedEventData) end
	eventEditor.Refresh()

	eventEditor.FireEvent("OnExecute")

	if aliases and #aliases > 0 then
		local cmdMap = {}
		for i,v in pairs(cmds) do
			cmdMap[v.NAME:lower()] = v
			for _,alias in pairs(v.ALIAS) do
				cmdMap[alias:lower()] = v
			end
		end
		for i = 1, #aliases do
			local cmd = string.lower(aliases[i].CMD)
			local alias = string.lower(aliases[i].ALIAS)
			if cmdMap[cmd] then
				customAlias[alias] = cmdMap[cmd]
			end
		end
		refreshaliases()
	end

	IYMouse.Move:Connect(checkTT)

	spawn(function()
		if pcall(function() loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/version'))() end) then
			if ver ~= Version then
				notify('Outdated','Get the new version at infyield.yolasite.com')
			end
			if Announcement and Announcement ~= '' then
				local AnnGUI = Instance.new("Frame")
				local background = Instance.new("Frame")
				local TextBox = Instance.new("TextLabel")
				local shadow = Instance.new("Frame")
				local PopupText = Instance.new("TextLabel")
				local Exit = Instance.new("TextButton")
				local ExitImage = Instance.new("ImageLabel")

				AnnGUI.Name = randomString()
				AnnGUI.Parent = PARENT
				AnnGUI.Active = true
				AnnGUI.BackgroundTransparency = 1
				AnnGUI.Position = UDim2.new(0.5, -180, 0, -500)
				AnnGUI.Size = UDim2.new(0, 360, 0, 20)
				AnnGUI.ZIndex = 10

				background.Name = "background"
				background.Parent = AnnGUI
				background.Active = true
				background.BackgroundColor3 = currentShade1
				background.BorderSizePixel = 0
				background.Position = UDim2.new(0, 0, 0, 20)
				background.Size = UDim2.new(0, 360, 0, 150)
				background.ZIndex = 10

				TextBox.Parent = background
				TextBox.BackgroundTransparency = 1
				TextBox.Position = UDim2.new(0, 5, 0, 5)
				TextBox.Size = UDim2.new(0, 350, 0, 140)
				TextBox.Font = Enum.Font.SourceSans
				TextBox.TextSize = 18
				TextBox.TextWrapped = true
				TextBox.Text = Announcement
				TextBox.TextColor3 = currentText1
				TextBox.TextXAlignment = Enum.TextXAlignment.Left
				TextBox.TextYAlignment = Enum.TextYAlignment.Top
				TextBox.ZIndex = 10

				shadow.Name = "shadow"
				shadow.Parent = AnnGUI
				shadow.BackgroundColor3 = currentShade2
				shadow.BorderSizePixel = 0
				shadow.Size = UDim2.new(0, 360, 0, 20)
				shadow.ZIndex = 10

				PopupText.Name = "PopupText"
				PopupText.Parent = shadow
				PopupText.BackgroundTransparency = 1
				PopupText.Size = UDim2.new(1, 0, 0.95, 0)
				PopupText.ZIndex = 10
				PopupText.Font = Enum.Font.SourceSans
				PopupText.TextSize = 14
				PopupText.Text = "Server Announcement"
				PopupText.TextColor3 = currentText1
				PopupText.TextWrapped = true

				Exit.Name = "Exit"
				Exit.Parent = shadow
				Exit.BackgroundTransparency = 1
				Exit.Position = UDim2.new(1, -20, 0, 0)
				Exit.Size = UDim2.new(0, 20, 0, 20)
				Exit.Text = ""
				Exit.ZIndex = 10

				ExitImage.Parent = Exit
				ExitImage.BackgroundColor3 = Color3.new(1, 1, 1)
				ExitImage.BackgroundTransparency = 1
				ExitImage.Position = UDim2.new(0, 5, 0, 5)
				ExitImage.Size = UDim2.new(0, 10, 0, 10)
				ExitImage.Image = "rbxassetid://6412053682"
				ExitImage.ZIndex = 10

				wait(1)
				AnnGUI:TweenPosition(UDim2.new(0.5, -180, 0, 150), "InOut", "Quart", 0.5, true, nil)

				Exit.MouseButton1Click:Connect(function()
					AnnGUI:TweenPosition(UDim2.new(0.5, -180, 0, -500), "InOut", "Quart", 0.5, true, nil)
					wait(0.6)
					AnnGUI:Destroy()
				end)
			end
		end
	end)

	wait()
	Credits:TweenPosition(UDim2.new(0,0,0.9,0), "Out", "Quart", 0.2)
	Logo:TweenSizeAndPosition(UDim2.new(0,175,0,175),UDim2.new(0,37,0,45), "Out", "Quart", 0.3)
	wait(1)
	for i=0,1,0.1 do
		Logo.ImageTransparency = i
		IntroBackground.BackgroundTransparency = i
		wait()
	end
	Credits:TweenPosition(UDim2.new(0,0,0.9,30), "Out", "Quart", 0.2)
	wait(0.2)
	Logo:Destroy()
	Credits:Destroy()
	IntroBackground:Destroy()
	minimizeHolder()
