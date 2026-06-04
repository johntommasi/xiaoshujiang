---
title: '(懵懂故事中)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？'
category: '/小书匠/收集/知乎问答/懵懂故事中/0738c1c11f6b8263c08d0d0dae64157d'
slug: 'https://www.zhihu.com/question/1968361285579150015/answer/1991096099008689610'
createDate: '2026-1-4 10:38:22'
grammar_mathjax: false
grammar_footnote: false
grammar_ins: false
emoji: '懵'
tags: '人工智能,涌现效应,LLM（大型语言模型）,LLM可解释性'

---


[toc]


# 问题

提问者：**<a href="https://www.zhihu.com/people/tomsheep">tomsheep</a>**
提问时间: 2025-11-2 16:58:20
总回答数: 233
总访问量: 1737158

研究领域对此有何解释？

# 回答

回答者： **<a href="https://www.zhihu.com/people/7919776925">懵懂故事中</a>**
回答时间: 2026-1-4 10:38:22
点赞总数: 4
评论总数: 0
收藏总数: 9
喜欢总数：1

## 涌现是什么？

在复杂系统科学和人工智能领域， **[「涌现（](https://en.wikipedia.org/wiki/Emergence)** Emergence **[）」](https://en.wikipedia.org/wiki/Emergence)** 指的是整体系统展现出超越其组成部分简单总和的新行为或性质（即“整体大于部分之和”，而这一表述最早可追溯到亚里士多德），其中[弱涌现（weak emergence）](https://www.templeton.org/news/what-is-emergence)指宏观行为虽然难以预测但并非全新原理（复杂但可由下而上推导），而[强涌现](https://www.templeton.org/news/what-is-emergence)则指整体确实具备全新性质，无法从部件属性推导理解。在自然界，最常见的例子就是如下图的白蚁构建的蚁丘：

![”大教堂“式的蚁丘](images/141v2-96986cf739889bdc6356c00523b19438.jpg)

 **“涌现不是‘凭空魔法’，每个个体只遵循很简单的局部规则，但当很多个体不断互动时，会出现一种新的宏观结构（团块、队形、波、同步）。这种结构并不等于任何单个个体的意图，而是由反馈机制把微小差异放大并稳定下来** 。如下图例子（[Schelling（谢林）分居模型](https://www.suz.uzh.ch/dam/jcr%3A00000000-68cb-72db-ffff-ffffff8071db/04.02_schelling_71.pdf)）：Schelling 模型的个体只做一件事： **看自己局部邻域里“同类比例”是否达到某个阈值；不满意就搬到空位** 。但系统演化后，宏观会出现稳定的  **空间团块/分离格局（segregation patterns）** ——这不是任何单个个体“计划”出来的结构，而是群体互动“长出来”的结构。 **Schelling 分居是“弱涌现”的典型——宏观分离是系统级性质，不等同于个体偏好；它源自局部互动的自组织放大。** 

![Schelling（谢林）分居模型](images/142v2-e3ed1246c47abde88327c75d38787477_720w.gif)

用涌现的机制语言解释 Schelling 的核心动力学：  **局部阈值触发** ：只要某个点附近同类比例略低于阈值，该个体就移动（局部决策）。 **团块一旦形成就更稳定** ：一小块同类聚集会让块内个体更“满意”，从而减少继续移动；与此同时，块边界附近更容易让异类不满意并迁出。 **因此出现正反馈** ：小小的随机波动会被放大，最终收敛到“块状分布”的 **吸引子（absorbing state）** 。这类“由局部规则驱动的宏观模式形成”正是复杂系统典型的涌现路径。除了Schelling（谢林）分居模型外，还有很多容易理解的例子：群集/队形涌现（[Boids 鸟群](https://www.red3d.com/cwr/boids/)），“无瓶颈也能堵”（[幽灵交通拥堵phantom jam](https://ir.library.osaka-u.ac.jp/repo/ouka/all/93262/NewJPhys_10_033001.pdf)），群体寻路与“信息网络”（[蚂蚁信息素路径](https://www.romjist.ro/content/pdf/04-jackson.pdf)），元胞自动机（[Game of Life 的滑翔子/机关枪](https://people.reed.edu/~mab/papers/weak.emergence.pdf)）。

## LLM的涌现

本文主要讨论LLM的涌现现象，为此可以从以下的阶段比较：  **传统复杂系统中的涌现** ；  **早期语言模型** （大型语言模型出现之前的模型，如n-gram、Word2Vec等）；  **大型语言模型(LLM)涌现能力初现阶段** （如GPT-3时代，首次广泛观察到LLM的涌现行为）； **当前最先进的LLM阶段** （如GPT-4/5、Google Gemini、Anthropic Claude 等）。具体的比较维度包括：涌现概念的定义来源、“整体大于部分之和”的特性、不可预测性、反馈机制、以及验证方法:

![](./attachments/143.table.html)

-    **早期语言模型：在LLM出现之前的语言模型（如基于统计的n-gram模型或词向量模型等）并没有强调“涌现”概念。其行为基本可以由组成部分和算法规则解释，属于模块化** 的人工设计系统。这些模型通过统计规律预测下一个词，模型能力随数据和参数规模增加而 **平滑提升** ，没有出现质变般的新功能跳跃。因此，早期语言模型并未被视为具有复杂系统意义上的涌现行为。

![Eight examples of emergence in the few-shot prompting setting](images/144v2-8e19bb2ce65784b436fbf05b0d97aba1.jpg)

-    **LLM涌现能力初现阶段（GPT-3）：随着GPT-3等大型语言模型横空出世，研究者借用了复杂系统中的“涌现”概念来描述其令人惊讶的新能力[georgetown](https://cset.georgetown.edu/article/emergent-abilities-in-large-language-models-an-explainer/)。Jason Wei等人（2022）将LLM的“涌现能力”定义为：某种能力在小模型中不存在，但在更大模型中出现，且无法通过插值外推小模型的性能来预测(如上图，**  _模型规模（横轴）在很长一段区间增加时，任务指标（纵轴）几乎贴着“随机水平”不动_ 。当规模跨过某个 **临界阈值** 后，性能会在很短的尺度区间内 **突然跃迁到显著高于随机** ——这就是“ **定量变化（算力/参数）→定性变化（能力出现）** ”的相变式涌现。因而， **不能用小模型的平滑外推** 来预测这些能力何时出现；在这些任务上，能力更像“开关被打开”，而不是线性变强。 **)。这一阶段的理论背景主要源于大规模模型的观察研究** ：研究者发现，当参数和数据规模超过某一阈值时，会突然出现过去未曾预料的新功能，这对传统的渐进改进认知提出挑战。 **如下图** [PaLM](https://research.google/blog/pathways-language-model-palm-scaling-to-540-billion-parameters-for-breakthrough-performance/)当模型参数规模增大到约  **8B**  时，模型会先出现一些 **可稳定复用的基础能力芽点** （如语言理解、算术、问答），看起来像从“不会”变成“会”。这说明能力并非随规模线性平滑增强，而更像跨过某个规模阈值后 **突然跃迁** 并带来新的可组合能力集合（相变式涌现）。

![As the scale of the model increases, the performance improves across tasks while also unlocking new capabilities.](images/145v2-d57354f24d7c77dcc722c4c9b27ca9db.jpg)

-    **当前最先进 LLM 阶段（GPT-4、5 等）：最新一代的超大规模模型（例如GPT-4、Google DeepMind Gemini、Claude 2等）延续并扩展了前述涌现概念。理论上，这些模型由于规模和训练方法的飞跃，被一些研究者视为在朝“通用智能”方向发展[arxiv.org](https://arxiv.org/abs/2303.12712#:~:text=exhibit%20more%20general%20intelligence%20than,In%20our%20exploration)。GPT-4 等模型不仅在语言任务上表现卓越，还能跨模态和跨领域解决复杂问题，展现出更加广泛和深入的智能能力。微软研究人员称GPT-4展示出“通用智能的火花”，因为它无需特殊提示就能在数学、编程、医学、法律等前所未有的广泛任务上接近人类水平** （如下图, _用几条“非常普通的指令”就让 GPT-4 同时完成诗歌化数学证明、代码生成图形（TikZ 独角兽）、Python 动画、以及数学推理题，体现的是一种跨任务/跨表征的“组合能力”突然变得稳定可用——这更像能力阈值被跨过后的质变，而不是单一指标的线性提升。_ ） **。总体而言，当前阶段的涌现行为被视作此前规模扩展趋势的延续和升级，并引发关于强涌现** （真正的新涌现规律）的讨论。

![Preliminary examples of GPT-4’s capabilities in language, vision, coding, and mathematics.5](images/146v2-a49e5d6bbfc7c2d318e4c35bd4d17388.jpg)

## LLM涌现和scaling laws 是什么关系？

 **Scaling laws 描述的是「模型变大 ⇒ 指标按幂律平滑提升」的平均趋势，而所谓 LLM 的“涌现能力”指的是某些任务在这个平滑曲线之上表现出“看起来像台阶跳变”的现象；目前比较主流的观点是：很多“涌现”其实是我们如何衡量性能（metric 选择）+任务定义方式** 造成的，看起来在 scaling law 曲线中是“断点”，但在更细致、合适的指标下往往仍然是 **平滑 scaling**  的一部分。

经典的 LLM scaling laws（Kaplan 等、DeepMind/Google 一系列工作）说的是：当按幂律扩大「参数量 N / 数据量 D / 训练算力 C」时，损失函数（如 cross-entropy loss）或一些任务指标， **大致按幂律平滑下降。** 这里没有“突然多出一种全新能力”的说法，只有“越大越好而且大致平滑”。换句话说：scaling laws 是一个「 **连续变化** 」的故事：没有哪一个点在理论上必须“质变”。Jason Wei 等人在 2022 年那篇 [Emergent Abilities of Large Language Models](https://arxiv.org/pdf/2206.07682) 就是沿着这个思路整理了一堆“台阶式能力”，并把它们命名为  **emergent abilities** （涌现能力）（你可以把它理解为： **在 scaling law 曲线的某些任务上，出现了“肉眼可见的非线性跳跃”** ）。

## 这些“涌现”，到底是模型真的突然学会了新东西，还是我们 **看曲线的方式** 导致“台阶错觉”？

-    **很多“涌现”是 metric 选择造成的。** 

如果你用的是「0/1 准确率」这类硬阈值指标，小模型长期在 0～5% 的随机区间晃，肉眼感觉“没有能力”； 到了一定规模，一下子跳到 50%/60%，看起来就像突然“开窍”。但如果你改用更细粒度的指标（比如 log-loss、校准后的概率、rank-based 分数），往往可以看到从小模型开始就是平滑上升的幂律曲线，只是早期的提升隐藏在“看起来都很烂”的区域里。 **换句话说：潜在能力的概率结构一直在随 scaling 平滑变好，只是被粗糙的指标“量化成了台阶”。** 

-    **从 scaling law 的视角看，“涌现”更像是局部的非线性，而不是新的物理定律。** 

在 log-loss、perplexity 这类“底层指标”上，几乎所有 LLM 都遵守非常漂亮的 scaling laws； 很多高层任务（翻译、推理、问答）其实是这些底层概率分布的函数映射，再叠加一个离散化阈值（例如 top-1 是否正确）；当底层分布在某个规模段跨过“成功阈值”时，上层任务就从肉眼看来“突然能做”，你就说“涌现了”。

-    **也有少量任务，在目前的数据下，即使用更细指标，仍然显得高度非线性。** 

这类情况更接近复杂系统里的“phase transition 类比”：scaling laws 描述背景趋势，而某些结构化任务可能在某个参数/数据组合下出现「结构突变」。但即便如此，大多数学者的态度还是谨慎：在我们没换 metric、没换任务定义、没看到足够细的数据之前，很难说是真正物理意义上的“强涌现”。

## 反击：涌现是不是“海市蜃楼”？

2023 年 Schaeffer 等的[《Are Emergent Abilities of Large Language Models a Mirage?》](https://arxiv.org/pdf/2304.15004)（NeurIPS 2023）直接打脸所谓的“涌现”现象：“大部分所谓“涌现能力”，是 **我们自己选的指标和统计方式搞出来的假象（mirage）** 。”（如下图）

> 他们做了几件事： 把 LLM 在某些任务上的表现，拆解成 **底层 per-token error / log-loss 的平滑 scaling** ； 证明：在这些底层连续指标上，模型性能 **随规模平滑幂律下降** ，没有任何“断点”；展示：一旦你把这些连续指标通过 **非线性/不连续 metric** （比如 0-1 accuracy、是否超过某个分数线）去“量子化”，就会产生 **看上去像台阶的曲线** ；再加上小模型上测试样本太少、估计方差很大，更容易让小模型看起来“一点都不会”。[arXiv](https://arxiv.org/pdf/2304.15004)

该文总结：Emergent abilities 大多是  **metric + sample size 选择** 导致的视觉效果； 在合适的连续度量下，这些能力同样 obey 普通 scaling laws；因此所谓“不可预测的质变能力”在很大程度上是  **“观测伪象”，而不是新物理规律** 。

![Emergent abilities of large language models are created by the researcher’s chosen metrics, not unpredictable changes in model behavior with scale](images/147v2-a0d1527a0f3dca1da90696b65e043416.jpg)

2025年Berti 等在《Emergent Abilities in Large Language Models: A Survey》中进一步：系统梳理了各种对“emergent ability”的定义，指出现有定义之间存在 **不一致与模糊** ；专门讨论了  **scaling laws、任务复杂度、度量指标、pre-training loss、量化、prompt 设计** 等因素，各自如何影响“是否观测到涌现”。同时，给出深入的认识： **部分“涌现”确实可以通过 Schaeffer 那种 metric 解释；但也有一些现象在换 metric 后依然表现为强烈非线性，需要更深入机制解释。** 把讨论从“涌现是真还是假的？”抬升到： **在什么任务、什么指标、什么训练条件下，会呈现出什么形态的涌现？”** 

## 未来几条可能演化方向

### (A) 「度量派」：一切归于 scaling + metric

-   代表态度：大多数学术保守派会站在 Schaeffer 一侧：“只要你换成合适的连续指标，绝大部分所谓涌现似乎都可以看成 scaling law 的自然投影。”
-   未来工作重点：继续为不同任务设计 **更细腻的连续指标** （例如 process-based reward、一步步推理路径的质量指标）；用这些指标拟合 scaling laws，看“涌现台阶”能否被消平。

### (B) 「结构派」：有些涌现确实反映了内部表征/算法的相变

-   代表态度：部分研究者认为，哪怕 metric 能解释一部分现象，依然可能存在  **内部表征层面** 的质变： 比如从“模式背诵”到“学到真正的符号/算法结构”；从“仅局部关联”到“形成更全局、因果式世界模型”。 例如：清华的Junhao Chen等的[States Hidden in Hidden States: LLMs Emerge Discrete State Representations Implicitly](https://arxiv.org/pdf/2407.11421)指出：LLM  **内部隐藏状态（hidden states）能够自动形成离散的“状态表示”** ，表面上看某些推理能力是“涌现”，但其实是模型通过训练内部隐式构建出 **离散表征结构** ，用于有效执行任务。2025年Matthieu Tehenan等发表的[Linear Spatial World Models Emerge in Large Language Models (2025)](https://arxiv.org/pdf/2506.02996)通过 probing（探测器）方法显示：LLM 的内部嵌入空间能够隐式编码 **线性空间模型（linear spatial world models）** ，即模型内部存在关于空间信息的几何结构，而不是随机统计（如下图）。

![Visualization of spatial relation basis vectors and their compositional structure in PCA space](images/148v2-9ff251689874379c916479f7cd6a2b18.jpg)

-   未来研究方向：利用 probing、mechanistic interpretability、神经元群分析， **在内部空间里找“表示相变点”** ；结合 RL + search（Large Reasoning Models）去看：推理深度/搜索策略是否有“临界规模”。

### (C) 「系统-社会派」：多智能体/多模型交互层面的新型涌现

-   最新有研究表明：让多个 LLM agent 在不完全信息 & 反复博弈下合作，它们能 **自发形成类人命名习惯和社会规范** ，类似语言/社会习俗的演化，是另一类“群体涌现”(如下图)。[Science](https://www.science.org/doi/10.1126/sciadv.adu9368)
-   未来方向可能从“单模型 scaling”转向“多模型生态”的涌现：群体协作协议、约定俗成的符号体系、甚至 agent 社会结构。

![Spontaneous emergence](images/149v2-03cef084c031a30e66de428f231e238c.jpg)

  

原文地址：[(懵懂故事中)为什么 LLM 仅预测下一词，就能「涌现」出高级能力？](https://www.zhihu.com/question/1968361285579150015/answer/1991096099008689610) 


