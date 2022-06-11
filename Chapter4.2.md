---
title: 'ggplot 绘图'
disqus: hackmd
---

ggplot 绘图


[TOC]



柱状图
---

```rust=

library(tidyverse)
# Data 
set.seed(1)
age <- factor(sample(c("Child", "Adult", "Retired"),
              size = 50, replace = TRUE),
              levels = c("Child", "Adult", "Retired"))
hours <- sample(1:4, size = 50, replace = TRUE)
city <- sample(c("A", "B", "C"),
               size = 50, replace = TRUE)

df <- data.frame(x = age, y = hours, group = city)
head(df)
```
> I choose a lazy person to do a hard job. Because a lazy person will find an easy way to do it. [name=Bill Gates]


```ruby=
# install.packages("ggplot2")
library(ggplot2)

ggplot(df, aes(x = x, fill = group)) + 
  geom_bar() 

```

> Read more about ggolot2 here: https://r-charts.com/part-whole/stacked-bar-chart-ggplot2/

![](https://i.imgur.com/kK8ceo8.png)


更改柱状图填充颜色
---

使用  `scale_fill_brewer() `自带的连续变色
```rust=

ggplot(df, aes(x = x, y = y, fill = group)) + 
  geom_bar(stat = "identity") +
  scale_fill_brewer() 

```
![](https://i.imgur.com/mP9VEFz.png)


使用`scale_fill_manual`设置自定义颜色

```rust=

ggplot(df, aes(x = x, y = y, fill = group)) + 
  geom_bar(stat = "identity") +
  scale_fill_manual(values = c("#DADAEB", "#9E9AC8", "#6A51A3")) 

```

![](https://i.imgur.com/eafqVpw.png)


## 更改边缘颜色

这里设置边缘颜色为黑色，你可以试试红色`red`
```rust=
ggplot(df, aes(x = x, fill = group)) + 
  geom_bar(color = "black") +
  scale_fill_manual(values = c("#DADAEB", "#9E9AC8", "#6A51A3")) 
```

![](https://i.imgur.com/C1FYtf2.png)


更改图例名称
---
原来的`Group`更改为`Title`

```rust=

ggplot(df, aes(x = x, y = y, fill = group)) + 
  geom_bar(stat = "identity") +
  guides(fill = guide_legend(title = "Title"))

```
![](https://i.imgur.com/GpJSAX2.png)


原来的图例各组名字`labels`更改为`"G1", "G2", "G3"`

```rust=

ggplot(df, aes(x = x, y = y, fill = group)) + 
  geom_bar(stat = "identity") +
  scale_fill_discrete(labels = c("G1", "G2", "G3")) 

```

![](https://i.imgur.com/8IBYMFz.png)


也可以消除图例。

```rust=

ggplot(df, aes(x = x, y = y, fill = group)) + 
  geom_bar(stat = "identity") +
  theme(legend.position = "none")

```

![](https://i.imgur.com/ujR84Hp.png)

