---
layout: post
title: How to install Tex Live in Fedora?
published: true
tag: LaTex
---



Here  is how to install the latest version of Tex Live in Fedora. 



1.  
```bash
sudo dnf -y install aria2 perl-Tk tk 
cd ~/Downloads
aria2c --seed-time=1 https://tug.org/texlive/files/texlive2021-20210325.iso.torrent
sudo mkdir /mnt/iso && sudo mount -t iso9660 -o ro,loop,noauto /home/murphy/Downloads/texlive*iso /mnt/iso
cd /mnt/iso/ 
sudo ./install-tl -gui 
```

2. Click on 'Advanced' ... 
![1stwintexlve]({{ site.url }}/assets/images/first_window_texlive.png)
3. Change the personal directory and the size of the paper (in Mexico we do not have A4 paper or at least is difficult to get it) and we hit the button 'Install' 
![2ndwintexlve]({{ site.url }}/assets/images/second_window_texlive.png)

4. After installation is complete do in your terminal `cd && echo PATH=/usr/local/texlive/YEAR/bin/x86_64-linux:$PATH >> ~/.bashrc`, where YEAR is the version of your Tex Live.

5. Set up Tex Live fonts for system-wide use. 

```bash
cd /
sudo find -name "texlive-fontconfig.conf"
cp /path/to/found/file /etc/fonts/conf.d/09-texlive.con
fc-cache -fsv
```

That's it.
