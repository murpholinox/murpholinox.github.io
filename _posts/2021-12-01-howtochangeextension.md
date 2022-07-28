---
layout: post
title: How to change the file extension to lots of files?
published: true
tag: command line
---

To change the file extension to multiple files, do:

```bash
for f in *.txt
  do
    mv -- "$f" "${f%.txt}.md"
  done
```

> Remember: GNU/Linux does not care about file extensions anyway...
