---
title: "XSkill: Continual Learning from Experience and Skills in Multimodal Agents"
arXiv: 2603.12056
date: 2026-03-12
authors: ["Guanyu Jiang", "Zhaochen Su", "Xiaoye Qu", "Yi R. Fung"]
tags: [agent-memory, continual-learning, multimodal-agents, skill-learning, experience-replay]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2603.12056
- **发表日期**: 2026-03-12
- **作者**: Guanyu Jiang, Zhaochen Su, Xiaoye Qu, Yi R. Fung
- **方向**: 持续学习（多模态 Agent 的经验与技能双流学习）

## 摘要

**背景**：多模态 Agent 能使用多样化工具处理复杂推理任务，但存在工具使用效率低和编排不灵活的问题。核心挑战是如何在无参数更新的情况下让 Agent 不断改进。

**方法**：XSkill 提出双流框架，从多路径 rollouts 中通过视觉锚定的总结和跨路径批评来提取和整合经验和技能。框架识别两种互补的知识形式：经验（提供工具选择和决策的动作级简洁指导）和技能（提供规划和工具使用任务级结构化指导）。

**实验结果**：在 5 个基准测试、4 个骨干模型上持续大幅超越仅工具和仅学习的基线方法，并展现优越的零样本泛化能力。

## 核心贡献

1. **双流知识框架**：首次明确区分并整合经验（experience）和技能（skill）两种互补知识形式
2. **视觉锚定的知识提取**：从视觉观察中提取和整合知识，保证知识与环境的 grounding
3. **持续学习循环**：推理时检索并适应知识，同时将使用历史反馈到积累阶段形成闭环
4. **跨域泛化**：5 个基准测试、4 个骨干模型均有效，零样本泛化能力强

## 为什么重要

XSkill 解决了多模态 Agent 的核心瓶颈：

- **无遗忘的持续学习**：不需要参数更新，避免了灾难性遗忘，同时保持对新任务的适应能力
- **工具使用优化**：解决了"工具调用效率低"的问题——这是当前 Agent 系统的普遍痛点
- **理论与实践结合**：从真实多模态 Agent 轨迹中学习，而非模拟数据

## 与端侧/移动端的相关性

对端侧多模态 Agent 有直接影响：

- **本地工具学习**：工具使用经验和技能可本地存储，无需云端同步
- **隐私保护**：学习来源是 Agent 自身轨迹，数据不外流
- **移动端多模态**：适合手机/AR 眼镜上的视觉推理 Agent，通过持续学习改进本地任务执行

## 参考文献

- arXiv: 2603.12056 | https://arxiv.org/abs/2603.12056
