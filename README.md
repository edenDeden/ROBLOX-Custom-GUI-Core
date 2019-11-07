# Chat
Custom chat filled with options

## Basic Message Example

```lua
local api = require(game.ReplicatedStorage.CustomChat.API)
local msg = api.Create("Sender","Text Goes here!",style) // style is from the extension folder
api.SendMessage(api) // will send the message
```

## Tags
### Adding a Tag
```lua
// Settings > Tags > Ranks > [Add Tag]
// Template

[TagKey / TagDisplay] = 
{
	Users = 
	{
		"username",
		"another_username"
	},
	Power = 100,
	Color = Color3.fromRGB(255,170,0)
},

```

### Adding/Removing a Tag at runtime
```lua
local tag = require(game.ReplicatedStorage.CustomChat.Classes.Tag)

tag.CreateTag(tag.new("Test",10,Color3.fromRGB(255,255,0)))
tag.AddPlayer("playerName","Test")

// removing
tag.RemovePlayerFromTag("edenDeden","Test")
```


