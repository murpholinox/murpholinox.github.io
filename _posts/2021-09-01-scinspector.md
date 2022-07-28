---
layout: post
title: How to inspect sidechains one by one?
published: true
tags: x-ray crystallography
---

## Coot

Do 'Calculate' -> 'Scripting' -> 'Python' `set_reoTABTAB` and put `1` inside the parenthesis.

## PyMOL

Do 'File' -> 'Run script' and pick `sc_inspector.pml`.

Where `sc_inspector.pml` contains the following code:

```python
# Sidechain Inspector
# This code maps the zooming of residue to the F1 key
python
stored.x = 0
def zoomnext(delta=1):
    stored.x += delta
    sele = 'i. {}'.format(stored.x)
    cmd.show('sticks', sele)
    cmd.zoom(sele, animate=1.0, buffer=1.5)
def zoomprev():
    zoomnext(-1)
cmd.set_key('F1', zoomnext)
cmd.set_key('F2', zoomprev)
python end
# initial view
zoomnext()
```
