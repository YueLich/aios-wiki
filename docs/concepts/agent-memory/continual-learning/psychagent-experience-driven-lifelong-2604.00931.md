---
title: "PsychAgent: An Experience-Driven Lifelong Learning Agent for Self-Evolving Psychological Counselor"
arXiv: 2604.00931
date: 2026-04-01
tags: [agent-memory, continual-learning, lifelong-learning, psychological-counseling]
reviewer: auto
source: arXiv
---

## 论文基本信息

- **作者**: Yutao Yang, Junsong Li, Qianjun Pan, Jie Zhou, Kai Chen
- **发表**: 2026-04-01
- **类别**: cs.AI

## 摘要

现有 AI 心理顾问主要依赖静态对话数据集的有监督微调，与人类专家通过临床实践和经验积累不断精进形成鲜明对比。本文提出 PsychAgent——一个经验驱动的终身学习智能体，旨在实现自我进化的心理辅导。PsychAgent 包含三个核心引擎：（1）记忆增强规划引擎（Memory-Augmented Planning Engine），为纵向多轮咨询交互设计，通过持久记忆和战略规划确保治疗连续性；（2）技能进化引擎（Skill Evolution Engine），从历史辅导轨迹中提取新的实践技能支持自我进化；（3）强化内化引擎（Reinforced Internalization Engine），通过拒绝微调将进化后的技能整合进模型。实验表明，PsychAgent 在所有评估维度上均优于 GPT-5.4、Gemini-3 等强基线模型，证明了终身学习可以提升多轮辅导响应的一致性和整体质量。

## 核心贡献

1. **记忆增强规划引擎**：为纵向多轮交互设计，确保治疗连续性，通过持久记忆维护来访者历史状态和战略规划
2. **技能进化引擎**：从历史咨询轨迹中自动提取新技能，支持智能体的持续自我进化
3. **强化内化引擎**：通过拒绝微调（rejection fine-tuning）将进化技能内化到模型权重
4. **首个经验驱动的心理辅导智能体终身学习框架**

## 为什么重要

当前心理辅导 AI 依赖静态数据集，无法从真实咨询经验中学习。PsychAgent 填补了这一空白，证明了终身学习可以让 AI 持续改进咨询质量，对多轮长期交互的 AI 系统具有广泛借鉴意义。

## 与移动端/端侧的相关性

论文主要面向云端部署的心理咨询场景，未特别关注端侧推理。不过其技能进化和拒绝微调机制对端侧个性化适应有参考价值。

---
*（参考文献待从原文补充）*
