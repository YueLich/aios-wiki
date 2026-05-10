---
title: "Memory Poisoning Attack and Defense on Memory Based LLM-Agents"
arXiv: 2601.05504
date: 2026-01-09
tags: [agent-memory, memory-privacy, memory-security, memory-poisoning, EHR-agents]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv ID**: 2601.05504
- **发表日期**: 2026-01-09
- **作者**: Balachandra Devarangadi Sunil, Isheeta Sinha, Piyush Maheshwari, Shantanu Todmal, Shreyan Mallik, Shuchi Mishra
- **方向**: 记忆安全 / 记忆投毒攻防
- **开源代码**: 暂未公开

## 摘要（翻译）

配备持久外部记忆的 LLM Agent 容易受到**记忆投毒攻击**，攻击者通过纯查询交互即可注入恶意指令，篡改 Agent 的长期记忆并影响未来响应。近期工作表明，MINJA（Memory Injection Attack）在理想条件下实现了 **95%+ 注入成功率**和 **70% 攻击成功率**。然而，这些攻击在真实部署中的鲁棒性和有效防御机制仍缺乏系统研究。

本文针对 **EHR（电子健康记录）Agent** 系统性地评估了记忆投毒攻击和防御。通过改变三个关键维度（初始记忆状态、指示提示数量和检索参数）研究攻击鲁棒性。在 GPT-4o-mini、Gemini-2.0-Flash 和 Llama-3.1-8B-Instruct 模型上，使用 MIMIC-III 临床数据进行的实验表明：**预存合法记忆的真实条件显著降低了攻击效果**。本文进一步提出并评估了两种新型防御机制：（1）**输入/输出审核**：跨多个正交信号的复合信任评分；（2）**记忆消毒**：采用时间衰减和基于模式的过滤的信任感知检索。

防御评估表明：有效的记忆消毒需要仔细的信任阈值校准——既要防止过度保守的拒绝（屏蔽所有条目），也要防止过滤不足（漏掉隐蔽攻击），为未来自适应防御建立了重要的基准线。

## 核心贡献

### 1. 系统性攻击评估
首次在真实 EHR 场景下系统评估记忆投毒攻击（MINJA）的鲁棒性，发现预存合法记忆显著降低攻击效果。

### 2. 防御机制设计
提出两种防御：
- **输入/输出审核**（I/O Moderation）：多信号复合信任评分
- **记忆消毒**（Memory Sanitization）：时间衰减 + 模式过滤的信任感知检索

### 3. 阈值校准洞察
发现信任阈值过高会过度保守（屏蔽所有条目），过低则过滤不足——建立了一个重要的工程基准线。

## 为什么重要

本文填补了记忆投毒攻击**从理论到真实场景**的评估空白，揭示了理想条件与真实部署之间的巨大差距（攻击效果显著下降），并提供了实用的防御方案。对于 EHR、金融等高风险场景的 Agent 记忆系统安全设计具有直接指导意义。

## 与端侧/移动端的相关性

移动端 EHR 助手和个人健康 Agent 是典型的高敏感场景。本文提出的轻量级信任评分和时间衰减机制非常适合资源受限的端侧部署，不需要 LLM 推理调用即可工作。

## 参考文献

1. See original paper for full reference list
