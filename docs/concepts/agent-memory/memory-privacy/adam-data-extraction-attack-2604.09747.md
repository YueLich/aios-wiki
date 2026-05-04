---
title: "ADAM: A Systematic Data Extraction Attack on Agent Memory via Adaptive Querying"
arXiv: 2604.09747
date: 2026-04-10
tags: [agent-memory, memory-privacy, security, RAG]
reviewer: auto
source: arXiv API
authors: "Xingyu Lyu, Jianfeng He, Ning Wang"
---

## 论文信息

- **arXiv**: 2604.09747
- **发表日期**: 2026-04-10
- **作者**: Xingyu Lyu, Jianfeng He, Ning Wang
- **方向**: 记忆隐私与安全

## 摘要

大型语言模型（LLM）Agent 已被广泛部署，通过记忆模块或 RAG 机制利用先前交互来提升推理和任务执行。然而，这种设计也引入了关键的隐私安全漏洞：存储在记忆中的敏感信息可通过基于查询的攻击被泄露。虽然这类攻击是可行的，但现有方法通常只能达到有限的性能，攻击成功率（ASR）较低。本文提出 ADAM，一种新型隐私攻击方法，通过对受害者 Agent 记忆的数据分布估计与熵引导查询策略，最大化隐私泄露。大量实验表明，ADAM 大幅超越最新方法，达到最高 100% 的 ASR。这些结果深刻揭示了当前 LLM Agent 对隐私保护方法的迫切需求。

## 核心贡献

1. **ADAM 攻击框架**：通过数据分布估计与自适应查询策略，系统性提取 Agent 记忆中的敏感信息
2. **隐私安全警示**：证明现有 Agent 记忆系统面临严重隐私风险，100% ASR 意味着几乎任何敏感信息都可能被提取
3. **防御需求**：揭示了当前 Agent 记忆系统在隐私保护方面的根本性缺陷

## 为什么重要

随着 LLM Agent 在生产环境中的普及，记忆模块存储了大量用户敏感信息（对话历史、偏好设置、工作文档等）。ADAM 攻击证明这些记忆可以被系统性提取，揭示了隐私保护的紧迫性。这对端侧 Agent 尤其重要——在共享设备上，记忆污染的持久性和隐私泄露的危害更加严重。

### 与移动端/端侧的相关性

- **端侧 Agent** 常运行在手机、电脑等共享设备上，记忆中的个人数据泄露风险更高
- **本地部署**的 Agent 虽然减少了网络攻击面，但仍然面临物理访问攻击
- **隐私计算**（联邦学习、安全 enclave）可能是防御方向
