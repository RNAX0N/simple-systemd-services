# simple-systemd-services
# Simple systemd services specifically meant for Arch Linux automation.

# System Services
(Coming Soon)

# User Services
Update Notification Service
Runs automatically after login and notifies you via desktop notification if pacman updates are available.


1. Prerequisites
Install the required tools for checking updates safely and sending notifications:

Bash

sudo pacman -S pacman-contrib libnotify


2. Installation
Create the files in your user configuration directory:

~/.config/systemd/user/

updates-notification.service

updates-notification.timer


3. Activation
Run these commands as your standard user (do not use sudo):

Bash

# Reload daemon to recognize new files
systemctl --user daemon-reload

# Enable and start the timer
systemctl --user enable --now update-notify.timer


4. Verification
You can force a test run immediately with:

Bash

systemctl --user start update-notify.service

How it Works
User Scope: These run under your user session (systemctl --user), ensuring notifications appear on your specific display.

Safety: The script uses checkupdates (from pacman-contrib), which safely checks for updates without syncing the root database or requiring root privileges.

Enjoy!
