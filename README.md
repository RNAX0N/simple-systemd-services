# simple-systemd-services
Some Simple systemd Services (Specifically Meant for Arch Linux)

# SYSTEM SERVICES

# USER SERVICES
# UPDATE NOTIFICATION SERVICE
*Runs at startup and informs the user if there are available pacman updates*

Install Packages:
sudo pacman -S pacman-contrib libnotify

Put the files at the following locations:
~/.config/systemd/user/updates-notification.service
~/.config/systemd/user/updates-notification.timer

Run as standard user WITHOUT sudo:
systemctl --user daemon-reload
systemctl --user enable --now update-notify.timer

You can test the service immediately with:
systemctl --user start update-notify.service

User Service: These run under your user session (systemctl --user), ensuring notifications appear on your specific display.

Safety: The script uses checkupdates (from pacman-contrib), which safely checks for updates without syncing the root database or requiring sudo.

Enjoy!
