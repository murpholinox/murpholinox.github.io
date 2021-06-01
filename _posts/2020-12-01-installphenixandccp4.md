---
layout: post
title: How to install CCP4 and Phenix in Fedora?
published: true
tags: XRC
---



To install [CCP4](https://www.ccp4.ac.uk/) and [Phenix](http://www.phenix-online.org/) in Fedora you have to do the following.



## CCP4

Download the installer and do...

```bash
sudo mkdir /opt/xtal
cd ~/Downloads
tar xvzf lin*setup.tar.gz
cd linux-x86_64_ccp4-7.1-setup/
./ccp4-7.1-setup
```

>Warning: in the first window do not forget to tick the option 'modify command line environment'.

Then just click 'next' a few times, fill in the blanks and click on 'Install' and then on 'Finish'

That's it.

## Phenix

Phenix used to be easier. Now you gotta register every time you download the suite.
![phenix]({{ site.url }}/assets/images/rect865.png)

After that the password is sent to your academic email address and you must download the software before the password expires (If I remember correctly it's about a week). 

Then do...

```bash
cd ~/Downloads
tar xvzf phen*
cd phenix-installer-1.19.2-4158-intel-linux-2.6-x86_64-centos6/
sudo ./install
cd
echo "#Phenix" >> .bashrc 
echo "source /usr/local/phenix-1.19.2-4158/phenix_env.sh" >> .bashrc
```

Be happy!
