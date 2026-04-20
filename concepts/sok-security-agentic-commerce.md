---
type: concept
tags: [Agent安全, 攻击向量, agentic commerce, 安全框架, 跨层防御]
related: [[gui-agent-privacy]], [[agent-persistent-identity]]
sources:
  - url: https://arxiv.org/abs/2604.15367
    title: "SoK: Security of Autonomous LLM Agents in Agentic Commerce"
    date: 2026-04-15
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# SoK: 自主 LLM Agent 在 Agentic Commerce 中的安全性

> 首个系统化知识框架，覆盖自主 LLM Agent 在商业场景中的 12 个跨层攻击向量（arXiv:2604.15367）

## 核心问题

OpenClaw 等自主 LLM Agent 正在将 agentic commerce 从人工监督辅助推向机器行为者——它们可以谈判、购买服务、管理数字资产、在链上和链下环境中执行交易。协议如 Trustless Agents (ERC-8004)、Agent Payments Protocol (AP2)、HTTP 402 支付协议 (x402)、Agent Commerce Protocol (ACP) 等使这成为可能，但也创建了现有安全框架无法充分捕获的攻击面。

## 方法/架构

**五维度统一安全框架**：

| 维度 | 威胁类型 | 示例 |
|------|---------|------|
| Agent 完整性 | 推理操纵、prompt 注入 | 恶意指令覆盖 agent 目标 |
| 交易授权 | 未授权交易、资金窃取 | 利用 agent 支付协议漏洞 |
| Agent 间信任 | 欺骗、中间人攻击 | 伪造 agent 身份进行欺诈 |
| 市场操纵 | 价格操纵、洗牌交易 | 多 agent 协同操控市场 |
| 合规监管 | 监管规避、洗钱 | 利用跨链/跨境复杂性 |

**12 个跨层攻击向量**：从推理层和工具层的失败传播到托管、结算、市场损害和合规暴露。

**分层防御架构**：覆盖 LLM 安全、协议设计、身份管理、市场监控和合规控制的协调防御。

## 关键洞察

1. **跨层问题**：agentic commerce 的安全本质上是跨层问题，需要 LLM 安全、协议设计、身份管理的协调控制
2. **故障传播链**：推理层和工具层的故障可传播到托管和结算层
3. **现有协议的安全空白**：当前 agent 支付协议（AP2、x402 等）存在授权缺口

## 为什么重要

对手机端 Agent 而言，随着 Agent 开始执行交易和管理敏感数据，安全问题变得至关重要。本框架为端侧 Agent 的安全设计提供了系统化的威胁模型——开发者可以据此评估自己的 Agent 系统在五个维度上的安全缺口。

## 关联
- [[gui-agent-privacy]] — GUI Agent 隐私保护可借鉴本框架的授权维度
- [[agent-persistent-identity]] — 持久化身份是解决 agent 间信任的基础
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧与云端工具调用的安全权衡
- [[subliminal-transfer-agent-distillation]] — 蒸馏安全是本框架未覆盖的新攻击面
