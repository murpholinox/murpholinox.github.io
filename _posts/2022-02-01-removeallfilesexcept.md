---
layout: post
title: How to remove all files in a folder except for...
published: true
tag: Linux
---


```
# Remove everything except `*.txt` files
rm !(*.txt)
```

```
# Remove everything except file "file"
rm !("file")
```

> Warning: Be sure to try it first with `ls`.
