#nmssavetool
A command line tool to decrypt, encrypt, and modify No Man's Sky game save files
===============================================

Created by [Matthew Humphrey](https://github.com/matthew-humphrey)

This is a simple tool to allow decoding, encoding, and convenient editing operations
on saves for the No Man's Sky game.

Download [precompiled binary](https://github.com/matthew-humphrey/nmssavetool/releases/latest)

##Usage

Run "nmssavetool help" for help.

```
> nmssavetool help

nmssavetool 1.5.5.0

  decrypt    Decrypt the latest game save slot and write it to a formatted JSON file.

  encrypt    Encrypt a JSON file and write it to the latest game save slot.

  modify     Refresh, repair, or refill exosuit, multitool, ship, or freighter inventory.

  help       Display more information on a specific command.

  version    Display version information.
```

Supported commands

* decrypt - Decrypt the latest save game for the specified game mode (normal/survival/creative) and write it to a file whose location you specify.
* encrypt - Encrypt the file you specify and write it to the latest save game slot for the specified game mode.
* modify - Edit the latest game save slot for the specified game mode to repair damage, maximize energy levels, and/or maximize inventory levels.
* help - Provide help on command-line syntax for any command.
* version - Displays the program's version information.

###decrypt
```
>nmssavetool.exe help decrypt

nmssavetool 1.5.5.0

  -o, --output       Specifies the file to which the decrypted, formatted game save will be written.

  -g, --game-mode    Required. Use saves for which game mode (normal|survival|creative|permadeath)

  -s, --save-dir     Path to game save folder (optional - determined automatically if not provided)

  -v, --verbose      Displays additional information during execution.

  --help             Display this help screen.

  --version          Display version information.
```

###encrypt
```
>nmssavetool.exe help encrypt

nmssavetool 1.5.5.0

  -i, --input         Specifies the JSON input file which will be encrypted and written to the latest game save slot.

  --v1-format         When encrypting, use the old NMS V1 format

  -b, --backup-dir    If provided, will back up game saves to the specified directory.

  -g, --game-mode     Required. Use saves for which game mode (normal|survival|creative|permadeath)

  -s, --save-dir     Path to game save folder (optional - determined automatically if not provided)

  -v, --verbose       Displays additional information during execution.

  --help              Display this help screen.

  --version           Display version information.
```

###modify
```
>nmssavetool.exe help modify

nmssavetool 1.5.0.0

  -a, --all                     Maximize exosuit, multi-tool, ship, freighter, and container inventory, health, fuel,
                                and energy levels. Repair all damage.

  -e, --energy                  Maximize exosuit, multi-tool, and ship energy and fuel (hyperdrive and launcher)
                                levels.

  -i, --inventory               Maximize exosuit, multi-tool, ship, freighter, and container inventory.

  -r, --repair                  Repair damage to exosuit, multi-tool, and ship.

  -t, --apply-to                (Default: exosuit multitool ship freighter container) What to apply changes to.

  --v1-format                   When encrypting, use the old NMS V1 format

  --randomize-ship-seed         Generate a new seed value for the Ship.

  --set-ship-seed               Set the seed value for the Ship.

  --randomize-multitool-seed    Generate a new seed value for the Multitool.

  --set-multitool-seed          Set the seed value for the Multitool.

  --randomize-freighter-seed    Generate a new seed value for the Freighter.

  --set-freighter-seed          Set the seed value for the Freighter.

  --set-units                   Set the player Units.

  --add-units                   Add the specified amount to player Units (negative units will subtract from total).

  --set-galactic-coordinates    Set the player position using the galactic coordinates displayed by signal scanners.

  --set-portal-coordinates      Set the player position using portal coordinates.

  --set-voxel-coordinates       Set the player position using the voxel coordinates used within the save-game file.
                                Format is (x,y,z,ssi).

  --set-galaxy                  Set the galaxy index (0 = Euclid Galaxy, 1 = Hilbert Dimension, 2 = Calypso Galaxy,
                                etc.)

  -b, --backup-dir              If provided, will back up game saves to the specified directory.

  -g, --game-mode               Required. Use saves for which game mode (normal|survival|creative|permadeath)

  -s, --save-dir                Path to game save folder (optional - determined automatically if not provided)

  -v, --verbose                 Displays additional information during execution.

  --help                        Display this help screen.

  --version                     Display version information.
```

##Changelog

###2017-09-02 1.6.0.0

* New verb: info. This can be used to dump information about the most recent game save, including
  the player's position and inventory contents.
* Backup now also writes a decrypted, formatted JSON file. This makes it easy to 
  restore a backup by simply using the encrypt command with one of these JSON files as input.
* Backup now includes the game mode in the output file name.

###2017-08-20 1.5.0.0

* New modify command options, set_galactic-coordinates, set-portal-coordinates, and set-voxel-coordinates allow 
  movement of the player position within the current galaxy
* New modify command option, set-galaxy, allows the player to change the current galaxy.

###2017-08-19 1.4.4.0

* Added the ability to set or add to the player Units total.

###2017-08-13 1.4.3.0

* Added support for new NMS 1.3 Exosuit and Ship inventory groups
* Added support for containers

###2017-03-12 1.4.2.0

* Added option (-s / --save-dir) to explicitly specify the folder containing the game save files.
* Added dump of some troubleshooting info (CLR version and APPDATA folder) to verbose mode display
* Modified game save location logic to work even if save directories do not contain the profile key
  number. This key is not needed for current versions of the game, so perhaps newer installs are
  no longer naming the directory this way.

###2017-03-12 1.4.1.0

* Fixed bug where GoG game save directory detection would only work if a Normal mode game had been saved.

###2017-03-12 1.4.0.0

* Added support for GoG game save directory
* Added support for Permadeath game mode

###2017-03-11 1.3.0.0

* Updated to work with new NMS save file format (version 4101) in the NMS Pathfinder update (version 1.2)

###2017-01-01 1.2.0.1

* Added backup feature

###2016-12-31 1.1.0.0

* Added damage repair to Refill Command
* Switched to a new command-line parsing library
* Moved to a verb-style command line interface, and provide more fine-grained control over modifications.
* Minor refactoring to reduce duplicated code

###2016-12-30 1.0.0.0

* Initial release

===============================================

Many thanks to the authors of the following software libraries used by nmssavetool:

* CsvHelper - http://joshclose.github.io/CsvHelper/
* Json.NET (NewtonSoft) - https://www.newtonsoft.com/json

I would also like to thank No Man's Sky mod maker 'nomansuniverse' and 'Mjjstral', who discovered how to 
decrypt the V1 format NMS save files.

