# Create a minigame
MINIGAMES.SK offers server operators to use Skript to make their minigames.
It uses functions that are used in Skript to make it easy to create minigames in Skript.


**1.** Select a name for your minigame and create a folder named by it (case sensitive) into the `plugins/Skript/scripts/MINIGAMES.SK/games/` folder.

---

**2.** Create the following files that can be empty for now: `init.sk`, `functions.sk`, `config.sk`.

---

**3.** Create functions that handle all interactions that can be made by players and add them to `functions.sk`.

**Example:**

```
function mgMyFirstGameStartgame():
  broadcast "my game has been started! 50 seconds to go!, rightclick!"
  
  loop 50 times:
    wait 1 second
    send action bar "%50 - loop-number% seconds left!" to all players

  set {_winner} to mgGetCurrentGamePointsWinner("MyFirstGame","clicks") 
  broadcast "%{_winner}% has won!"

  mgFinishGame()

function mgMyFirstGameRightclick(player:player):
  message "you rightclicked, that's 1 point for you!" to {_player}
  
  mgAddCurrentGamePoints("MyFirstGame",{_player},"clicks",1)
  mgSetSidebarToplist("MyFirstGame","clicks",5,1)
  
```

---

**4.** Add all events and function calls that need to be triggered for the functions into `init.sk`.
**Example:**
```
on rightclick:
  mgMyFirstGameRightclick(player)
```

---

**5.** Add a function or your scripting that starts your minigame to the `on load` event in `init.sk`
**Example:**
```
on load:
  mgMyFirstGameStartgame()
```

---

**6.** Once your game finishes, call the `mgFinishGame()` function. You can do much more with MINIGAMES.SK, check out the [functions](functions.md) and the [documentation](documentation.md).
