# symbolic-kernels
A research sketch for treating symbolic and metaphysical systems as Gaussian Process kernel hypotheses: structured priors over similarity, covariance, cycles, and transformation.


# 中文版

我几乎从未真正怀疑过“玄学”的有效性。作为一个经验主义者，我有超过十年的塔罗牌经验，并在最近两年开始系统研究八字和星盘。在我的经验里，它们确实是 work 的：无论过程如何绕行，结果往往会以某种方式回到测算所指向的方向。因此，这项研究建立在一个很基本的判断上：有效的玄学体系，本质上是一种人工驱动的机器学习算法。

从哲学角度看，如果存在某种可被经验接近的真理结构，那么任何长期有效的体系，都可以被视为对真理的局部投影。它未必完整，也未必拥有正确的因果解释；但只要它持续 work，就意味着它的内部结构可能捕捉到了某些真实相关性。这个项目正是试图把这种“可能的相关性”翻译成可检验的 kernel。

我真正好奇的是另一件事：如果一个玄学体系能长期存在，它到底在组织什么样的相似性？
直白地来说：比如八字、占星、易经、塔罗这些体系，表面上是在解释命运、性格、事件或者选择。但更仔细看，它们都在做一件很核心的事：把人、时间、事件、问题、关系和变化放进一套符号结构里，然后判断哪些东西彼此相近、相冲、相合、相生、相克、同象、异象、同周期、不同相位。这听起来不像一个普通的预测模型，它更像是在定义一种相似性函数。

所以这完全可以看作一个Gaussian Process中的kernel：
```text
a symbolic system = a hand-designed prior over covariance
玄学体系不是一组神秘特征，而是一组关于 covariance 的结构化先验。
```
```text
or to be shorter：
symbolic system = kernel hypothesis
```

## Why Kernel？
很多机器学习做法会把符号系统简单地one-hot encode：
- 太阳星座是什么
- 八字日主是什么
- 抽到了哪张大阿卡纳
- 得到了哪一卦

我们假设它是一个类似这样的形式：
$k_{\text{total}}(x, x') = w_{\text{cycle}} k_{\text{cycle}}(x, x') + \epsilon$


这样我们就可以问一个更精确的问题：
> 哪一部分传统结构真的贡献了可泛化的相似性？

## What this is Not
这个项目并不是为了证明玄学是真的，也并非把玄学包装成科学，更不是把一堆符号丢进模型里，让模型自己乱学
我想做的是把一个古老的争论换成一个更可检验的问题：
>一个符号，是否编码了一组可用的function-space prior？

>如果有用，它应当能在样本外预测、校准、不确定性估计或模型证据上提供增益

>如果没用，我们也可以退一步研究：到底是周期结构没用，关系结构不够有用，还是某些传统规则只在叙事上有意义，而在统计上没有贡献？

## 可以研究的体系：
可能的方向包括：
- 八字：天干地支、五行、生克、合冲刑害、大运流年
- 占星：星体位置、相位、宫位、守护关系、行运
- 易经：卦象、爻变、错卦、综卦、互卦
- 塔罗：牌序、元素、数字、宫廷牌、牌阵位置
- 历法与择日系统：周期、节气、相位、时间结构

## 最小实验
第一步不应该试图“预测命运”。
更合理的做法是选一个很窄、可记录、可验证的问题。

## Working Hypothesis
- 输入：一个人的出生符号结构，加上某一年的时间结构
- 输出：该年是否发生职业变化、迁居、关系变化、重大压力、自评满意度等
- baseline：年龄、地区、职业、教育、普通时间变量
- 对照 kernel：linear kernel、RBF kernel、random symbolic kernel
- 测试 kernel：根据某个符号体系构造的 composite kernel
- 评估：log predictive density、calibration、Brier score、AUC、marginal likelihood、kernel ablation

## 初步工作流：
1. 选择一个最小体系作为起点。
2. 定义它的基本符号对象。
3. 把传统相似性规则转化为 kernel components。
4. 建立普通 baseline 和 symbolic kernel baseline。
5. 做 ablation 与 calibration test。
6. 记录哪些结构有用、哪些结构无效、哪些结构容易过拟合。





