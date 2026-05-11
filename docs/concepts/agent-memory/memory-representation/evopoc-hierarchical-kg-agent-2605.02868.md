---
title: "EvoPoC: Automated Exploit Synthesis for DeFi Smart Contracts via Hierarchical Knowledge Graphs"
arXiv: "2605.02868"
date: "2026-05-04"
tags: [agent-memory, knowledge-graph, structured-memory, agentic-system, security]
reviewer: auto
source: arXiv API
---

## 摘要

Smart contract vulnerabilities in Decentralized Finance (DeFi) caused over billions of dollars losses every year. The security community faces a critical bottleneck: identifying a vulnerability is not the same as proving it is exploitable. Manual PoC (Proof of Concept) construction is prohibitively labor-intensive.

This paper proposes **EvoPoC**, a knowledge-driven agentic system for end-to-end contract vulnerability detection and exploit synthesis. The core insight is that **exploit synthesis is not a code generation task but a structured reasoning problem** that requires grounded knowledge of protocol semantics, failure root cause, and exploit primitives.

## 核心贡献

1. **层次知识图谱（Hierarchical Knowledge Graph, HKG）**：作为 LLM 引导多跳推理的结构化记忆（structured memory），组织以下知识：
   - 协议语义（protocol semantics）
   - 失败根本原因（failure root cause）
   - 利用原语（exploit primitives）

2. **两阶段验证框架**：超越代码合成，验证 exploit 可行性
   - **SMT 求解检查 exploit 路径可达性**（逻辑可行性）
   - **资产级状态模拟检查利润可实现性**（经济可行性）

3. **端到端 Agent 系统**：从检测到利用合成的完整自动化流程

## 关键洞察

**核心观点**：exploit synthesis 不是代码生成任务，而是结构化推理问题。

这与 Agent 记忆系统的设计直接相关——Agent 需要维护：
- **协议语义知识**（长期记忆）
- **当前漏洞上下文**（工作记忆）
- **利用原语库**（可检索的记忆片段）

**HKG 作为结构化记忆**：不同于平铺的文本记忆，HKG 提供分层组织的知识结构，支持多跳推理。

## 方法细节

### HKG 结构
层次结构组织 exploit 知识：
- 协议层（protocol semantics）
- 漏洞层（failure root cause）
- 原语层（exploit primitives）

### 两阶段验证
1. **SMT 求解**：exploit 路径的逻辑可行性
2. **状态模拟**：资产转移的经济可行性

### Agent 工作流
LLM 引导的多跳推理，基于 HKG 进行结构化推理

## 实验结果

- **数据集**：88 个真实 DeFi 攻击 + 72 个审计项目（2,573 份合约）
- **检测**：98% recall，0.9 F1-score
- **Exploit 成功率**：96.6% (ESR)
- **历史 exploit 再现**：85 个
- **挽回收入**：超过 $116.2M
- ** vs SOTA fuzzers**：ESR 高 5×，可挽回价值高 300×
- ** vs LLM-based exploit generator A1**：分别高 2× 和 8.5×

**Bug bounty 评估**：发现 16 个确认的 0-day 漏洞，帮助保护超过 $70.6M，赚取 $2,900 bounty

## 为什么重要

1. **HKG 作为 Agent 结构化记忆的范式**：分层组织的知识图谱比扁平记忆更适合复杂推理任务
2. **记忆 + 验证的闭环**：记忆不仅存储知识，还通过验证机制确保知识的正确性
3. **Agentic 系统的记忆需求**：大型任务需要维护多种类型的记忆（语义、上下文、原语），并能在推理时高效检索

## 与移动端/端侧相关性

- 端侧 Agent 在执行敏感操作（如金融交易）时需要维护安全相关的记忆
- HKG 的分层结构可用于端侧任务记忆的层次化组织
- 两阶段验证机制可作为端侧 Agent 决策的安全检查层

## 参考文献
