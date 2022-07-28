---
layout: post
title: Permissions on Linux
published: true
tag: command line
---

Here is a guide to file permissions on Linux. Enjoy!

## Some background
We can read, write and execute a file. The clever way to abbreviate this is with three characters: `rwx`. To remove a particular permission we use a dash, so `r-x` means we can read and execute the file but not write to it. 

## Problem
In the Linux world, you might be sharing the computer you are using. So we have three sets of permissions `rwxrwxrwx`. The acronym UGO will help you remember that... the first set of permissions is for the 'User' (meaning the owner of the file); the next three for the 'Group' (meaning the users in the group of the owner); and the last three for 'Others' (meaning everybody else). So a Linux file with `rw-r-----` permissions means that the owner of the file can read and write to it, but not execute it... users on your group can read the file and all others can do nothing with it. 

## How to change permissions
With `chmod` we can change the permissions given to a file. The change is absolute. To change permissions, all we need to know is how to count in binary from 0 to 7. 


 Binary | Decimal
--------|--------
 000    |   0
 001    |   1
 010    |   2
 011    |   3
 100    |   4
 101    |   5
 110    |   6
 111    |   7

and we also need a bit of logic ...


## The bit of logic

1. Think about the permissions the file should have (let's say we want `rwxrw-r-x`, this will be your 'string').
2. Convert to binary your 'string'.
   - For every character in our 'string', put a 1 instead of a letter and a 0 instead of a dash (so `rwxrw-r-x` translates to `111110101`)
3. Convert your binary 'string' to decimal.
   - Cut your string into 3 sets and convert: the table above shows that `111`, `110` and `101` are 7, 6 and 5, respectively.
4. Change permissions to file with `chmod 765 file`.

## Example
```bash
[murphy@eva02]$ ls -lrt file
-rw-rw-r--. 1 murphy murphy 0 Mar 01 21:26 file
[murphy@eva02]$ chmod 765 file
[murphy@eva02]$ ls -lrt file
-rwxrw-r-x. 1 murphy murphy 0 Mar 01 21:26 file
```

  





