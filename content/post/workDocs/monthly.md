---
title: "Monthly"
date: 2020-07-03T22:34:55+08:00
lastmod: 2020-07-03T22:34:55+08:00
draft: false
keywords: ["TSTP", "纯度"]
description: "工作文档-月度总结"
tags: ["Work Docs", "TSTP", "纯度"]
categories: ["Work Docs"]
author: "zhangyunlong"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
postMetaInFooter: false
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---

# Summary

> 2020年工作文档月报。

<!--more-->

## 20207月6日

---

## 2020年6月6日

### 近期主要工作情况

1. **调整TSTP系统相关细节问题**：
   - 添加计数坐标轴，便于计数
   - 调整碱基背景颜色透明度，将与参考序列相同的碱基背景色变淡，这样更能凸显差异
   - 国际化问题，完善部分页面英文显示，将默认语言修改成英文



这里以一个序列文件SSR9.fas展示该对齐功能，该功能根据指定的Motif（ATG）和Motif区重复长度（9）自动找出每条序列的重复区（以黄色标记），同时将所有序列按照重复区左右对齐，由此可以清晰的看出每条序列的变化情况（图中的第一条序列为参考序列）。
![alignment.gif](https://cdn.nlark.com/yuque/0/2020/gif/222486/1591356868414-1f0624bf-6ea6-4635-82e3-9a2a85fe442c.gif#align=left&display=inline&height=894&margin=%5Bobject%20Object%5D&name=alignment.gif&originHeight=894&originWidth=1665&size=7199772&status=done&style=none&width=1665)

2. **计算基因频率相关工作：**

该部分工作主要计算了审定库自交系和杂交种样品的基因频率和相关绘图，供论文写作小组使用。这里对该部分工作进行简要概述，详细内容[在这里记录](https://www.yuque.com/docs/share/835643d6-6df1-4429-9cf2-540abe64fbed)


   - 自交系和杂交种等位基因频率表

![P04.png](https://cdn.nlark.com/yuque/0/2020/png/222486/1591357725265-73ba351c-08de-4aec-9ecc-eac95d6e3b7c.png?x-oss-process=image%2Fresize%2Cw_1492)

   - 自交系和杂交种基因型频率表（两种方式计算，思考：这两种方法的差异与含义！）
      - 方式一：根据真实数据统计
      - 方式二：根据等位基因表将每个位点上的等位基因两两组合成基因型（频率相乘）



   - 合并等位基因

如图所示我们将高峰348，左右各1bp的等位基因进行了合并（思考：为什么这样做？）
![P04.png](https://cdn.nlark.com/yuque/0/2020/png/222486/1591357900395-85de0e8a-02b5-41e8-9a70-88e2e7fc654a.png#align=left&display=inline&height=2500&margin=%5Bobject%20Object%5D&name=P04.png&originHeight=2500&originWidth=7500&size=468083&status=done&style=none&width=7500)

   - 制作自交系和杂交种每个基因型的字典表

这里使用部分数据描述一下该字典表的内容

| 样品条码号 | P01 | P01的实际基因型频率 | P01的理论基因型频率 | P01合并等位基因后的基因型频率 | ··· | P40 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| BGG1 | 241/241 | 0.431864016 | 0.263354369 | 0.365779276 | ··· | ··· |


_**对于纯度检定来说我们希望能以现有数据为基础总结规律，以使用相对较少的位点即可检定样品纯度，这是个值得思考的问题。**_


3. **协助处理论文进度展示系统相关技术：**
   - webpack打包静态文件，配置env环境变量
   - graphql查询；更新操作语句
   - token认证相关问题




4. **模拟制作测序序列数据：**
   - 按照指定规则制造fa序列文件。
   - 制作fastq文件并统计序列中随机碱基与固定碱基占比，平均序列长度；GC占比等。

根据规则制作了1万；10万；100万；三种级别的fastq文件,使用已知结果的数据验证SSR-pipeliner测序分析工具的准确性
```
平均reads长度: 199.7218
随机碱基数量: 875936
随机碱基占比: 0.5481671356049304
确定碱基数量: 722000
确定碱基占比: 0.45183286439506964
GC-ratio 0.48971569453109276
```

### 思考总结

1. 在制作位点对齐图时其实存在一个性能问题，即当上传的序列文件比较大时（如有上万条序列）页面渲染将会消耗大量浏览器资源，致使卡顿甚至是浏览器崩溃，这里采用懒加载的方式对序列进行选择性渲染，即只渲染当前屏幕可见的序列，大大减轻浏览器压力。

2. 当使用一些分析工具时，可使用模拟数据验证功能的可靠性，而不是直接使用真实的实验数据。

3. 两种基因型频率的区别：

使用方法二计算得出的基因型频率，存在实际样品数据中没有的基因型，这对于一个全新的样品来说是有利地。也可理解为通过该方法计算的基因型频率具有更好的通用型。

4. 为什么要合并高峰左右1bp的等位基因频率

对于高峰348来说，等位基因频率较高，并不具有明显的位点区分能力，而他左右1bp的347；349又是较小的频率，为了避免误差所以将这三个位点视为一个。
