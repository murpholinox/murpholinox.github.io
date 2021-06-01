---
layout: post
title: How to get a 'minimal' Fedora with a Gnome Desktop?
published: true
tag: Fedora
---



...some might disagree with the 'minimal' term.



## Installation

1. Download the `iso`  [file](https://download.fedoraproject.org/pub/fedora/linux/releases/32/Everything/x86_64/iso/Fedora-Everything-netinst-x86_64-32-1.2.iso).
2. Burn it to a USB drive with `sudo dd if=/path/to/file.iso of=/dev/sdX`, where you can find the value of X by typing the command `df -h` before and after inserting your USB drive into the computer.
3. Reboot (You gotta told your BIOS to read your USB drive before the HD).
4. Set the language, choose the keyboard layout, set the proper time zone, check that the software sources will be downloaded from the Internet (closest mirror), set the hostname, and finally choose where and how Fedora will be installed (I normally choose the standard partition scheme).
5. In the software selection window, choose "Fedora custom OS" in the first column and "Standard" on the second column. 
> Warning: I have not tried anything else but this works fine.
6. When everything is set, you can go ahead and click on "Begin installation".
7. After installation is complete, reboot and remove your USB drive.

## Add the desktop and some useful applications
Now login and do `sudo dnf -y install @base-x gnome-shell gnome-terminal gnome-tweaks firefox nautilus git vim evince eog` and after that do `sudo systemctl set-default graphical.target`. Reboot and be happy.
