---
type: concept
tags: [Agent, 多Agent, 端侧计算, 智能手机, 逻辑编程, 去中心化, 无服务器]
related: [[clawmobile-agentic]], [[secagent-mobile-gui]], [[emommas-edge-negotiation]]
sources:
  - url: https://arxiv.org/abs/2602.06934
    title: "Implementing Grassroots Logic Programs with Multiagent Transition Systems and AI"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Grassroots Logic Programs（GLP）智能手机多 Agent 系统

> GLP 是一种为智能手机端无服务器、去中心化平台设计的多 Agent 并发逻辑编程语言，通过 Dart 实现工作站和手机端部署。

## 核心问题

传统的分布式系统依赖中心化服务器，而 grassroots 平台需要：
- 多个实例可独立运行，不依赖任何全局资源
- 实例间可自由合并形成更大的系统
- 目标架构是智能手机之间的 P2P 通信

## 方法/架构

### GLP 语言特性
- **线性逻辑 + futures/promises**: 变量分为 reader（future）和 writer（promise），赋值最多产生一次、消费最多一次
- **多向通信**: 额外的 reader/writer 支持丰富的多方向通信模式
- **单次出现不变量（SO Invariant）**: 保证变量的唯一性，这是正确性证明的基础

### 实现架构（madGLP）
- **本地变量对 + 全局链接**: 跨 Agent 的共享变量实现为两个本地变量对，通过 writer→reader 全局链接连接
- **无变量迁移**: 所有变量保留在原始 Agent 的解析器中，避免复杂的路由表更新
- **统一消息传递**: cold calls（无先验共享变量的 Agent 间消息）统一实现为发送到保留索引-0 共享变量的常规项

### 形式化验证
- dGLP（单 Agent）和 madGLP（多 Agent）的确定性操作语义已证明与抽象语义一致
- 关键引理：不相交替换交换性（来自 SO 不变量）+ 持久性

## 关键洞察

1. **AI 辅助实现**: Claude 被用作形式化规范的编程助手，从 dGLP 规范自动生成 Dart 实现——这本身就是 AI Agent 协作的案例
2. **设计迭代**: madGLP 经历了两次重大设计修订，均由实现困难驱动。初始设计使用路由表跟踪变量位置，变量迁移时更新复杂易错；最终方案完全消除变量迁移
3. **形式化优先**: 先证明正确性再实现，而非先实现再验证——这在端侧系统中尤为重要

## 为什么重要

- **去中心化移动 AI**: GLP 提供了在智能手机上构建无服务器多 Agent 系统的形式化基础，与当前端侧 AI Agent 的发展趋势高度契合
- **形式化保证**: 对于移动安全和隐私场景，形式化验证的正确性保证比 ad-hoc 实现更有价值
- **P2P 架构**: 不依赖云端服务器的 P2P 通信模式，天然适合隐私敏感场景

## 关联

- [[clawmobile-agentic]] — 另一个手机端 Agent 系统架构，原生化设计
- [[secagent-mobile-gui]] — 移动端 GUI Agent 的感知编码
- [[emommas-edge-negotiation]] — 边缘多 Agent 协商系统
