| [MINIGAMES.SK](https://github.com/Abwasserrohr/MINIGAMES.SK) Documentation | [Index](index.md) | [Setup](setup.md) | [Functions](functions.md) | [Create a minigame](create_a_minigame.md) |
| -------- | -------- | -------- | -------- | -------- |

# Functions

Here, the functions of MINIGAMES.SK core are explained. Use `Strg + F` to search in your browser for what you want.

## Index:

* **[Points](#Points)**
* **[Sidebar](#Sidebar)**
* **[World](#World)**
* **[Language](#Language)**
* **[Database](#Database)**
* **[Miscellaneous](#Miscellaneous)**
* **[Library](#Library)**



## Points
Points are used to determine the progress of a player. You are able to create custom points for every game, points are always non-persistent and get deleted once a game ends.

---

##### `mgSetCurrentGamePoints(game:text,player:player,pointsname:text,points:number)`
This function allows you to set the points for a specific game and points name of a player to a value. If the points don't exist yet, they will be created automatically by this.

---

##### `mgRemoveCurrentGamePoints(game:text,player:player,pointsname:text,points:number)`
This function is going to remove the given amount of points from the player's points.

---

##### `mgGetCurrentGamePointsWinner(game:text,pointsname:text) :: offline player`
This function will select the winner of the game depending on the game and the points name that is defined.

---

##### `mgGetCurrentGamePointsList(game:text,pointsname:text) :: HashMap(player,amount)`
Returns a HashMap out of all players that have points.

---

##### `mgGetCurrentGamePoints(game:text,player:player,pointsname:text) :: number`
Returns the number of points the player has for this game and points name.

---

##### `mgAddCurrentGamePoints(game:text,player:player,pointsname:text,points:number)`
Adds the given amount of points to the game and points name for the player. If the points don't exist yet, this function will also create them automatically.



## Sidebar
The sidebar is used for custom information that can be set by the minigame. MINIGAMES.SK has integrated functions to use the sidebar easy and efficient.

---

##### `mgWipePersonalSidebarContent(player:player or null)`
Players can have personal content on their sidebar, if necessary, it can be wiped with this function.
By setting the parameter to null, all player sidebars are going to be wiped out.

---

##### `mgWipeGlobalSidebarContent()`
To remove any content that is globally stored on the sidebar, use this function.

---

##### `mgStartSidebarProcess(player:player)`
Do not use this function, since it will start automatically, you don't have to call it to enable the sidebar.
Starts a sidebar process for the defined player, this has an integrated check that will monitor the process to ensure a working sidebar.

---

##### `mgSetSidebarToplist(game:text,pointsname:text,limit:number,startslot:number)`
This function sets a toplist into the sidebar. The game and points name has to be definied to make sure the right points are counted.
The size of the toplist and the start slot on the toplist within the sidebar can be defined to allow better customizability.

---

##### `mgSetPersonalSidebarSlotContent(slotnumber:number,player:player,translationgame:text,translationkey:text,placeholders:HashMap(find,replace))`
Sets the personal sidebar slot of a player to a predefined translation key of a game. You can use placeholders, which are a `HashMap`, the key is the searched key, the value the replaced value for the placeholder.
You can create a HashMap placeholder replacement like this:
```
set {_placeholder} to HashMap()
{_placeholder}.put("<ReplaceMe>","replaced!")
```
This function uses translation keys instead of simple strings to allow a good user experience, since the sidebar will display the text in the client language.

---

##### `mgSetGlobalSidebarSlotContent(slotnumber:number,translationgame:text,translationkey:text,placeholders:object)`
Sets the global sodebar slot to a predefined translation key of a game. You can use placeholders, which are a `HashMap`, the key is the searched key, the value the replaced value for the placeholder.
You can create a HashMap placeholder replacement like this:
```
set {_placeholder} to HashMap()
{_placeholder}.put("<ReplaceMe>","replaced!")
```
This function uses translation keys instead of simple strings to allow a good user experience, since the sidebar will display the text in the client language.

---

##### `mgRemovePersonalSidebarContent(slot:number,player:player)`
Removes a specific sidebar slot from the personal sidebar of a player.

---

##### `mgRemoveGlobalSidebarContent(slot:number)`
Removes a specific sidebar slot from the global sidebar.

---


## World
Each minigame gets it's own world that gets deleted after a game ends. This is very efficient, as it doesn't require a separate process to restore.

---

##### `mgGetCurrentWorld() :: world`
Returns the current minigame world that is being used for the game.

---

##### `mgDeleteGameWorld(world:world)`
Teleports all players out, unloads all chunks and deletes the defined world instantly.

---

##### `mgCreateGameWorld(game:text,source:text)`
Creates a new game world. This function can copy a world from a custom source and copy it to use it for the game.

---

## Language
Minigames should support multiple languages to offer each player a good gameplay experience. These functions will help with that.

---

##### `mgSetTranslation(lang:text,game:text,key:text,value:text)`
Sets a translation to a game and a key. You can use placeholders that can be replaced later on.

---

##### `mgGetTranslation(lang:text,game:text,key:text,placeholders:object=null) :: text`
Returns the translation for the givenn language, game and translation key. Also placeholders can be used.
To use placeholders, a `HashMap(find,replace)` is used. Here is an examle to define a placeholders variable for this function:
```
set {_placeholder} to HashMap()
{_placeholder}.put("<ReplaceMe>","replaced!")
```
If you don't want to use placeholders, use `null` to prevent any errors. 

---

## Database
Persistent data is stored in the database. These functions use the database to retrieve the data.
Since the database has to be called first, it takes some ticks until the data is available. To make the process easier, functions have been added to manage this.

---

##### `mgAddPlayerToplistWin(game:text="global",player:offline player,amount:number=1)`
Adds a win by a player for the specified game to the toplist.

---

##### `mgRemovePlayerToplistWin(game:text="global",player:offline player,amount:number=1)`
Removes a win by a player for the specified game from the toplist.

---

##### `mgAddPlayerToplistScore(game:text="global",player:offline player,amount:number=1)`
Adds the specified score of a player for the specified game to the toplist.

---

##### `mgRemovePlayerToplistScore(game:text="global",player:offline player,amount:number=1)`
Removes the specified score of a player for the specified game from the toplist.

---

##### `mgGetToplistByWin(game:text="global",limit:number=10)`
Returns a uuid text that can be used to retrieve the toplist.
Use `mgGetToplistByWinResponse(uuid:text) :: object` to get the HashMap(uuid,wins) that is the toplist.
An example how you can use these functions is showed below at the `mgGetPlayerScore` function.

---

##### `mgGetToplistByScore(game:text="global",limit:number=10)`
Returns a uuid text that can be used to retrieve the toplist.
Use `mgGetToplistByScoreResponse(uuid:text) :: object` to get the HashMap(uuid,wins) that is the toplist.
An example how you can use these functions is showed below at the `mgGetPlayerScore` function.

---

##### `mgGetPlayerWin(game:text="global",player:offline player)`
Returns a uuid text that can be used to retrieve the wins of the player.
Use `mgGetPlayerWinResponse(uuid:text) :: number` to get the wins.
An example how you can use these functions is showed below at the `mgGetPlayerScore` function.

---

##### `mgGetPlayerScore(game:text="global",player:offline player)`
Returns a uuid text that can be used to retrieve the score of the player.
Use `mgGetPlayerScoreResponse(uuid:text) :: number` to get the score.
Example usage, you can apply this also to other database functions that work similar.
```
command /score:
  trigger:
    set {_transaction} to mgGetPlayerScore("global",player)
    while mgGetPlayerScoreResponse({_transaction}) is not set:
      wait 1 tick
    set {_score} to mgGetPlayerScoreResponse({_transaction})
    message "Your Score: %{_score}%"
```

---

## Miscellaneous
MINIGAMES.SK has various other function that haven't been categorized to one of the listed topics. These are listed here.

---

##### `mgSetTemporaryGameData(key:text,object:object)`
Set any variable to a key that is stored until the game is over.

---

##### `mgGetTemporaryGameData(key:text) :: object`
Returns the stored variable that has been stored to this key.

---

##### `mgSetCurrentGameStatus(status:text)`
Sets the current game status of the minigame. Can be used to determine the current game status within the minigame.

---

##### `mgGetCurrentGameStatus() :: text`
Returns the current game status that has been set previously.

---

##### `mgSetCurrentGame(game:text)`
Sets the current game name. Is used by the lobby script and internally.

---

##### `mgGetCurrentGame() :: text`
Returns the current game name. Can be used to stop while loops of the minigame once this changes.

---

##### `mgFinishGame()`
Use this function to stop your minigame once it has finished.

---

##### `mgStartGame(game:text)`
Starts a minigame with the given name. This should only be used by the Lobby game.

---

##### `mgClearGameData()`
Clears the temporary game data. Is being used by internal functions, use this only for debugging.

---

##### `mgGetAvailableMinigames() :: objects`
Returns a list that contains all minigame names as text.

---

##### `mgDisplayBossbarCountdown(seconds:number,translationtextgame:text,translationtextkey: text,placeholders:object)`
Creates a bossbar countdown for the given seconds and a specified translation game and key. Accepts placeholders, if no placeholders are given, use null.
The placeholder parameter must be a HashMap(find, replace), example:
```
set {_placeholder} to HashMap()
{_placeholder}.put("<ReplaceMe>","replaced!")
```

---

##### `mgCreateAnimatedTextList(text:text,color1:text,color2:text,effect:text) :: objects`
Creates a list that can be played to animate the text. It allows to switch between two colors and animate with multiple effects.
Currently available effects: "shine", "fill", "fillshine"

---

## Library
MINIGAMES.SK uses some custom made libraries to allow custom features to be used.

---

##### `getClientLanguage(player:player) :: text`
Returns the language code of the client as text.

---

##### `getDummy() :: block`
Returns a block that can be used to store temporary metadata.

---

##### `HashMap() :: HashMap`
Returns a new HashMap, removes the need to load java.util.HashMap in Skript.

---

##### `createBossBar(title:text,barcolor:text="white",barstyle:text="solid") :: Bossbar`
Returns a Bossbar that can be used for display purposes. If you use bossbars in your minigame, make sure to remove them from the view of the player once the game stops.

Possible bar colors are: `"blue","green","pink","purple","red","white","yellow"`

Possible bar styles are: `"solid","6","10","12","20"`

---

##### `opengui(player:player,size:integer,name:text,invtype:inventory type=chest inventory)`
Opens a GUI menu to the player with the defined size, name and inventory type. This GUI function has an additional function to add items into it.
Valid inventory types:
```
chest inventory, dispenser inventory, dropper inventory, furnace inventory, 
workbench inventory, crafting table inventory, enchanting table inventory, 
brewing stand inventory, player inventory, creative inventory, merchant inventory, 
ender chest inventory, anvil inventory, beacon inventory, hopper inventory, 
shulker box inventory
```

---

##### `setguiitem(player:player,slot:number,item:item,amount:integer,name:text,lore:text,exec:text="",close:boolean=false)`
Sets a specific item into the GUI of the player. You can execute a custom function on click by setting the exec parameter to a string based function. The function is later called with SkQuery evaluate.

---
