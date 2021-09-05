---
layout: post
title: How to install R without all the Tex Live dependencies?
published: true
tag: R
---



If you try to install `R` in Fedora, `dnf` will try to download and install 534 packages.

```bash
Transaction Summary
================================================================================
Install  534 Packages

Total download size: 309 M
Installed size: 731 M
Is this ok [y/N]: N
```

Lots of those packages are Tex Live dependencies that I don't need.

> I don't need them because I always install the latest version of Tex Live. [Here]({% post_url 2021-04-01-installTexLive %}) is how to do that.


 To fix this we are gonna lie to `dnf` (hehehe)


 1. So we go to [ctan](https://www.ctan.org/) and search for 'dummy'. Then we click on number five on the list (`texlive-dummy-enterprise-linux-8`) and proceed to download the zip file.

    ![Dummy]({{ site.url }}/assets/images/dummy.png)

 2. The zip file will be in the 'Downloads' folder so we just do

 ```bash
 cd ~/Downloads
 unzip Enter*
 cd EnterpriseLinux-8/
 sudo dnf -y install texlive-dummy-2020-4.el8.noarch.rpm
 ```

After that the next `sudo dnf install R` will download and install  only 79 packages.

```bash

Transaction Summary
================================================================================
Install  79 Packages

Total download size: 107 M
Installed size: 267 M
Is this ok [y/N]: N
```

So... that's a lot of bandwidth saved, you are welcome.
