---
title: "Trojan Hippo: Weaponizing Agent Memory for Data Exfiltration"
arXiv: 2605.01970
date: 2026-05-03
tags: [agent-memory, memory-privacy]
reviewer: auto
source: arXiv RSS/API
---

# Trojan Hippo: Weaponizing Agent Memory for Data Exfiltration

**作者:** Debeshee Das, Julien Piet, Darya Kaviani, Luca Beurer-Kellner, Florian Tramèr
**发表:** 2026-05-03

## 摘要

Memory systems enable otherwise-stateless LLM agents to persist user information across sessions, but also introduce a new attack surface. We characterize the Trojan Hippo attack, a class of persistent memory attacks that operates in a more realistic threat model than prior memory poisoning work: the attacker only controls the content of the memory, not the agent's system prompt or tools. We show that an LLM agent with memory is vulnerable to a particularly dangerous attack we call memory tunneling, where a malicious memory can induce the agent to repeatedly retrieve and act on the poisoned memory, effectively turning the agent into an exfiltration device. We demonstrate that even sparse, carefully placed poisoned memories can cause agents to leak sensitive information (e.g., passwords, personal data) to attacker-controlled locations via the agent's existing tool-use capabilities.

## 核心貢獻

1. **Trojan Hippo 攻击框架**: 首个针对 LLM Agent 记忆系统的持久化攻击框架，比传统记忆投毒更现实——攻击者只需控制记忆内容，无需控制系统 prompt 或工具
2. **Memory Tunneling（记忆隧道）**: 恶意记忆诱导 Agent 重复检索和执行被污染的记忆，将 Agent 转变为数据渗出设备
3. **最小化攻击假设**: 即使稀疏、精心放置的污染记忆也能导致敏感信息泄露，无需大规模注入
4. **通过现有工具渗出**: 利用 Agent 自身的 tool-use 能力（邮件、消息等）进行数据外传，绕过对外部网络的直接访问控制
5. **威胁模型分析**: 系统性分析了攻击者能力边界（仅控制记忆内容）与攻击效果之间的关系

## 為什麼重要

随着 LLM Agent 配备长期记忆系统，记忆本身成为新的攻击面。Trojan Hippo 揭示了一个此前被低估的威胁：攻击者无需攻破 Agent 的系统 prompt 或工具链，只需污染记忆内容即可实现持续性数据窃取。记忆隧道效应意味着即使单次污染也能触发多次信息泄露，且难以通过传统对抗样本检测发现。这对移动端 Agent 和个人助理系统的安全性有直接警示意义。

## 與端側/移動端相關性

1. **本地记忆风险**: 移动端 Agent 通常将用户个人数据存储在本地记忆，攻击面更大
2. **跨会话持久性**: 恶意记忆一旦写入，可跨多会话持续影响 Agent 行为
3. **Tool-use 滥用**: Agent 调用工具的能力（发邮件、消息）可被记忆劫持用于数据外传
4. **隐私保护设计**: 需要在记忆系统中引入记忆来源验证和内容完整性检查机制
