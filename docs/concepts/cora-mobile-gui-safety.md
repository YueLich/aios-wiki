---
type: concept
tags: [Agent, 安全, 移动GUI, 对抗鲁棒性, 风险控制]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[turing-test-mobile-gui]], [[gui-agent-privacy]]
sources:
  - url: https://arxiv.org/abs/2604.09155
    title: "CORA: Conformal Risk-Controlled Agents for Safeguarded Mobile GUI Automation"
    date: 2026-04-10
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# CORA: 基于共形风险控制的安全移动 GUI Agent 框架

> 在 VLM 驱动的 GUI Agent 与用户之间插入统计保障层，通过共形风险控制提供可调安全预算。

## 核心问题

VLM 驱动的 GUI Agent 正从被动辅助走向自主操作。但无约束的动作空间暴露用户于严重且不可逆的财务、隐私或社交危害。现有安全措施（提示工程、脆弱启发式、VLM-as-critic）缺乏形式化验证和用户可调的安全保障。

## 方法/架构

### CORA 三组件架构

1. **Guardian（守护者模型）**：为每个提议步骤估计条件风险。利用**共形风险控制（Conformal Risk Control）**校准执行/拒绝边界，满足用户指定的风险预算 α。

2. **Diagnostician（诊断者模型）**：对被拒绝的动作执行多模态推理，推荐干预措施（确认、反思、或中止），最小化用户负担。

3. **Goal-Lock 机制**：将评估锚定到已澄清的、冻结的用户意图上，抵抗视觉注入攻击。

### 关键设计
- **后策略、前动作**的安全框架：不修改 Agent 的策略，而是在执行前拦截
- **选择性动作执行**：将安全重新定义为选择性执行问题
- 用户可调风险预算：α 参数控制安全与体验的权衡

## 实验结果

CORA 引入了 **Phone-Harm** 基准，包含真实场景下的步骤级危害标签：
- CORA 改善了安全性-帮助性-中断性 Pareto 前沿
- 在多种 baseline 上验证有效性
- 统计保障使得安全不再是"感觉上安全"，而是"数学上可控"

## 关键洞察

1. **共形风险控制是 Game Changer**：传统方法用启发式阈值判断安全性，阈值在不同场景下波动剧烈。共形校准提供统计保障——用户指定风险预算，系统保证有害动作执行概率不超过该预算。

2. **Goal-Lock 抵抗视觉注入**：攻击者可以在 App 界面注入误导性视觉元素诱导 Agent 执行危险操作。Goal-Lock 将用户意图冻结，即使界面被篡改也不会偏离原定目标。

3. **安全与体验的 Pareto 最优**：不是简单拒绝所有有风险的操作，而是在安全性和用户体验之间找最优平衡。

## 为什么重要

端侧 AI Agent 安全是规模化部署的瓶颈：没有形式化安全保障，用户不敢让 Agent 操作银行 App。EU AI Act 等法规要求高风险 AI 系统提供可证明的安全性。CORA 提供了将学术安全理论落地到移动 Agent 的实用路径。

## 关联
- [[secagent-mobile-gui]] — SecAgent 关注效率，CORA 关注安全
- [[pspa-bench-gui-agent]] — CORA 评估需要类似的个性化 GUI 基准
- [[turing-test-mobile-gui]] — Agent 安全性是"Humanization"的前提
- [[gui-agent-privacy]] — 隐私保护与安全控制是 Agent 信任的两个维度
