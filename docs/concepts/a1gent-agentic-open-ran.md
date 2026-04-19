---
type: concept
tags: [open-ran, edge-computing, llm-agent, intent-driven, mobile-network, 5g, agentic, 自组网]
related: [[edge-cloud-offloading]], [[mcp-deployment-patterns]], [[emommas-edge-negotiation]], [[on-device-vs-cloud-agentic-tool-calling]]
sources:
  - url: https://arxiv.org/abs/2604.13384
    title: "Agentic Open RAN: A Deterministic and Auditable Framework for Intent-Driven Radio Control"
    date: 2026-04-15
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# A1gent: 面向 Open RAN 的可审计 Agent 控制框架

> 用 LLM Agent 实现意图驱动的无线网络控制，同时保持近实时执行的确定性和可审计性

## 核心问题

移动网络正向 AI 原生运营演进——运营商希望用自然语言表达"网络应该达到什么目标"，而非手动配置每个控制循环。O-RAN 架构通过 A1/E2/O1 分层接口提供了这种可能性，但存在两个根本性缺口：

1. **推理与执行的矛盾**：如何在注入意图级推理的同时，不破坏近实时（near-RT）控制环路的确定性保证？
2. **可审计性**：如何让 LLM 驱动的推理可追溯、可回放、有明确的作用域？

## 方法/架构

提出 **A1gent**，一个分层的 agentic 控制栈：

### 架构概览
```
非 RT 层 (rApp)          近 RT 层 (xApps)
┌─────────────────┐     ┌──────────────────┐
│ LLM + IaC       │     │ QoE Firefighter  │
│ 意图→A1 策略翻译 │────→│ Load Balancer    │
│ 策略选择 (L1)    │     │ Energy Saver     │
│ 目标混合 (L2)    │     └──────────────────┘
└─────────────────┘              │
                          E2 (移动性/负载)
                          O1 (能效 via SMO)
```

### 关键设计决策

**推理-执行分离**：
- **非 RT rApp**：LLM 负责意图理解和策略生成，输出类型化的 A1 策略实例
- **近 RT xApps**：固定频率（1 Hz）控制循环，使用最近发布的 A1 策略，永不阻塞在 rApp 上
- **IaC 守护栏**：LLM 输出必须通过基础设施即代码定义的约束检查（clamp、budget、cadence）

**三层 Agent 协调**：
1. **QoE Firefighter**：通过 E2SM-MHO 管理切换，保护用户体验
2. **Load Balancer**：通过 E2SM-RC+MHO 优化 PRB 分配，平衡负载
3. **Energy Saver**：通过 O1/SMO 管理基站休眠/唤醒

**安全机制**：
- 固定优先级 Action Merger 解决 xApp 间冲突
- 编码护栏（guardrails）限制 LLM 输出范围
- 每个 A1 策略实例有明确的类型约束

## 实验结果

### 场景设置
- **拓扑**：3 扇区 × 3 站点宏蜂窝网格（9 cells），X2 连接
- **仿真器**：扩展的 ns3-oran
- **场景**：3 阶段意图切换（Normal → Emergency → Recovery）

### 核心发现

| 指标 | A1gent | 基线 |
|------|--------|------|
| 意图翻译 | LLM 自动生成类型化 A1 策略 | 手工配置 |
| 执行确定性 | 1 Hz 固定频率，永不阻塞 | 依赖 LLM 响应时间 |
| 多阶段适应 | 自动切换 Normal/Emergency/Recovery | 需要人工干预 |
| 可审计性 | 完整的 IaC 策略日志 + E2/O1 行动追踪 | 有限 |

### 关键实验发现
1. **Phase-aware 意图有效**：运营商可表达"Normal 保持均衡；Emergency 保护弱势用户；Recovery 恢复节能"，A1gent 自动翻译为对应策略
2. **LLM 超时安全**：当 LLM prompt 超时时，启发式混合策略提供降级保证
3. **E2/O1 分离合理**：移动性和负载控制走 E2（高频），能效走 O1/SMO（低频），符合实际部署约束

## 关键洞察

1. **确定性与智能的平衡点在策略层而非执行层**：LLM 的非确定性被"关在"A1 策略生成阶段，执行层完全确定。这与 Agent 在移动端的设计哲学一致——推理离线化，执行在线化
2. **IaC 作为 LLM 的安全网**：不是让 LLM 自由输出，而是通过预定义的策略目录和约束来限界 LLM 的输出空间
3. **MCP 范式的 RAN 实现**：Dual-MCP 工作的 tool-centric、human-in-the-loop 规划架构影响了 A1gent 的审计设计

## 为什么重要

对于移动 AIOS 生态：
- **网络层 Agent 化**：移动网络基础设施的 Agent 化意味着端侧设备将与更智能的网络协同
- **意图驱动接口**：类似 Android Intent 系统在应用层的作用，A1gent 在网络层实现了意图驱动的控制
- **边缘-云协同新模式**：推理（LLM）在云端/非 RT 层，执行在边缘/近 RT 层——这种分离模式可推广到其他端云协同场景
- **对 MiniCPM/端侧 Agent 的启示**：当端侧 Agent 需要调用网络资源时，背后的网络控制层可能就是 A1gent 这样的 Agent 系统

## 关联
- [[edge-cloud-offloading]] — 边缘-云协同卸载
- [[mcp-deployment-patterns]] — MCP 部署模式与 Agent 工具调用
- [[emommas-edge-negotiation]] — 边缘多 Agent 协商
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端 Agent 工具调用对比
