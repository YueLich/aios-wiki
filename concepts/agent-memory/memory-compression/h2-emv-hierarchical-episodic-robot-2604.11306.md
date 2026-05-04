---
title: "Learning to Forget -- Hierarchical Episodic Memory for Lifelong Robot Deployment"
arXiv: 2604.11306
date: 2026-04-13
tags: [agent-memory, memory-compression, episodic-memory, robot, selective-forgetting]
reviewer: auto
source: arXiv RSS/API
---

# Learning to Forget: Hierarchical Episodic Memory for Lifelong Robot Deployment

## 论文基本信息

- **arXiv ID**: 2604.11306
- **作者**: (From paper)
- **提交日期**: 2026-04-13
- **类别**: cs.RO, cs.AI, cs.CL

## 摘要

Robots must verbalize their past experiences when users ask "Where did you put my keys?" or "Why did the task fail?" Yet maintaining life-long episodic memory (EM) from continuous multimodal perception quickly exceeds storage limits and makes real-time query impractical, calling for selective forgetting that adapts to users' notions of relevance. We present H$^2$-EMV, a framework enabling humanoids to learn what to remember through user interaction. Our approach incrementally constructs hierarchical EM, selectively forgets using language-model-based relevance estimation conditioned on learned natural-language rules, and updates these rules given user feedback about forgotten details. Evaluations on simulated household tasks and 20.5-hour-long real-world recordings from ARMAR-7 demonstrate that H$^2$-EMV maintains question-answering accuracy while reducing memory size by 45% and query-time compute by 35%. Critically, performance improves over time -- accuracy increases 70% in second-round queries by adapting to user-specific priorities -- demonstrating that learned forgetting enables scalable, personalized EM for long-term human-robot collaboration.

## 核心贡献

1. **H²-EMV 框架**：学习性遗忘的分层情景记忆框架，通过用户交互学习记忆优先级。
2. **基于 LM 的相关性估计**：使用语言模型估计记忆相关性，结合学习的自然语言规则进行选择性遗忘。
3. **用户反馈更新机制**：用户可反馈「遗忘的细节」，系统据此更新遗忘规则，实现个性化。
4. **显著效率提升**：内存减少45%，查询计算减少35%，第二轮查询准确率提升70%。

## 为什么重要

这是首篇将「学习遗忘」作为主动能力而非被动衰减的研究。H²-EMV 证明：(1) 选择性遗忘 + 用户反馈可以持续提升个性化记忆质量；(2) 遗忘不是简单删除，而是学习用户相关性感知的自适应过程。70%的第二轮查询准确率提升说明遗忘机制实际上是学习过程的一部分。对移动端/端侧的意义：存储受限的移动设备需要智能遗忘来管理记忆规模。

## 与移动端/端侧相关性

- 移动端 Assistant（如手机语音助手）需要回答「我上周在哪里买过咖啡？」等长时记忆问题
- 用户反馈驱动的遗忘机制适合个性化移动助手——不同用户对「重要」记忆的定义不同
- 45%内存减少和35%查询计算减少对资源受限的移动端至关重要
- 多模态情景记忆与移动端传感器数据（摄像头、GPS等）自然对齐
