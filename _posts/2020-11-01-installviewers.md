---
layout: post
title: How to install PyMOL, Chimera and VMD in Fedora?
published: true
tag: x-ray crystallography
---

## PyMOL

We have three ways to install PyMOL. 

1.  Install from the source code, follow the [wiki](https://pymolwiki.org/index.php/Linux_Install). This is sometimes a pita, sometimes it just works.
2.  Install it with the package manager of your Linux distribution `sudo dnf -y install pymol`. The problem with this approach is that the version installed is not the latest and is the 'educational version'. Debian-based distros, like Ubuntu, will have an older version than Fedora. The good thing is that it just works. 
3.  Get a license [here](https://pymol.org/dsc/index.php?ip=license/) and download `pymol` from [here](https://pymol.org/2/). After that do:

```bash
cd ~/Downloads
tar xvf PyMOL*bz2
cd pymol
cd bin
./pymol
# If you want to run PyMOL from anywhere you have to make an alias
cd
echo "# PyMOL alias" >> .bashrc 
echo "alias pymol='/home/`whoami`/Downloads/pymol/bin/pymol'" >> .bashrc
```

> Warning: This `pymol` does not work in Fedora 34. You only get a black screen. The error is the following:

```bash
libGL error: MESA-LOADER: failed to open iris: /home/murphy/Downloads/pymol/lib/python3.7/site-packages/pymol/../../../libstdc++.so.6: version `GLIBCXX_3.4.29' not found (required by /usr/lib64/dri/iris_dri.so) (search paths /usr/lib64/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open iris: /home/murphy/Downloads/pymol/lib/python3.7/site-packages/pymol/../../../libstdc++.so.6: version `GLIBCXX_3.4.29' not found (required by /usr/lib64/dri/iris_dri.so) (search paths /usr/lib64/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open swrast: /home/murphy/Downloads/pymol/lib/python3.7/site-packages/pymol/../../../libstdc++.so.6: version `GLIBCXX_3.4.29' not found (required by /usr/lib64/dri/swrast_dri.so) (search paths /usr/lib64/dri)
libGL error: failed to load driver: swrast
```

> Update: I gotta say I bought an academic license for a year and supposedly you get documentation and support but the latter is really unnecessary and the documentation was way too old. 


## Chimera

Go [here](https://www.cgl.ucsf.edu/chimera/download.html) and download the appropriate installer for your machine. Then do...

```bash
cd ~/Downloads
chmod +x chimera*.bin
# run it
./chimera-1.15-linux_x86_64.bin
# Press enter three times and you are done
# Do an alias
cd
echo "#Chimera alias" >> .bashrc
echo "alias chimera='/home/murphy/.local/UCSF-Chimera64-1.15rc/bin/chimera'" >> .bashrc
```

> `chimera` is a good alternative to `pymol` and is free of charge for noncommercial use. The main disadvantage is that **Chimera is no longer under active development**, and is only  updated for critical maintenance.


## ChimeraX

`chimeraX` is going to substitute `chimera`. So far I am unable to install it.

```bash
[murphy@eva02 Downloads]$ sudo rpm -i ./ucsf-chimerax-1.2.5-1.el8.x86_64.rpm 
[sudo] password for murphy: 
error: Failed dependencies:
	fftw-libs-single is needed by ucsf-chimerax-1.2.5-1.el8.x86_64
	mesa-libOSMesa is needed by ucsf-chimerax-1.2.5-1.el8.x86_64
[murphy@eva02 Downloads]$ sudo dnf install ./ucsf-chimerax-1.2.5-1.el8.x86_64.rpm 
Last metadata expiration check: 2:29:59 ago on Mon 31 May 2021 07:01:27 PM CDT.
Dependencies resolved.
================================================================================
 Package               Arch        Version              Repository         Size
================================================================================
Installing:
 ucsf-chimerax         x86_64      1.2.5-1.el8          @commandline      307 M
Upgrading:
 mesa-libGL            x86_64      21.1.1-1.fc34        updates           171 k
 mesa-libglapi         x86_64      21.1.1-1.fc34        updates            55 k
Installing dependencies:
 fftw-libs-single      x86_64      3.3.8-10.fc34        fedora            953 k
 mesa-libOSMesa        x86_64      21.1.1-1.fc34        updates           3.1 M

Transaction Summary
================================================================================
Install  3 Packages
Upgrade  2 Packages

Total size: 311 M
Total download size: 4.3 M
Is this ok [y/N]: y
Downloading Packages:
(1/4): fftw-libs-single-3.3.8-10.fc34.x86_64.rp 588 kB/s | 953 kB     00:01    
(2/4): mesa-libGL-21.1.1-1.fc34.x86_64.rpm       83 kB/s | 171 kB     00:02    
(3/4): mesa-libglapi-21.1.1-1.fc34.x86_64.rpm   112 kB/s |  55 kB     00:00    
(4/4): mesa-libOSMesa-21.1.1-1.fc34.x86_64.rpm  1.1 MB/s | 3.1 MB     00:02    
--------------------------------------------------------------------------------
Total                                           1.1 MB/s | 4.3 MB     00:03     
Running transaction check
Transaction check succeeded.
Running transaction test
The downloaded packages were saved in cache until the next successful transaction.
You can remove cached packages by executing 'dnf clean packages'.
Error: Transaction test error:
  file /usr/lib/.build-id/34/aac32bb4d3c0f44e72e57cf253a871240a1154 from install of ucsf-chimerax-1.2.5-1.el8.x86_64 conflicts with file from package rstudio-1.4.1106-1.x86_64
  file /usr/lib/.build-id/80/916a3578c4abf8d9433986b7ca87ee58797eb5 from install of ucsf-chimerax-1.2.5-1.el8.x86_64 conflicts with file from package rstudio-1.4.1106-1.x86_64
  file /usr/lib/.build-id/ea/6a2369dae8e186543b5e0fa413cb7ee7058c84 from install of ucsf-chimerax-1.2.5-1.el8.x86_64 conflicts with file from package rstudio-1.4.1106-1.x86_64

[murphy@eva02 Downloads]$ dnf clean packages
0 files removed
[murphy@eva02 Downloads]$ sudo dnf install ./ucsf-chimerax-1.2.5-1.el8.x86_64.rpm 
Last metadata expiration check: 2:30:45 ago on Mon 31 May 2021 07:01:27 PM CDT.
Dependencies resolved.
================================================================================
 Package               Arch        Version              Repository         Size
================================================================================
Installing:
 ucsf-chimerax         x86_64      1.2.5-1.el8          @commandline      307 M
Upgrading:
 mesa-libGL            x86_64      21.1.1-1.fc34        updates           171 k
 mesa-libglapi         x86_64      21.1.1-1.fc34        updates            55 k
Installing dependencies:
 fftw-libs-single      x86_64      3.3.8-10.fc34        fedora            953 k
 mesa-libOSMesa        x86_64      21.1.1-1.fc34        updates           3.1 M

Transaction Summary
================================================================================
Install  3 Packages
Upgrade  2 Packages

Total size: 311 M
Is this ok [y/N]: y
Downloading Packages:
[SKIPPED] fftw-libs-single-3.3.8-10.fc34.x86_64.rpm: Already downloaded        
[SKIPPED] mesa-libOSMesa-21.1.1-1.fc34.x86_64.rpm: Already downloaded          
[SKIPPED] mesa-libGL-21.1.1-1.fc34.x86_64.rpm: Already downloaded              
[SKIPPED] mesa-libglapi-21.1.1-1.fc34.x86_64.rpm: Already downloaded           
Running transaction check
Transaction check succeeded.
Running transaction test
The downloaded packages were saved in cache until the next successful transaction.
You can remove cached packages by executing 'dnf clean packages'.
Error: Transaction test error:
  file /usr/lib/.build-id/34/aac32bb4d3c0f44e72e57cf253a871240a1154 from install of ucsf-chimerax-1.2.5-1.el8.x86_64 conflicts with file from package rstudio-1.4.1106-1.x86_64
  file /usr/lib/.build-id/80/916a3578c4abf8d9433986b7ca87ee58797eb5 from install of ucsf-chimerax-1.2.5-1.el8.x86_64 conflicts with file from package rstudio-1.4.1106-1.x86_64
  file /usr/lib/.build-id/ea/6a2369dae8e186543b5e0fa413cb7ee7058c84 from install of ucsf-chimerax-1.2.5-1.el8.x86_64 conflicts with file from package rstudio-1.4.1106-1.x86_64
[murphy@eva02 Downloads]$ sudo dnf install ucsf-chimerax-1.2.5-1.el7.x86_64.rpm
Last metadata expiration check: 2:38:46 ago on Mon 31 May 2021 07:01:27 PM CDT.
Error: 
 Problem: conflicting requests
  - nothing provides libgfortran4 needed by ucsf-chimerax-1.2.5-1.el7.x86_64
  - nothing provides mesa-private-llvm needed by ucsf-chimerax-1.2.5-1.el7.x86_64
(try to add '--skip-broken' to skip uninstallable packages)
```

> Update: ticket is [here](https://plato.cgl.ucsf.edu/trac/ChimeraX/ticket/4709#comment:1).

> 2nd Update: I installed it. Check the previous link. Had to remove `rstudio`, install `chimerax`, and reinstall `rstudio` (but the one from the Fedora repositories).


## VMD

`vmd` is another good alternative to `pymol` and it is free. Go [here](https://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=VMD) and download it, then do:

```bash
cd ~/Downloads
tar xvzf vmd-*tar.gz 
cd vmd-VERSION/
./configure  
cd src/
sudo make install
```

Where `VERSION` is the version of  `vmd`. 
