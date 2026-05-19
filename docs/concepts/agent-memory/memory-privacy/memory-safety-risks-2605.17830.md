---
title: "Remembering More, Risking More: Longitudinal Safety Risks in Memory-Equipped LLM Agents"
arXiv: 2605.17830
date: 2026-05-18
tags: [agent-memory, memory-privacy, security, safety]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: 多机构合作

**核心问题**: 现有 memory-augmented LLM agent 的安全评估都是**单任务内**评估（single-scenario adversarial robustness），忽略了真实世界中的长时序安全隐患——随着 agent 记忆内容的不断积累，攻击面会扩大，且历史记忆中的信息可能在多轮交互后被攻击者间接利用。

**方法**: 首次系统研究记忆-equipped LLM agent 的**纵向安全风险（longitudinal safety risks）**，通过模拟真实场景中记忆随时间积累的过程，评估三类安全威胁的演化。

### 三类安全威胁

1. **记忆中毒攻击（Memory Poisoning）**：攻击者通过多轮交互逐步向 agent 记忆注入恶意内容，而非单次注入
2. **记忆劫持（Memory Hijacking）**：利用已有记忆内容作为跳板，通过记忆联想间接获取本不应访问的信息
3. **记忆污染累积（Pollution Accumulation）**：每次交互中的无害偏差在记忆中累积，最终导致 agent 在后续任务中产生系统性偏差

## 核心贡献

1. **首个纵向安全风险分类体系**：将记忆-equipped LLM agent 的安全威胁按时间维度分类，揭示单任务安全评估的局限性
2. **大规模纵向攻击模拟**：设计了针对记忆系统的多轮攻击协议，覆盖 3 类威胁、7 种攻击策略
3. **揭示记忆放大效应**：实验证明，攻击成功率随记忆积累呈非线性增长——记忆越丰富的 agent，攻击者越容易找到可利用的记忆路径
4. **提出记忆安全设计原则**：基于攻击模式分析，给出 5 条记忆系统安全设计建议（访问隔离、最小暴露、定期记忆审计等）

## 为什么重要

这篇论文敲响了 memory-augmented agent 安全的警钟——现有评估只看单任务安全，但真实部署中 agent 记忆会不断积累，攻击面也随之扩大。随着 memory 系统成为 LLM agent 的标配，这种纵向安全风险将成为真实部署的主要威胁。

## 与移动端/端侧的相关性

端侧 agent 的安全风险尤其值得关注：设备上的记忆更容易被本地攻击者（恶意应用、供应链攻击）访问，且用户难以像在云端那样审计 agent 的记忆内容。本文提出的记忆安全设计原则对端侧记忆系统架构有直接指导意义。

## 参考文献

- Al-Tawaha, A., et al. (2026). Remembering More, Risking More: Longitudinal Safety Risks in Memory-Equipped LLM Agents. arXiv:2605.17830.
