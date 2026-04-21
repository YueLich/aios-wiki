---
type: concept
tags: [推理优化, agentic-ai, power-efficiency, inference-serving, 功耗优化, 边缘推理]
related: [[edgeflow-cold-start]], [[on-device-inference-memory-pressure]], [[llamacpp]], [[agent-persistent-identity]]
sources:
  - url: https://arxiv.org/abs/2604.16682
    title: "KAIROS: Stateful, Context-Aware Power-Efficient Agentic Inference Serving"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# KAIROS: 有状态上下文感知的 Agentic 推理功耗优化

> 专为 Agentic AI 推理工作流设计的功耗优化系统，利用 Agent 上下文作为一级控制信号，联合管理 GPU 频率和批处理，解决传统单轮 LLM 功耗方案在多轮工具交互场景下的失效问题。

## 核心问题

随着 Agentic AI 成为主要的推理工作负载类别，功耗已成为 AI 推理的核心瓶颈。然而，现有的功耗管理技术几乎完全聚焦于**单轮 LLM 推理服务**，而 Agentic 推理的行为模式根本不同：

1. **长生命周期上下文**：每个请求携带在多次工具交错轮次中演化的长上下文（KV Cache 持续增长）
2. **频率-内存压力悖论**：降低 GPU 频率会将系统推入"抖动(thrashing)"状态——内存压力急剧恶化，同时性能和能效双双下降
3. **传统 DVFS 策略失效**：单轮推理中"降频省电"的直觉在 Agentic 场景下适得其反

## 方法/架构

KAIROS 提出**上下文感知功耗优化**，核心创新：

### Agent 上下文作为控制信号
- 将 Agent 的多轮交互上下文（工具调用历史、KV Cache 状态、轮次间隔）作为功耗调度的一级信号
- 区分"活跃推理阶段"和"等待工具响应阶段"，分别采用不同频率策略

### 联合 GPU 频率 + 批处理管理
- 不单独调整频率或批大小，而是联合优化
- 在工具等待窗口中主动降频并清理内存
- 在推理恢复前预提升频率，避免冷启动延迟

### 状态感知调度
- 跟踪每个 Agent 会话的上下文演化
- 预测下一轮的计算需求（基于历史模式）
- 避免在上下文密集阶段降频导致的抖动

## 实验结果

论文分析揭示了 Agentic 推理与传统单轮推理的关键差异：
- Agentic 工作负载的**内存访问模式**与单轮推理截然不同——长 KV Cache 导致内存带宽成为瓶颈
- 传统降频策略在 Agentic 场景下可能导致 **2-3x 的性能退化**（因内存抖动）
- KAIROS 通过上下文感知调度，在保持服务质量的同时显著降低功耗

## 关键洞察

1. **Agentic ≠ 单轮推理的串行拼接**：多轮交互中的上下文演化创造了一个全新的优化维度，传统推理优化忽视了这一点
2. **功耗优化需要端到端视角**：单独优化 GPU 频率或批处理无法解决 Agentic 场景的根本问题——需要联合调度
3. **对移动端的启示**：手机端 Agent（如 [[secagent-mobile-gui]]、[[clawmobile-agentic]]）面临更严峻的功耗约束，KAIROS 的思路可迁移到移动端 NPU/GPU 调度

## 为什么重要

KAIROS 直接解决了手机端 AIOS 的核心挑战之一——**Agent 推理的功耗问题**。当前手机端 Agent（如语音助手、GUI Agent）需要在多轮交互中保持低功耗，而 KAIROS 的上下文感知调度思路为：
- **端侧 Agent 功耗优化**提供了新的设计范式
- **NPU/GPU 联合调度**提供了理论基础
- **用户体验与续航平衡**提供了解决路径

## 关联
- [[edgeflow-cold-start]] — 冷启动优化与 KAIROS 的频率预提升互补
- [[on-device-inference-memory-pressure]] — 内存压力管理是 KAIROS 的核心挑战之一
- [[llamacpp]] — llama.cpp 推理引擎可集成 KAIROS 的功耗调度策略
- [[agent-persistent-identity]] — Agent 持久化身份产生的长上下文正是 KAIROS 要优化的场景
- [[secagent-mobile-gui]] — 移动端 GUI Agent 的多轮交互可直接受益于 KAIROS
