# functions.md

Here, the functions of MINIGAMES.SK core are explained. Use `Strg + F` to search in your browser for what you want.


## Points
Points are used to determine the points of a player. You are able to create custom points for every game, points are always non-persistent and get deleted once a game ends.

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



