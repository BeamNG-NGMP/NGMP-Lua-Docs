# NGMP Lua Documentation
Who doesn't love Lua :D


## Table of contents
1. [Plugins explained](#plugins-explained)
2. [Events](#events)
3. [Functions](#functions)

## Plugins explained
Plugins follow a very similar design to Lua mods in vanilla BeamNG.Drive.<br>
Each plugin should be structured as follows:
```lua
local M = {} -- Creates a table to hold the plugin data

local function onPluginLoad()
    print("Hello from Lua!")
end

M.onPluginLoad = onPluginLoad -- We can now assign M.onPluginLoad to our function, and it will now be called whenever our plugin loads.

return M -- We return M here as the lua system will run our lua file and take the return value as our plugin. This is how it knows what functions to call!
```

Plugins get loaded into a single, shared Lua state. This means that communicating with other plugins is very simple, and
depending on other plugins is also very straight-forward.

## Events
### onPluginLoad
Signature: `function onPluginLoad()`<br>
This function gets called whenever the plugin has been loaded.

### onPlayerAuth
Signature: `function onPlayerAuth(steam_id: String, name: String) -> bool`<br>
This function gets called the moment a client has fully authenticated, but BEFORE they start downloading mods.<br>
**Return true to block the player from joining, or return false (or nothing) to allow the player to join.**

### onPlayerLeave
Signature: `function onPlayerLeave(steam_id: String)`<br>
This function gets called if a player leaves for any reason.
Their connection might have dropped, they might have gotten kicked by a Lua plugin, they might have gotten sending incorrect packets.

## Functions
### NGMP.getPlayerName
Signature: `function NGMP.getPlayerName(steam_id: String)`<br>
This function returns the name of the player with that steam_id as a string, or nil if there is no player with that steam_id connected to the server.

### NGMP.getPlugins
Signature: `function NGMP.getPlugins()`<br>
This function returns a list of strings, each entry being the name of a plugin currently loaded.
