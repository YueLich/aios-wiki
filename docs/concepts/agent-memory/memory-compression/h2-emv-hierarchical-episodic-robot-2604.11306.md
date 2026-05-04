---
title: "Learning to Forget: Hierarchical Episodic Memory for Lifelong Robot Deployment"
arXiv: 2604.11306
date: 2026-04-13
authors: ["Leonard Bärmann", "Joana Plewnia", "Alex Waibel", "Tamim Asfour"]
tags: [agent-memory, memory-compression, episodic-memory, robot, selective-forgetting, lifelong-learning]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.11306
- **作者**: Leonard Bärmann, Joana Plewnia, Alex Waibel, Tamim Asfour
- **提交日期**: 2026-04-13
- **方向**: 情景记忆 / 选择性遗忘 / 机器人

## 摘要（全文翻译）

机器人必须能够回答用户的问题（如"我的钥匙放哪了？"或"任务为什么失败了？"），这要求它们具备长期情景记忆（episodic memory, EM）。然而，从连续多模态感知中维护终身 EM 很快会超出存储限制，使实时查询变得不切实际，因此需要**适应用户相关性概念的选择性遗忘**。

本文提出 **H²-EMV**，一个让人形机器人通过用户交互学习"该记住什么"的框架。方法逐步构建层次化 EM，使用基于语言模型的相关性估计进行选择性遗忘，并以用户反馈更新遗忘规则。在模拟家庭任务和 ARMAR-7 机器人 20.5 小时真实世界记录的评估表明，H²-EMV 在维持问答准确率的同时，**减少 45% 记忆大小和 35% 查询计算量**。关键的是，性能随时间提升——第二轮对话中准确率提升 70%。

## 核心贡献

1. **层次化情景记忆（H²-EMV）**：将多模态感知逐步构建为层次化情景记忆表示
2. **用户相关的选择性遗忘**：遗忘规则由用户反馈调整，使记忆优先保留用户关心的内容
3. **遗忘-学习闭环**：用户反馈触发遗忘规则的迭代更新，形成学习闭环
4. **真实世界验证**：在 20.5 小时真实记录上验证，而非仅模拟数据

## 为什么重要

这是真正解决"机器人如何决定遗忘什么"的论文——不是固定规则，而是通过用户交互学习遗忘标准。45% 记忆压缩 + 35% 计算减少 + 随时间提升的准确率，这是一个在保持实用性上有显著改进的系统。

## 与端侧/移动端的相关性

H²-EMV 的层次化 EM 结构对移动端记忆系统有参考价值。设备上的机器人或助手需要从连续感知中构建情景记忆，同时管理存储和计算约束。用户反馈驱动的遗忘规则可以在设备端实现，无需云端 LLM。
