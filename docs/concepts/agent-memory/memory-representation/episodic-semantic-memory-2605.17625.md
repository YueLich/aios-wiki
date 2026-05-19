---
title: "Episodic-Semantic Memory Architecture for Long-Horizon Scientific Agents"
arXiv: 2605.17625
date: 2026-05-17
tags: [agent-memory, memory-representation, scientific-discovery, episodic-memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: Independent researcher

**核心问题**: 科学发现 agent 需要在长时序迭代中同时维护两类知识：情景记忆（Specific experiments tried, data observed）和语义记忆（General scientific principles, domain knowledge）。现有 agent 架构往往只关注其中一类，导致科学发现流程要么缺乏灵活性（纯规则系统），要么缺乏可解释性（纯黑盒神经网络）。

**方法**: 提出Episodic-Semantic Memory Architecture (ESMA)，在科学发现 agent 中同时维护两个互补的记忆系统，并设计专门的跨记忆推理机制。

### 双记忆架构

1. **情景记忆（Episodic Memory）**：以时间轴方式记录每次实验的输入、执行过程、观察结果，保留完整的实验轨迹
2. **语义记忆（Semantic Memory）**：以知识图谱方式组织科学领域知识，支持高层次推理和假设生成
3. **跨记忆推理**：当面临新科学问题时，同时检索情景记忆（"过去哪些类似实验失败了，原因是什么"）和语义记忆（"相关科学原理是什么"），综合形成新的实验假设

## 核心贡献

1. **首个科学发现 agent 的双记忆架构**：系统解决科学发现中灵活性与可解释性的矛盾
2. **情景-语义跨记忆检索机制**：设计专门的跨记忆查询和融合算法，而非简单拼接
3. **科学假设生成评估协议**：提出评估科学发现 agent 假设质量的指标（新颖性、可验证性、与现有知识的一致性）
4. **在化学合成任务上的验证**：在 12 个闭域化学合成任务中，ESMA 的假设成功率达 61%，显著高于单记忆 baseline

## 为什么重要

科学发现是 LLM agent 的重要应用场景，而科学发现的长时序性（需要多轮迭代实验）和知识复杂性（需要同时利用领域知识和实验经验）使其成为记忆系统的绝佳测试平台。ESMA 的双记忆设计对其他需要"经验+知识"融合的 agent 场景也有参考价值。

## 与移动端/端侧的相关性

端侧科学 agent（如移动端的化学合成助手、药物发现工具）需要同时在设备上维护领域知识（语义记忆）和用户个人实验记录（情景记忆）。ESMA 的双记忆分离设计适合端侧部署——语义记忆可以预加载、情景记忆需要加密保护。

## 参考文献

- Milosevic, N. (2026). Episodic-Semantic Memory Architecture for Long-Horizon Scientific Agents. arXiv:2605.17625.
