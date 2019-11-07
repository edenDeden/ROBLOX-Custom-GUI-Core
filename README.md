# Chat Documentation
## Classes
<details open?>
<summary>Message</summary>

### Constractor
will create a new message object</br>
Note: Style is the name of a style that is in the Extensions > Styles module
```lua
Message.new(string sender,string text,[optional] string style)
```
### Functions
will create a new style and return it based on the given params (if a param is nil the assign style property will be the default from Settings)</br>
Note: the style can be creted from one script and accessed by all</br>
```lua
static Style CreateStyle(Color3 senderColor,Color3 textColor,Enum.Font senderFont,Enum.Font textFont)
```
gets a message and assigns the style
```lua
static void AssignStyle(Message msg)
```
will add a tag to the message
```lua
void AddTag(Tag tagInfo)
```
</details>
<details open?>
<summary>Tag</summary>

### Constractor
```lua
Tag.new(string name,int power,Color3 color)
```

### Functions
will add the tag to the tags list
```lua
static void CreateTag(Tag tag)
```
will add the player to the tag player list
```lua
static void AddPlayer(Tag tag)
```
will remove the player from the tag player list
```lua
static void RemovePlayerFromTag(string playerName,string tagName)
```
will remove the player from the tag player list
```lua
static Tag GetTagByName(string name)
```
returns a table with the tags in the order from most powerfull to least or a table with a single tag if MultipleTags is false
```lua
static string[] GetPlayerTags(object player)
```
</details>

## Extensions
<details open?>
<summary>Styles</summary>
Create built in message styles!
Note: comes with some premade styles, change as you wish

### Template
Note: if you assign as nil the style that will be assigned is default from Settings
Note2: you dont have to assing as nil it's just for the example
```lua
StyleName = { -- what you write to apply
  SenderColor = Color3.fromRGB(255,170,0),
  TextColor = Color3.fromRGB(255,85,0),
  SenderFont = nil,
  TextFont = nil,	
}
 ```
</details>

<details open?>
<summary>Commands</summary>
Extensions > CommandsHandler > Commands
Built in admin commands system!
Note: can be disabled at the Settings and comes with some built in commands

### How To use
```lua
Now to use this system:
	1)  each command gets this structure
		CommandInfoTable = 
		{
			MessageSender = {string} the player name that sent the command,
			CommandPrefix = {string} the command name (e.g /m)
			Params = {string[]} a table comntaining all the parameters in the right order	
		}
	so for example the command: [edenDeden]:/ws e 32, will return 
		MessageSender = "edenDeden",
		CommandPrefix = "/ws"
		Params = {32}
			
	2) A command can have the 'all' tag which means instead of a player name there will be either @all or -all 
```
### Template
```lua
CommandKey = {
  Name = "commandKey",
  PermissionLevel = ChatSettings.Commands.PermissionLevels.Mod,
  Description = "wwhat will be displayed whn you hover",
  Structure = ChatSettings.Commands.Prefix.."ws [player | all][amount]",
  
  Fire = function(commandInfo)
  	
  	
  	if commandInfo.Params[1] == "@all" then
  		for i,v in pairs(game.Players:GetChildren())do
  			if v.Character then v.Character.Humanoid.WalkSpeed = commandInfo.Params[2] end 
  		end
  	end
  	if commandInfo.Params[1] == "-all" then
  		for i,v in pairs(game.Players:GetChildren())do
  			if v.Name ~= commandInfo.MessageSender and v.Character then v.Character.Humanoid.WalkSpeed = commandInfo.Params[2] end 
  		end
  	end
  	
  	local player = GetPlayerFromShortCut(commandInfo.Params[1])
  	if player then
  		if player.Character then player.Character.Humanoid.WalkSpeed = commandInfo.Params[2] end 
  	end
  end
},
```
</details>







