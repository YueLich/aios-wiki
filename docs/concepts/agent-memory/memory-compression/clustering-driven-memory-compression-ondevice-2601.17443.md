---
title: "Clustering-Driven Memory Compression for On-device Large Language Models"
arXiv: 2601.17443
date: 2026-01-24
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Clustering-Driven Memory Compression for On-device Large Language Models

## 论文基本信息

- **作者**: Hyun Jong Won, et al.
- **arXiv**: https://arxiv.org/abs/2601.17443
- **领域**: cs.CL, cs.AI

## 摘要

大语言模型通常依赖从过去交互中提炼的用户特定记忆来实现个性化生成。常见做法是将这些记忆拼接到输入提示，但很快耗尽移动端 LLM 有限的上下文。通过平均压缩记忆可以缓解上下文增长，但因语义冲突损害性能。本工作提出基于聚类的记忆压缩策略，按相似性将记忆分组，在拼接前先在组内合并，从而在保持一致性的同时减少冗余。实验表明，该方法显著减少记忆 token 数量，同时优于基线策略（如朴素平均或直接拼接）。

## 核心贡献

1. **Clustering-based Memory Compression**: 按相似性分组记忆，组内合并后拼接
2. **一致性保留**: 组内合并减少语义冲突，保持记忆一致性
3. **显著 Token 减少**: 在保持生成质量的同时大幅减少记忆 token
4. **上下文效率**: 对固定上下文预算，聚类合并产生更紧凑的记忆表示
5. **生成质量提升**: 聚类驱动合并策略一致提升生成质量

## 研究背景与问题

端侧 LLM 需要维护用户特定记忆（如聊天历史、个人偏好），但上下文窗口有限。朴素平均会因语义冲突损害性能，直接拼接则超过上下文限制。

## 核心方法

1. **Memory Clustering**: 用语义相似度将异构记忆聚类分组
2. **Intra-cluster Merging**: 组内记忆合并（加权平均或选代表），生成组级记忆
3. **Adaptive Cluster Size**: 根据上下文预算自适应决定聚类粒度
4. **Cluster-conditioned Generation**: 生成时以聚类记忆为条件
5. **Conflict Resolution**: 聚类内冲突通过注意力权重解决

## 为什么重要

聚类驱动压缩是记忆压缩领域的重要进展，填补了"全部压缩"和"全部保留"之间的空白。对移动端个性化 Agent 的记忆管理有直接参考价值。

## 与移动端/端侧相关性

1. **端侧原生设计**: 方法专为移动端 LLM 设计，考虑资源限制
2. **上下文受限场景**: 非常适合手机、AR 眼镜等上下文有限的设备
3. **用户隐私**: 个性化记忆可本地存储和压缩，不上传云端
4. **自适应粒度**: 根据设备能力动态调整压缩程度
