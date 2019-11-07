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




