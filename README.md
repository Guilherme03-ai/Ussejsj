local Options = {
    Keybind = 'Home', -- Tecla para abrir/fechar UI
    Tempo = 1.2, -- Tempo entre mensagens
    Rainbow = false, -- UI colorida (apenas decorativo)

    Config = {
        Min = 0, -- Número mínimo
        Max = 99999999999, -- Número máximo
        Mensagem = "Seu código é", -- Texto da mensagem
        Separado = true, -- true = envia mensagem e número em mensagens diferentes
        Repetir = false, -- true = repete automaticamente
        Intervalo = 3 -- intervalo entre repetições (se Repetir = true)
    }
}

loadstring(game:HttpGet("https://raw.githubusercontent.com/seuusuario/seurepo/main/AutoChat.lua"))(Options)
