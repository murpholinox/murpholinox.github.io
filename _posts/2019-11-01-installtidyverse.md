---
layout: post
title: How to install the tidyverse?
published: true
tag: R
---



Installing the [tidyverse](https://www.tidyverse.org/) in `rstudio` fails miserably. Here is how to install the whole `tidyverse` without problems. 

Do in your terminal `sudo dnf -y install openssl-devel libcurl-devel`, then in `R` you can do `install.packages("tidyverse")` and this time it will succeed.



>  Warning: you probably do not need the whole `tidyverse`, the most useful packages are: `ggplot2` for nice plots and `dplyr` to manipulate your data.

