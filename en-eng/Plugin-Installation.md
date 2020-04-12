## Installation

Python version 3.5 or higher required &amp; Domoticz version 3.87xx or greater.
For more information on Python requirements we advise you to go to the [Domoticz Python page](https://www.domoticz.com/wiki/Using_Python_plugins).
Make sure that you have the __python3-dev__ package installed.

To install:

1. If you are on a Synology NAS platform
   * [Plugin-Installation on Syno](Plugin-Installation-on-Synology-NAS.md)
   
1. Integrated Domoticz and Plugin installation ** In case you start from scratch (no Domoticz installed yet) **
   * Simply go to [Packaging Domoticz for Debian, Ubuntu, Raspbian and Fedora](https://danielpocock.com/domoticz-packaging-debian-ubuntu-raspbian-fedora/)
   
1. If you run Fedora on an ARM and you want to use PiZiGate 
   * https://github.com/pipiche38/Domoticz-Zigate-Wiki/blob/master/en-eng/PiZigate_on_Fedora.md
   
1. Installation from GitHub Repository
   
   1. If you are installing and using the plugin with a PiZigate you have to check some pre-requisities :
      * You must be on a Raspbian distribution
      * You must install the wiringPi package to get access to gpio commands
      * A Cookbook for PiZigate on an RPI3B+ is available [here](https://github.com/pipiche38/Domoticz-Zigate-Wiki/blob/master/en-eng/PiZigate-RPI3B+-Cookbook.md)
   
      1. ```
         sudo apt-get update
         sudo apt-get upgrade
         sudo apt-get install wiringpi
         ```
     
      1. `hash -r`
     
      1. In order to test if wiringPi is well installed you can :
     
         `gpio -v`
     
         `$ gpio readall`
     
      * You must be on a plugin version at least equal to 4.1
        Starting with that version, you have a tool available under the plugin Tools folder named `pi-zigate.sh`
        Before starting the plugin, you must set the PiZigate in running mode and for that you have to run
     
         `Tools/pi-zigate.sh run`
     
         You'll see the Blue lead on the Pi-Zigate switchin on.
     
        From there go ahead
     
   1. For Unix system using the Python Plugin Manager
      * If you have [pp-manager](https://github.com/ycahome/pp-manager) installed on your system
      * Just search for "Zigate Plugin" entry and add it.

   1. For manual installation
      * Go in your Domoticz directory using a command line and open the plugins directory.
      * Usually you should be under <code>domoticz/plugins</code>
      * Run: `git clone https://github.com/pipiche38/Domoticz-Zigate.git`
      * It will create a folder 'Domoticz-Zigate'
      * Make the plugin.py file executable `chmod +x Domoticz-Zigate/plugin.py`
      * Restart Domoticz.

In the Domoticz Web UI, navigate to [the Hardware page](https://github.com/pipiche38/Domoticz-Zigate-Wiki/blob/master/en-eng/DzPluginMenu.md). 

  * In the hardware dropdown there will be an entry called &quot;Zigate plugin&quot;.
  * On the first use of the Zigate, you have also to set True the ErasePDM in order to reset the ZIgate and get it initialized with the plugin.



## Update

The plugin is regularly updated. For bug fixing or enhancement. In order to keep the plugin up to date

* Go in your Domoticz directory using a command line and open the plugins directory then the Domoticz-Zigate-Plugin directory.
* Run: `git pull`
* In case you have edited/updated some of the plugin controlled file, you might get an error message protecting any update. In such situation you can reset those files with the latest version with the following commands
  ```
  git reset –-hard
  git pull --force
  ```

* Run: `sudo chmod +x plugin.py`
* Restart Domoticz.

## Protect your data

You have __critical__ files under the Domoticz-Zigate folder. In case of crash, you might want to have backup to restore. Here after are the files to backup

    Conf/PluginConf-*.json
    Data/*
    Reports/*

Of course you must backup the Domoticz Database `domoticz.db` (check to Domoticz) __at the same time__ in order to have consistency between the two.

## Plugin branches

The plugin is under constant development in order to fix bugs and add new features as well as to support new devices.

The code is available under different branches

## About release channels

In order to provide stability and also provide more recent development, Zigate plugin has the following channels :

### stable

This is considered as a solid , reliable version.

### beta

We can open the beta channel to provide early version and to stabilize the version prior to move to the stable channel

## How to switch from one channel to the other

`git pull`

`git checkout stable  // will move you to the stable channel`

`git checkout beta    // will move you to the beta channel`
