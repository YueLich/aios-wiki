---
title: Governed Collaborative Memory as Artificial Selection in LLM-Based Multi-Agent Systems
arXiv: 2605.04264
date: 2026-05-05
tags: [agent-memory, memory-retrieval, multi-agent, memory-governance]
reviewer: auto
source: arXiv RSS/API
---

# Governed Collaborative Memory as Artificial Selection in LLM-Based Multi-Agent Systems

## 论文基本信息

- **arXiv ID**: 2605.04264
- **发表日期**: 2026-05-05
- **作者**: Diego F. Cuadros, Abdoul-Aziz Maiga, Helen Meskhidze, Andre Curtis-Trudel
- **方向**: Multi-Agent Memory, Memory Governance, Collaborative Memory
- **类别**: cs.MA (Multi-Agent Systems)

## 摘要（翻译）

持久记忆正在将基于语言模型的智能体从孤立交互中的无状态参与者转变为 LLM 多智能体系统中承载状态的角色。随着记忆变得持久、可重新加载并跨智能体、会话或版本影响行为，一个设计问题浮现出来——这个问题无法仅用检索准确性或访问控制来捕获：哪些候选记忆应该成为共享的制度性状态？

本文将此问题框架为**有治理的协作记忆（Governed Collaborative Memory）**。作者认为，记忆治理作为一种选择机制，决定了哪些记忆变体被保留、哪些保持私有、哪些被拒绝、弃权或取代。文章区分了四种选择机制：无治理持久化、宪政或混合选择、自动基于指标的选择、以及人类批准的人工选择，强调这些机制不是排名而是针对目标属性的设计选择。

随后描述了一种分层架构，将智能体本地记忆、共享制度记忆、档案记忆和项目连续性记忆分开，并通过起源和版本 lineage 使选择可审查。来自一个运行的 LLM 多智能体生态系统的文档化追踪说明了无管理的错误记忆持久化、批准的制度记忆、拒绝和修订、身份保持扩展以及作为学习的治理。

## 核心贡献

### 1. 记忆治理的设计框架
文章的核心贡献是将记忆治理问题形式化为**选择机制设计**。关键洞察：记忆治理不是关于检索准确性，而是关于**哪些记忆应该成为跨智能体共享的制度性状态**。

### 2. 四种选择 regime
- **无治理持久化（Ungoverned Persistence）**：记忆一旦写入就永久保留，无选择机制
- **宪政/混合选择（Constitutional/Hybrid Selection）**：由规则或策略驱动的选择
- **自动基于指标的选择（Automatic Metric-based Selection）**：由精确度、相关性等指标驱动
- **人类批准的人工选择（Human-ratified Artificial Selection）**：关键记忆由人类批准成为共享状态

### 3. 分层记忆架构
提出四层记忆架构：
1. **Agent-Local Memory**：单个智能体的私有记忆
2. **Shared Institutional Memory**：跨智能体共享的制度性记忆
3. **Archive Memory**：归档的长期记忆
4. **Project-Continuity Memory**：项目连续性相关的记忆

### 4. 可审查的选择机制
通过**起源（Provenance）和版本 lineage** 使记忆选择过程可追踪和审查。

## 为什么重要

1. **范式转变**：从"检索准确性"到"选择治理"——记忆系统设计的根本问题不仅是"如何检索"，更是"哪些记忆应该存在"

2. **多智能体系统的现实需求**：当多个智能体共享记忆时，缺乏治理会导致错误记忆的级联传播

3. **设计空间明确化**：四种选择 regime 不是优劣之分，而是针对不同应用场景的设计选择

## 与移动端/端侧的相关性

1. **边缘部署的多智能体**：移动端的多智能体系统（如多个本地 AI 助手协作）同样面临哪些信息值得共享的问题

2. **隐私与效率的权衡**：端侧设备在资源受限环境下，需要决定哪些记忆值得保留在本地、哪些可以丢弃

3. **选择性遗忘的实现**：本文的"选择 regime"框架为端侧记忆的智能压缩提供了理论基础

## 关键洞察

> "Memory governance functions as a selection regime, determining which memory variants persist, which remain private, and which are rejected, abstained from, or superseded."

这篇文章是**Viewpoint论文**，不是实证研究。它的价值在于提出了一个**记忆系统设计的新框架**——将记忆治理概念化为选择机制设计。这个视角对于构建真实世界的多智能体记忆系统具有重要的概念性指导意义。

## 参考文献

- 相关工作：MemArchitect (2603.18330) 提出的策略驱动记忆治理层
- 相关工作：When to Forget (2604.12007) 提出的记忆治理原语
- 相关工作：TreeMem (2605.04811) 提出的多智能体记忆信用分配
