
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Drixn1/Ghostcore/main/library.lua"))()
local Tab1 = library:Window("Scripts")

game.StarterGui:SetCore("SendNotification", {
   Title = "GhostCore";
   Text = "Best Roblox Hub";
   Icon = "";
   Duration = "2";
})

Tab1:Label("Lag Commands", Color3.fromRGB(127, 143, 166))

Tab1:Button("Lag Server", function()
while wait() do
local args = {
[1] = "PickingCar",
[2] = "RV"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local A_1 = "PickingCar"
local A_2 = "FordGT"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local args = {
   [1] = "PickingCar",
   [2] = "FoodTruck"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local A_1 = "PickingCar"
local A_2 = "CopSUV"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local args = {
   [1] = "PickingCar",
   [2] = "Van"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local A_1 = "PickingCar"
local A_2 = "FireTruck"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local args = {
   [1] = "PickingCar",
   [2] = "Ambulance"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local A_1 = "PickingCar"
local A_2 = "Bus"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local A_1 = "PickingCar"
local A_2 = "CopUnderCoverSUV"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local A_1 = "PickingCar"
local A_2 = "QuadStock"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local A_1 = "PickingCar"
local A_2 = "Challenger"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local A_1 = "PickingCar"
local A_2 = "Jeep"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local A_1 = "PickingCar"
local A_2 = "CopChallenger"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local A_1 = "PickingCar"
local A_2 = "Cadillac"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Car
Event:FireServer(A_1, A_2)
wait()
local args = {
   [1] = "PickingCar",
   [2] = "GolfCart"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local args = {
   [1] = "PickingCar",
   [2] = "NPHarleyDavison"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local args = {
   [1] = "PickingCar",
   [2] = "Horse"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local args = {
   [1] = "PickingCar",
   [2] = "ScooterVehicle"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
wait()
local args = {
   [1] = "PickingCar",
   [2] = "SmartCar"
}
game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end
end)

Tab1:Label("Fun Commands", Color3.fromRGB(127, 143, 166))

Tab1:Button("0 Gravity Unanchored Things", function()
spawn(function()
while true do
game.Players.LocalPlayer.MaximumSimulationRadius = math.pow(math.huge,math.huge)*math.huge
game.Players.LocalPlayer.SimulationRadius = math.pow(math.huge,math.huge)*math.huge
game:GetService("RunService").Stepped:wait()
end
end)
local function zeroGrav(part)
   if part:FindFirstChild("BodyForce") then return end
   local temp = Instance.new("BodyForce")
   temp.Force = part:GetMass() * Vector3.new(0,workspace.Gravity,0)
   temp.Parent = part
end

for i,v in ipairs(workspace:GetDescendants()) do
   if v:IsA("Part") and v.Anchored == false then
       if not (v:IsDescendantOf(game.Players.LocalPlayer.Character)) then
           zeroGrav(v)
       end
   end
end

workspace.DescendantAdded:Connect(function(part)
   if part:IsA("Part") and part.Anchored == false then
       if not (part:IsDescendantOf(game.Players.LocalPlayer.Character)) then
           zeroGrav(part)
       end
   end
end)
end)

Tab1:Button("Bring Unanchored Bricks [E]", function()
local UserInputService = game:GetService("UserInputService")
local Mouse = game:GetService("Players").LocalPlayer:GetMouse()
local Folder = Instance.new("Folder", game:GetService("Workspace"))
local Part = Instance.new("Part", Folder)
local Attachment1 = Instance.new("Attachment", Part)
Part.Anchored = true
Part.CanCollide = false
Part.Transparency = 1
local Updated = Mouse.Hit + Vector3.new(0, 5, 0)
local NetworkAccess = coroutine.create(function()
  settings().Physics.AllowSleep = false
  while game:GetService("RunService").RenderStepped:Wait() do
      for _, Players in next, game:GetService("Players"):GetPlayers() do
          if Players ~= game:GetService("Players").LocalPlayer then
              Players.MaximumSimulationRadius = 0
              sethiddenproperty(Players, "SimulationRadius", 0)
          end
      end
      game:GetService("Players").LocalPlayer.MaximumSimulationRadius = math.pow(math.huge,math.huge)
      setsimulationradius(math.huge)
  end
end)
coroutine.resume(NetworkAccess)
local function ForcePart(v)
  if v:IsA("Part") and v.Anchored == false and v.Parent:FindFirstChild("Humanoid") == nil and v.Parent:FindFirstChild("Head") == nil and v.Name ~= "Handle" then
      Mouse.TargetFilter = v
      for _, x in next, v:GetChildren() do
          if x:IsA("BodyAngularVelocity") or x:IsA("BodyForce") or x:IsA("BodyGyro") or x:IsA("BodyPosition") or x:IsA("BodyThrust") or x:IsA("BodyVelocity") or x:IsA("RocketPropulsion") then
              x:Destroy()
          end
      end
      if v:FindFirstChild("Attachment") then
          v:FindFirstChild("Attachment"):Destroy()
      end
      if v:FindFirstChild("AlignPosition") then
          v:FindFirstChild("AlignPosition"):Destroy()
      end
      if v:FindFirstChild("Torque") then
          v:FindFirstChild("Torque"):Destroy()
      end
      v.CanCollide = false
      local Torque = Instance.new("Torque", v)
      Torque.Torque = Vector3.new(100000, 100000, 100000)
      local AlignPosition = Instance.new("AlignPosition", v)
      local Attachment2 = Instance.new("Attachment", v)
      Torque.Attachment0 = Attachment2
      AlignPosition.MaxForce = 9999999999999999
      AlignPosition.MaxVelocity = math.huge
      AlignPosition.Responsiveness = 200
      AlignPosition.Attachment0 = Attachment2
      AlignPosition.Attachment1 = Attachment1
  end
end
for _, v in next, game:GetService("Workspace"):GetDescendants() do
  ForcePart(v)
end
game:GetService("Workspace").DescendantAdded:Connect(function(v)
  ForcePart(v)
end)
UserInputService.InputBegan:Connect(function(Key, Chat)
  if Key.KeyCode == Enum.KeyCode.E and not Chat then
     Updated = Mouse.Hit + Vector3.new(0, 5, 0)
  end
end)
spawn(function()
  while game:GetService("RunService").RenderStepped:Wait() do
      Attachment1.WorldCFrame = Updated
  end
end)
end)


Tab1:Label("Tool Commands", Color3.fromRGB(127, 143, 166))

Tab1:Box("Tool Kill Player", function(text, focuslost)
if focuslost then
local pl = game.Players.LocalPlayer.Character.HumanoidRootPart
local humanoid = game.Players.LocalPlayer.Character.Humanoid
local RunService = game:GetService("RunService")
local OldPosition = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position
RunService.RenderStepped:Wait()
game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame =  game:GetService("Players")[text].Character.HumanoidRootPart.CFrame * CFrame.Angles(0,math.rad(0),0)* CFrame.new(-0,0,5.5)
wait()
local A_1 = "PickingTools"
local A_2 = "Stretcher"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Tools
Event:InvokeServer(A_1, A_2)
wait(0)
local Character = game.Players.LocalPlayer.Character
local Backpack = game.Players.LocalPlayer.Backpack
local Tool = "Stretcher"
Character.Humanoid:EquipTool(Backpack[Tool])
wait(3)
Character.Humanoid:UnequipTools()
wait(0.1)
pl.CFrame = CFrame.new(-13612,444,-2855)
wait(1)
Character.Humanoid:EquipTool(Backpack[Tool])
wait(0.1)
local A_1 = "PickingTools"
local A_2 = "Stretcher"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Tools
Event:InvokeServer(A_1, A_2)
wait(0.2)
pl.CFrame = CFrame.new(OldPosition)
  end
end)





Tab1:Box("Tool Bring Player", function(text, focuslost)
if focuslost then
local pl = game.Players.LocalPlayer.Character.HumanoidRootPart
local humanoid = game.Players.LocalPlayer.Character.Humanoid
local RunService = game:GetService("RunService")
local OldPosition = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position
RunService.RenderStepped:Wait()
game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame =  game:GetService("Players")[text].Character.HumanoidRootPart.CFrame * CFrame.Angles(0,math.rad(0),0)* CFrame.new(-0,0,5.5)
wait()
local A_1 = "PickingTools"
local A_2 = "Stretcher"
local Event = game:GetService("ReplicatedStorage").RemoteEvents.Tools
Event:InvokeServer(A_1, A_2)
wait(0)
local Character = game.Players.LocalPlayer.Character
local Backpack = game.Players.LocalPlayer.Backpack
local Tool = "Stretcher"
Character.Humanoid:EquipTool(Backpack[Tool])
wait(3)
Character.Humanoid:UnequipTools()
wait(0.1)
pl.CFrame = CFrame.new(OldPosition)
wait(0.1)
Character.Humanoid:EquipTool(Backpack[Tool])
wait(0.3)
Character.Humanoid:UnequipTools()
end
end)

Tab1:Button("Spawn Item to Brick Spam", function()
while wait() do
local args = {
  [1] = "PickingTools",
  [2] = "Taser"
}
game:GetService("ReplicatedStorage").RemoteEvents.Tools:InvokeServer(unpack(args))
end
end)

Tab1:Toggle("Brick Spam", false, function(bool)
drop = bool
while drop == true and wait() do
for _,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
game.Players.LocalPlayer.Character.Humanoid:EquipTool(v)
v.Handle.Mesh:Destroy()
v.Parent = workspace
end
end
end)



Tab1:Label("FE Music Commands", Color3.fromRGB(127, 143, 166))


Tab1:Box("Gun Play Song", function(text, focuslost)
  if focuslost then
local args = {
   [1] = "PickingTools",
   [2] = "Sniper"
}
game:GetService("ReplicatedStorage").RemoteEvents.Tools:InvokeServer(unpack(args))
wait(0.1)
local Character = game.Players.LocalPlayer.Character
local Backpack = game.Players.LocalPlayer.Backpack
local Tool = "Sniper"
Character.Humanoid:EquipTool(Backpack[Tool])
     wait(0.1)
local args = {
   [1] = game:GetService("Players").LocalPlayer.Character.Sniper.Handle,
   [2] = text,
   [3] = 1
}
game:GetService("ReplicatedStorage").GunSounds:FireServer(unpack(args))
  end
end)





Tab1:Box("House Play Song", function(text, focuslost)
  if focuslost then
     local args = {
   [1] = "PickingHouseMusicText",
   [2] = text
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse:FireServer(unpack(args))
end
end)










local Tab2 = library:Window("Scripts")

Tab2:Label("Admin Commands", Color3.fromRGB(127, 143, 166))

Tab2:Button("Jump All", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)

Tab2:Toggle("Loop Jump All", false, function(bool)
jump = bool
Players = game:GetService("Players")
while jump == true and wait() do
for i, all in pairs(Players:GetPlayers()) do
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end
end)


Tab2:Box("Jump Player", function(text, focuslost)
  if focuslost then
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
     
  end
end)


Tab2:Box("Mega Jump Plr", function(text, focuslost)
if focuslost then
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
  end
end)



Tab2:Button("Kill All v1", function()
Players = game:GetService("Players")
game.Players.LocalPlayer.Character.Head:Destroy()
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "Client2Client",
   [2] = "Request: Piggyback!",
   [3] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
local args = {
   [1] = "BothWantPiggyBackRide",
  [2] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab2:Button("Kill All v2", function() -- I cant see a diffrences between kill all v1 and kill all v2 in his hub
game.workspace.Camera:Destroy()
Players = game:GetService("Players")
game.Players.LocalPlayer.Character.Head:Destroy()
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "Client2Client",
   [2] = "Request: Piggyback!",
   [3] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
local args = {
   [1] = "BothWantPiggyBackRide",
  [2] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)




Tab2:Box("Kill Any Player", function(text, focuslost)
if focuslost then
local Lp = game.Players.LocalPlayer.name
game.Players.LocalPlayer.Character.Head:Destroy()
local A_1 = "Client2Client"
local A_2 = "Request: Piggyback!"
local A_3 = game:GetService("Players")[Lp]
local Event = game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent
Event:FireServer(A_1, A_2, A_3)
local args = {
   [1] = "BothWantPiggyBackRide",
   [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
  end
end)




Tab2:Box("Freeze Player", function(text, focuslost)
if focuslost then
local Lp = game.Players.LocalPlayer.name
local A_1 = "Client2Client"
local A_2 = "Request: Piggyback!"
local A_3 = game:GetService("Players")[Lp]
local Event = game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent
Event:FireServer(A_1, A_2, A_3)
wait()
local args = {
   [1] = "BothWantPiggyBackRide",
   [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantPiggyBackRide",
   [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantPiggyBackRide",
   [2] = game:GetService("Players")[Lp]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[Lp]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
game.Players.LocalPlayer.Character["HumanoidRootPart"].Anchored = true
end
end)





Tab2:Box("Skydive Player", function(text, focuslost)
if focuslost then
local Lp = game.Players.LocalPlayer.name
local A_1 = "Client2Client"
local A_2 = "Request: Carry!"
local A_3 = game:GetService("Players")[Lp]
local Event = game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent
Event:FireServer(A_1, A_2, A_3)
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[Lp]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[Lp]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
game.Players.LocalPlayer.Character["HumanoidRootPart"].Anchored = true
wait(0.025)
game.Players.LocalPlayer.Character["HumanoidRootPart"].Anchored = false
wait(0.1)
game.Players.LocalPlayer.Character["Humanoid"]:Destroy()
wait(0.1)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,20000,0)
end
end)



Tab2:Box("Carry Player", function(text, focuslost)
if focuslost then
local Lp = game.Players.LocalPlayer.name
local A_1 = "Client2Client"
local A_2 = "Request: Carry!"
local A_3 = game:GetService("Players")[Lp]
local Event = game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent
Event:FireServer(A_1, A_2, A_3)
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[Lp]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[Lp]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
game.Players.LocalPlayer.Character["HumanoidRootPart"].Anchored = true
wait(0.05)
game.Players.LocalPlayer.Character["HumanoidRootPart"].Anchored = false
end
end)



Tab2:Box("Bring Player", function(text, focuslost)
if focuslost then
local pl = game.Players.LocalPlayer.Character.HumanoidRootPart
local humanoid = game.Players.LocalPlayer.Character.Humanoid
local RunService = game:GetService("RunService")
local OldPosition = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position
local Lp = game.Players.LocalPlayer.name

local A_1 = "Client2Client"
local A_2 = "Request: Carry!"
local A_3 = game:GetService("Players")[Lp]
local Event = game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent
Event:FireServer(A_1, A_2, A_3)
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[text]
}

game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[text]
}

game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[text]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
   [1] = "BothWantCarryHurt",
   [2] = game:GetService("Players")[Lp]
}

game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait()
local args = {
  [1] = "DropButtonStopAll",
  [2] = game:GetService("Players")[Lp]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
wait(0.1)
game.Players.LocalPlayer.Character["HumanoidRootPart"].Anchored = true
wait(0.05)
game.Players.LocalPlayer.Character["HumanoidRootPart"].Anchored = false
wait(0.1)
game.Players.LocalPlayer.Character["Humanoid"]:Destroy()
wait(0.1)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(OldPosition)
wait(6)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(OldPosition)
  end
end)




Tab2:Toggle("Loop Teleport+Annoy", false, function(bool)
annoy = bool
while annoy and wait(0.1) do
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
   
   local args = {
   [1] = "Client2Client",
   [2] = "Request: Piggyback!",
   [3] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
local args = {
   [1] = "BothWantPiggyBackRide",
  [2] = game:GetService("Players")[all.name]
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
   
end  
end
end)



Tab2:Toggle("Rainbow House", false, function(bool)
rainbowh = bool
while rainbowh and wait() do
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(1, 0, 0.0531912);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(1, 0, 0.723851);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(0.529121, 0, 1);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(0, 0.192412, 1);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(0.0693014, 1, 0.953011);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(0, 1, 0.188863);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(1, 0.969094, 0.0636657);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingHouseColor";
local userdata_1 = Color3.new(1, 0.969094, 0.0636657);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersHouse;
Target:FireServer(string_1, userdata_1);
wait(0.0)
end
end)
   
   
Tab2:Label("Car Upgrade Gamepass", Color3.fromRGB(127, 143, 166))
Tab2:Toggle("Rainbow Car", false, function(bool)
rainbowc = bool
while rainbowc and wait() do
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(1, 0, 0.0531912);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(1, 0, 0.723851);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(0.529121, 0, 1);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(0, 0.192412, 1);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(0.0693014, 1, 0.953011);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(0, 1, 0.188863);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(1, 0.969094, 0.0636657);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.1)
local string_1 = "PickingCarColor";
local userdata_1 = Color3.new(1, 0.969094, 0.0636657);
local Target = game:GetService("ReplicatedStorage").RemoteEvents.PlayersCar;
Target:FireServer(string_1, userdata_1);
wait(0.0)
end
end)



local Tab3 = library:Window("LocalPlayer")

Tab3:Button("FE Clown Head", function()
   
local A_1 = "wear"
local A_2 = 4272833564
local Event = game:GetService("ReplicatedStorage").RemoteEvents.UpdateAvatar
Event:FireServer(A_1, A_2)
   
end)




Tab3:Slider("Walkspeed",16,120,0, function(value)
  game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = value
end)

Tab3:Slider("JumpPower",50,300,0, function(value)
  game.Players.LocalPlayer.Character.Humanoid.JumpPower = value
end)


Tab3:Button("Rejoin Server", function()
game:GetService'TeleportService':TeleportToPlaceInstance(game.PlaceId,game.JobId,game:GetService'Players'.LocalPlayer)
end)
noclip = false
Tab3:Toggle("Noclip", false, function(bool)
noclip = bool

game:GetService('RunService').Stepped:connect(function()
if noclip then
game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
end
end)
plr = game.Players.LocalPlayer
mouse = plr:GetMouse()
mouse.KeyDown:connect(function(key)

if key == "e" then
noclip = not noclip
game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
end
end)



   
end)


Tab3:Button("Reset Character", function()
game.Players.LocalPlayer.Character["Humanoid"]:Destroy()
end)



local Tab4 = library:Window("Give Tool To Player")

Tab4:Label("Give To All Players", Color3.fromRGB(127, 143, 166))

Tab4:Button("Give Money Bag [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4535110571",
   [4] = "Money"
}

game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)



Tab4:Button("Give Big Money Bag [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4587924680",
   [4] = "DuffleBagMoney"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))

end
end)


Tab4:Button("Give Coca Cola [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4548052009",
   [4] = "Coke"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give Stroller [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4529218345",
   [4] = "Stroller"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give Hairbrush [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
   local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=5480682123",
   [4] = "Hairbrush"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give Sign [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=6001822792",
   [4] = "Sign"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give Rose [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=5211788490",
   [4] = "Roses"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give Soccer Ball [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4598172149",
   [4] = "SoccerBall"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give Gun [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4529288610",
   [4] = "Assault"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give C4 [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4587924290",
   [4] = "Bomb"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)


Tab4:Button("Give Shovel [ALL]", function()
Players = game:GetService("Players")
for i, all in pairs(Players:GetPlayers()) do
local args = {
   [1] = "ToolGiveToServer",
   [2] = game:GetService("Players")[all.name],
   [3] = "http://www.roblox.com/asset/?id=4617189079",
   [4] = "Shovel"
}
game:GetService("ReplicatedStorage").RemoteEvents.PlayerTriggerEvent:FireServer(unpack(args))
end
end)



Tab4:Label("Give To Yourself", Color3.fromRGB(127, 143, 166))

local dropdown = Tab4:Dropdown("Give Yourself Item", {"Iphone", "Camcorder", "BabyBoy", "BabyGirl", "Wagon", "Sign", "Syringe", "Ear", "Trophy", "Taser", "SWATShield", "Cuffs", "Glock", "Shotgun", "Assault", "Sniper", "Bomb", "DuffleBagMoney", "Money", "CreditCardBoy", "CreditCardGirl", "Umbrella", "Roses", "Present", "SoccerBall", "Apple", "Chips", "Bloxaide", "Milk",}, function(name)
local args = {
   [1] = "PickingTools",
   [2] = name
}

game:GetService("ReplicatedStorage").RemoteEvents.Tools:InvokeServer(unpack(args))

end)



local Tab5 = library:Window("Spawn Cars")

Tab5:Label("Instant Spawn Cars", Color3.fromRGB(127, 143, 166))

Tab5:Button("Scooter", function()
local args = {
   [1] = "PickingCar",
   [2] = "ScooterVehicle"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("NPHarleyDavison", function()
local args = {
   [1] = "PickingCar",
   [2] = "NPHarleyDavison"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("Cadillac", function()
local args = {
   [1] = "PickingCar",
   [2] = "Cadillac"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("CopChallenger", function()
local args = {
   [1] = "PickingCar",
   [2] = "CopChallenger"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("Challenger", function()
local args = {
   [1] = "PickingCar",
   [2] = "Challenger"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("Bus", function()
local args = {
   [1] = "PickingCar",
   [2] = "Bus"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("Jeep", function()
local args = {
   [1] = "PickingCar",
   [2] = "Jeep"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("FireTruck", function()
local args = {
   [1] = "PickingCar",
   [2] = "FireTruck"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("CopUnderCoverSUV", function()
local args = {
   [1] = "PickingCar",
   [2] = "CopUnderCoverSUV"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("GolfCart", function()
local args = {
   [1] = "PickingCar",
   [2] = "GolfCart"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("Van", function()
local args = {
   [1] = "PickingCar",
   [2] = "Van"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("FordGT", function()
local args = {
   [1] = "PickingCar",
   [2] = "FordGT"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("CopSUV", function()
local args = {
   [1] = "PickingCar",
   [2] = "CopSUV"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)

Tab5:Button("RV", function()
local args = {
   [1] = "PickingCar",
   [2] = "RV"
}

game:GetService("ReplicatedStorage").RemoteEvents.Car:FireServer(unpack(args))
end)






local Tab6 = library:Window("Server-Side Fun Tags")


Tab6:Button("Admin Tag 1", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "782790468",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)

Tab6:Button("Admin Tag 2", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "105095367",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Normal VIP Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "1292335373",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Mega VIP Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "1255544221",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Ultra VIP Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "1292342698",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("VIP Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "32578003",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Moderator Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "415986666",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Owner Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "2980546857",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Creator Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "2497143214",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Brookhaven Logo Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "6336646536",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Pikachu Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "1473416194",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Hacker Face Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "3284478282",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Scary Pikachu Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "127039538",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("HD Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "2821573888",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Old Roblox Logo Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "148012526",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Roblox Admin Logo Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "1151106808",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Diamond Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "4424298",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Hacking Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "626372353",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Nascar Car Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "463277467",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Girl Face Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "555878469",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Wall Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "1844422643",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Meme Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "261677904",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Coffee Meme Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "261676710",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)






Tab6:Label("Scary", Color3.fromRGB(127, 143, 166))


Tab6:Button("Scary Face Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "1243374078",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("2 Eye Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "5839301773",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Scary Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "2120834873",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Smiley Face Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "333476199",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)


Tab6:Button("Scary Dog Tag", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "5817435822",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))

end)


Tab6:Button("Scary Cat", function()
local args = {
   [1] = "GiveJobUIMenu",
   [2] = "23355113",
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end)



Tab6:Box("Custom Image", function(text, focuslost)
if focuslost then
local args = {
   [1] = "GiveJobUIMenu",
   [2] = text,
   [3] = "Made by GhostCore",
   [4] = true
}

game:GetService("ReplicatedStorage").RemoteEvents.Jobs:FireServer(unpack(args))
end
end)


library:Keybind("Tab")
