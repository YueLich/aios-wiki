---
title: "ADAM: A Systematic Data Extraction Attack on Agent Memory via Adaptive Querying"
arXiv: 2604.09747
date: 2026-04-10
authors: ["Xingyu Lyu", "Jianfeng He", "Ning Wang", "Yidan Hu", "Tao Li", "Danjue Chen", "Shixiong Li", "Yimin Chen"]
tags: [agent-memory, memory-privacy, privacy-attack, data-extraction, agent-security]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.09747
- **作者**: Xingyu Lyu, Jianfeng He, Ning Wang, Yidan Hu, Tao Li, Danjue Chen, Shixiong Li, Yimin Chen
- **提交日期**: 2026-04-10
- **方向**: 记忆隐私 / 数据安全 / Agent 安全

## 摘要（全文翻译）

LLM Agent 已快速普及并在广泛应用中展示了卓越能力。为提升推理和任务执行，现代 LLM Agent 集成了**记忆模块**或 RAG 机制，使它们能够进一步利用先验交互或外部知识。然而，这种设计也引入了一组关键隐私漏洞：存储在记忆中的敏感信息可能通过**基于查询的攻击**泄露。虽然可行，但现有攻击通常只达到有限的性能，攻击成功率（ASR）较低。

本文提出 **ADAM**，一种新颖的隐私攻击方法，其特点是：**估计受害者 Agent 记忆的数据分布**，并采用**熵引导的查询策略**来最大化隐私泄露。大量实验表明，ADAM 大幅超越 SOTA，达到**最高 100% 的 ASR**。这些结果揭示了当前 LLM Agent 对隐私保护方法的迫切需求。

## 核心贡献

1. **ADAM 攻击框架**：估计受害者 Agent 记忆的数据分布，用熵引导查询策略选择最可能触发敏感记忆的查询
2. **自适应查询**：通过分析 Agent 的响应模式推断记忆内容分布，动态调整攻击查询
3. **极致攻击效果**：在多个基准上达到接近 100% 的攻击成功率，展示了当前 Agent 记忆系统的隐私脆弱性
4. **系统安全启示**：强调了对记忆模块做隐私保护的迫切需求

## 为什么重要

ADAM 是记忆安全领域的重要论文，它系统性地揭示了 **Agent 记忆系统面临的数据泄露风险**。核心攻击思路——用熵引导的查询策略探测记忆内容——表明即使 Agent 不主动透露记忆内容，攻击者也可以通过精心设计的查询序列重建记忆。

对于记忆系统的设计者，这意味着：
- 记忆存储不能只考虑检索效率，还必须考虑**访问控制**
- 熵引导的探测说明单靠"不直接输出记忆"不够，需要**防止记忆内容的间接推断**
- 高 ASR 表明当前 Agent 记忆模块的隐私保护基本空白

## 与端侧/移动端的相关性

**高度相关**。移动端 Agent（手机助手、可穿戴设备）存储大量个人敏感信息（健康数据、位置历史、私人对话）。ADAM 攻击框架如果适配到这些场景，攻击者可以通过看似正常的语音/文本查询逐步提取用户的私人记忆。端侧部署的优势之一是数据不离开设备，但 ADAM 表明即使数据在本地，查询接口本身也可能成为泄露通道。

## 关键引文

> "sensitive information stored in memory can be leaked through query-based attacks... our attack substantially outperforms state-of-the-art ones, achieving up to 100% ASRs"

---

## 攻击方法

### 数据分布估计

ADAM 首先通过观察 Agent 对各类查询的响应模式，推断其内部记忆的数据分布——即 Agent 存储了哪些类型的敏感信息。

### 熵引导查询策略

选择查询时优先选择**最大熵**方向——即最可能揭示新信息的查询。这是一种主动探测策略，通过迭代查询逐步缩小记忆内容的范围。

### 防御方向

ADAM 的高成功率（100%）警示需要：
- 记忆访问的速率限制
- 查询相似性检测（阻止探测性查询序列）
- 记忆内容的差分隐私保护
- 访问控制的细粒度化
