---
title: '(xiaobo Xie)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？'
category: '/小书匠/收集/知乎问答/xiaobo Xie/fbd5c2e8aa9a9f651b2ffbe3aafb3f16'
slug: 'https://www.zhihu.com/question/1968361285579150015/answer/2045061272358605657'
createDate: '2026-6-2 8:36:42'
grammar_mathjax: false
grammar_footnote: false
grammar_ins: false
emoji: 'x'
tags: '人工智能,涌现效应,LLM（大型语言模型）,LLM可解释性'

---


[toc]


# 问题

提问者：**<a href="https://www.zhihu.com/people/tomsheep">tomsheep</a>**
提问时间: 2025-11-2 16:58:20
总回答数: 233
总访问量: 1737160

研究领域对此有何解释？

# 回答

回答者： **<a href="https://www.zhihu.com/people/xiaobo-xie">xiaobo Xie</a>**
回答时间: 2026-6-2 8:36:42
点赞总数: 1
评论总数: 0
收藏总数: 2
喜欢总数：0

机器学习的目标就是通过训练去寻找那个Y=F(X)中的那个F，既事物之间的规律。

首先LLM也属于机器学习的产物，通过大量的语料训练，从而找到文字和文字之间的规律，即所谓的学习到了“知识”。我一直认为LLM其实是一种“知识”的representation，经过训练将自然语言“知识”通过神经网络的权重来表达，当我们需要使用的时候，通过指令和提示词让其进行检索和输出。其实所谓的涌现，也只是通过那个训练获得的F来不断输出而已。

  

原文地址：[(xiaobo Xie)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？](https://www.zhihu.com/question/1968361285579150015/answer/2045061272358605657) 


