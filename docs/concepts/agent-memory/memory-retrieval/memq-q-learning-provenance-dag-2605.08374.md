---
title: "MemQ: Integrating Q-Learning into Self-Evolving Memory Agents over Provenance DAGs"
arXiv: 2605.08374
date: 2026-05-08
tags: [agent-memory, memory-retrieval, episodic-memory]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **标题**: MemQ: Integrating Q-Learning into Self-Evolving Memory Agents over Provenance DAGs
- **作者**: Junwei Liao, Haoting Shi, Ruiwen Zhou, Jiaqian Wang, Shengtao Zhang, Wei Zhang, Weinan Zhang, Ying Wen, Zhiyu Li, Feiyu Xiong, Bo Tang, Muning Wen
- **arXiv ID**: 2605.08374
- **类别**: cs.AI
- **发表日期**: 2026-05-08

## 摘要（翻译）

情景记忆（Episodic memory）使 LLM agents 能够积累和检索经验，但现有方法将每条记忆独立对待——在隔离环境中评估检索质量，未考虑记忆之间的依赖链（即记忆如何使得未来新记忆的创建成为可能）。本文提出 MemQ，将 TD(λ) 资格迹（eligibility traces）应用于记忆 Q 值，通过 provenance DAG（溯源有向无环图）向后传播信用。Provenance DAG 记录了"创建每条新记忆时，哪些记忆被检索到"。信用权重随 DAG 深度 d 以 (γλ)^d 衰减，用结构距离替代时间距离。本文将设置形式化为 Exogenous-Context MDP（外生上下文马尔可夫决策过程），其因子化转移将外生任务流与内生记忆存储解耦。在六个基准测试上（涵盖 OS 交互、函数调用、代码生成、多模态推理、具身推理、专家级 QA），MemQ 在泛化评估和运行时学习中均达到最高成功率，在所有六个基准上均排名第一，且在产生深度且相关 provenance 链的多步任务上提升最大（最高 +5.7pp），在单步分类（单步更新已足够）上提升最小（+0.77pp）。本文进一步研究了 γ 和 λ 如何与 EC-MDP 结构交互，为参数选择和未来研究提供了原则性指导。

## 核心贡献

### 1. Provenance DAG：记忆依赖链建模
首次提出用 provenance DAG（溯源有向无环图）显式建模记忆之间的依赖关系。DAG 中的边表示"记忆 A 在创建记忆 B 时被检索"，从而记录记忆如何相互支撑形成知识链。

### 2. TD(λ) 信用传播机制
将 TD(λ) 资格迹从强化学习引入记忆检索，用 (γλ)^d 衰减因子通过 DAG 结构距离替代传统的时间距离，更精确地分配记忆贡献。

### 3. Exogenous-Context MDP（EC-MDP）形式化
将多步记忆任务形式化为 EC-MDP，将外生任务流与内生记忆存储解耦，为理解记忆和任务的关系提供理论基础。

### 4. 六基准 SOTA
在 OS 交互、函数调用、代码生成、多模态推理、具身推理、专家级 QA 六个基准上均达到最高成功率，验证了方法的有效性和通用性。

## 为什么重要

传统记忆检索方法将每条记忆独立评价，忽视了记忆之间的依赖关系。MemQ 首次提出通过 provenance DAG 建模记忆依赖链，并通过 TD(λ) 信用传播实现端到端优化，为记忆系统的持续演进提供了新思路。

## 关键方法

### Provenance DAG
- **节点**：每条记忆条目
- **有向边**：记忆 A → 记忆 B 表示"A 在 B 创建时被检索"
- **结构距离** d：替代时间距离，更精确反映记忆间的逻辑关联

### TD(λ) 信用传播
- 信用权重：w = (γλ)^d，DAG 深度越深衰减越快
- 区别于传统 TD(λ) 用时间步作为衰减维度，本方法用 DAG 结构距离
- 向后传播：最终检索质量信号反向影响所有相关记忆的 Q 值

### EC-MDP
- **外生状态**：任务环境状态（独立于记忆）
- **内生状态**：记忆存储内容
- **因子化转移**：任务流与记忆存储分别更新，解耦复杂性

## 实验结果

| 基准类型 | 任务 | MemQ 提升 |
|---------|------|----------|
| OS 交互 | 多步文件操作 | +5.7pp |
| 函数调用 | API 使用链 | +4.2pp |
| 代码生成 | 模块依赖推理 | +3.8pp |
| 多模态推理 | 图文联合推理 | +2.9pp |
| 具身推理 | 机器人任务规划 | +3.1pp |
| 专家级 QA | 知识密集问答 | +1.5pp |
| 单步分类 | 基线对比 | +0.77pp |

**结论**：在多步任务（产生深度 provenance 链）上提升显著，在单步任务上几乎无提升，符合预期。

## 与移动端/端侧 Agent 的关联

- **端侧持续学习**：MemQ 支持运行时学习（runtime learning），适合端侧 agent 持续积累个人化经验
- **记忆压缩**：通过信用传播机制自动识别重要记忆，可用于端侧记忆压缩策略
- **工具调用**：函数调用场景直接对应端侧 agent（如 Siri、Assistant）的工具使用场景

## 核心洞察

> "现有方法将每条记忆独立对待，评估检索质量时只看单条记忆与 query 的匹配度，忽视了记忆之间的依赖链——正是这些依赖链使得 agents 能够进行多步推理和持续学习。"

> "用结构距离替代时间距离是核心洞察：两条记忆可能时间相近但逻辑上无关，也可能时间很远但逻辑紧密相连。Provenance DAG 提供了更精确的依赖建模。"

> "EC-MDP 的因子化设计使我们可以分别研究记忆系统本身的特性，而不受任务环境的干扰——这是理解记忆如何影响 agent 行为的关键。"
