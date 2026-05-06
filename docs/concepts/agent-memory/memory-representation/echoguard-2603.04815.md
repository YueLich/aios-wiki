---
title: "EchoGuard: An Agentic Framework with Knowledge-Graph Memory for Detecting Manipulative Communication in Longitudinal Dialogue"
arXiv: 2603.04815
date: 2026-03-05
tags: [agent-memory, memory-representation, knowledge-graph, privacy]
reviewer: auto
source: arXiv RSS/API
---

# EchoGuard: An Agentic Framework with Knowledge-Graph Memory for Detecting Manipulative Communication in Longitudinal Dialogue

## 论文基本信息

- **作者**: Ratna Kandala, Niva Manchanda, Akshata Kishore Moharir, Ananth Kandala
- **arXiv**: https://arxiv.org/abs/2603.04815

## 摘要

操纵性沟通（煤气灯效应、情感胁迫等）往往难以被个体识别。现有 Agentic AI 系统缺乏结构化的纵向记忆来追踪这些微妙的、依赖上下文的策略，常因上下文窗口限制和灾难性遗忘而失败。EchoGuard 使用知识图谱（KG）作为 Agent 的核心情景记忆和语义记忆，采用结构化的 Log-Analyze-Reflect 循环：① 用户记录交互，Agent 将事件、情感、说话者结构化为节点和边，构建个人情景 KG；② 系统执行复杂图查询，检测六种基于心理学基础的操纵模式（存储在语义 KG 中）；③ LLM 生成苏格拉底式提示，基于检测到模式的子图引导用户自我发现。

## 核心贡献

1. **EchoGuard 框架**: 知识图谱记忆支撑的 Agentic 操纵检测系统
2. **Log-Analyze-Reflect 循环**: 结构化记忆-分析-反思工作流
3. **情景 KG + 语义 KG 双记忆**: 追踪个人交互历史 + 心理学操纵模式库
4. **苏格拉底式引导**: 基于图查询结果的自我发现式干预

## 研究背景与问题

操纵性沟通（gaslighting、guilt-tripping、emotional coercion）在日常关系中普遍但难以识别。现有 AI 系统的问题：
- **上下文窗口限制**：无法长期追踪跨越多次会话的微妙操纵模式
- **灾难性遗忘**：无法在新对话中保持对历史交互的记忆
- **缺乏结构化表示**：原始文本无法有效表达情感和关系演变

## 核心方法

### Log-Analyze-Reflect 循环

**1. Log（记录）**
- 用户记录与特定人员的对话
- Agent 将交互结构化为知识图谱节点和边：
  - 节点：事件、情感状态、说话者
  - 边：因果关系、时序关系、情感影响
- 构建个人情景 KG（Episodic KG）

**2. Analyze（分析）**
- 在情景 KG 上执行复杂图查询
- 与语义 KG 中的六种操纵模式匹配：
  1. Gaslighting（煤气灯效应）
  2. DARVO（Deny-Attack-Reverse Victim & Offender）
  3. Love Bombing（爱情轰炸）
  4. Silent Treatment（冷暴力）
  5. Guilt Tripping（情感内疚）
  6. Emotional Coercion（情感胁迫）
- 检测结果存储为匹配的子图

**3. Reflect（反思）**
- LLM 基于检测到的子图生成苏格拉底式提问
- 引导用户通过自我反思识别操纵模式
- 保持用户自主性和主动性

### 记忆架构

- **情景 KG（Episodic KG）**：个人历史交互的结构化记忆，捕捉事件、情感、说话者关系
- **语义 KG（Semantic KG）**：六种操纵模式的心理学定义和特征库
- 双 KG 协同实现跨时间的操纵检测

## 为什么重要

EchoGuard 展示了知识图谱记忆在需要纵向追踪的场景中的独特价值。相比向量检索或纯文本记忆，KG 能表达实体间的结构化关系（因果、时序、情感），对追踪需要跨多次会话的微妙操纵模式至关重要。

## 与移动端/端侧相关性

有参考价值但存在部署挑战：
- KG 存储和查询在资源受限设备上开销较高
- Log-Analyze-Reflect 循环的实时性对移动端有挑战
- 苏格拉底式引导的推理可云端执行，KG 记忆可考虑端侧缓存
