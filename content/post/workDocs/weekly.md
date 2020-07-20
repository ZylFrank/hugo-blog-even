---
title: "Weekly"
date: 2020-07-03T22:46:27+08:00
lastmod: 2020-07-03T22:46:27+08:00
draft: false
keywords: ["Weekly"]
description: "工作周报"
tags: ["Work Docs", "Weekly"]
categories: ["Work Docs"]
author: "zhangyunlong"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
postMetaInFooter: false
hiddenFromHomePage: true
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

> 2020年工作文档周报。

<!--more-->
## **七月**

### 7月13日至7月17日

1. 部署(域名)AMGT-TS系统，并解决部署过程中的一些问题
2. 使用Hugo部署AMGT-TS系统使用文档(双语)
3. 修改AMGT-TS系统的默认语言为英文
4. 制作模拟数据用于测试AMGT-TS系统的分析功能
5. 解决域名部署时的websocket报错问题
6. 修改项目使其支持多目录分析

### 7月6日至7月10日

1. 格式化种质库管理系统的样品数据，条码号全部改成大写，补全样品信息
2. 添加数据库备份脚本
3. TSTP系统添加修改项目相关路径的功能，并进行校验
4. 种质库管理系统样品入库是添加进度条
5. TSTP系统集成对05目录的finder功能

### 6月28日至7月3日

1. 准备SWMS系统汇报PPT
2. 229服务器部署SWMS系统
3. 录入1号库2号库样品数据
4. 解决SWMS系统parse域名访问问题
5. 修改TSTP系统，允许其创建不用在线运行的项目
6. 制作模拟序列

## **六月**

### 6月6日至6月28日

1. 根据讨论研究杂交种纯度检定时的引物选择问题的内容，总结引物选择的方法，编写文档和代码
2. 总结自交系纯度鉴定时的引物选择问题，编写代码和文档
3. 学习使用prisma，nexus结合graphql搭建graphql服务端项目。并实现基本的CRUD操作和分页查询等功能
4. 处理种质资源库系统的部署，修改一些bug
5. 制作TSTP项目的详细设计说明书，以便著作权的申请
6. TSTP项目添加Muscle对齐功能

### 6月1日至6月5日

1. 调整TSTP系统相关细节问题：
   1. 添加计数坐标轴，便于计数
   1. 调整碱基背景颜色透明度，将与参考序列相同的碱基背景色变淡，这样更能凸显差异
   1. 国际化问题，完善部分页面英文显示，将默认语言修改成英文
2. 计算基因频率相关工作：
   1. 合并自交系；杂交种基因频率图
   1. 合并等位基因：将峰值左右1bp的等位基因频率合并
   1. 使用等位基因频率计算基因型频率
3. 协助处理论文进度展示系统相关技术难点：
   1. webpack打包问题
   1. graphql查询；更新操作
   1. token认证相关问题
4. 模拟制作测序序列数据：
   1. 按照指定规则制造fa序列文件
   1. 制作fastq文件并统计序列中随机碱基与固定碱基占比，平均序列长度；GC占比等；供霍主任验证序列分析工具

## **五月**

### Plink

