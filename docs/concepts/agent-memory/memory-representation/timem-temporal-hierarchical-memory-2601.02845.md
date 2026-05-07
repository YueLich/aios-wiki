---
title: TiMem: Temporal-Hierarchical Memory Consolidation for Long-Horizon Conversational Agents
arXiv: 2601.02845
date: 2026-01-06
tags: [agent-memory, memory-representation, continual-learning, conversational-agent]
reviewer: auto
source: arXiv API
---

## 论文信息

- **标题**: TiMem: Temporal-Hierarchical Memory Consolidation for Long-Horizon Conversational Agents
- **arXiv**: 2601.02845
- **作者**: Kai Li, Xuanqing Yu, Ziyi Ni, Yi Zeng, Yao Xu, Zheqing Zhang, Xin Li, Jitao Sang, Xiaogang Duan, Xuelei Wang, Chengbao Liu, Jie Tan
- **发表**: 2026-01-06
- **开源代码**: https://github.com/TiMEM-AI/timem

## 摘要（翻译）

长程会话 Agent 需要管理不断增长的对话历史，这些历史很快就会超出大语言模型（LLM）有限的上下文窗口。现有记忆框架对跨层次的时间结构化信息支持有限，往往导致记忆碎片化和不稳定的长期个性化。TiMem 提出了**Temporal Memory Tree（TMT）**，通过时间记忆树组织对话，实现从原始对话观察到逐步抽象的人格表征的系统性记忆整合。TiMem 具备三个核心特性：（1）通过 TMT 实现时间-层次化组织；（2）语义引导的整合，无需微调即可实现跨层次记忆融合；（3）复杂度感知的记忆召回，平衡不同复杂度查询的精度和效率。在一致的评估设置下，TiMem 在 LoCoMo 和 LongMemEval-S 两个基准上分别达到 75.30% 和 76.88% 的最优准确率，同时在 LoCoMo 上将召回记忆长度减少 52.20%。

## 核心贡献

1. **Temporal Memory Tree（TMT）**: 首次将时间连续性作为记忆组织的一等公民，通过树结构对对话历史进行层次化时间建模
2. **语义引导的整合（Semantic-guided Consolidation）**: 跨层次记忆融合无需微调，保持 LLM 原有能力的同时实现动态知识整合
3. **复杂度感知的召回（Complexity-aware Recall）**: 根据查询复杂度动态调整召回策略，平衡精度与效率
4. **SOTA 性能**: LoCoMo 75.30%、LongMemEval-S 76.88%，同时将召回长度减少 52.20%

## 为什么重要

当前 LLM Agent 的记忆系统普遍存在两个问题：（1）将所有历史等权重对待，导致重要信息被稀释；（2）缺乏时间结构，跨会话的长期偏好学习不稳定。TiMem 提出了一个原则性的时间层次框架，将记忆组织为树结构，使得：
- 最近的对话在叶子层，抽象的人格表征在根节点层
- 语义引导的整合可以在不遗忘原有知识的情况下注入新信息
- 复杂度感知的召回可以根据任务类型选择不同深度的记忆

这对设计能够**在端侧长期运行**的个性化助手（手机语音助手、车载对话系统）具有重要的工程价值。

## 与端侧/移动端的相关性

1. **内存效率高**: 52.20% 的召回长度 reduction 对移动设备资源受限场景意义重大
2. **无需微调**: 语义引导整合不需要云端协同，适合纯端侧部署
3. **层次化组织**: TMT 结构天然支持增量更新，新增对话可直接追加到叶子层
4. **时间优先**: 移动端个性化助手的核心需求就是"记住用户上次说了什么"，TMT 的时间建模直接对齐这一需求

## 相关论文

- [Mem-Continue](memory-retrieval/mem-continue-long-term-conversation-2602.15731): LoCoMo 基准提出者
- [Memoria](memory-retrieval/memoria-proactive-conversational-2601.09652): 会话记忆 benchmark
- [PERMA](memory-retrieval/perma-personalized-memory-benchmark-2603.23231): 个性化记忆评估基准

## 参考文献

- Kai Li et al. "TiMem: Temporal-Hierarchical Memory Consolidation for Long-Horizon Conversational Agents." arXiv:2601.02845, 2026.
