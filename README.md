# Construct Modding API

Welcome to the Construct Modding API! This API allows developers to add custom pages and features to the Construct game. Dive into the core functionality and start creating your own modules to enhance gameplay.

## Table of Contents
- Getting Started
- Libraries
- Example Script
- Events and Signals
- Using Vyn
- UI Elements
- Custom Pages
- Contributing

---

## Getting Started

To get started, create a Lua script in Roblox Studio or a notes application. Begin by getting all the necessary services:

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RunService = game:GetService("RunService")

-- Initialization wait
task.wait(3)

## Libraries

The API uses several libraries to help you create and manage features for the game:

- **Signal**: Manages custom events and signals for interactive functionality.
- **Lynx**: Assists with GUI creation and layout management.
- **Logger**: Provides logging features for debugging.
- **LuaVoxel**: Handles voxel-based operations.
- **Vyn**: Interacts with the game’s backend for various data operations.
- **CMenu**: Creates context-sensitive menus in the UI.
- **Coretex**: Core framework for UI page creation.
- **Textup/Textip**: Manages text input/output.
- **UIShadow**: Adds shadow effects to UI elements.
- **Utilities**: Provides general helper functions.

## Example Script

Here’s a basic example of how to create a custom page in the Construct game:

return function(Holder: ScreenGui)
    local Signal = require(Libraries.Signal)
    local Coretex = require(Libraries.Coretex)

    -- Create signal for the marketplace
    Signal.new("Marketplace")

    -- Create a new page
    local CanvasGroup = Coretex:Page("Marketplace")
    CanvasGroup.BackgroundTransparency = 1
    CanvasGroup.Visible = false
    CanvasGroup.Parent = Holder

    -- Create a title
    local Title = Coretex:Title("Marketplace")
    Title.Position = Title.Position + UDim2.new(0, 0, 0, 50)
    Title.TextSize = 50
    Title.Parent = CanvasGroup

    -- Setup container and layout
    local Container = Coretex:Container(0.9, 0.8, false, Enum.AutomaticSize.None)
    Container.Parent = CanvasGroup

    -- Additional UI elements and layout management here
end

## Events and Signals

Use the Signal library to fire and listen to custom events. For example:

Signal:fire("MainMenu", "NewButton", "Marketplace", "icon_id", function()
    -- Define behavior when the marketplace button is clicked
end)

## Using Vyn

Vyn handles communication between the game and the backend, allowing for data requests and updates. Example usage:

- Request marketplace items:

    Vyn:Fire("Game", "GetMarketItems")

- Receive data from the backend:

    Vyn:Listen("Game", function(path, request, data)
        if request == "GetMarketItems" then
            for i, item in pairs(data) do
                -- Handle each market item
            end
        end
    end)

- Trigger actions like buying items:

    Vyn:Fire("Game", "BuyItem", itemID)

## UI Elements

The Coretex library provides tools for UI creation. Key elements include:

- **Page**: Creates new UI pages.
- **Title**: Adds titles to pages.
- **Container**: Manages layout and organization.
- **TextBox**: Custom input fields.
- **Frame**: Frames elements.

Example:

local Title = Coretex:Title("My Custom Page")
Title.TextSize = 40
Title.Parent = Holder

## Custom Pages

Creating custom pages is straightforward with Coretex. This API allows you to dynamically add new content and features, such as marketplaces or custom tools.

## Contributing

To become a verified creator and have your mods featured, submit your mod to the [Luaq Discord Server](https://discord.gg/PPpVrxFsrc). Verified creators gain the ability to create mods directly in-game, allowing for a more integrated and immersive development experience. Our team will review your submission for verification and inclusion. Contributions are welcome, so feel free to fork the repository and create a pull request with your improvements.
