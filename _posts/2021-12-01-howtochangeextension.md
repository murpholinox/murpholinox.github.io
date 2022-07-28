---
layout: post
title: How to change file extension to lots of files?
published: true
tag: cli
---

To change the file extension to multiple files, do:

```
for f in *.txt
  do
    mv -- "$f" "${f%.txt}.md"
  done
```

> Ps... GNU/Linux does not care about file extensions anyway...