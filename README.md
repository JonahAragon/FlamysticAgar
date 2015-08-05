# Agar Emulator (by [Flamystic](http://www.flamystic.com/))
A fully functional open source Agar.io server implementation, written in Node.js. This emulator is designed to be used with the latest Agar.io client.

## Official Website
The official website for this project is [www.flamystic.com](http://www.flamystic.com). You can register on our forums to chat with other users, get support, advertise your server, and more.

## Purchased this emulator?
If you've purchased a copy of this emulator, you've probably been ripped off. Flamystic is providing this modified version of the "Ogar" project under a open source license, as illustrated at [LICENSE.md](LICENSE.md), for free usage.

## Obtaining and Using

### Prerequisites

 * Node.js and NPM
  * This can be downloaded from your distro's package manager (for *nix systems), or from [the Node website](http://nodejs.org) (for Windows, Mac).
 * Python
  * Usually preinstalled with *nix distros. On Windows it can be downloaded from [this page](https://www.python.org/downloads/windows/). You will need to download Python 2.7.x, not Python 3.x.x!
 * "ws" Node module
  * In your command line/terminal, enter `npm install ws` (this requires Node.js and Python first!)
 * Git
  * Usually preinstalled with *nix distros. If not run `sudo apt-get install git` (Debian/Ubuntu) or `yun install git` (Fedora/OpenSUSE). On Mac it can be downloaded from [git-scm.com](https://git-scm.com/download/mac). On Windows you can download it from [git-scm.com](https://git-scm.com/download/win) or download [GitHub for Windows](https://windows.github.com/).

Windows:

 * Download the Agar.io Emulator [here](https://github.com/JonahAragon/FlamysticAgar/archive/master.zip).
 * Unzip the archive
 * Inside the [`src`](/src) folder, double click [`Start.bat`](/src/Start.bat).

Linux:
```sh
~$ git clone git://github.com/JonahAragon/FlamysticAgar.git FlamysticAgar
~$ npm install ws
~$ cd FlamysticAgar
~$ node index.js
```

Currently, the emulator listens on the following ports:
* *:80 - for the master server
* *:443 - for the game server

Please note that on some systems, you may have to run the process as root or otherwise elevate your privileges to allow the process to listen on the needed ports. **If you are getting an EADDRINUSE error, it means that the port required to run this emulator is in use. Usually, Skype is the culprit. To solve this, either close out skype, or change the serverPort value in gameserver.ini to a different port. You will have to change your connection ip to "127.0.0.1:PORT"**

Once the game server is running, you can connect (locally) by typing `agar.io/?ip=127.0.0.1:443` into your browser's address bar.

## Configuring the server
Use `gameserver.ini` to modify the server's configurations field. Player bots are currently basic and for testing purposes. To use them, change `serverBots` to a value higher than zero in the configuration file. To add/remove bot names, edit the file named `botnames.txt` which is in the same folder as `gameserver.ini`. Names should be separated by using the enter key.

## Custom Game modes
This has support for custom game modes. To switch between game modes, change the value of "serverGamemode" in the configurations file to the selected game mode id and restart the server. The current supported game modes are:

Id   | Name
-----|--------------
0    | Free For All
1    | Teams
2    | Experimental (As of 6/13/15)
10   | Tournament
11   | Hunger Games
12   | Zombie Mode
13   | Team Z
14   | Team X
20   | Rainbow FFA - Hint: Use with "setAcid(true)"

## Console Commands
The current available console commands are listed here. Command names are not case sensitive, but player names are.

 - Addbot [Number]
   * Adds [Number] of bots to the server. If an amount is not specified, 1 bot will be added.
 - Board [String 1] [String 2] [String 3] ...
   * Replaces the text on the leaderboard with the string text.
 - Boardreset
   * Resets the leaderboard to display the proper data for the current gamemode
 - Change [Config setting] [Value]
   * Changes a config setting to a value. Ex. "change serverMaxConnections 32" will change the variable serverMaxConnections to 32. Note that some config values (Like serverGamemode) are parsed before the server starts so changing them mid game will have no effect.
 - Clear
   * Clears the console output
 - Color [Player ID] [Red] [Green] [Blue]
   * Replaces the color of the specified player with this color.
 - Exit
   * Closes the server.
 - Food [X position] [Y position] [Mass]
   * Spawns a food cell at those coordinates. If a mass value is not specified, then the server will default to "foodStartMass" in the config.
 - Gamemode [Id]
   * Changes the gamemode of the server. Warning - This can cause problems.
 - Kick [Player ID]
   * Kicks the specified player or bot from the server.
 - Kill [Player ID]
   * Kills all cells belonging to the specified player.
 - Killall
   * Kills all player cells on the map.
 - Mass [Player ID] [Number]
   * Sets the mass of all cells belonging to the specified player to [Number].
 - Name [Player ID] [New Name]
   * Changes the name of the player with the specified id with [New Name].
 - Playerlist
   * Shows a list of connected players, their IP, player ID, the amount of cells they have, total mass, and their position. 
 - Pause
   * Pauses/Unpauses the game.
 - Reload
   * Reloads the config file used by the server. However, the following values are not affected: serverPort, serverGamemode, serverBots, serverStatsPort, serverStatsUpdate.
 - Status
   * Shows the amount of players currently connected, time elapsed, memory usage (memory used/memory allocated), and the current gamemode.
 - Tp [Player ID] [X position] [Y position]
   * Teleports the specified player to the specified coordinates.
 - Virus [X position] [Y position] [Mass]
   * Spawns a virus cell at those coordinates. If a mass value is not specified, then the server will default to "virusStartMass" in the config.

## Contributing
Please see [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## License
Please see [LICENSE.md](LICENSE.md).
