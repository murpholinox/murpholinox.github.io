---
layout: post
title: geom_histogram(binwidth=1) vs. geom_bar()
published: true
tag: Ggplot2
---

For a plot of factors vs frequency it is the same to do.

```
ggplot(data=datos, aes(x=var)) + labs(x="Number of things", y="Frequency") + geom_histogram(binwidth = 1)
# Same as... 
ggplot(data=datos, aes(x=var)) + labs(x="Number of things", y="Frequency") + geom_bar()
```

The only difference is that the bars in the barplot will be slightly separated. This is valid because `x` is a factor and I am using `binwidth=1`.


