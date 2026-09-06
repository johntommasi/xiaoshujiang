---
title: '(香港市民董先生)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？'
category: '/小书匠/收集/知乎问答/香港市民董先生/cd2c9e656b83907607ba4ab6423bd6e8'
slug: 'https://www.zhihu.com/question/1968361285579150015/answer/1968666581992183534'
createDate: '2025-11-3 13:11:29'


tags:
- 人工智能
- 涌现效应
- LLM（大型语言模型）
- LLM可解释性

---


[toc]


# 问题

提问者：**<a href="https://www.zhihu.com/people/tomsheep">tomsheep</a>**
提问时间: 2025-11-2 16:58:20
总回答数: 233
总访问量: 1737157

研究领域对此有何解释？

# 回答

回答者： **<a href="https://www.zhihu.com/people/dong-bu-dong-95-73">香港市民董先生</a>**
回答时间: 2025-11-3 13:11:29
点赞总数: 34
评论总数: 3
收藏总数: 35
喜欢总数：1

 **本质上是因为已经通过文本tokens建立了相对完整的世界模型world model，不断进行下一个词预测的过程，就是世界模型不断构建并加固的过程。** 

为方便理解，可以做个类比。我们如果有一个3D world model，那么你可以把每个文本理解成其中的voxels（三维体素，类似于游戏我的世界中，每一个立方体），

 **但是文本token具有很高的embedding维度，而且这个embedding经过训练后质量很高（这才是精髓所在），** 

—— 于是每个token对应了更多更丰富的voxel含义，这也是为什么可以通过固定vocabulary大小的dataset进行pre-training，可以实现相对完整world model的建模。

当然，这种建模本质上是缺乏对应视觉vision和物理physical信息的，沿着一维文本维度（vision可以理解为二维，加上physical物理世界可以理解为三维）的world model，这也是为什么会有另外两条路线，即VLM和VLA。

VLM就是试图在LLM所建立的文本world model基础上扩展视觉vision维度，弥补LLM在二维世界上的缺失；VLA则是试图加上物理世界信息，实现physical intelligence，——这正是具身智能这个方向现在火热的主要基础路线之一（具体分析可以参考我之前的文章：

  

原文地址：[(香港市民董先生)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？](https://www.zhihu.com/question/1968361285579150015/answer/1968666581992183534) 


