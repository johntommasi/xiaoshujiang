---
title: '(PENG Bo)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？'
category: '/小书匠/收集/知乎问答/PENG Bo/64d972cc5bae62489442e35b32dc0fce'
slug: 'https://www.zhihu.com/question/1968361285579150015/answer/2023893715052237934'
createDate: '2026-4-4 22:44:23'
grammar_mathjax: false
grammar_footnote: false
grammar_ins: false
emoji: 'P'
tags: '人工智能,涌现效应,LLM（大型语言模型）,LLM可解释性'

---


[toc]


# 问题

提问者：**<a href="https://www.zhihu.com/people/tomsheep">tomsheep</a>**
提问时间: 2025-11-2 16:58:20
总回答数: 233
总访问量: 1737155

研究领域对此有何解释？

# 回答

回答者： **<a href="https://www.zhihu.com/people/bopengbopeng">PENG Bo</a>**
回答时间: 2026-4-4 22:44:23
点赞总数: 479
评论总数: 24
收藏总数: 458
喜欢总数：12

群里有人转这个问题。我发现这里的回答都漏了关键。我说个适合理解的原因。

___

如果你没有训练过LLM，可能会误以为，训练时在做这个：

输入：The biggest lesson that can be read from 70 years of AI research is that general methods that leverage

输出：computation

也就是，每次给一段文字，要求预测下一个词。

那这看上去就很低效，而且模型像是有偷懒的空间（例如，试图去找到一些简单的匹配规则）。

___

但实际，训练这段文字时，是要求模型同时做N个任务：

输入：The

输出：biggest

输入：The biggest

输出：lesson

输入：The biggest lesson

输出：that

......

输入：The biggest lesson that can be read from 70 years of AI research is that general methods that

输出：leverage

输入：The biggest lesson that can be read from 70 years of AI research is that general methods that leverage

输出：computation

这么多个任务，同时都需要做好。于是模型没法偷懒了。

因此，不要被“预测下一词”的表面意思骗了。实际输入一段长度1000的文字，可以构建出999个任务（如果在前面加个开始符，可以构建出1000个），而不是1个任务。

 **由于训练的任务如此密集，模型在做中间任务时，必须让自己做中间任务的方法，有助于解决后面的任务。模型必须在内部建立合理的表征。** 

这就是我们最常用的LM loss，是在做teacher-forcing的next token prediction。

这个方法是不是很聪明？这个teacher-forcing “密集对齐”是几十年前RNN年代的人发明的，见wiki：

The term "teacher forcing" was introduced in 1989 by Ronald J. Williams and David Zipser, who reported that the technique was already being "frequently used in dynamical supervised learning tasks" around that time.

从数学可以严格证明，这是无偏的loss（即，在此把所有子任务的loss直接加起来作为总loss，不需要任何额外的加权，恰好就可以让LM趋于数据的概率分布）。这也是为什么LM loss比BERT loss更scalable。

因为：出现ABC的概率 = 出现A的概率 \* 在A之后出现B的概率 \* 在AB之后出现C的概率

注意，很多loss通不过这关。例如如果你naively用MTP loss，训练的模型是有偏的，你的LM将不是收敛到数据的概率分布  _——_  只不过，很多人不在乎这点，说到底，我们的训练数据已经是有偏的，而且各种后训练让它更偏。

我们已有无偏的loss，我们仍缺无偏的数据。我会说，如果你知道什么是无偏的数据，怎么得到无偏的数据，那么practically你得到了真正的AGI  _——_  这是tautology，相当于说你有oracle。如果你能写出partition function，你都已经是神级了。

___

最后，以上只是介绍目前常规的理解。这一套看似在数学上完善的理论，实际有破绽。

例如，人类显然很不擅长NTP（我会说，人类擅长给自己做NTP）。例如，概率公式也可以有问题。


![](images/08PENG%20Bo.webp)
  

原文地址：[(PENG Bo)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？](https://www.zhihu.com/question/1968361285579150015/answer/2023893715052237934) 


