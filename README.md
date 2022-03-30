## This will overwrite your ercf_software.cfg use at your own risk! 
I try to keep this as up to date as possible with the current configurations of the ERCF, but as it is done manually, some updates may take longer.
This has been tested using an EASYbrd and is what I am currently running on my machine, please reach out if you are having any issues. My discord username is @str1pes#8901.

# Installation instructions

1. ssh into your pi and run the following commands.This will install the ERCF module and additional config files.

`cd ~/`

`git clone https://github.com/cpiercedev/ERCFUpdater.git`


`ERCFUpdater/install.sh`



2. Update your Moonraker.conf to include the following

```
[update_manager client ERCF]
type: git_repo
path: /home/pi/ERCFUpdater
origin: https://github.com/cpiercedev/ERCFUpdater.git
install_script: install.sh
```

3. If you are currently using the standard setup described in the manual, you should not need to make any changes. If you are using an EASYBRD follow the steps below. Please verify your config as each machine may be different.
      - Replace the contents of `ercf_hardware.cfg` with `EASYBRD_ercf_hardware.cfg`.
      - Update the serial for mcu ERCF in `ercf_user_vars_cfg`. You can find the serial by running the following on your pi.
	      `ls -l /dev/serial/by-id/`.
        
4. ERCF will now be present in the update manager.


## Note

|Files|Updates| Static |
|-------|--|-----|
|   ercf_software.cfg    |   :heavy_check_mark:  | :x:
|   ercf.py   |   :heavy_check_mark:    | :x:
|   ercf_user_vars.cfg   |   :x:    | :heavy_check_mark: 
|   ercf_vars.cfg   |   :x:   | :heavy_check_mark: 
|   ercf_hardware.cfg   |    :x:  | :heavy_check_mark: 

Files containing configurations specific to your printer will not be updated. This means if there is a change to those files on the main ERCF branch they will need to be manually updated in your config. Moving forward I will be sure to add any changes that need to be made to those files to new commits.  

## Changes to static configs
- 3/23/22 
	- `ercf_user_vars.cfg`
		- `[gcode_macro ERCF_VAR]` changed to `[gcode_macro _ERCF_VAR]` 
		- New variable added  `variable_sensorless_selector: 0` under `variable_endless_spool_mode: 0`
	- `ercf_hardware.cfg`
		- [Commit](https://github.com/EtteGit/EnragedRabbitProject/commit/d6bfdd953ca2b423e540f732638cb535b9b59270) added to set up stallguard functionality. You can copy these changes from the up to date `ercf_user_vars.cfg` or `EASYBRD_ercf_user_vars.cfg` files.

##
Install script modified from klipper_z_calibration
https://github.com/protoloft/klipper_z_calibration

Config/Module from Ette from the Enraged Rabit Project
https://github.com/EtteGit/EnragedRabbitProject
