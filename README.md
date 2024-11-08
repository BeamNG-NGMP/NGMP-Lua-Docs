# NGMP Lua Documentation
Who doesn't love Lua :D


## Table of contents
1. [Events](#events)

## Events
### onPlayerAuth
Signature: `function onPlayerAuth(steam_id: String, name: String) -> bool`
This function gets called the moment a client has fully authenticated, but BEFORE they start downloading mods.
Return true to block the player from joining, or return false (or nothing) to allow the player to join.

### onPlayerLeave
Signature: `function onPlayerLeave(steam_id: String)`
This function gets called if a player leaves for any reason.
Their connection might have dropped, they might have gotten kicked by a Lua plugin, they might have gotten sending incorrect packets.
