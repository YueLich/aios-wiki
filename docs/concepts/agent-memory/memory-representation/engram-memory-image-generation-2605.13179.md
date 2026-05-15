---
title: "Does Engram Do Memory Retrieval in Autoregressive Image Generation?"
arXiv: 2605.13179
date: 2026-05-13
tags: [agent-memory, memory-representation, engram, associative-memory]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

本文研究 Engram 模块在自回归图像生成中的实际作用机制。Engram 是一种注入到 Transformer 层的哈希键控 O(1) 联想记忆，曾被解释为"内容寻址的快捷方式来 recurring 局部 token 模式"。本文通过系统实验发现这一解释在图像生成领域不成立：Engram 在所有内存预算比例下都拖累 FID。gate-clamp 实验显示 Engram 表现为一种" gated 侧路径"——作为哈希键控的残差流，其收益主要来自路径本身而非内容寻址的检索机制。具体发现：禁用 Engram 路径是灾难性的，但使用 tiny constant gate（g=0.10）即可匹配或超越学习到的门；donor-probe 实验显示哈希输入对生成分布无显著影响，而随机化或折叠表格则严重降低质量。

## 核心贡献

1. **揭示 Engram 的真实机制**：在 AR 图像生成中，Engram 不是内容寻址检索器，而是一种 gated 侧路径架构。

2. **系统性实验证据**：
   - gate-clamp sweep：constant tiny gate (g=0.10) 匹配或超越学习门
   - donor-probe：哈希输入变化对分布无影响，但随机化/折叠表格严重影响质量
   - 噪声表格从头训练：表冻结为 N(0,1) 噪声仅损失 ΔFID=0.10，反而提升 Inception Score

3. **对 Engram 机制的重新诠释**：Engram 的收益主要来自路径本身（架构侧路径的残差流），表格贡献仅是小幅分布调整。

4. **对 LLM 中 Engram 机制的启示**：本文揭示的机制可能也适用于 LLM 中的 Engram——其内容寻址检索的解释需要重新审视。

## 为什么重要

Engram 作为一种高效的 O(1) 关联记忆，被认为是 AGI 记忆系统的有前途方向。但本文告诉我们，即使 Engram 在 LLM 中有效，其工作机制可能与最初假设不同。如果 Engram 的收益来自"gated 侧路径"而非"内容寻址检索"，那么设计更优的记忆系统需要不同的优化目标。

## 与移动端/端侧的相关性

移动端部署的生成模型（如设备上的图像生成）可能从 Engram 架构中受益，但需要正确的机制理解。本文指出 Engram 在图像生成中并不改善质量，但其作为侧路径架构的特性（低 FLOPs 开销）仍可能对端侧部署有参考价值。此外，理解 Engram 的真实机制有助于设计更高效的端侧记忆模块。

## 参考文献

（参考文献待从原文补充）
