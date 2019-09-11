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

