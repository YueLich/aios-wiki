---
title: "Robo-Cortex: A Self-Evolving Embodied Agent via Dual-Grain Cognitive Memory and Autonomous Knowledge Induction"
arXiv: 2605.18729
date: 2026-05-18
tags: [agent-memory, embodied-memory, continual-learning, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: Nara Institute of Science and Technology (NAIST) 等

**核心问题**: 真实世界 embodied agent 在未知环境中导航时面临"经验性失忆症"（experiential amnesia）——无法将从先前经验中获得的知识迁移到新环境中。

**方法**: 提出 Robo-Cortex，一个自进化 embodied agent，通过双粒度认知记忆（dual-grain cognitive memory）和自主知识归纳实现持续适应。

### 双粒度记忆架构

1. **粗粒度语义记忆（Coarse-grained Semantic Memory）**：存储从多次经验中归纳的高层语义知识，例如"障碍物类型"、"空间拓扑关系"等，可跨任务复用
2. **细粒度情景记忆（Fine-grained Episodic Memory）**：按时间顺序记录 agent 与环境的交互轨迹，保留丰富的感官细节，支持精确回溯

双粒度协同机制允许 agent 在新环境中快速检索相关语义知识，同时通过情景记忆回填具体执行细节。

### 自主知识归纳

Robo-Cortex 能够在无需人工干预的情况下，从连续经验流中自动归纳新知识，并将其整合到语义记忆中，实现"边做边学"。

## 核心贡献

1. **双粒度认知记忆架构**：首次提出结合粗粒度语义知识与细粒度情景记忆的 embodied agent 框架
2. **自进化机制**：agent 能在运行中自主扩展知识，无需人工标注或预训练重置
3. **跨环境泛化**：在多个 3D 导航基准（Habitat-Matterport、Gibson）上显著优于基线，尤其在零样本迁移场景中
4. **神经符号混合推理**：知识归纳模块同时利用神经网络学习能力和符号推理的可解释性

## 为什么重要

现有的 embodied memory 系统要么只存储粗粒度语义（缺乏细节），要么只记录情景（缺乏泛化）。Robo-Cortex 通过双粒度架构解决了这一两难问题。更重要的是，其自进化能力使 agent 能够在真实世界的长时序部署中持续改进，而非"一次训练、部署即冻结"。

## 与移动端/端侧的相关性

该工作对端侧部署有重要参考价值：双粒度架构允许将粗粒度语义知识缓存在本地知识库中，而细粒度情景记忆可以按需压缩存储。论文的自进化特性意味着智能体能够在设备上持续适应环境而无需云端更新，这对边缘计算和自主导航设备尤其有意义。

## 参考文献

- Chan, N.T., et al. (2026). Robo-Cortex: A Self-Evolving Embodied Agent via Dual-Grain Cognitive Memory and Autonomous Knowledge Induction. arXiv:2605.18729.
