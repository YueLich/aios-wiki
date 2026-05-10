---
title: "From Recall to Forgetting: Benchmarking Long-Term Memory for Personalized Agents"
arXiv: "2604.20006"
date: "2026-04-21"
tags: [agent-memory, memory-retrieval, benchmark, continual-learning]
reviewer: auto
source: arXiv ti: search
---

# From Recall to Forgetting: Benchmarking Long-Term Memory for Personalized Agents

## 论文基本信息

- **arXiv ID**: 2604.20006
- **发表日期**: 2026-04-21
- **作者**: Md Nayem Uddin, Kumar Shubham, Eduardo Blanco, Chitta Baral, Gengyu Wang
- **类别**: cs.CL (Computation and Language)
- **来源**: arXiv ti: search

## 摘要

个性化智能体需要跨会话维护持久记忆，并在情况变化时更新记忆。然而现有基准将长期记忆评估框架为从过去对话中检索事实，无法深入洞察智能体随时间整合记忆的能力或处理频繁知识更新的能力。本文提出 **Memora**，一个长期记忆基准，涵盖数周到数月的用户对话。基准评估三类记忆支撑任务：**记忆（remembering）、推理（reasoning）和推荐（recommending）**。为确保数据质量，本文采用自动化记忆锚定检查和人工评估。本文进一步提出 **Forgetting-Aware Memory Accuracy (FAMA)** 指标，在评估长期记忆时惩罚对过时或失效记忆的依赖。对四个 LLM 和六个记忆智能体的评估揭示了频繁重用无效记忆以及无法协调演化记忆的问题。记忆智能体仅带来边际改进，暴露了个性化智能体长期记忆的不足。

## 核心贡献

1. **Memora 基准**：首个涵盖"记忆→推理→推荐"全流程的长期记忆评估基准，时间跨度达数周至数月
2. **FAMA 指标**（Forgetting-Aware Memory Accuracy）：惩罚对过时/失效记忆依赖的评估指标，引导记忆系统学会"何时遗忘"
3. **系统性诊断**：揭示现有记忆智能体普遍存在无效记忆重用和演化记忆协调失败的问题

## 为什么重要

长期记忆研究长期受制于"事实检索"这一单一评估范式，忽略了记忆的时效性本质。Memora 的价值在于：
- **时间维度**：将记忆评估从单会话拓展到跨会话的月级时间尺度
- **遗忘感知**：FAMA 指标首次将"何时遗忘"纳入评估体系，直接对应记忆治理的核心问题
- **应用覆盖**：记忆→推理→推荐的完整任务链条，比单一 QA 更接近真实应用场景

## 与移动端/端侧的相关性

端侧个性化智能体（如手机助手、可穿戴设备）最需要长期记忆，但资源受限环境下无法存储完整对话历史。Memora 的遗忘感知评估框架（FAMA）可为端侧记忆系统的"重要性判断"提供基准参考——学会判断何时应该保留、何时可以压缩或遗忘，是端侧记忆系统的核心能力。

## 参考文献

（详见原论文）