> 使用Plink软件辅助许博士进行数据处理，[https://www.yuque.com/docs/share/7181f82d-d34e-4fa5-9d74-2f973ae47c4e?#](https://www.yuque.com/docs/share/7181f82d-d34e-4fa5-9d74-2f973ae47c4e?#)

### 基因频率计算

> 计算自交系与杂交种的基因频率并统计绘图 [https://www.yuque.com/docs/share/835643d6-6df1-4429-9cf2-540abe64fbed#wl61J](https://www.yuque.com/docs/share/835643d6-6df1-4429-9cf2-540abe64fbed#wl61J)

### 5月9日

1. 解决cloudlims系统移动端滚动列表的bug，DatePicker组件中文显示的问题，自定义MultiSelectMenu组件，添加记录表单时提供“使用上次记录填充表单”功能
1. 解决TSTP系统位点对齐图在少量数据时不能横向滚动的bug
1. 制作cloudlims更新描述文档

### 5月8日

1. 添加维护记录；检定记录；维修申请；运行检查记录；降级/报废申请的表单页面并集成
1. 准备安全登录系统著作权相关资料
1. 更新发布cloudlims

### 5月7日

1. 移动端添加创建使用记录页面
2. 在仪器详情页关联使用记录
3. 将仪器使用记录导出成word文档
4. 服务端添加使用记录接口并集成

### 5月6日

1. 使用apidoc生成接口文档
2. 参加周例会
3. 制作模版文件批量导出运行检查记录；降级/报废记录；导出主要仪器设备一览表

## **四月**

### 4月28日

1. 按仪器类型导出维护记录zip包；导出检定周期表
2. 调整位点对齐图
3. CloudLims添加Dashboard展示近期需要检定、维护、运行检查的仪器列表

### 4月27日

1. 按照仪器类型批量导出检定信息zip包
2. 制作购置计划、维护保养、验收调试、维修申请、降级/报废 记录的word模版，并导出历年记录。
3. 调整位点对齐图

### 4月26日

1. 添加仪器类型字典
1. 聚合查询检定记录表
1. 参加周例会
1. 导出检定信息word文档

### 4月22日

1. Cloudlims系统所有列表页添加日期查询功能，调整角色权限，优化移动端列表查询功能。
1. 制作新的位点对齐程序，对序列分阶段着色。

### 4月21日

1. 封装移动端记录Card
1. 使用折叠面板的方式展示移动端仪器详情页面相关记录
1. 为6中记录添加滚动列表，实现在移动端查看仪器的全部相关记录
1. 存储仪器档案版本记录，实现查询仪器历年的档案信息等查询方式

### 4月20日

1. 批量录入购置计划表，添加列表与详情页面
1. 参加周例会
1. 优化移动端列表查询条件的使用方式与查询逻辑

### 4月17日

1. CloudLims添加6种记录的详情页面
1. 每种记录列表添加删除功能
1. 完善公众号的一些细节问题

### 4月16日

1. 录入系统调试记录；降级报废记录
1. 集成相关列表
1. PC端与移动端的信息关联查询

### 4月15日

1. CloudLims批量录入维修记录；运行检查记录并实现相关列表与关联查询
1. 移动端添加仪器列表
1. 移动端仪器详情页关联四种记录

### 4月14日

1. CloudLims批量录入维护保养记录，检定记录
1. 关联查询维护保养记录
1. 修正分页问题

### 4月13日

1. 制作完成TSTP项目著作权相关文档
1. 制作完成TSTP项目总结文档
1. 参加周例会
1. CloudLims系统新增导出Excel功能，用于标签打印
1. 使用python-docx解析word文档，已批量录入仪器档案信息

### 4月10日

1. CloudLims系统新增导出仪器档案Word文档功能
1. 更改TSTP项目的主题色，修改了一些页面细节问题
1. 整理TSTP项目著作权资料，形成初稿

### 4月8日

1. CloudLims系统添加生成仪器标签图片功能
1. 更新部署CloudLims系统

### 4月7日

1. CloudLims系统添加移动端仪器信息详情页面
1. 参加周例会
1. CloudLims系统添加仪器信息卡组件

### 4月2日

1. 小程序列表集成分页功能（下拉刷新；加载更多）；调整页面样式
1. CloudLims系统添加仪器信息的查询功能；添加更新braft-editor功能；修改删除功能与创建表单的bug；

### 4月1日

1. 青云服务器部署CloudLims系统
1. 安全登录系统集成系统管理列表
1. 调整小程序页面样式，封装request组件，本地联调服务器接口
1. CloudLims系统新增解析word文档，填充表单数据功能

## **三月**

### 3月31日

1. 创建CloudLims小程序，集成仪器列表；详情页面
1. 修改安全登录系统更新端口的接口

### 3月25日

1. TSTP系统获取并存储部分脚本运行日志
1. 提供下载服务器日志文件功能
1. 初始化CloudLims系统系统

### 3月24日

1. 分析addAmpliconLen.pl脚本流程，查找缺少5end数据的原因（推测为引物序列导致）
1. 调整TSTP页面部分翻译内容
1. TSTP添加任务状态标识
1. 绘图工具支持解析excel数据

### 3月23日

1. 参加周例会
1. 调整入口数据结构再使用AmpSeq-SSR分析
1. 调试bath.pl查找样品数据格式name_xnumber中number表示的意思

### 3月18日

1. TSTP系统使用js封装对齐fas文件的脚本，通过脚本生成可供页面加载的数据文件
1. 生成AMPL1563868 SSR16_16.fas的序列对齐页面
1. 给所有显示序列的页面添加等宽字体
1. 使用react-router配置匹配layout

### 3月17日

1. 调试addAmpliconLen.pl脚本，找出sample1.stat.addLen.xls 没有数据的原因（https://gitlab.com/acdna/maize/-/issues/7762）
1. 比对SSR-Pipeliner的两次分析结果（https://gitlab.com/acdna/maize/-/issues/7759）
1. 扩展安全登录系统的接口功能（https://gitlab.com/acdna/maize/-/issues/7763）
1. 梳理AmpSeq-SSR项目步骤（https://gitlab.com/acdna/maize/-/issues/7764）

### 3月16日

1. 分析AmpSeq项目process.pl；alleleProfile.pl；addAmpliconLen.pl脚本，查找sample1.stat.addLen.xls文件没有数据的原因
2. 查找koa项目启动时的warring的原因，并消除
3. 查找mongodb createIndexes 警告原因，并消除

### 3月11日

1. 分析AmpSeq项目extract4SSR.pl代码；制作分析文档
2. 更新部署TSTP系统和安全登录系统

### 3月10日

1. 分析AmpSeq项目extract4SSR.pl代码；制作分析文档。(分析文档至代码的276行)
2. 安全登录系统添加日志模块

### 3月9日

1. 分析AmpSeq项目extract4SSR.pl代码；制作分析文档。
2. TSTP项目添加xterm用于显示服务器运行脚本的日志。
3. 总结Perl基础语法，制作PPT。
4. 参加周例会

### 3月4日

1. 分析AmpSeq项目extract4SSR.pl代码；查找分析数据报错原因。
2. 调整TSTP项目webpack配置，提高项目构建速度。
3. 增加安全登录系统jwt过期提示，调整程序入口页面样式

### 3月3日

1. 分析AmpSeq代码；查找分析数据报错原因。
2. 格式化SNP序列信息

### 3月2日

1. 参加周例会
2. 安全登录系统实现给用户分配系统的功能；修改获取端口方式。
3. 解决sample1提取序列失败的Bug
4. 分析AmpSeq代码

## **二月**

### 2月28日

1. 办公系统安全登录系统完成服务端随机生成端口号
2. 发送邮箱验证码，设置验证码过期时间
3. 完成验证登录功能
4. 添加修改系统端口的接口

### 2月27日

1. 完成办公系统安全登录系统用户管理页的全部功能，包括用户信息的CURD；前端界面和后端接口

### 2月26日

1. 完善TSTP系统的国际化功能（参考序列模块;样品比对模块）
2. 完成办公系统安全登录系统前后端服务搭建，完成前端界面开发；集成两个后端接口

### 2月25日

1. 查找AmpSeq分析IonXpress_015_rawlib样品的失败原因。(https://gitlab.com/acdna/maize/issues/7653)
2. TSTP系统添加通过分析脚本日志来判断脚本运行情况的功能。
3. TSTP系统在执行分析脚本时，将日志信息通过前端展示。
4. TSTP系统发布V1.0.5.20200225版本。
5. 解决日期选择器组件的国际化问题
6. 青云服务器安装AmpSeq-SSR运行环境，并测试运行sample1.fa

### 2月24日

1. 使用SNPhylo分析maize310数据，查找运行报错原因
2. 参加周例会
3. 整理TSTP系统设计文档
4. 将fq文件格式化为fa格式，使用AmpSeq分析IonXpress_015_rawlib样品
5. TSTP使用SSR分型进行样品比对

### 2月19日

1. 创建任务时添加选择参考序列功能
2. 执行分析脚本时根据参考序列信息传入对应的参数
3. 调整展示分析结果时获取参考序列的方式，同时给SSR分型添加链接
4. 将02_read/sample/site/SSR24.fas 数据进行SSR区对齐，展示在前端页面中

### 2月18日

1. TSTP添加版本记录列表（https://gitlab.com/acdna/maize/issues/7612）
2. TSTP添加自定义路径上传文件至脚本运行环境功能（https://gitlab.com/acdna/maize/issues/7610）
3. 整理TSTP环境变量配置（https://gitlab.com/acdna/maize/issues/7609）
4. 上传并解析参考序列文件（https://gitlab.com/acdna/maize/issues/7611）
5. 集成参考序列详情列表

### 2月17日

1. 使用cypress测试框架，创建First Test
2. TSTP提供参数设置界面，及英文对照（https://gitlab.com/acdna/maize/issues/7504#note_5589425ec3660be6db44365830cc9d0a6af85789）
3. TSTP添加参考文件列表及参考文件上传前的校验功能
4. 参加周例会

### 2月14日

1. 任务创建前添加任务名校验功能，避免服务器覆盖已存在的文件
2. 调整汇总分析结果脚本，使其输出格式相同的json文件
3. 调整分许结果和样品之间的存储结构，改为json格式存入数据库。
4. 完善页面国际化
5. 解决分析脚本运行多次的问题
6. 更新青云服务器TSTP系统V1.0.3.20200214

### 2月13日

1. 展示两个结果序列的SSR区对齐结构(AMPL1563876 SSR36.fas; AMPL1563890_SSR33.fas)
2. TSTP系统修改任务删除功能，同时删除该任务下所有样品及其分析结果
3. TSTP系统上传分析结果到数据库之前检查样品的分析结果是否已存在
4. 优化TSTP系统任务执行过程。
5. 更新青云服务器TSTP系统

### 2月12日

1. 新增导出样品名称，进行样品列表间的两两比对功能
2. 添加展示比对结果页，提供导出比对结果功能。
3. 调试运行AmpSeq-SSR项目，生成分析结果
4. 学习疫情防控知识

### 2月11日

1. 调试办公室网络，添加[自动重连VPN定时任务](https://www.pocketables.com/2018/06/how-to-automatically-reconnect-windows-10-vpn.html)。
2. TSTP系统添加样品比对功能，进行单个样品间的比对。
3. 调整TSTP服务器docker部署代码，更改SSR-pipeliner执行环境的映射目录

### 2月10日

定点测序数据SSR分型平台（TSTP）
完成的工作：
1.调整任务和样品的对应关系：一对多
2.将样品分析结果的树形结构封装成单独的页面
3.添加样品列表，和条件查询功能。
