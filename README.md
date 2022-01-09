# sesrv-script
Bash script for running Space Engineers on a linux server

-------------------------

# What does this script do?

This script creates a new non-sudo enabled user and installes the game in a folder called server in the user's home folder. It also installs systemd services for starting and shutting down the game server when the computer starts up, shuts down or reboots and also installs systemd timers so the script is executed on timed intervals (every 15 minutes) to do it's work like automatic game updates, backups and syncing from ramdisk to hdd. It will also create a config file in the script folder that will save the configuration you defined between the installation process. The reason for user creation is to limit the script's privliges so it CAN NOT be used with sudo when handeling the game server. Sudo is only needed for installing the script (for user creation) and installing packages (if the script supports the distro you are running).

-------------------------

**Features:**

- auto backups

- auto updates

- script logging

- auto restart if crashed

- delete old backups

- delete old logs

- run from ramdisk

- sync from ramdisk to hdd/ssd

- start on os boot

- shutdown gracefully on os shutdown

- can run multiple servers

- script auto update from github

- send email notifications after 3 crashes within a 5 minute time limit (optional)

- send email notifications when server updated (optional)

- send email notifications on server startup (optional)

- send email notifications on server shutdown (optional)

- send discord notifications after 3 crashes within a 5 minute time limit (optional)

- send discord notifications when server updated (optional)

- send discord notifications on server startup (optional)

- send discord notifications on server shutdown (optional)

- supports multiple discord webhooks

-------------------------

# Supported distros

- Arch Linux

- Ubuntu 20.04 LTS

- Ubuntu 19.10

- Ubuntu 18.04 LTS (see known issues)

- Debian 10

The script can, in theory run on any systemd-enabled distro. So if you are not using any of the above listed distros I suggest you check your distro's wiki on how to install the required packages. The script can, in theory install packages for any Ubuntu version, but the repositories for old versions of Ubuntu might have outdated packages and cause problems.

-------------------------

# WARNING

- Script updates from GitHub: This will enable the script to update itself from github WITHOUT your consent. If you don't trust me, leave this off.

-------------------------

# Installation

**Required packages**

- xvfb

- rsync

- tmux (minimum version: 2.9a)

- wine (minimum version: 5.0)

- winetricks (minimum version: 20191224)

- steamcmd

- curl

- wget

- cabextract

- postfix (optional for email notifications)

- zip (optional but required if using the email feature)

-------------------------

**Download the script:**

Log in to your server with ssh and execute:

`git clone https://github.com/7thCore/sesrv-script`

Make it executable:

`chmod +x ./sesrv-script.bash`

-------------------------

**Installation:**

If you wish you can have the script install the required packages with (only for supported distros):

`sudo ./sesrv-script.bash -install_packages`

After that run the script with root permitions like so (necessary for user creation):

`sudo ./sesrv-script.bash -install`

You can also install bash aliases to make your life easier by logging in to the newly created user and executing the script with the following command:

`./sesrv-script.bash -install_aliases`

After the installation finishes you can log in to the newly created user and fine tune your game configuration and then reboot the operating system and the service files will start the game server automaticly on boot.

-------------------------

**World and config files**

The easiest way to do this is to just generate them locally and copy them over to the server, this can be done by using the dedicated server tool on your windows box, the tool is located in

`[Steam install directory]\steamapps\common\SpaceEngineers\Tools\DedicatedServer\SpaceEngineersDedicated.exe`

Select the Default profile, set up the world, save the config and start to generate the world. After that shutdown the server.

The files will be stored in

