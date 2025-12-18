# simple-systemd-services
Simple systemd services specifically meant for Arch Linux automation.
<br>
# System Services
(Coming Soon)
<br>
# User Services
<br>
# Update Notification Service
Runs automatically after login and notifies you via desktop notification if pacman updates are available.
<br>
1. Prerequisites
Install the required tools for checking updates safely and sending notifications:
$ sudo pacman -S pacman-contrib libnotify
<br>
2. Installation
Create the files in your user configuration directory:
~/.config/systemd/user/
updates-notification.service
~/.config/systemd/user/update-notify.service
updates-notification.timer
~/.config/systemd/user/update-notify.timer
<br>
3. Activation
Run these commands as your standard user (do not use sudo):
Reload daemon to recognize new files
$ systemctl --user daemon-reload
Enable and start the timer
$ systemctl --user enable --now update-notify.timer
<br>
4. Verification
You can force a test run immediately with:
$ systemctl --user start update-notify.service
<br>
How it Works
User Scope: These run under your user session (systemctl --user), ensuring notifications appear on your specific display.
<br>
Safety: The script uses checkupdates (from pacman-contrib), which safely checks for updates without syncing the root database or requiring root privileges.
<br>
Enjoy!
