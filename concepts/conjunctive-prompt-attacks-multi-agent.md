---
type: concept
tags: [multi-agent, security, prompt-attack, adversarial, agent-reliability]
related: [[diversity-collapse-multi-agent]], [[semantic-consensus-multi-agent]], [[gui-agent-focused-distraction-attack]], [[self-improving-error-diagnosis-multi-agent]]
sources:
  - url: https://arxiv.org/abs/2604.16543
    title: "Conjunctive Prompt Attacks in Multi-Agent LLM Systems"
    date: 2026-04-18
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# 多 Agent 系统的合取式提示攻击

> 多 Agent LLM 系统面临一种新型攻击模式：攻击者只需入侵一个子 Agent，就能通过合取式提示（Conjunctive Prompt）将恶意载荷扩散到整个协作链路。这对手机端多 Agent 架构的安全设计具有直接警示意义。

## 核心问题

随着 LLM 从单一聊天模型演进为多 Agent 协作系统，安全攻击面也发生了根本性变化。传统提示注入攻击针对单一模型，但在多 Agent 系统中，攻击者可以利用 Agent 间的消息传递链路，通过**合取式攻击**（将恶意指令拆分嵌入多个子 Agent 的输出中）来绕过单点安全检测。

典型的多 Agent 流水线包含：用户 → 编排 Agent → 专业子 Agent（如航班查询、酒店预订）→ 外部工具/数据库。每个子 Agent 都可能被入侵，而恶意内容可以沿着通信链传播，最终影响编排 Agent 的决策。

## 方法/架构

论文提出了多 Agent LLM 系统的安全分析框架，主要发现：

1. **攻击面分解**：将多 Agent 系统的攻击面分为三个层级：
   - **输入层**：用户提示直接注入
   - **Agent 间通信层**：子 Agent 输出中嵌入恶意载荷（最危险）
   - **工具调用层**：通过外部工具返回值注入

2. **合取式攻击模式**：攻击者不需要在单一消息中包含完整恶意指令，而是将攻击载荷分散到多个 Agent 的正常输出中，每个片段看起来无害，但组合后产生恶意效果。

3. **黑盒威胁模型**：攻击者无需了解系统内部结构，仅通过与系统的有限交互即可构造有效攻击。

## 实验结果

论文在多个多 Agent 架构上评估了合取式攻击的有效性：
- 与传统单 Agent 提示注入相比，合取式攻击在多 Agent 系统中的**成功率显著更高**
- 即使每个子 Agent 都经过安全对齐，攻击载荷通过组合仍能绕过检测
- 现有的单 Agent 防御机制（如输入过滤、输出审查）在多 Agent 场景下效果有限

## 关键洞察

- **涌现性漏洞**：多 Agent 系统的安全漏洞不是单个 Agent 漏洞的简单叠加，而是从 Agent 间交互中涌现的新型威胁。这与分布式系统中的"组合安全"问题类似。
- **防御不能简单叠加**：为每个 Agent 单独部署安全检测不足以防御合取式攻击，需要从系统层面设计防御机制。
- **手机端的放大效应**：在手机端多 Agent 系统中（如语音助手调用多个 App Agent），攻击面更加分散，且用户难以察觉跨 Agent 的异常行为。

## 为什么重要

手机端 AIOS 正在走向多 Agent 架构——系统级 Agent 编排多个专业 App Agent 完成复杂任务。这篇论文揭示了一个关键安全盲区：**当多个看似安全的 Agent 协作时，攻击者可以通过组合方式突破整体防线**。对手机端 Agent 系统设计而言，这意味着：
- Agent 间通信需要加密和完整性验证
- 需要系统级的行为监控，而非仅依赖单 Agent 的安全审查
- 用户需要对跨 Agent 操作有透明的知情权

## 关联

- [[diversity-collapse-multi-agent]] — 多 Agent 系统的另一结构性风险：多样性坍塌
- [[semantic-consensus-multi-agent]] — 企业级多 Agent 冲突检测与解决机制
- [[gui-agent-focused-distraction-attack]] — 另一种针对 Agent 的注意力分散攻击
- [[self-improving-error-diagnosis-multi-agent]] — 提高多 Agent 系统可靠性的自改进方法
- [[agent-persistent-identity]] — Agent 身份管理与安全信任链
