---
type: concept
tags: [agent, delegation, trust, document-editing, reliability, 工具使用]
related: [[policybank-agent-policy-understanding]], [[gui-agent-privacy]], [[clawmobile-agentic]]
sources:
  - url: https://arxiv.org/abs/2604.15597
    title: "LLMs Corrupt Your Documents When You Delegate"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# LLM 委托编辑中的文档损坏问题

> 即使是前沿模型（Gemini 3.1 Pro, Claude 4.6 Opus, GPT 5.4），在长委托工作流中也会平均损坏 25% 的文档内容。来自 Philippe Laban 等人 (arXiv 2604.15597)。

## 核心问题

LLM Agent 正在通过"委托工作"（delegated work，如 vibe coding）改变知识工作的交互范式。委托需要信任——期望 LLM 忠实执行任务而不引入错误。但这种信任是否合理？

## 方法/架构

**DELEGATE-52** 基准测试：
- 模拟跨 52 个专业领域的长委托工作流
- 涵盖编程、晶体学、音乐记谱等多样化的文档编辑场景
- 测试深度文档编辑的完整流程，而非简单单轮任务

## 实验结果

- **19 个 LLM 的大规模实验**：揭示当前模型在委托中确实会降解文档
- **前沿模型也未能幸免**：Gemini 3.1 Pro、Claude 4.6 Opus、GPT 5.4 在长工作流末尾平均损坏 25% 的文档内容
- 错误随工作流长度累积——越长的委托链，损坏越严重
- 不同领域损坏模式各异：代码可能引入逻辑错误，晶体学可能破坏结构表示

## 关键洞察

这不是"偶尔犯错"的问题，而是系统性的信任危机。当 Agent 在手机端执行文档编辑任务时，用户期望的是无缝委托。但实际中，Agent 可能在用户不知情的情况下逐步破坏文档结构。

对于移动端 Agent，这一问题更加严峻：
- 移动屏幕小，用户难以验证大量修改
- 委托链条往往更长（语音指令 → Agent 理解 → 多步执行）
- 文档类型更碎片化（备忘录、日程、消息、代码片段）

## 为什么重要

- **Agent 可靠性**：直接挑战了"委托即信任"的假设，对移动 Agent 设计有深远影响
- **验证机制需求**：移动 Agent 需要内置的变更验证/回滚机制
- **渐进式委托**：应将长工作流分解为可验证的短步骤

## 关联
- [[policybank-agent-policy-understanding]] — 策略理解可作为委托约束
- [[clawmobile-agentic]] — ClawMobile 原生 Agent 架构的可靠性设计
- [[gui-agent-privacy]] — 文档损坏也涉及隐私泄露风险
- [[mga-memory-gui-agent]] — 记忆机制可用于追踪文档变更历史
