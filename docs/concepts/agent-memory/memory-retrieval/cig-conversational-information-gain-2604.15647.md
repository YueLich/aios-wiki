---
title: "CIG: Measuring Conversational Information Gain in Deliberative Dialogues with Semantic Memory Dynamics"
arXiv: 2604.15647
date: 2026-04-17
authors: ["Ming-Bin Chen", "Jey Han Lau", "Lea Frermann"]
tags: [agent-memory, memory-retrieval, semantic-memory, deliberation, conversation-quality]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.15647
- **作者**: Ming-Bin Chen, Jey Han Lau, Lea Frermann
- **提交日期**: 2026-04-17
- **方向**: 语义记忆 / 对话评估 / 集体推理
- **发布**: 24页，5图，发表于 EXTRAAMAS 2026 workshop

## 摘要（全文翻译）

衡量公共审议质量不仅需要评估礼貌性或论点结构，还需评估对话的**信息进展**。本文提出**会话信息增益（CIG）**框架，评估每个发言如何推进对目标话题的集体理解。

为将 CIG 可操作化，本文建模一个**进化的语义记忆**：系统从发言中提取原子主张（atomic claims），并逐步将它们整合为结构化的记忆状态。利用此记忆，按三个可解释的维度对每次发言评分：**新颖性（Novelty）**、**相关性（Relevance）**和**蕴含范围（Implication Scope）**。

本文对来自两个moderated审议场景（电视辩论和社区讨论）的80个片段进行了标注，表明记忆衍生动态（如主张更新次数）比传统启发式方法（如发言长度或 TF-IDF）更能预测人类感知的信息增益。开发的 LLM-based CIG 预测器为信息导向的对话质量分析奠定了基础。

## 核心贡献

1. **CIG 框架**：提出用语义记忆动态来衡量对话中的信息增益，而非依赖表面特征
2. **三维度评分**：Novelty（与已有记忆的增量信息）、Relevance（与讨论主题的相关性）、Implication Scope（主张的泛化范围）
3. **原子主张提取**：从发言中提取原子级别的知识单元，逐步构建结构化记忆状态
4. **标注数据集**：80个来自真实审议场景的片段，三个维度的标注

## 为什么重要

这篇论文的核心洞察是：**对话质量的核心是信息增量，而非表面礼貌或结构**。它将语义记忆的动态变化（记忆状态的演化）作为衡量对话质量的信号。对于 Agent 记忆系统，这意味着：

- 记忆不是静态存储，而是**不断更新的结构化状态**
- 评估记忆的价值可以用**信息增益**而非简单的时间/频率衰减
- 发言/交互的价值不在于其本身，而在于它如何改变 Agent 对世界的认知模型

## 与端侧/移动端的相关性

CIG 的原子主张提取和增量记忆更新机制对**移动端个性化记忆系统**有参考价值。设备端可以通过追踪用户交互的信息增量来决定记忆的重要性，而非仅靠访问频率或时间戳。对于 social robot 或个人助理这类需要长期记忆用户的场景，CIG 提供了一种衡量"这个交互是否真的增加了对用户的理解"的方法。

## 关键引文

> "We model an evolving semantic memory of the discussion: the system extracts atomic claims from utterances and incrementally consolidates them into a structured memory state"

> "memory-derived dynamics (e.g., the number of claim updates) correlate more strongly with human-perceived CIG than traditional heuristics such as utterance length or TF-IDF"

---

## 方法细节

### 记忆状态演化

```
发言 t1 → 提取主张 C1, C2 → 记忆状态 M1 = {C1, C2}
发言 t2 → 提取主张 C3    → 评估 C3 对 M1 的贡献 → M2 = M1 ∪ {C3}
...
```

### 三维度评分

- **Novelty**：该主张是否引入新信息（与已有记忆对比）
- **Relevance**：该主张与讨论目标主题的相关程度
- **Implication Scope**：该主张的泛化范围（影响窄/宽）
