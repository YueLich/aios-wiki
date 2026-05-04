---
title: "GR4CIL: Gap-compensated Routing for CLIP-based Class Incremental Learning"
arXiv: 2604.17822
date: 2026-04-20
authors: ["Tianqi Wang", "Jingcai Guo"]
tags: [agent-memory, continual-learning, class-incremental, CLIP, routing]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.17822
- **作者**: Tianqi Wang, Jingcai Guo
- **提交日期**: 2026-04-20
- **方向**: 类增量学习 / CLIP / 路由机制

## 摘要（全文翻译）

类增量学习（CIL）旨在持续获取新类别同时保留已学知识。CLIP 模型因强大泛化能力在 CIL 上展示出很强潜力。然而现有方法仍面临两个关键挑战：共享参数适应容易导致旧知识漂移，任务识别仍然困难。

## 核心贡献

1. **间隙补偿路由**：为 CLIP 基础 CIL 设计的路由机制，补偿特征空间中的间隔
2. **解决双重挑战**：同时应对知识漂移和任务识别问题
3. **CLIP 泛化能力的利用**：利用 CLIP 的零样本泛化能力辅助新类别学习

## 为什么重要

CLIP 在视觉-语言预训练中展示的强大泛化能力为 CIL 提供了新思路，但这篇论文指出现有方法未能充分利用这一优势——需要专门设计的路由机制来解决 CLIP 特征空间与 CIL 需求之间的 mismatch。
