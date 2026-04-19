---
type: concept
tags: [Agent, 调试, 可观测性, 故障定位, 多Agent, 微软]
related: [[agent-persistent-identity]], [[gui-agent-privacy]], [[exectune-guide-core-policy]], [[planning-failure-escalation]], [[agent-system-reliability]]
sources:
  - url: https://www.microsoft.com/en-us/research/blog/systematic-debugging-for-ai-agents-introducing-the-agentrx-framework/
    title: "Systematic debugging for AI agents: Introducing the AgentRx framework"
    date: 2026-03-12
    reliability: high
  - url: https://github.com/microsoft/AgentRx
    title: "AgentRx GitHub Repository"
    date: 2026-03-12
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# AgentRx: AI Agent 系统化调试框架

> 通过从工具模式和领域策略中合成可执行约束，逐步记录违规证据，精确定位 Agent 故障的首个不可恢复步骤

## 核心问题

AI Agent 从简单聊天机器人演进为自主系统（管理云事件、操作复杂 Web 界面、执行多步骤 API 工作流），但一个新的挑战浮现：**透明性**。

人类犯错时可以追溯逻辑链，但 AI Agent 失败时——可能是幻觉了工具输出或偏离了策略——真正的根因往往被埋没在冗长、随机、且常常是多 Agent 的轨迹中。

## 方法/架构

### 核心思路
AgentRx 从工具模式（tool schema）和领域策略（domain policies）中自动合成**可守卫的可执行约束**（guarded executable constraints），然后在 Agent 执行轨迹中逐步检查约束违反，精确定位**首个不可恢复的"关键故障"步骤**。

### 故障分类体系
提出了一个有据可依的**九类故障分类法**，覆盖 Agent 失败的全谱系。

### 工作流程
1. 从工具模式和策略推导约束
2. 沿执行轨迹逐步检查约束
3. 记录带证据的违规日志
4. 定位首个关键故障步骤
5. 输出根因归因

## 实验结果

在 AgentRx Benchmark 上评估（包含 115 个人工标注的失败轨迹，跨 τ-bench、Flash 和 Magentic-One）：
- **故障定位**提升 +23.6%（相比 prompting 基线）
- **根因归因**提升 +22.9%（相比 prompting 基线）

开源了框架和数据集。

## 关键洞察

1. **约束驱动而非统计驱动**：AgentRx 不依赖大量失败样本训练诊断模型，而是从工具规范中推导约束——这种方法可泛化到任意 Agent 架构

2. **首个不可恢复步骤**是关键概念：故障往往在链条早期就已发生，但后果在后续步骤才显现。找到这个"转折点"比列举所有错误更有价值

3. **多 Agent 调试的必要性**：随着多 Agent 系统（如 Magentic-One）的普及，单 Agent 调试工具不足以定位跨 Agent 的协调故障

4. **工具模式是最丰富的调试信息来源**：工具的输入/输出规范本身就隐含了大量可检查的约束，比黑盒模型行为更可靠

## 为什么重要

在移动 AIOS 中，Agent 系统日益复杂——个人助理、自动化任务、多设备协同。当 Agent 行为异常时，用户需要可解释的故障诊断。AgentRx 提供的系统化调试方法可以嵌入到移动 OS 的 Agent 运行时中，实现：
- 自动故障检测和报告
- 用户友好的错误解释
- 开发者友好的调试日志

特别是其约束驱动的方法——不依赖云端大模型，可以在端侧执行约束检查。

## 关联
- [[agent-persistent-identity]] — Agent 身份的可观测性需要调试基础设施
- [[gui-agent-privacy]] — 调试日志涉及隐私——哪些信息应该被记录
- [[exectune-guide-core-policy]] — Guide 模型的策略可以作为 AgentRx 的领域策略输入
- [[planning-failure-escalation]] — 规划失败是 AgentRx 能检测的关键故障类型
- [[agent-system-reliability]] — AgentRx 是构建可靠 Agent 系统的调试层
