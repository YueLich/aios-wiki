---
title: "Towards Benchmarking Privacy Vulnerabilities in Selective Forgetting with Large Language Models"
arXiv: "2512.18035"
date: "2025-12-19"
tags: [agent-memory, memory-privacy, selective-forgetting, security]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **首个选择性遗忘隐私漏洞基准**：系统评估当前机器遗忘（machine unlearning）方法在隐私保护方面的漏洞。
2. **多维度隐私泄露分析**：在多种受害者数据、SOTA 遗忘攻击、遗忘方法、模型架构上全面评估隐私泄露。
3. **揭示遗忘-隐私悖论**：证明当前的遗忘方法存在根本性隐私问题——被"遗忘"的数据可能通过特定查询恢复。
4. **公平评估框架**：解决现有攻击使用不同实验设置导致的评估不公平问题。

## 方法详解

### 问题背景
选择性遗忘（机器遗忘）是 AI 隐私保护的重要范式，被"遗忘"的数据应该无法从模型中恢复。但新提出的隐私攻击不断超越前任，且各自使用不同实验设置，可能导致过度乐观的评估。

### 研究发现
- 多种主流遗忘方法都存在隐私泄露问题
- 即使某些数据被标记为"遗忘"，攻击者仍可通过精心设计的查询恢复这些信息
- 遗忘方法的隐私保护能力远未达到真正隐私法规的要求

## 为什么重要

随着 AI 系统部署在敏感领域（医疗、金融、法律），记忆的隐私性变得至关重要。传统观点认为"遗忘"就是删除，但论文表明：LLM 中的遗忘是复杂的，被"遗忘"的数据可能以隐蔽方式残留在模型中。对 agent 记忆系统的隐私设计有直接警示意义。

## 与端侧/移动端的相关性

**中等相关**。端侧 agent 处理大量个人隐私数据（对话历史、位置、照片）。如果选择性遗忘存在漏洞，在边缘设备上本地执行的"遗忘"操作可能无法真正保护隐私。对可穿戴设备、手机等私人设备上的记忆治理有参考价值。

## 摘要

The rapid advancements in artificial intelligence (AI) have primarily focused on the process of learning from data to acquire knowledgeable learning systems. As these systems are increasingly deployed in critical areas, ensuring their privacy and alignment with human values is paramount. Recently, selective forgetting (also known as machine unlearning) has shown promise for privacy and data removal tasks, and has emerged as a transformative paradigm shift in the field of AI. It refers to the ability of a model to selectively erase the influence of previously seen data, which is especially important for compliance with modern data protection regulations and for aligning models with human values. Despite its promise, selective forgetting raises significant privacy concerns, especially when the data involved come from sensitive domains. While new unlearning-induced privacy attacks are continuously proposed, each is shown to outperform its predecessors using different experimental settings, which can lead to overly optimistic and potentially unfair assessments that may disproportionately favor one particular attack over the others. In this work, we present the first comprehensive benchmark for evaluating privacy vulnerabilities in selective forgetting. We extensively investigate privacy vulnerabilities of machine unlearning techniques and benchmark privacy leakage across a wide range of victim data, state-of-the-art unlearning privacy attacks, unlearning methods, and model architectures. We systematically evaluate and identify critical factors related to unlearning-induced privacy leakage. With our novel insights, we aim to provide a standardized tool for practitioners seeking to deploy customized unlearning applications with faithful privacy assessments.

## 参考文献

- Wei Qian, Chenxu Zhao, Yangyi Li, Mengdi Huai. "Towards Benchmarking Privacy Vulnerabilities in Selective Forgetting with Large Language Models." arXiv:2512.18035, 2025.
