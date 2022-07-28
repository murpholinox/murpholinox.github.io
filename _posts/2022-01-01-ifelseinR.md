---
layout: post
title: If/Else construct in R
published: true
tag: R
---

So, I have been learning R, mostly through [datacamp](https://learn.datacamp.com/) as there was an offer: all courses free for one week. That was nice ...

```
number <- 2500
if (number < 11) {
  if (number < 6) {
    result <- "extra small"
  } else {
    result <- "small"
  }
} else if (number < 100) {
  result <- "medium"
} else {
  result <- "large"
}
print(result)
```