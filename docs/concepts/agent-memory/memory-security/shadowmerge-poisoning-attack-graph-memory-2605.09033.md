---
title: "ShadowMerge: A Novel Poisoning Attack on Graph-Based Agent Memory via Relation-Channel Conflicts"
arXiv: "2605.09033"
date: "2026-05-09"
tags: [agent-memory, memory-security, graph-memory, poisoning-attack]
reviewer: auto
source: arXiv API
---

# ShadowMerge: A Novel Poisoning Attack on Graph-Based Agent Memory via Relation-Channel Conflicts

## 摘要

基于图的 Agent 记忆为 LLM Agent 提供结构化长期记忆和多跳推理能力，但也引入新的**投毒攻击面**：攻击者可以向图记忆注入精心构造的关系，使记忆在后续被检索时影响 Agent 行为。现有 Agent 记忆投毒攻击主要针对扁平文本记录，对图结构记忆效果有限——恶意关系难以被提取、难以合并到目标锚点邻域、难以对受害查询检索成功。ShadowMerge 针对图结构记忆设计新型投毒攻击，利用**关系-通道冲突**（Relation-Channel Conflicts）机制实现隐蔽而高效的投毒。

## 核心贡献

1. **首个针对图结构 Agent 记忆的投毒攻击**：填补了图记忆安全研究的空白，系统分析现有扁平攻击在图结构上失效的原因。
2. **Relation-Channel Conflicts 攻击机制**：利用图的共享节点结构和关系特定嵌入空间的差异，构造跨关系冲突的恶意关系，使攻击关系在检索时被高置信度匹配。
3. **攻击有效性验证**：在多种图记忆架构上验证 ShadowMerge 可实现高成功率、低可察觉性的投毒。
4. **安全启示**：为图记忆的防御性安全研究提供攻击基准和方向。

## 为什么重要

随着 Agent 系统在生产环境部署，图结构记忆成为多跳推理的核心基础设施。ShadowMerge 揭示了图记忆的**信任边界问题**——如果攻击者可向记忆图注入恶意关系，Agent 的推理可靠性将系统性受损。这一工作对记忆系统的安全评估和防御设计有重要推动作用。

## 与移动端/端侧相关性

端侧 Agent 通常依赖本地知识图谱和记忆系统，ShadowMerge 的攻击机制（利用图的共享节点结构）表明本地图记忆同样面临投毒风险，对注重隐私和安全的端侧部署有直接警示意义。

## 参考文献

- 详见原论文
