---
title: "Towards Benchmarking Privacy Vulnerabilities in Selective Forgetting with Large Language Models"
arXiv: "2512.18035"
date: "2025-12-19"
tags: [agent-memory, memory-privacy, selective-forgetting, security]
reviewer: auto
source: arXiv RSS
---

## 核心贡献

论文系统研究了 LLM 中选择性遗忘（selective forgetting / machine unlearning）的隐私漏洞问题。

**核心问题**：
- 选择性遗忘（机器遗忘）旨在让模型有选择性地擦除已见数据的影响
- 这对隐私保护和数据删除任务很有前景
- 但这类方法在对抗性场景下的安全性尚未被系统评估

**研究内容**：
1. 构建了首个选择性遗忘方法的隐私漏洞基准
2. 发现多种遗忘方法存在隐私泄露问题——即使某些数据被"遗忘"，攻击者仍可通过特定查询恢复这些信息
3. 揭示了当前遗忘方法与真正隐私保护之间的差距

## 为什么重要

随着 AI 系统部署在敏感领域（医疗、金融、法律），记忆的隐私性变得至关重要。传统观点认为"遗忘"就是删除，但论文表明：LLM 中的遗忘是复杂的，被"遗忘"的数据可能以隐蔽方式残留在模型中。对 agent 记忆系统的隐私设计有直接警示意义。

## 与端侧/移动端的相关性

**中等相关**。端侧 agent 处理大量个人隐私数据（对话历史、位置、照片）。如果选择性遗忘存在漏洞，在边缘设备上本地执行的"遗忘"操作可能无法真正保护隐私。对可穿戴设备、手机等私人设备上的记忆治理有参考价值。

## 摘要

The rapid advancements in artificial intelligence (AI) have primarily focused on the process of learning from data to acquire knowledgeable learning systems. As these systems are increasingly deployed in critical areas, ensuring their privacy and alignment with human values is paramount. Recently, selective forgetting (also known as machine unlearning) has shown promise for privacy and data removal tasks, and has emerged as a transformative paradigm shift in the field of AI. It refers to the ability of a model to selectively erase the influence of previously seen data, which is especially important in privacy-sensitive applications.

## 参考文献

待补充
