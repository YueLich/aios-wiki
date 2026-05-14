---
title: "EconAI: Dynamic Persona Evolution and Memory-Aware Agents in Evolving Economic Environments"
arXiv: 2605.13762
date: 2026-05-13
tags: [agent-memory, memory-representation, multi-agent-simulation]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

EconAI 是一个将大型语言模型（LLM）应用于经济模拟的框架，通过经济情感索引（ESI）、记忆加权和动态决策机制解决短期优化与长期战略规划之间的张力。传统方法依赖静态数据驱动预测，无法整合由经济情感、市场波动和个人目标影响的自适应行为。EconAI 通过量化经济信念、调整历史数据影响力、链接工作-消费行为，实现更类人化的决策过程，智能体根据市场信号和长期目标调整行动。EconAI 是首个能在统一框架内模拟宏/微观经济环境和交互的 LLM 驱动模拟系统。

## 核心贡献

1. **经济情感索引（ESI）**：首次将经济信念量化，通过情感维度捕捉智能体对市场的心理预期
2. **记忆加权机制**：根据时间衰减和相关性动态调整历史数据对当前决策的影响力
3. **工作-消费行为链接**：将智能体的经济行为与其消费决策关联，提升模拟真实性
4. **动态决策机制**：结合短期市场信号和长期战略目标，支持多尺度推理

## 为什么重要

现有 LLM 智能体在经济模拟中存在两个关键缺陷：① 缺乏记忆机制导致无法利用历史经验；② 无法捕捉宏观经济与微观行为的双向反馈。EconAI 通过记忆加权解决了第一个问题，使智能体能根据历史数据的市场表现动态调整影响力权重。这是将记忆系统应用于经济决策的关键探索。

## 与移动端/端侧的相关性

- **记忆权重自适应**：根据端侧设备的计算资源动态调整记忆检索深度
- **轻量级情感索引**：ESI 机制简单，适合资源受限的端侧部署
- **实时决策支持**：记忆加权加速关键经济信号的识别，对需要快速响应的端侧场景有价值

## 参考文献

- Liu, A., et al. (2026). EconAI: Dynamic Persona Evolution and Memory-Aware Agents in Evolving Economic Environments. arXiv:2605.13762.
