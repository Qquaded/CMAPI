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
- License

---

## Getting Started

To get started, clone this repository and ensure you have all the necessary libraries and dependencies installed within your project.

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local RunService = game:GetService("RunService")

After a brief initialization wait (task.wait(3)), the required libraries are loaded.

## Libraries

The API uses several libraries that help create and manage features for the game. Here’s a list of the core libraries you can use:

- **Signal**: Manages custom events and signals for interactive functionality.
- **Lynx**: Helps with GUI creation and layout management.
- **Logger**: Provides logging features for debugging purposes.
- **LuaVoxel**: For voxel-based operations.
- **Vyn**: Interacts with the game’s backend for various data operations.
- **CMenu**: Helps create context-sensitive menus in the UI.
- **Coretex**: Core framework for UI page creation.
- **Textup/Textip**: For managing text input/output.
- **UIShadow**: Adds shadow effects to UI elements.
- **Utilities**: General utilities that provide helper functions.

## Example Script

Here is a basic example of how to create a custom page in the Construct game:

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

You can fire and listen to custom events using the Signal library. Example:

Signal:fire("MainMenu", "NewButton", "Marketplace", "icon_id", function()
    -- Define behavior when the marketplace button is clicked
end)

## Using Vyn

Vyn is a library that handles communication between the game and the backend, enabling data requests and updates. It can be used to fetch and send data like marketplace items, player inventories, and more.

To use Vyn, fire events or listen to events from the backend.

Example for requesting marketplace items:

Vyn:Fire("Game", "GetMarketItems")

To receive data from the backend, use the **Listen** method:

Vyn:Listen("Game", function(path, request, data)
    if request == "GetMarketItems" then
        for i, item in pairs(data) do
            -- Handle each market item here
        end
    end
end)

You can also use Vyn to trigger actions like getting datastores:

Vyn:Fire("Game", "GetAllDatastores")

This enables dynamic interaction with the game's backend, making it possible to retrieve and manipulate data based on your needs.

## UI Elements

The API provides robust tools for UI creation using the Coretex library. Available elements include:
- **Page**: Creates new UI pages.
- **Title**: Adds titles to pages.
- **Container**: Manages layout and organization of elements.
- **TextBox**: Custom input fields.
- **Frame**: For custom framing of elements.

Example:

local Title = Coretex:Title("My Custom Page")
Title.TextSize = 40
Title.Parent = Holder

## Custom Pages

Creating custom pages is simple with the Coretex library. This API enables developers to dynamically add new content and features to Construct, including marketplaces, custom tools, and more.

You can design unique features and interactions for players to enjoy by using the built-in UI libraries and connecting with game signals.

## Contributing

If you want to contribute to the API or suggest features, feel free to fork this repository and create a pull request.
