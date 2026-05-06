---
title: "The Price of Meaning: Why Every Semantic Memory System Forgets"
arXiv: "2603.27116"
date: "2026-03-28"
tags: [agent-memory, memory-compression, semantic-memory, theory]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **语义记忆的内在代价理论**：证明相同的几何结构在赋予语义泛化能力的同时，也使得干扰、遗忘和错误回忆不可避免。
2. **形式化分析框架**：对 semantically continuous kernel-threshold memories（语义连续核阈值记忆）进行严格分析。
3. **四项理论结果**：
   - 语义有用表示具有有限有效秩（finite effective rank）
   - 有限局部维度意味着正竞争者质量（positive competitor mass）
   - 在增长记忆下，保留率衰减到零，呈现幂律遗忘曲线
   - 对于满足 δ-凸条件的关联诱饵，错误回忆无法通过阈值调节消除
4. **五大架构验证**：在向量检索、图记忆、注意力上下文、BM25 文件系统检索、参数记忆五种架构上验证理论预测。

## 方法详解

### 核心洞察
生产系统中的 AI 记忆都按语义组织信息。这种组织方式支撑了泛化、类比和概念检索，但代价是：使干扰、遗忘和错误回忆不可避免。

### 理论框架
考虑 retrieval score 是语义特征空间内积的单调函数的记忆系统。论文证明：
- 语义泛化能力 → 有限局部维度 → 正竞争者质量
- 增长记忆 + 幂律到达统计 → 幂律遗忘曲线
- 阈值调节无法消除错误回忆

### 推理增强系统的代价
加入推理增强（reasoning-augmented）可以部分缓解症状，但会将 graceful degradation 转变为 catastrophic failure。

## 为什么重要

这是第一篇从理论层面证明"按语义组织记忆必然导致遗忘"的论文。它为记忆压缩和选择性遗忘提供了理论基础——不是工程上的缺陷，而是语义组织的内在代价。

## 与端侧/移动端的相关性

**高度相关**。边缘设备的存储限制使得记忆压缩和遗忘策略必不可少。这篇论文告诉我们：遗忘不是缺陷，而是语义记忆系统的本质特征。端侧记忆系统的设计应当拥抱有策略的遗忘，而非试图完全避免它。

## 摘要

Every major AI memory system in production today organises information by meaning. That organisation enables generalisation, analogy, and conceptual retrieval -- but it comes at a price. We prove that the same geometric structure enabling semantic generalisation makes interference, forgetting, and false recall inescapable. We formalise this tradeoff for \textit{semantically continuous kernel-threshold memories}: systems whose retrieval score is a monotone function of an inner product in a semantic feature space with finite local intrinsic dimension.
  Within this class we derive four results: (1) semantically useful representations have finite effective rank; (2) finite local dimension implies positive competitor mass in retrieval neighbourhoods; (3) under growing memory, retention decays to zero, yielding power-law forgetting curves under power-law arrival statistics; (4) for associative lures satisfying a $δ$-convexity condition, false recall cannot be eliminated by threshold tuning.
  We test these predictions across five architectures: vector retrieval, graph memory, attention-based context, BM25 filesystem retrieval, and parametric memory. Pure semantic systems express the vulnerability directly as forgetting and false recall. Reasoning-augmented systems partially override these symptoms but convert graceful degradation into catastrophic failure. Systems that escape interference entirely do so by sacrificing semantic generalisation.
  The price of meaning is interference, and no architecture we tested avoids paying it.

## 参考文献

- Sambartha Ray Barman, Andrey Starenky, Sofia Bodnar, Nikhil Narasimhan, Ashwin Gopinath. "The Price of Meaning: Why Every Semantic Memory System Forgets." arXiv:2603.27116, 2026.
