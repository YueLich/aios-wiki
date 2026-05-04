---
title: "Lifecycle-Aware Federated Continual Learning in Mobile Autonomous Systems"
arXiv: 2604.20745
date: 2026-04-22
authors: ["Beining Wu", "Jun Huang"]
tags: [agent-memory, continual-learning, federated-learning, mobile-robots, lifecycle]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.20745
- **作者**: Beining Wu, Jun Huang
- **提交日期**: 2026-04-22
- **方向**: 联邦持续学习 / 移动自主系统 / 生命周期感知

## 摘要（全文翻译）

联邦持续学习（FCL）允许分布式自主车队在扩展的任务生命周期中协作适应进化的地形类型。然而当前方法存在几个关键问题：使用统一保护策略，未考虑不同网络层对遗忘的敏感性差异；主要关注防止遗忘而忽视其他方面。

## 核心贡献

1. **生命周期感知的 FCL**：考虑移动系统在不同生命周期阶段的遗忘敏感性差异
2. **层级别保护策略**：不同网络层需要不同程度的防遗忘保护
3. **联邦协作适应**：多车队共享经验同时保护本地数据隐私

## 为什么重要

FCL 结合了联邦学习的隐私保护和持续学习的知识保留，但现有方法忽视了实际部署中的生命周期动态——不同任务阶段、不同地形类型对模型不同部分的影响不同。
