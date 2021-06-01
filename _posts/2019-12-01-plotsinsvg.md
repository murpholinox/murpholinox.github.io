---
layout: post
title: How to save ggplots in svg format?
published: true
tag: R
---



To save plots in `svg` format do:



1- `install.packages("svglite")`.

2-  Load the package with `library(svglite)`.

3- Now you can save plots in `svg` format with `ggsave("/file.svg", width = 20, units = "cm")`.

More information on how to use `ggsave` is [here](https://ggplot2.tidyverse.org/reference/ggsave.html). 

