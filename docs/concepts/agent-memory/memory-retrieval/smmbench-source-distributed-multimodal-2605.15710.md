---
title: SMMBench: A Benchmark for Source-Distributed Multimodal Agent Memory
arXiv: 2605.15710
date: 2026-05-15
tags: [agent-memory, multimodal-memory, benchmark]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **作者**: Huacan Chai, Yingxuan Yang, Dan Peng, Yuanyi Song
- **发表**: 2026-05-15
- **类别**: cs.CL
- **机构**: （待从原文补充）

## 摘要（原文翻译）

现有 Multimodal Memory Reasoning 基准测试大多在预组装上下文内评估系统，但**低估了 Agent 能否使用分布在独立来源的证据**。本文认为，**源分布式记忆组合（source-distributed memory composition）** 是 Multimodal Agent Memory 中一个重要但未被充分审视的瓶颈——尤其是当相关证据分散在异构制品（如对话、个人资料、截图、表格、图像和文档）中时。为填补这一空白，本文提出 Source-distributed Multimodal Memory Benchmark（SMMBench），用于评估 Agent 能否检索、对齐和组合**分散在多个来源的多模态证据**，而非在单一整理好的上下文内推理。SMMBench 评估四种核心能力：（1）跨来源多模态推理；（2）冲突解决；（3）偏好推理；（4）记忆引导的动作预测。基准测试包含 1877 个样本，扎根于 264 个来源。对代表性记忆风格和基于检索的基线系统的实验表明，当前系统在这些问题上仍有明显不足，源分布式多模态记忆仍是 Multimodal Agent 面临的重要且未被充分评估的挑战。

## 核心贡献

1. **源分布式记忆组合场景**：首次系统研究跨异构来源（对话、截图、表格、图像、文档等）的多模态记忆检索与组合
2. **1877 样本 / 264 来源的大规模基准**：覆盖真实场景的碎片化信息整合挑战
3. **四项核心能力评估**：跨来源推理、冲突解决、偏好推理、动作预测
4. **揭示当前系统的不足**：SOTA 记忆和检索系统在多来源场景下仍有明显差距

## 为什么重要

真实世界的 Agent 面对的不是"整理好的上下文"，而是**碎片化、跨来源、异构模态**的信息。用户可能在聊天中提到某个产品，在邮件中收到相关信息，在相册中有相关截图——现有记忆系统无法有效组合这些分散证据。SMMBench 填补了这一评估空白，为下一代多模态 Agent 记忆系统指明了方向。

## 与移动端/端侧的相关性

移动端是典型的"碎片化多来源"场景：相册、短信、邮件、社交媒体、文档分散在不同应用中。SMMBench 的发现直接指导端侧多模态记忆系统的设计：
- **跨应用信息整合**：端侧 Agent 需要跨应用检索和组合记忆
- **冲突解决能力**：同一实体在不同来源可能有冲突描述
- **存储效率**：264 个来源的证据如何高效压缩存储是端侧挑战

## 参考文献

- Chai, H., et al. (2026). SMMBench: A Benchmark for Source-Distributed Multimodal Agent Memory. arXiv:2605.15710.
