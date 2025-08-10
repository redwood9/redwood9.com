---
title: Ictcals 2009 Linux版破解过程
description: "研究对ictcals 2009 LINUX版进行二进制破解"
date: 2010-04-03
taxonomies:
  tags: [Code]
---

中科院分词Linux版破解过程
1，ar -x libICTCLAS30.a 拆分成对象文件

2，将生成的ICTCLAS30.o用IDA打开
<a href="/assets/0.png"><img class="alignnone size-full wp-image-10" title="ictclas-2009-ida" src="/assets/0.png" alt="ictclas 2009 IDA 破解" width="435" height="30" /></a>

3，上面的地方是关键
69B处的机器码是7665，不高于跳转；改成71 ，不溢出跳转

4，ar -r  libICTCLAS30.a  ICTCLAS30.o
将生成的ICTCLAS30.o替换进静态库

重新编译程序，时间调整到2010年，运行成功！