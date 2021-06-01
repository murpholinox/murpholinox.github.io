---
layout: post
title: How to install Oracle Java in Fedora?
published: true
tag: Java
---



Here is how to install `java` from Oracle on Fedora. We normally do not want this, unless we need to run a `java` program. 




1. Go [here](https://www.java.com/en/download/linux_manual.jsp) and download the Linux x64 `rpm` version.

2. Then install with
```bash
cd Downloads/
# do not install with dnf but with rpm
sudo rpm -ihvh ./jre*linux-x64.rpm 
```
3. Tell your system which `java` you are going to use with `sudo  /usr/sbin/alternatives --config java` and choose number 2 (number 1 should be the open java version...)


Be happy!

