---
layout: post
title: How to set root's password in Fedora?
published: true
tag: fedora
---

A few Fedora versions ago, and if you install the 'Fedora Workstation' version, root password is never set. 

> Warning: This is not the case when installing Fedora Everything. 

You get a user with `sudo` privileges. To set up `root` password you have to do the following:

```bash
[murphy@eva02 ~]$ sudo -i
[sudo] password for murphy: 
[root@eva02 ~]# passwd
Changing password for user root.
New password: 
Retype new password: 
passwd: all authentication tokens updated successfully.
[root@eva02 ~]# 
logout
[murphy@eva02 ~]$ su -c 'echo lolo' # Checking with my password
Password: 
su: Authentication failure
[murphy@eva02 ~]$ su -c 'echo lolo' # Checking with root's password
Password: 
lolo
```

This how-to was taken from this nice [video](https://www.youtube.com/watch?v=PO0aQL3Jhnw).
