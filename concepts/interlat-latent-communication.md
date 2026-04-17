---
type: concept
tags: [multi-agent, latent-communication, agent协作, 隐空间通信, LLM推理优化]
related: [[agentcomm-semantic-communication]], [[clawmobile-agentic]], [[emommas-edge-negotiation]], [[chain-of-modality]]
sources:
  - url: https://arxiv.org/abs/2511.09149
    title: "Enabling Agents to Communicate Entirely in Latent Space"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Interlat: 让 Agent 在隐空间中直接通信

> 突破自然语言的离散瓶颈，Agent 之间直接传递连续隐状态，实现更高效的多 Agent 协作

## 核心问题

LLM Agent 的自然语言通信存在根本性瓶颈：Agent 必须将丰富的高维内部状态压缩为离散 token 序列（每个 token 仅约 15 bits），这严重限制了信息传输的深度和细微度。就像人类用语言描述一幅画时必然会丢失细节，Agent 之间的"对话"也存在信息损耗。

## 方法/架构

**Interlat** 提出让 Agent 直接传输 Transformer 的最后隐层状态而非 token 序列：

**核心机制**：
1. **隐状态提取**：Agent 在生成回复时，收集每个解码步骤的最后隐层状态 h_ℓ ∈ R^d，组成矩阵 H ∈ R^{L×d}
2. **通信适配器**：通过轻量级适配器处理隐状态，使其适配接收方 Agent 的架构
3. **隐空间传输**：使用特殊 token 标记隐通信的开始和结束
4. **跨模型兼容**：支持异构模型之间的隐空间通信（如 Qwen2.5-7B → LLaMA3.1-8B）

**关键带宽对比**：
- 自然语言：~15 bits/token
- 隐状态：~40K bits/hidden-state（**约 2600 倍带宽**）

## 实验结果

在 AlfWorld（多步规划任务）和 MATH（数学推理）上的评估：

| 方法 | 表现 | 通信效率 |
|------|------|---------|
| No-CoT（无通信） | 基线 | 最高 |
| Text（自然语言） | 中等 | 低 |
| **Interlat（隐空间）** | **最优** | 高 |
| CrossTask（跨任务隐） | 低于 Interlat | 高 |

**关键发现**：
- 隐空间通信在任务成功率上持续优于自然语言通信
- 隐通信能促进 Agent 的探索行为——隐状态携带的信息更丰富
- 跨模型通信（Qwen → LLaMA）仍然有效，证明隐空间表示具有通用性
- 隐空间压缩（reassembling）可以在大幅减少传输量的同时保持性能

**异构模型兼容性实验**：用 Qwen2.5-7B 的隐状态训练 LLaMA3.1-8B，性能仍优于自然语言基线，证明隐空间表示具有跨架构通用性。

## 关键洞察

**隐空间通信是多 Agent 系统的范式转变**：传统多 Agent 系统以自然语言为通信媒介（如 AutoGen、CrewAI），Interlat 证明了绕过这一瓶颈可以带来显著增益。

**对移动端的深层意义**：
- 隐空间通信的**带宽效率**直接适用于带宽受限的端-端或端-云 Agent 通信
- 异构模型兼容性意味着不同手机上的 Agent（可能使用不同模型）可以直接协作
- 压缩后的隐通信可以减少端侧多 Agent 系统的通信开销
- 但需要注意：隐空间通信牺牲了人类可读性，在调试和审计场景下需要回退到自然语言

## 为什么重要

Interlat 揭示了一个被忽视的方向：Agent 之间的通信不需要人类可读。对于手机端 AIOS：
- 多 Agent 协作（如一个 Agent 处理日程、一个处理消息）可以通过隐空间高效协调
- 端-云协同中，隐空间压缩可以减少数据传输量
- 异构兼容性为不同厂商设备上的 Agent 互通提供了理论基础
- 40K bits vs 15 bits 的带宽差异在移动网络环境下意义重大

## 关联
- [[agentcomm-semantic-communication]] — AgentComm 关注语义通信压缩，Interlat 更激进地完全绕过语言
- [[clawmobile-agentic]] — ClawMobile 的原生 Agent 架构可以集成隐空间通信层
- [[emommas-edge-negotiation]] — EmoMAS 的情感感知多 Agent 协商可以利用隐空间传递情感状态
- [[chain-of-modality]] — 多模态链式推理与隐空间通信在表示学习层面有共通之处
