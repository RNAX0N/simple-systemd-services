# simple-systemd-services
## Simple systemd services specifically meant for Arch Linux automation

## System Services
(Coming Soon)
<br>
## User Services
### Update Notification Service
* Runs automatically after login and notifies you via desktop notification if pacman updates are available.
#### Prerequisites
Install the required tools for checking updates safely and sending notifications: <br><br> $ sudo pacman -S pacman-contrib libnotify

#### Installation
Put the files in your user configuration directory:<br><br>
~/.config/systemd/user/update-notify.service<br>
~/.config/systemd/user/update-notify.timer<br>
#### Activation
Run these commands as your standard user (do not use sudo):
Reload daemon to recognize new files:<br><br>
$ systemctl --user daemon-reload
Enable and start the timer:<br>
$ systemctl --user enable --now update-notify.timer
<br>
#### Verification
You can force a test run immediately with:<br><br>
$ systemctl --user start update-notify.service
#### How it Works
User Scope: These run under your user session (systemctl --user), ensuring notifications appear on your specific display.
#### Safety
The script uses checkupdates (from pacman-contrib), which safely checks for updates without syncing the root database or requiring root privileges.

#### Enjoy!

