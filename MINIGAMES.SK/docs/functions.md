# functions.md

Here, the functions of MINIGAMES.SK core are explained. Use `Strg + F` to search in your browser for what you want.


## Points
Points are used to determine the progress of a player. You are able to create custom points for every game, points are always non-persistent and get deleted once a game ends.

#### mgSetCurrentGamePoints(game:text,player:player,pointsname:text,points:number)
This function allows you to set the points for a specific game and points name of a player to a value. If the points don't exist yet, they will be created automatically by this.

#### mgRemoveCurrentGamePoints(game:text,player:player,pointsname:text,points:number)
This function is going to remove the given amount of points from the player's points.

#### mgGetCurrentGamePointsWinner(game:text,pointsname:text) :: offline player
This function will select the winner of the game depending on the game and the points name that is defined.

#### mgGetCurrentGamePointsList(game:text,pointsname:text) :: HashMap(player,amount)
Returns a HashMap out of all players that have points.

#### mgGetCurrentGamePoints(game:text,player:player,pointsname:text) :: number
Returns the number of points the player has for this game and points name.

#### mgAddCurrentGamePoints(game:text,player:player,pointsname:text,points:number)
Adds the given amount of points to the game and points name for the player. If the points don't exist yet, this function will also create them automatically.



## Sidebar
The sidebar is used for custom information that can be set by the minigame. MINIGAMES.SK has integrated functions to use the sidebar easy and efficient.

#### mgWipePersonalSidebarContent(player:player or null)
Players can have personal content on their sidebar, if necessary, it can be wiped with this function.
By setting the parameter to null, all player sidebars are going to be wiped out.

#### mgWipeGlobalSidebarContent()
To remove any content that is globally stored on the sidebar, use this function.

#### mgStartSidebarProcess(player:player)
Do not use this function, since it will start automatically, you don't have to call it to enable the sidebar.
Starts a sidebar process for the defined player, this has an integrated check that will monitor the process to ensure a working sidebar.

#### mgSetSidebarToplist(game:text,pointsname:text,limit:number,startslot:number)
This function sets a toplist into the sidebar. The game and points name has to be definied to make sure the right points are counted.
The size of the toplist and the start slot on the toplist within the sidebar can be defined to allow better customizability.

#### mgSetPersonalSidebarSlotContent(slotnumber:number,player:player,translationgame:text,translationkey:text,placeholders:HashMap(find,replace))
Sets the personal sidebar slot of a player to a predefined translation key of a game. You can use placeholders, which are a `HashMap`, the key is the searched key, the value the replaced value for the placeholder.
You can create a HashMap placeholder replacement like this:
```
set {_placeholder} to HashMap()
{_placeholder}.put("<ReplaceMe>","replaced!")
```
This function uses translation keys instead of simple strings to allow a good user experience, since the sidebar will display the text in the client language.

#### mgSetGlobalSidebarSlotContent(slotnumber:number,translationgame:text,translationkey:text,placeholders:object)
Sets the global sodebar slot to a predefined translation key of a game. You can use placeholders, which are a `HashMap`, the key is the searched key, the value the replaced value for the placeholder.
You can create a HashMap placeholder replacement like this:
```
set {_placeholder} to HashMap()
{_placeholder}.put("<ReplaceMe>","replaced!")
```
This function uses translation keys instead of simple strings to allow a good user experience, since the sidebar will display the text in the client language.

#### mgRemovePersonalSidebarContent(slot:number,player:player)
Removes a specific sidebar slot from the personal sidebar of a player.

#### mgRemoveGlobalSidebarContent(slot:number)
Removes a specific sidebar slot from the global sidebar.


## World
Each minigame gets it's own world that gets deleted after a game ends. This is very efficient, as it doesn't require a separate process to restore.

#### mgGetCurrentWorld() :: world
Returns the current minigame world that is being used for the game.

#### mgDeleteGameWorld(world:world)
Teleports all players out, unloads all chunks and deletes the defined world instantly.

#### mgCreateGameWorld(game:text,source:text)
Creates a new game world. This function can copy a world from a custom source and copy it to use it for the game.

## Language
Minigames should support multiple languages to offer each player a good gameplay experience. These functions will help with that.

#### mgSetTranslation(lang:text,game:text,key:text,value:text)
Sets a translation to a game and a key. You can use placeholders that can be replaced later on.

#### mgGetTranslation(lang:text,game:text,key:text,placeholders:object=null) :: text
Returns the translation for the givenn language, game and translation key. Also placeholders can be used.
To use placeholders, a `HashMap(find,replace)` is used. Here is an examle to define a placeholders variable for this function:
```
set {_placeholder} to HashMap()
{_placeholder}.put("<ReplaceMe>","replaced!")
```
If you don't want to use placeholders, use `null` to prevent any errors. 

## Library
MINIGAMES.SK uses some custom made libraries to allow custom features to be used.

#### getClientLanguage(player:player) :: text
Returns the language code of the client as text.

#### getDummy() :: block
Returns a block that can be used to store temporary metadata.

#### HashMap() :: HashMap
Returns a new HashMap, removes the need to load java.util.HashMap in Skript.

#### createBossBar(title:text,barcolor:text="white",barstyle:text="solid") :: Bossbar
Returns a Bossbar that can be used for display purposes. If you use bossbars in your minigame, make sure to remove them from the view of the player once the game stops.
Possible bar colors are: `"blue","green","pink","purple","red","white","yellow"`
Possible bar styles are: `"solid","6","10","12","20"`

#### opengui(player:player,size:integer,name:text,invtype:inventory type=chest inventory)
Opens a GUI menu to the player with the defined size, name and inventory type. This GUI function has an additional function to add items into it.
Valid inventory types:
```
chest inventory, dispenser inventory, dropper inventory, furnace inventory, 
workbench inventory, crafting table inventory, enchanting table inventory, 
brewing stand inventory, player inventory, creative inventory, merchant inventory, 
ender chest inventory, anvil inventory, beacon inventory, hopper inventory, 
shulker box inventory
```

#### setguiitem(player:player,slot:number,item:item,amount:integer,name:text,lore:text,exec:text="",close:boolean=false)
Sets a specific item into the GUI of the player. You can execute a custom function on click by setting the exec parameter to a string based function. The function is later called with SkQuery evaluate.
