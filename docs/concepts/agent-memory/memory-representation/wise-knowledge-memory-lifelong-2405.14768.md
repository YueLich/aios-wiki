---
title: WISE - Rethinking the Knowledge Memory for Lifelong Model Editing of Large Language Models
arXiv: 2405.14768
date: 2024-05-23
tags: [agent-memory, knowledge-memory, model-editing, continual-learning]
reviewer: auto
source: arXiv API
---

# WISE: Rethinking the Knowledge Memory for Lifelong Model Editing

## 摘要

大模型需要知识更新以跟上不断增长的世界事实并纠正幻觉响应，这推动了终身模型编辑方法的发展。更新后的知识存储在记忆中是一个根本性问题。本文发现知识记忆中的知识以"参数化程度"连续分布，从高度参数化（存储在模型权重中）到完全非参数化（存储在外部 RAG 记忆）。文章提出 WISE 框架，通过显式建模知识在不同参数化程度之间的流动，实现更精准、更可扩展的终身知识更新。

## 核心贡献

1. **知识参数化程度谱系**：发现知识记忆中的知识是连续分布的
2. **WISE 框架**：显式建模知识的参数化程度和流动
3. **混合记忆架构**：同时维护参数化记忆和非参数化记忆
4. **精准知识定位**：确定知识在参数化程度谱上的位置
5. **高效终身编辑**：支持连续的知识更新而不遗忘

## 技术方法

### 知识参数化谱
- **高参数化端**：存储在模型权重中（传统微调）
- **低参数化端**：存储在外部 RAG 中（非参数化）
- **中间状态**：通过 LoRA/Adapter 等半参数化方法

### WISE 机制
1. 评估每条知识在谱上的位置
2. 根据知识特性选择最优的参数化形式
3. 动态调整知识在不同形式之间的分配
4. 支持知识的增量更新和选择性遗忘

## 为什么重要

WISE 揭示了"知识记忆不是非黑即白的——而是有参数化程度的光谱"。这对 Agent 记忆系统设计的启发：应该根据知识的特性（稳定性、更新频率、使用频率）选择不同的存储形式，而不是一刀切地全部用 RAG 或全部用微调。

## 与移动端/端侧相关性

1. **端侧知识更新**：在移动设备上高效更新模型知识
2. **个性化记忆**：用户特定知识用轻量方式存储
3. **隐私敏感知识**：高隐私知识用非参数化形式本地存储
4. **计算效率**：根据任务动态选择记忆形式，减少推理开销

## 参考文献

- Peng Wang, Zexi Li, Ningyu Zhang, Ziwen Xu. "WISE: Rethinking the Knowledge Memory for Lifelong Model Editing of Large Language Models." arXiv:2405.14768, 2024.
