---
type: concept
tags: [multi-agent, belief-revision, agent-protocol, deliberation, conformity, social-pressure, formal-methods]
related: [[agent-persistent-identity]], [[clawmobile-agentic]], [[mga-memory-gui-agent]]
sources:
  - url: https://arxiv.org/abs/2604.15558
    title: "Preregistered Belief Revision Contracts"
    date: 2026-04-17
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# 预注册信念修正合约 (PBRC)

> 一种协议级机制，严格分离开放通信与可接纳的认知改变，防止多 Agent 系统中的"社会压力级联"。

## 核心问题

LLM 驱动的多 Agent 系统中，Agent 通过交换消息、批评和自信度报告进行协商。但实证研究发现三个严重问题：

1. **从众效应（Conformity）**：Agent 倾向于跟随多数意见而非独立判断
2. **同伴压力（Peer Pressure）**：高自信度的错误回答比低自信度的正确回答更有影响力
3. **"错误但确信"级联（Wrong-but-Sure Cascades）**：群体在走向错误答案时反而变得更加确信

根本问题是：**如何设计一个协议，在保持开放通信的同时，拒绝纯粹的社会压力作为信念改变的理由？**

## 方法/架构

PBRC 将信念修正合约定义为一个公开元组：

```
PBRC Contract = (Triggers, Revision Operators, Priority, Fallback)
```

- **Triggers（触发器）**：一阶证据条件，定义何时可以修正信念
- **Revision Operators（修正算子）**：允许的信念更新操作
- **Priority（优先级）**：冲突证据的处理规则
- **Fallback（回退策略）**：无新证据时的行为——关键：保持当前假设（argmax-preserving）

核心创新是 **证据门控（Evidence-Gating）**：将消息交换（通信层）与认知改变（信念层）严格分离。Agent 可以自由通信，但只有经过验证的证据令牌才能触发信念修正。

### 五项贡献

1. **协议语义**：形式化 PBRC 合约为带有见证证书和显式路由语义的结构
2. **社会安全保证**：证明在保守回退策略下，纯社会性轮次无法放大自信度，无法产生"错误但确信"级联（定理 1、2）
3. **规范形式与可审计性**：证明审计触发协议存在证据门控 PBRC 规范形式，任何顶层假设变更都可归因于具体的非空见证集（定理 7、17）
4. **令牌-轨迹分解**：对于令牌不变合约，受执行的信念动态仅依赖于验证令牌暴露轨迹（定理 10）
5. **鲁棒性分析**：形式化伪造、重放、共谋和遗漏对抗者；推导新鲜性和多证明鲁棒性条件

## 实验结果/关键数据

论文为理论工作，主要结果为形式化证明：

| 定理 | 内容 |
|------|------|
| 定理 1-2 | 保守回退下，社会性轮次无法放大自信度、无法产生级联 |
| 定理 7 | 审计触发协议存在规范形式，保留信念轨迹和审计记录 |
| 定理 10 | 令牌不变合约的信念动态仅依赖暴露轨迹 |
| 定理 13-14 | 泛洪传播下的轨迹等价刻画，含紧直径界 |
| 定理 17 | 任何顶层假设变更可归因于具体见证集 |

## 关键洞察

**1. "通信自由但信念受限"是正确的设计模式**

传统方法要么限制通信（减少信息量），要么允许无约束修正（导致级联）。PBRC 证明存在第三条路：让 Agent 自由交流，但严格控制什么能改变信念。

**2. 回退策略是安全性的核心**

"无新证据时保持当前假设"这个简单的策略，配合证据门控，就能保证社会性轮次不会产生错误级联。这对移动端 Agent 的多轮对话有直接指导意义。

**3. 可审计性对安全敏感场景至关重要**

PBRC 的见证集机制保证任何信念变更都可追踪到具体的验证令牌。对于手机端涉及隐私、金融、安全的 Agent 操作，这种可审计性是刚需。

**4. 拓扑无关性**

论文证明在泛洪传播下，信念动态仅依赖于令牌暴露轨迹，与消息传播的具体拓扑无关。这意味着 PBRC 可以适配不同的 Agent 通信架构（星型、P2P、层级）。

## 为什么重要

手机端 AIOS 中，多个 Agent 模块经常需要协作（如日历 Agent、消息 Agent、导航 Agent 协调规划行程）。PBRC 提供了：

- **防止错误决策级联**：一个 Agent 的错误不会通过社交压力传播到其他 Agent
- **轻量级形式化保证**：不需要训练/微调，纯协议层解决
- **可审计的决策链路**：用户可以追溯任何 Agent 决策的证据来源
- **适用于端侧低资源场景**：协议开销远小于模型级解决方案

## 关联

- [[agent-persistent-identity]] — PBRC 与 Agent 持久化身份的结合可实现长期一致的信念管理
- [[clawmobile-agentic]] — ClawMobile 多 Agent 架构可集成 PBRC 防止协作错误
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent 中，信念修正影响记忆写入策略
- [[edge-cloud-offloading]] — 端-云 Agent 协作中的信念同步问题
- [[agentic-ai-cpu-execution]] — PBRC 的协议开销对 CPU 执行流水线的影响
