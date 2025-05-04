
return function(Options)
    local UIS = game:GetService("UserInputService")
    local RS = game:GetService("RunService")
    local ChatEvent = game:GetService("ReplicatedStorage"):WaitForChild("DefaultChatSystemChatEvents"):WaitForChild("SayMessageRequest")

    local UIVisible = true

    local function enviarChat(msg)
        ChatEvent:FireServer(msg, "All")
    end

    local function gerarENotificar()
        local num = math.random(Options.Config.Min, Options.Config.Max)
        if Options.Config.Mensagem ~= "" then
            if Options.Config.Separado then
                enviarChat(Options.Config.Mensagem)
                wait(Options.Tempo)
                enviarChat(tostring(num))
            else
                enviarChat(Options.Config.Mensagem .. " " .. tostring(num))
            end
        else
            enviarChat(tostring(num))
        end
    end

    if Options.Config.Repetir then
        task.spawn(function()
            while true do
                gerarENotificar()
                wait(Options.Config.Intervalo)
            end
        end)
    else
        gerarENotificar()
    end

    UIS.InputBegan:Connect(function(input, gameProcessed)
        if not gameProcessed and input.KeyCode.Name == Options.Keybind then
            UIVisible = not UIVisible
            print("[AutoChat] Ativado:", UIVisible)
        end
    end)
end
