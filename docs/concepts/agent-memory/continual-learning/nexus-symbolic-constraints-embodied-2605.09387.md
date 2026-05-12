---
title: "NEXUS: Continual Learning of Symbolic Constraints for Safe and Robust Embodied Planning"
arXiv: 2605.09387
date: 2026-05-10
tags: [agent-memory, continual-learning, embodied-ai, safety]
reviewer: auto
source: arXiv API
---

# NEXUS: Continual Learning of Symbolic Constraints for Safe and Robust Embodied Planning

## 论文信息

- **arXiv ID**: 2605.09387
- **发表日期**: 2026-05-10
- **作者**: Tiehan Cui, Peipei Liu, Yanxu Mao et al.
- **方向**: 持续学习 / 具身智能 / 安全
- **开源**: 待确认

## 摘要（英译中）

大语言模型（LLM）推动了具身智能的进步，但它们的内在概率不确定性与物理世界所需的严格决定论和可验证安全要求之间存在根本差距。

作者提出 **NEXUS**，一个用于具身智能体持续学习的模块化框架。与之前将符号 artifact 仅视为静态接口的工作不同，NEXUS 利用它们进行符号接地和知识演化。框架明确解耦物理可行性从安全规范：智能体的能力通过闭环执行反馈改进，而概率风险评估被接地到确定性硬约束以建立严格的事前防御。

在 SafeAgentBench 上的实验表明，NEXUS 实现了优越的任务成功率，同时有效拒绝不安全指令，表现出对对抗攻击的鲁棒防御，并通过知识积累逐步提高规划效率。

## 核心贡献

1. **符号约束持续学习**：通过闭环执行反馈持续改进能力
2. **概率-确定解耦**：将概率风险评估接地为确定性硬约束
3. **事前防御**：不等事后纠错，在行动前确保安全
4. **SafeAgentBench 基准**：首个具身规划安全评估基准
5. **知识积累**：规划效率随经验不断提升

## 关键洞察

> 框架明确解耦物理可行性从安全规范：能力通过闭环执行反馈改进，而概率风险评估被接地为确定性硬约束。

概率模型给出风险估计，但最终行动需要确定性约束——LLM 的概率不确定性与安全关键系统的确定性要求之间的鸿沟，通过将概率风险接地为硬约束来弥合。

## 为什么重要

- **安全关键系统**：首个将持续学习与具身安全结合的框架
- **实际部署**：NEXUS 代表了将 LLM 智能体部署到物理世界的实际路径
- **对抗鲁棒性**：明确防御对抗攻击，而非事后检测

## 与端侧/移动端的相关性

- 机器人/自动驾驶是端侧部署的直接场景
- 安全约束的确定性本质适合实时推理
- 持续学习使系统能从部署经验中不断改进

## 参考文献

- 原论文: https://arxiv.org/abs/2605.09387
