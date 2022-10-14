---
title: ggplot画柱状图
author: chenxinhua
date: '2022-10-13'
slug: ggplot
categories:
  - R
tags:
  - plot
---
直接上代码

```r
library(ggplot2)
```

```
## Registered S3 methods overwritten by 'tibble':
##   method     from  
##   format.tbl pillar
##   print.tbl  pillar
```

```r
filePath <- 'E:/Pythonfiles/miRNA文章作图/20221013miR家族成员/knownMirFamilyStat.csv'
df <- read.csv(filePath,header = T, stringsAsFactors = T)


df
```

```
##    geneName size
## 1    miR951    1
## 2   miR6171    1
## 3   miR3704    1
## 4  miR11482    1
## 5    miR319    1
## 6   miR2950    1
## 7    miR168    1
## 8    miR162    1
## 9  miR11551    1
## 10 miR11571    1
## 11   miR829    1
## 12   miR397    2
## 13  miR8175    2
## 14   miR160    2
## 15   miR159    2
## 16   miR156    2
## 17 miR11524    2
## 18 miR11512    2
## 19   miR535    3
## 20   miR398    3
## 21 miR11438    3
## 22 miR11476    3
## 23  miR3701    3
## 24  miR1316    3
## 25   miR529    3
## 26 miR11544    3
## 27  miR1312    3
## 28 miR11532    4
## 29  miR1314    4
## 30   miR947    5
## 31  miR3693    6
## 32   miR396    6
## 33   miR169    6
## 34 miR11487    8
## 35 miR11425    9
## 36  miR3710    9
## 37  miR1313   10
## 38 miR11466   10
## 39   miR166   12
## 40   miR946   18
## 41   miR482   19
## 42   miR950   24
```


```r
plot_0 <- ggplot(df, aes(x=reorder(geneName,-size),y=size)) + 
  geom_bar(stat = 'identity',fill = 'deepskyblue4',) +
  geom_text(aes(label = size), vjust = 0.5,hjust = -0.5,size = 5.5) +
  ylab("Number of known miRNA members per family") +
  xlab("miRNA family") +
  labs(fill=NULL) +
  theme_classic() +
  # scale_y_continuous(expand = c(0, 0),limits = c(0, 30)) + #设置Y轴截距
  #scale_fill_manual(values = c("deepskyblue4")) +
  theme(axis.text.x = element_text(size = 15, color = "black")) +  #设置字体颜色，字号
  theme(axis.text.y = element_text(size = 15, color = "black"),axis.title.y=element_text(colour="black",size = 15)) +
  # theme(panel.background = element_rect(colour = "black")) +
  theme(legend.key.size = unit(.3,"inches"),legend.text=element_text(colour="black",size=15)) +
  theme(legend.position = c(0.8,0.8)) +
  expand_limits(x=c(1,0)) +#设置x轴截距
  scale_y_continuous(expand = c(0, 0)) + #设置Y轴截距
  coord_flip() 


plot_0
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />




