---
title: shell批量处理文件
author: chenxinhua
date: '2022-10-14'
slug: shell
categories:
  - shell
tags:
  - shell script
---

思路：for循环把命令写入一个.sh脚本，然后执行这个脚本。

第一，for循环写出处理不同文件的命令。

```{bash}
for i in *.fastq
do 
echo "bowtie -p 5 -v 1 -q $i -x ~/Database/Rfam/rfamIndx -S ~/microRNA/fq_filtered18_30_microRNA/mapped2rfam/$(basename $i .fastq).sam" >> deal.sh
done
```
得到如下文件