`C:\Users\<username>\AppData\Roaming\SpaceEngineersDedicated\Default\`

Copy the files with the `Saves` folder to the following directory on your Linux box (if you didn't use the default user name at the begining of the script installation procedure change space_engineers to the user you specified. The script now has multi instance support (defaut instance is 01)

`/home/space_engineers/server/drive_c/users/space_engineers/Application\ Data/SpaceEngineersDedicated/01`

**Essential world tweaks**

You'll have to change the `<LoadWorld>` tag in `SpaceEngineers-Dedicated.cfg` so it point to the correct directory.

If the Save folder is located in

`/home/space_engineers/server/drive_c/users/space_engineers/Application\ Data/SpaceEngineersDedicated/01/Saves/Star System`

the `<LoadWorld>` tag must look like this, where `{username}` is the same as `$(whoami)`

`<LoadWorld>C:\Users\space_engineers\Application Data\SpaceEngineersDedicated\01\Saves\Star System</LoadWorld>` 

You still need to use windows paths and backshlashes in the `SpaceEngineers-Dedicated.cfg` file.

You have to edit each server instance's configuration the same way.

That should be it.

-------------------------

# Available commands:

| Command | Description |
| ------- | ----------- |
| `-help` | Prints a list of commands and their description |
| `-diag` | Prints out package versions and if script files are installed |
| `-add_server` | Adds a server to the active server list. |
| `-remove_server` | Removes a server from the active server list. |
| `-start <server number>` | Start the server. If the server number is not specified the function will start all servers |
| `-start_no_err <server number>` | Start the server but don't require confimation if in failed state |
| `-stop <server number>` | Stop the server. If the server number is not specified the function will stop all servers |
| `-restart <server number>` | Restart the server. If the server number is not specified the function will restart all servers |
| `-sync` | Sync from tmpfs to hdd/ssd |
| `-backup` | Backup files, if server running or not. |
| `-autobackup` | Automaticly backup files when server running |
| `-deloldbackup` | Delete old backups |
| `-delete_save` | Delete the server's save game with the option for deleting/keeping the SpaceEngineers-Dedicated.cfg file |
| `-deloldsavefiles` | Delete the server's save game (leaves the latest number files specefied in the script conf file |
| `-change_branch` | Changes the game branch in use by the server (public,experimental,legacy and so on) |
| `-install_aliases` | Installs .bashrc aliases for easy access to the server tmux session |
| `-rebuild_tmux_config` | Reinstalls the tmux configuration file from the script. Usefull if any tmux configuration updates occoured |
| `-rebuild_services` | Reinstalls the systemd services from the script. Usefull if any service updates occoured |
| `-rebuild_prefix` | Reinstalls the wine prefix. Usefull if any wine prefix updates occoured |
| `-disable_services` | Disables all services. The server and the script will not start up on boot anymore |
| `-enable_services <server number>` | Enables all services dependant on the configuration file of the script |
| `-reload_services` | Reloads all services, dependant on the configuration file |
| `-update` | Update the server, if the server is running it wil save it, shut it down, update it and restart it |
| `-verify` | Verifiy game server files, if the server is running it will save it, shut it down, verify it and restart it |
| `-update_script` | Check github for script updates and update if newer version available |
| `-update_script_force` | Get latest script from github and install it no matter what the version |
| `-attach <server number>` | Attaches to the tmux session of the specified server |-
| `-status` | Display status of server |
| `-install` | Installs all the needed files for the script to run, the wine prefix, systemd services and timers and the game |
| `-install_packages` | Installs all the needed packages (Supports only Arch linux & Ubuntu 19.10 and onward)

-------------------------

# Known issues:

| Issue | Resolution |
| ----- | ---------- |
| Ubuntu 18.04 LTS Support (Script can't enable services during installation) | This version of Ubuntu has a bug in it's systemd component, meaning the script CAN NOT enable the services required for the game to start up after boot. You will have to do this manually by rebooting the os and logging in with the username you designated at the beginning of the install procedure then execute the script with the `-enable_services` argument. |

-------------------------

# How to convert from legacy to the new multi-instance version:

Due to a lot of rewriting of core functions the old version of the script was moved to the legacy branch. All script installations with auto updates enabled have recieved an update co continue checking for updates from the legacy branch. If you want to convert to the new multi-instance version follow this guide:

- shutdown the server

- execute the script with -disable_services

- navigate to the folder /home/$USER/.config/systemd/user and delete the following:
  sesrv-mkdir-tmpfs.service, sersrv-tmpfs.service, sersrv.service

- delete the script from the scripts folder

- download the new script version and copy it to the scripts folder

- make it executable with chmod +x ./home/$USER/scripts/sersrv-script.bash

- execute the script with -rebuild_services

- execute the script with -reload_services

- navigate to the SpaceEngineersDedicated application data and create a new folder (example: StarSystem01):

- move all files (Saves, SpaceEngineers-Dedicated.cfg, Mods, content, cache, temp, appworkshop_244850.acf) to the newly created folder

- make sure to edit the SpaceEngineers-Dedicated.cfg and the LastSession.sbc files to point to the right directory (you changed the paths with the new folder)

- execute the script with the -add_server argument and add server StarSystem01

- execute the script with -enable_services StarSystem01

- start the server with -start StarSystem01

-------------------------

**Disclamer**

Credit goes to github users CoffeePirate and tvwenger. I stumbled upon  CoffeePirate's github page and tvwenger's comment on the same page on how to get it to work. I just modified one of my existing scripts so it would be a bit easier to install and manage the server.

The page is located here:
https://gist.github.com/CoffeePirate/102e789310719cad6457
