---
layout: post
title: How to remove a soft link to a directory?
published: true
tag: Linux 
---



Just as the title says! Check the comments!



```bash
# Create a soft link
ln -s dir1 dir1-sym2
# Show what we have
ls -li
total 8
36049241 drwxrwxr-x. 2 murphy murphy 4096 Feb  1 11:33 dir1
36049251 lrwxrwxrwx. 1 murphy murphy    4 Feb  1 11:34 dir1-sym2 -> dir1
36177087 drwxrwxr-x. 2 murphy murphy 4096 Feb  1 11:18 dir2
# Try to remove the link
rm dir1-sym2/
rm: cannot remove 'dir1-sym2/': Is a directory
# Force of habit kicks in
rm -r dir1-sym2/
rm: cannot remove 'dir1-sym2/': Not a directory
# Wait!.. what!? Force of habit again kicks in
rm -rf dir1-sym2/
# Not a single error message, hehehe we won! let's check
ls -li
total 8
36049241 drwxrwxr-x. 2 murphy murphy 4096 Feb  1 11:33 dir1
36049251 lrwxrwxrwx. 1 murphy murphy    4 Feb  1 11:34 dir1-sym2 -> dir1
36177087 drwxrwxr-x. 2 murphy murphy 4096 Feb  1 11:18 dir2
# Whaaaaat?! It's still there!
# So... before breaking your computer you have to remember that
# the link is a file pointing to a directory. The proper way to remove it is
# by not including the final slash (so tabtab was our enemy) 
rm dir1-sym2
# Confirm
ls -li
total 8
36049241 drwxrwxr-x. 2 murphy murphy 4096 Feb  1 11:33 dir1
36177087 drwxrwxr-x. 2 murphy murphy 4096 Feb  1 11:18 dir2
```

