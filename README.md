## This will overwrite your ercf_software.cfg use at your own risk!

# Installation instructions

1. ssh into your pi and run the following commands.This will install the ERCF module and additional config files.

`cd ~/`

`gitclone https://github.com/cpiercedev/ERCFUpdater.git`

`cd ERCFUpdater`

`.\install.sh`


2. Update your Moonraker.conf to include the following

```
[update_manager]
enable_repo_debug: True

[update_manager client ERCF]
type: git_repo
path: /home/pi/ERCFUpdater
origin: https://github.com/cpiercedev/ERCFUpdater.git
install_script: install.sh
```

3. Update ercf_user_vars.cfg and ercg_hardware.cfg to match your setup.
4. ERCF will now be present in the update manager.


Install script modified from klipper_z_calibration
https://github.com/protoloft/klipper_z_calibration

Config/Module from Ette from the Enraged Rabit Project
https://github.com/EtteGit/EnragedRabbitProject
