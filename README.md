# MINIGAMES.SK
A minigames library for servers using skript with high customizability and an easy API to add new minigames on your own.
	

### Dependencies
- [Spigot](https://hub.spigotmc.org/stash/projects/SPIGOT) Minecraft Java version 1.13.2
- [Skript](https://github.com/SkriptLang/Skript)
- [skript-mirror](https://github.com/btk5h/skript-mirror)
- [SkQuery](https://www.spigotmc.org/resources/unofficial-skquery-fork-1-6-1-12.36631/)


### Why MINIGAMES.SK
MINIGAMES.SK has a unique vote & play system which allows even small servers to offer minigames, since it only needs one server on which all minigames of this library can be voted before the game and then also be played. Thanks to a changeable minimum amount of players for specific minigames, only fitting minigames for the amount of players are selected to be voted on.
MINIGAMES.SK aims to give a great experience for players and servers and their server operators with a player base of 1 (singleplayer mode) to 60 players per game. Skript is [well documented](http://skriptlang.github.io/Skript/), free and accessible to everyone who can read and write.

### Demo servers
If you're running MINIGAMES.SK, feel free to create a issue to get your server displayed here.
- join.skyroad.me
  - [Website](https://skyroad.me)
  - [Discord](https://discord.gg/FRuK5BC)

### Roadmap
- Add Core functionality 
- Add voting system
- Automatic loading of used and unloading of unused minigame skripts
- Add statistics system (mysql & yaml storage)
- Add a API which can be used by minigames:
- - timer
- - game status
- - game points
- - game money
- - stop game
- - start game (should only be used by the core)
- - temporary ingame variable function using metadata
- - game finish function which can halt any minigame + can be used by the minigames
- - player stats
- - toplists per game & global
- Add custom function execution on the end in the configuration to allow customized things to happen per game & global.
- Add more minigames
- Create a documentation
- Add a tutorial on how to create new minigames
- Add  multible languages to the project
- Add new addons which improve the game
- Publish MINIGAMES.SK to https://forums.skunity.com and maintain/update it for future versions of minecraft
