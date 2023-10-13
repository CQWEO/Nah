--Universal ESP Script 
local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "DOORS ESP", HidePremium = true, SaveConfig = true, ConfigFolder = "OrionTest"})
local Tab = Window:MakeTab({
	Name = "ESP",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})
OrionLib:MakeNotification({
	Name = "Info!",
	Content = "Esp Highlight",
	Image = "rbxassetid://4483345998",
	Time = 5
})
getgenv().esp = false
getgenv().teamcheck = false
getgenv().Color = Color3.fromRGB(255, 0, 0)
Tab:AddToggle({
	Name = "ESP",
	Default = false,
	Callback = function(Value)
		getgenv().esp = Value
		spawn(function()
		while wait() do
		    if not getgenv().esp then
		          for i,v in pairs(CurrentRooms:GetChildren()) do
		              if v.Door and v.Door:FindFirstChild("Highlight") then
		                  local Highlight = v.Door:FindFirstChild("Highlight")
		                  Highlight.Enabled = false
    		      end
		      end 
		      else
		          for i,v in pairs(CurrentRooms:GetChildren()) do
		             if getgenv().teamcheck == true then
		               if v.Door and v ~= Door.Door and v.TeamColor ~= Door.Door.TeamColor then
    		                 if v.Character:FindFirstChild("Highlight") then
    		                 local Highlight = v.Door:FindFirstChild("Highlight") 
    		                 Highlight.Enabled = true
    		                 Highlight.FillColor = getgenv().Color
    		                 Highlight.Adornee = v.Door
    		                 else
    		                 local Highlight = Instance.new("Highlight",v.Door)
    		                 Highlight.Enabled = true
    		                 Highlight.FillColor = getgenv().Color
    		                 Highlight.Adornee = v.Door
    		              end       
    		           end  
		                if v.TeamColor == Door.Door.TeamColor then
    		              if v.Door and v.Door:FindFirstChild("Highlight") then
    		                  local Highlight = v.Door:FindFirstChild("Highlight")
        		              Highlight.Enabled = false
        		          end    
    		            end 
    		          else
    		              if v.Door and v ~= Door.Door then
    		                 if v.Door:FindFirstChild("Highlight") then
    		                 local Highlight = v.Door:FindFirstChild("Highlight") 
    		                 Highlight.Enabled = true
    		                 Highlight.FillColor = getgenv().Color
    		                 Highlight.Adornee = v.Door
    		                 else
    		                 local Highlight = Instance.new("Highlight",v.Door)
    		                 Highlight.Enabled = true
    		                 Highlight.FillColor = getgenv().Color
    		                 Highlight.Adornee = v.Door
    		              end       
    		           end    
		            end       
		      end    
		    end  
		end    
		end)
	end    
})
Tab:AddColorpicker({
	Name = "Esp Color",
	Default = Color3.fromRGB(255, 0, 0),
	Callback = function(Value)
		getgenv().Color = Value
	end	  
})
Tab:AddToggle({
	Name = "Teamcheck",
	Default = false,
	Callback = function(Value)
		getgenv().teamcheck = Value
	end    
})
Tab:AddToggle({
	Name = "Rainbow ESP",
	Default = false,
	Callback = function(Value)
		getgenv().Rainbow = Value
		while wait() do
		    if not getgenv().Rainbow then return end
		    getgenv().Color = Color3.new(148, 0, 211)
		    wait(1.25)
		    getgenv().Color = Color3.new(75, 0, 130)
		    wait(1.3)
		    getgenv().Color = Color3.new(0, 0, 255)
		    wait(1.35)
		    getgenv().Color = Color3.new(0, 255, 0)
		    wait(1.3)
		    getgenv().Color = Color3.new(255, 255, 0)
		    wait(1.2)
		    getgenv().Color = Color3.new(255, 127, 0)
		    wait(1.1)
		    getgenv().Color = Color3.new(255, 0 , 0)
		    wait()
		end    
	end    
})
