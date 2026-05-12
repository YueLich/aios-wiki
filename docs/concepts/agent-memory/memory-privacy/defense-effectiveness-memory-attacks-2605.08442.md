---
title: "Defense effectiveness across architectural layers: a mechanistic evaluation of persistent memory attacks on stateful LLM agents"
arXiv: 2605.08442
date: 2026-05-08
tags: [agent-memory, memory-privacy, security]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **标题**: Defense effectiveness across architectural layers: a mechanistic evaluation of persistent memory attacks on stateful LLM agents
- **作者**: Jun Wen Leong
- **arXiv ID**: 2605.08442
- **类别**: cs.CR (Computer Security)
- **发表日期**: 2026-05-08

## 摘要（翻译）

持久性记忆攻击（Persistent memory attacks）对开源 LLM agents 达到高攻击成功率。攻击方式为：通过 RAG 检索文档注入恶意指令，存储在持久性记忆中，在后续会话执行。然而，此前尚无系统性的防御有效性评估。本文评估了六种防御方法，涵盖四个架构层级，对九个开源模型（5,040 runs，N=40 per condition）进行延迟触发攻击（delayed-trigger attacks）测试。结果显示：四种防御在约基线攻击成功率（88-89%）下失败，在统计上与未防御基线（88.6%）无法区分。Prompt Hardening 部分失败（77.8% ASR），改善来自两个模型，其中一个为真实防御效果，另一个为模型层面的拒绝（与防御无关）。架构层面的解释成立：输入级防御无法观察 RAG 注入内容，检索级分类器被"顺从框架语义掩码"（compliance-framed semantic masking）击败。仅有一种防御——记忆层的工具门控（Memory Sandbox）——将 ASR 降至 0%（九模型中八个）。唯一例外完全反转了防御效果：某个推理模型在无防御时通过执行拒绝达到 0% ASR，但在 Memory Sandbox 下反而升至 100%，因为移除显式召回强制模型进入 RAG 路径，而其拒绝机制在该路径下不激活。Memory Sandbox 在无攻击情况下 BTCR = 100%（所有条件），零效用损失。这些结果首次系统性地揭示了每类防御为何对持久性记忆攻击失败，为防御投资决策提供了依据。

## 核心贡献

### 1. 首个系统性防御评估框架
首次对持久性记忆攻击的防御有效性进行系统性评估，覆盖六种防御×四层架构×九模型=完整矩阵。

### 2. 防御失败机制揭示
- **输入级防御**（Minimizer、Sanitizer）：无法观察 RAG 注入内容，攻击内容在记忆层注入
- **检索级防御**（RAG Sanitizer、RAG LLM Judge）：被"顺从框架语义掩码"击败——攻击内容以顺从语气包装，规避分类器
- **Prompt Hardening**：部分有效（77.8% ASR），但效果不稳定
- **唯一有效**：Memory Sandbox（记忆层工具门控）——通过移除攻击所需的召回能力实现 0% ASR

### 3. 防御反转（Defense Inversion）现象
推理模型（如某推理模型）在无防御时通过执行拒绝达到 0% ASR，但 Memory Sandbox 强制其进入 RAG 路径后，推理模型的拒绝机制不激活，反而升至 100% ASR。这揭示了工具门控防御的边界条件。

### 4. 零效用损失保证
Memory Sandbox 在无攻击情况下 BTCR = 100%，即不牺牲正常任务性能。

## 为什么重要

持久性记忆攻击是针对有状态 LLM agent 的新型威胁，攻击者在早期会话注入恶意指令存储于 agent 的持久性记忆中，在后续会话触发恶意行为。本文的系统性评估为实际部署有状态 LLM agents 的安全决策提供了关键参考。

## 与移动端/端侧 Agent 的关联

- **端侧 agent**通常需要持久性记忆（如个人助手、穿戴设备上的 agent），这类攻击面对本地部署模型同样有效
- **Memory Sandbox 防御**可在端侧部署，但需要架构支持工具门控
- 移动端 LLM agents（如 iOS/Android 助手）若支持记忆持久化，均面临此类攻击威胁

## 防御层级分类

| 防御层级 | 具体防御 | ASR | 有效性 |
|---------|---------|-----|--------|
| 输入层 | Minimizer | 88-89% | ❌ 无效 |
| 输入层 | Sanitizer | 88-89% | ❌ 无效 |
| 检索层 | RAG Sanitizer | 88-89% | ❌ 无效 |
| 检索层 | RAG LLM Judge | 88-89% | ❌ 无效 |
| Prompt 层 | Prompt Hardening | 77.8% | ⚠️ 部分有效 |
| 记忆层 | Memory Sandbox | 0% | ✅ 有效 |

## 方法论亮点

- **延迟触发攻击（Delayed-Trigger Attack）**：在早期会话注入，攻击在后续会话触发，更贴近真实威胁模型
- **大尺度实验**：5,040 runs，N=40 per condition，统计显著性充分
- **机制性解释**：不仅报告 ASR 数字，还深入解释为何每类防御成功/失败

## 核心洞察

> "输入级和检索级防御失败的根本原因：它们无法观察到 RAG 注入的内容——这些内容在存储时对防御系统不可见，只有在检索时才会被注入 agent 的上下文中。"

> "唯一有效的 Memory Sandbox 防御通过移除攻击所需的召回能力来实现，而不是检测攻击内容本身——这是一种根本性的缓解策略而非检测策略。"
