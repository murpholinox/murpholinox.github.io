---
layout: post
title: How to install RIDL?
published: true
tag: x-ray crystallography
---

To install [ridl](https://github.com/charliebury/RIDL), we need to do...

```bash
conda create -n ridl python=2.7 
conda activate ridl
```
Then, inside the `ridl` environment...

```python
pip install future==0.16.0
pip install seaborn==0.9.0
pip install scikit-learn==0.19.2
```

Finally `python $REPOS/RIDL/runRIDL.py --dependencies` should say everything is ok...

:)

> Warning: python 2.7 and 3.6 are already [dead](https://endoflife.date/python).
