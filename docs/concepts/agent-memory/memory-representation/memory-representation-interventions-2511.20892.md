---
title: Representation Interventions Enable Lifelong Knowledge Memory Control in LLMs
arXiv: 2511.20892
date: 2025-11-25
tags: [agent-memory, knowledge-memory, model-editing, continual-learning]
reviewer: auto
source: arXiv API
---

# Representation Interventions: Lifelong Knowledge Memory Control in LLMs

## 摘要

大模型在部署后常产生不正确或过时内容。高效准确的知识更新且无需昂贵重训练是重大挑战。这一问题在终身设置中尤为严峻，因为复杂、非结构化的知识必须与既有知识共存。本文提出基于表征干预的终身知识记忆控制方法，通过调整模型内部表征实现知识的精确注入、更新和遗忘，为 LLMs 提供可解释、可控的知识记忆管理能力。

## 核心贡献

1. **表征干预框架**：通过调整模型内部表征实现知识操作
2. **终身知识管理**：支持知识的持续注入、更新和选择性遗忘
3. **无需重训练**：推理时干预，不修改模型权重
4. **可解释性强**：知识操作直接反映在表征空间中
5. **与既有知识兼容**：新知识不干扰模型已掌握的知识

## 技术方法

### 表征空间的知识编辑
1. **知识定位**：找到与目标知识相关的表征方向
2. **表征对齐**：将新知识对齐到模型已学习的表征空间
3. **干预执行**：在推理时沿表征方向调整激活
4. **遗忘控制**：通过反向干预实现选择性遗忘

### 终身学习场景
- 新知识持续注入而不遗忘旧知识
- 特定知识的定向遗忘（如隐私信息）
- 知识冲突解决：新旧知识的表征协调

## 为什么重要

这是"知识记忆"领域的重大突破——证明了可以通过表征空间的干预来控制模型的知识存储。相比 RAG（外部记忆）和微调（修改权重），表征干预提供了一种介于两者之间的"中庸之道"：既不需要外部存储，也不需要修改权重，而是在推理时直接调整表征。

## 与移动端/端侧相关性

1. **隐私记忆控制**：可定向遗忘敏感信息
2. **个性化知识注入**：在设备端动态调整模型知识
3. **低资源更新**：无需 GPU 即可更新模型知识
4. **即时生效**：推理时干预，立即反映知识变化

## 参考文献

- Xuyuan Liu, Shengyu Chen, Xinshuai Dong, Yanchi Liu. "Representation Interventions Enable Lifelong Knowledge Memory Control in LLMs." arXiv:2511.20892, 2025.
