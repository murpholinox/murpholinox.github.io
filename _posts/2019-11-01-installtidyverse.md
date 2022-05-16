---
layout: post
title: How to install the tidyverse?
published: true
tag: R
---



Installing the [tidyverse](https://www.tidyverse.org/) in `rstudio` fails miserably. Here is how to install the whole `tidyverse` without problems. 

Do in your terminal `sudo dnf -y install openssl-devel libcurl-devel`, then in `R` you can do `install.packages("tidyverse")` and this time it will succeed.



>  Warning: you probably do not need the whole `tidyverse`, the most useful packages are: `ggplot2` for nice plots and `dplyr` to manipulate your data.

> Update: In Fedora 36, openssl conflicts with a similar package

```bash
[murphy@eva03 install-tl-20220504]$ sudo dnf -y install openssl-devel libcurl-devel
[sudo] password for murphy: 
Last metadata expiration check: 1:38:38 ago on Thu 05 May 2022 07:56:50 PM CDT.
Error: 
 Problem: problem with installed package openssl1.1-devel-1:1.1.1n-1.fc36.x86_64
  - package openssl1.1-devel-1:1.1.1n-1.fc36.x86_64 conflicts with openssl-devel provided by openssl-devel-1:3.0.2-4.fc36.i686
  - conflicting requests
  - package openssl1.1-devel-1:1.1.1n-1.fc36.x86_64 conflicts with openssl-devel provided by openssl-devel-1:3.0.2-4.fc36.x86_64
(try to add '--allowerasing' to command line to replace conflicting packages or '--skip-broken' to skip uninstallable packages)
```
