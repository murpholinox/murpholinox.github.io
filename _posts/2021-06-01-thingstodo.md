---
layout: post
title: Things to do after installing Fedora 34
published: true
tag: Fedora
---


Fedora 34 is very nice. Here are a few things you must do after installing Fedora ...  

## Update
Open your terminal and do `sudo dnf update`. 

## Install some stuff
### Typora
```bash
cd Downloads
wget https://typora.io/linux/Typora-linux-x64.tar.gz
tar xvzf Typo*
cd
echo "alias typora='/home/`whoami`/Downloads/bin/Typora-linux-x64/Typora'" >> .bashrc
```
or try  `marker` with `sudo dnf -y install marker`.

### Vim 
`sudo dnf -y install vim`.

### VLC
Enable the RPM-Fusion repositories with
```bash
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm 
```
and then do `sudo dnf -y install vlc`.

## Change some settings
Open the settings application and ...

### Change the default hostname
Go to 'About' section (at the bottom) and substitute the 'Device Name' from 'fedora' to your favorite hostname.

###  Set the night light mode
Go to 'Displays' (12th entry), click on the 'Night Light' button and choose your preferences.  

### Add a keyboard shortcut for the terminal
Go to 'Keyboard' (14th entry) and scroll to the bottom to find 'Customize Shortcuts', click on it and scroll again to the bottom to find 'Custom Shortcuts'. Click on 'Add Shortcut' and fill in the blanks. 

![shortcut]({{ site.url }}/assets/images/shortcut.png)

### Add an international keyboard layout
Still in 'Keyboard', go to 'Input Sources', and click on the plus sign to add a new keyboard layout. Choose 'English (United States)' and then scroll down until you find something like 'English (intl., with AltGr dead keys)', choose it. Remove the old keyboard layout.

## Some tweaks
Install `gnome-tweaks` with `sudo dnf -y install gnome-tweaks` and open it.
### Make a useful touchpad
Go to 'Keyboard & Mouse' and choose 'Area' under 'Mouse Click Emulation'.

### Bring back the maximize and minimize buttons to all windows
Now go to the 'Window Titlebars' section and toggle the maximize and minimize buttons.

## Firefox preferences

Sign in to your Firefox account to synchronize all of your extensions and preferences.

![signinfirefox]({{ site.url }}/assets/images/signinfirefox.png)

> Update: A nice alternative is the brave browser.
