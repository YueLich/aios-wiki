---
title: "Rashomon Memory: Towards Argumentation-Driven Retrieval for Multi-Perspective Agent Memory"
arXiv: 2604.03588
date: 2026-04-04
authors: ["Albert Sadowski", "Jarosław A. Chudziak"]
tags: [agent-memory, memory-retrieval, multi-perspective, argumentation, knowledge-graph]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.03588
- **作者**: Albert Sadowski, Jarosław A. Chudziak
- **提交日期**: 2026-04-04
- **方向**: 多视角记忆检索 / 论证系统
- **发布**: Accepted to EXTRAAMAS workshop at AAMAS 2026

## 摘要（全文翻译）

AI Agent 在长期运作中积累服务于多个并发目标的经验，常常需要对同一事件维持**相互冲突的解释**。例如，客户谈判中的让步可能被编码为某个战略目标的"信任建立投资"，同时也是另一个目标的"合同法律责任"。

现有记忆架构假设单一正确编码，或最多支持对统一存储的多视图查询。本文提出 **Rashomon Memory**：一种并行目标条件 Agent 用各自优先级编码经验的架构，在查询时通过**论证（argumentation）**进行协商。每个视角维护自己的本体和知识图谱。在检索时，各视角提出解释，用非对称领域知识相互批评对方的提案，Dung 的论证语义决定哪些提案存活。

产生的攻击图（attack graph）本身就是一种**解释**：它记录了哪个解释被选中、考虑了哪些替代方案、以及它们基于什么理由被拒绝。本文提供了一个概念验证，展示了检索模式（选择、组合、冲突呈现）如何从攻击图拓扑中涌现，以及冲突呈现模式——系统报告真实分歧而非强制解决——如何让决策者直接看到底层的解释冲突。

## 核心贡献

1. **Rashomon Memory 架构**：允许多个并发目标维持相互冲突的记忆解释，而非强制统一编码
2. **论证驱动的检索**：用 Dung 的形式论证语义在多个视角间做检索决策
3. **攻击图作为解释**：检索结果包含完整的推理过程（哪些解释被拒绝，为什么）
4. **三种检索模式涌现**：Selection（选择）、Composition（组合）、Conflict Surfacing（冲突呈现）

## 为什么重要

这篇论文挑战了记忆系统的基本假设：**同一事件不需要统一的记忆编码**。Rashomon Memory 引入了"记忆的多元性"——不同目标可能需要对同一经验有不同的理解和解释。论证驱动的检索使得记忆系统能够：

- 维持**目标导向的视角多样性**而非强制一致性
- 在检索时通过正式论证解决冲突，而非简单投票或优先级排序
- 输出**可解释的检索决策**（攻击图记录了完整的拒绝理由）

## 与端侧/移动端的相关性

多视角记忆对**个人 Agent 的隐私场景**有直接意义：用户对同一事件的记忆可能需要同时服务于"工作目标"和"个人目标"，两个视角对敏感信息有不同的访问权限。攻击图提供了一种可解释的访问控制机制——可以明确地解释为什么某个记忆对某个视角可见/不可见。

## 关键引文

> "A concession during a client negotiation encodes as a 'trust-building investment' for one strategic goal and a 'contractual liability' for another. Current memory architectures assume a single correct encoding"

> "The resulting attack graph is itself an explanation: it records which interpretation was selected, which alternatives were considered, and on what grounds they were rejected"

---

## 方法细节

### 攻击图拓扑与检索模式

- **Selection 模式**：攻击图拓扑选择唯一 surviving 提案
- **Composition 模式**：多个提案被合并为一个复合解释
- **Conflict Surfacing 模式**：系统报告真实分歧，呈现底层的解释冲突，不强制解决

### Dung 论证语义

每个视角提出自己的解释提案，用非对称领域知识攻击其他提案的弱点。最终由 Dung 的论证语义确定哪些提案是"可接受的"——这是记忆检索决策的形式化基础。
