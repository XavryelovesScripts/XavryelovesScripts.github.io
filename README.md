-- Xavrye's fly script
-- Version: 1.0

-- Instances:

local FlyGUI = Instance.new("ScreenGui")
local DragFrame = Instance.new("TextLabel")
local UICorner = Instance.new("UICorner")
local TextButton = Instance.new("TextButton")
local UICorner_2 = Instance.new("UICorner")
local FlyFrame = Instance.new("Frame")
local UICorner_3 = Instance.new("UICorner")
local TextLabel = Instance.new("TextLabel")
local FlyBtn = Instance.new("TextButton")

--Properties:

FlyGUI.Name = "FlyGUI"
FlyGUI.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
FlyGUI.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

DragFrame.Name = "DragFrame"
DragFrame.Parent = FlyGUI
DragFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
DragFrame.Position = UDim2.new(0.258792758, 0, 0.767042756, 0)
DragFrame.Size = UDim2.new(0, 51, 0, 30)
DragFrame.Font = Enum.Font.FredokaOne
DragFrame.Text = "Drag"
DragFrame.TextColor3 = Color3.fromRGB(153, 153, 153)
DragFrame.TextSize = 20.000
DragFrame.TextStrokeColor3 = Color3.fromRGB(58, 58, 58)

UICorner.Parent = DragFrame

TextButton.Parent = DragFrame
TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton.Position = UDim2.new(-0.012379067, 0, 1.20000005, 0)
TextButton.Size = UDim2.new(0, 91, 0, 29)
TextButton.Font = Enum.Font.FredokaOne
TextButton.Text = "Toggle Gui"
TextButton.TextColor3 = Color3.fromRGB(153, 153, 153)
TextButton.TextSize = 18.000

UICorner_2.Parent = TextButton

FlyFrame.Name = "FlyFrame"
FlyFrame.Parent = DragFrame
FlyFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
FlyFrame.Position = UDim2.new(-3.19999409, 0, 0.106531158, 0)
FlyFrame.Size = UDim2.new(0, 154, 0, 61)

UICorner_3.Parent = FlyFrame

TextLabel.Parent = FlyFrame
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.Position = UDim2.new(0.0454545468, 0, -0.508196712, 0)
TextLabel.Size = UDim2.new(0, 139, 0, 31)
TextLabel.Font = Enum.Font.FredokaOne
TextLabel.Text = "Made by Xavryex"
TextLabel.TextColor3 = Color3.fromRGB(197, 197, 197)
TextLabel.TextSize = 18.000
TextLabel.TextStrokeTransparency = 0.000

FlyBtn.Name = "FlyBtn"
FlyBtn.Parent = FlyFrame
FlyBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
FlyBtn.BorderColor3 = Color3.fromRGB(27, 42, 53)
FlyBtn.BorderSizePixel = 0
FlyBtn.Position = UDim2.new(0.0649350584, 0, 0.114754096, 0)
FlyBtn.Size = UDim2.new(0, 136, 0, 46)
FlyBtn.Font = Enum.Font.FredokaOne
FlyBtn.Text = "Fly"
FlyBtn.TextColor3 = Color3.fromRGB(57, 57, 57)
FlyBtn.TextSize = 28.000

-- Scripts:

local function DFLDPAR_fake_script() -- FlyGUI.Dragify 
	local script = Instance.new('LocalScript', FlyGUI)

	local UIS = game:GetService("UserInputService")
	function dragify(Frame)
	    dragToggle = nil
	    local dragSpeed = 5.50
	    dragInput = nil
	    dragStart = nil
	    local dragPos = nil
	    function updateInput(input)
	        local Delta = input.Position - dragStart
	        local Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + Delta.X, startPos.Y.Scale, startPos.Y.Offset + Delta.Y)
	        Frame:TweenPosition(Position,"Out","Quad",.5,true)
	    end
	    Frame.InputBegan:Connect(function(input)
	        if (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch) and UIS:GetFocusedTextBox() == nil then
	            dragToggle = true
	            dragStart = input.Position
	            startPos = Frame.Position
	            input.Changed:Connect(function()
	                if input.UserInputState == Enum.UserInputState.End then
	                    dragToggle = false
	                end
	            end)
	        end
	    end)
	    Frame.InputChanged:Connect(function(input)
	        if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
	            dragInput = input
	        end
		end)
		
		Frame.InputEnded:connect(function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				dragStart = nil
				dragInput = nil
			end
		end)
	    game:GetService("UserInputService").InputChanged:Connect(function(input)
	        if input == dragInput and dragToggle then
	            updateInput(input)
	        end
	    end)
	end
	
	dragify(script.Parent.DragFrame)
end
coroutine.wrap(DFLDPAR_fake_script)()
local function CUNKS_fake_script() -- TextButton.LocalScript 
	local script = Instance.new('LocalScript', TextButton)

	script.Parent.MouseButton1Click:Connect(function()
		script.Parent.Parent.FlyFrame.Visible = not script.Parent.Parent.FlyFrame.Visible
	end)
	
end
coroutine.wrap(CUNKS_fake_script)()
local function VWBTC_fake_script() -- FlyBtn.Button Script 
	local script = Instance.new('LocalScript', FlyBtn)

	--Button Script--
	script.Parent.MouseButton1Click:Connect(function()
		script.Parent.Text = "Loaded!"
		wait(1)
		script.Parent.Text = "Fly"
	end)
	
end
coroutine.wrap(VWBTC_fake_script)()
local function BISWNJH_fake_script() -- FlyBtn.Flying Script 
	local script = Instance.new('LocalScript', FlyBtn)

	--Flying Script--
	script.parent.MouseButton1Down:connect(function()
		repeat wait() 
		until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Head") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
		local mouse = game.Players.LocalPlayer:GetMouse() 
		repeat wait() until mouse
		local plr = game.Players.LocalPlayer 
		local torso = plr.Character.Head 
		local flying = true --Making This False Will Not Work In Mobile--
		local deb = true 
		local ctrl = {f = 0, b = 0, l = 0, r = 0} 
		local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		local maxspeed = 50 
		local speed = 0 
	
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
			if key:lower() == "e" then 
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
end
coroutine.wrap(BISWNJH_fake_script)()
