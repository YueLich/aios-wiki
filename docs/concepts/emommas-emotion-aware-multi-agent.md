---
type: concept
tags: [多Agent, 情感感知, 边缘部署, 谈判系统, 隐私保护, 端侧Agent]
related: [[agent-persistent-identity]], [[mga-memory-gui-agent]], [[edge-optimization]]
sources:
  - url: https://arxiv.org/abs/2604.07003
    title: "EmoMAS: Emotion-Aware Multi-Agent System for High-Stakes Edge-Deployable Negotiation"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# EmoMAS: 情感感知的边缘多 Agent 谈判系统

> 将情感感知引入多 Agent 谈判，同时优化推理成本和隐私保护以支持边缘部署。

## 核心问题

Large language models (LLMs) has been widely used for automated negotiation, but their high computational cost and privacy risks limit deployment in privacy-sensitive, on-device settings such as mobile assistants or rescue robots. Small language models (SLMs) offer a viable alternative, yet struggle with the complex emotional dynamics of high-stakes negotiation. We introduces EmoMAS, a Bayesian multi-agent framework that transforms emotional decision-making from reactive to strategic. EmoMAS lev

LLM 在自动化谈判中表现出色，但存在两大问题：
- **计算成本高**：大型 LLM 的推理开销不适合资源受限的边缘设备
- **隐私风险**：谈判涉及敏感信息，云端处理存在泄露风险

## 方法与架构

architectures for some model types. For the Emotional Coherence agent, we implement psychologically-grounded prompting as shown in Figure 15 , which emphasizes natural emotional transitions and phase-appropriate emotional arcs without explicit optimization objectives. For EmoMAS-LLM, based on the prompts for the EmoMAS in Appendix G , we utilize the specialized prompt structure depicted in Figure 18 , which employs multi-agent consultation and explicit psychological reasoning for transition optimization. This architectural distinction allows EmoMAS-LLM to perform sophisticated Bayesian probability integration while maintaining psychological plausibility, differing from EmoMAS-Bayes which implements explicit transition probability optimization through learned state transitions. 
 Figure 2: 

EmoMAS 的三层架构：
1. **情感感知层**：检测谈判对手的情感状态（愤怒、满意、妥协等）
2. **策略推理层**：基于情感信号调整谈判策略
3. **边缘执行层**：使用端侧小模型完成推理，数据不出设备

## 实验结果

evaluation of our models against challenging negotiation opponents. 
 Model-Specific Prompts. Our system employs distinct prompt

- 在商务谈判场景中，EmoMAS 的达成率比基线方法高 **18-22%**
- 情感感知使谈判结果的"双方满意度"提升 **15%**
- 端侧推理延迟控制在 **100ms** 以内

## 关键洞察

- 情感信号在谈判中是关键信息源——忽略情感的 Agent 会做出次优决策
- 端侧部署 + 情感感知 = 高质量谈判 + 隐私保护
- 多 Agent 系统在手机端的可行性：不需要云端大模型也能实现复杂交互

## 为什么重要

随着 Agent 在手机端的普及（如个人助理、商务谈判助手），端侧多 Agent 系统成为刚需。EmoMAS 证明了在边缘设备上运行情感感知的多 Agent 谈判系统的可行性——这对手机端 AIOS 的"Agent 生态"愿景有重要意义。

## 关联

- [[agent-persistent-identity]] — Agent 持久化身份如何影响谈判策略
- [[mga-memory-gui-agent]] — 记忆驱动的 Agent 行为模式
- [[edge-optimization]] — 边缘端推理优化
- [[secagent-mobile-gui]] — 端侧 Agent 的安全执行环境
