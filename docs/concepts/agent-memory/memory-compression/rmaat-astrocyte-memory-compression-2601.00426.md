---
title: "RMAAT: Astrocyte-Inspired Memory Compression and Replay for Efficient Long-Context Transformers"
arXiv: 2601.00426
date: 2026-01-01
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# RMAAT: Astrocyte-Inspired Memory Compression and Replay for Efficient Long-Context Transformers

**作者:** Md Zesun Ahmed Mia, Malyaban Bal, Abhronil Sengupta
**发表:** 2026-01-01

## 摘要

自注意力机制的二次复杂度严重阻碍了 Transformer 模型在长序列上的应用。星形胶质细胞（astrocytes）是胶质细胞的一种，对生物记忆和突触调制至关重要。本文探索从星形胶质细胞中提取的计算原理——作为传统架构修改方法的补充方案来处理高效自注意力。提出 RMAAT（Recurrent Memory Augmentation via Astrocyte-inspired Transformer），一种受星形胶质细胞启发的记忆压缩和重放机制。

## 核心貢獻

1. **受星形胶质细胞启发的记忆压缩**: 首次将生物星形胶质细胞的计算原理引入 Transformer 记忆压缩
2. **RMAAT 架构**: 通过循环记忆增强机制压缩长上下文，将二次复杂度降为线性
3. **记忆重放机制**: 模仿生物记忆巩固过程，在压缩后选择性重放重要记忆
4. **突触调制启发**: 星形胶质细胞调节突触强度，RMAAT 通过可学习的门控机制选择性地加强或遗忘记忆

## 為什麼重要

长上下文 Transformer 的计算成本是端侧部署的主要障碍。RMAAT 从生物记忆系统汲取灵感，提供了一种不需要专门硬件加速的压缩方案，对移动端和边缘设备有直接价值。

## 與端側/移動端相關性

1. **线性复杂度**: 将二次复杂度降为线性，适合移动端 CPU 推理
2. **无需专用硬件**: 纯算法方案，不依赖 GPU 或 TPU
3. **生物启发**: 星形胶质细胞启发的记忆机制更节能，符合端侧低功耗需求
4. **可扩展记忆窗口**: 在有限硬件上实现更长上下文
