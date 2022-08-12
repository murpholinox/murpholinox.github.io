---
layout: post
title: How to read/write data to your HD?
published: true
tag: molecular biology
---

It's super easy. Just do 

```bash
cd /go/to/your/hd
sudo chown -R -v murphy:murphy *
find . \( -type d -exec chmod 0755 -- {} + \) -o \( -type f -exec chmod 0644 -- {} + \)
```

