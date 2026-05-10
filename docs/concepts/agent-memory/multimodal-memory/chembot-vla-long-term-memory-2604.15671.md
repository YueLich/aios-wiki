---
title: "Long-Term Memory for VLA-based Agents in Open-World Task Execution"
arXiv: "2604.15671"
date: "2026-04-17"
tags: [agent-memory, multimodal-memory, embodied-memory, VLA]
reviewer: auto
source: arXiv ti: search
---

# Long-Term Memory for VLA-based Agents in Open-World Task Execution

## 论文基本信息

- **arXiv ID**: 2604.15671
- **发表日期**: 2026-04-17
- **作者**: Xu Huang, Weixin Mao, Yinhao Li, Hua Chen, Jiabao Zhao
- **类别**: cs.RO (Robotics)
- **来源**: arXiv ti: search

## 摘要

视觉-语言-动作（Vision-Language-Action, VLA）模型在具身决策中展现出重要潜力；然而，由于长时推理能力有限且缺乏持续经验积累，其在复杂化学实验室自动化等领域的应用仍受限制。现有框架通常将规划与执行解耦，往往无法将成功策略整合为可复用资产，导致多阶段协议中反复试错、效率低下。

本文提出 **ChemBot**，一个双层闭环框架，集成了自主 AI 智能体与进度感知的 VLA 模型（Skill-VLA），用于层次化任务分解与执行。ChemBot 利用**双层记忆架构**将成功轨迹整合为可检索资产，并通过 Model Context Protocol (MCP) 服务器协调子智能体和工具调用。针对 VLA 模型的固有局限，本文进一步实现了一种基于未来状态的异步推理机制，以缓解轨迹不连续性问题。在协作机器人上的广泛实验表明，ChemBot 在复杂长时化学实验中相较于现有 VLA 基线取得了更高的操作安全性和任务成功率。

## 核心贡献

1. **ChemBot 双层框架**：将任务分解（上层智能体）与执行控制（下层 VLA）解耦又协同
2. **双层记忆架构**：
   - 上层：任务进度记忆（progress-aware memory）
   - 下层：成功轨迹记忆（trajectory memory）
3. **MCP 服务器**：标准化子智能体和工具编排，降低记忆-执行耦合
4. **未来状态异步推理**：解决 VLA 模型固有的轨迹不连续问题

## 为什么重要

这是**首个将长期记忆机制引入 VLA 具身智能体**的系统性工作。传统 VLA 研究聚焦于单回合视觉-语言-动作映射，ChemBot 填补了"如何让 VLA 智能体从历史成功中持续学习"这一关键空白。双层记忆架构对移动端/端侧具身智能体有直接参考价值。

## 与移动端/端侧的相关性

虽然 ChemBot 聚焦于化学实验室机器人，但其双层记忆架构可迁移至移动端具身智能体：
- **端侧具身记忆**：手机/机器人需要从历史交互中学习用户习惯和物理环境规律
- **MCP 协议**：跨设备/跨场景的工具调用标准化，减少记忆-工具的耦合开销
- **轨迹压缩**：成功经验的高效存储和检索是端侧资源受限环境的关键

## 参考文献

（详见原论文）
