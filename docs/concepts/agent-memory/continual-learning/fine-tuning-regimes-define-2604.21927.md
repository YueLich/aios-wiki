---
title: "Fine-Tuning Regimes Define Distinct Continual Learning Problems"
arXiv: 2604.21927
date: 2026-04-23
authors: ["Paul-Tiberiu Iordache", "Elena Burceanu"]
tags: [agent-memory, continual-learning, fine-tuning, evaluation-benchmark]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.21927
- **作者**: Paul-Tiberiu Iordache, Elena Burceanu
- **提交日期**: 2026-04-23
- **方向**: 持续学习 / 评估基准 / 微调机制

## 摘要（全文翻译）

持续学习（CL）研究模型如何在保留已学知识的同时顺序获取任务。尽管 CL 方法在基准测试方面取得了实质性进展，但比较评估通常**固定微调机制**。本文认为，由可训练参数子空间定义的微调机制本身就是**关键评估变量**。

本文形式化了一个框架，将微调机制与 CL 方法解耦，从而能够系统地研究两者的交互。

## 核心贡献

1. **微调机制作为评估变量**：揭示了微调 regime（哪些参数可训练）对 CL 性能的巨大影响
2. **解耦框架**：将微调机制与 CL 方法分离，允许独立评估两者
3. **系统性研究**：展示了不同微调 regime 导致本质上不同的 CL 问题

## 为什么重要

这篇论文提醒 CL 研究社区：基准测试中的"最优方法"可能只是对特定微调 regime 的过拟合。将微调机制作为独立变量引入评估，可以更公平地比较 CL 方法，并发现真正具有鲁棒性的解决方案。

## 与端侧/移动端的相关性

端侧持续学习通常受限于哪些参数可以更新（全量微调 vs. LoRA vs. 冻结骨干）。本文的发现对端侧 CL 基准测试设计有直接指导意义——需要在实际部署的微调 regime 下评估方法。
