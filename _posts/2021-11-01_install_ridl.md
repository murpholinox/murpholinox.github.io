---
layout: post
title: Installing RIDL 
published: true
tag: XRC 
---

To install [ridl](https://github.com/charliebury/RIDL), we need to do...

```
conda create -n ridl python=2.7 
conda activate ridl
pip install future==0.16.0
pip install seaborn==0.9.0
pip install scikit-learn==0.19.2
```

Then, `python $REPOS/RIDL/runRIDL.py --dependencies` should say evrything is up and running (or something like that...)

:)

> Ps... Python 2.7 and 3.6 are already [dead](https://endoflife.date/python).
