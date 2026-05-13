---
title: "Memory Transfer Learning: How Memories are Transferred Across Domains in Coding Agents"
arXiv: 2604.14004
date: 2026-04-15
tags: [agent-memory, memory-representation, coding-agents, cross-domain]
reviewer: auto
source: arXiv RSS/API
---

# Memory Transfer Learning: How Memories are Transferred Across Domains in Coding Agents

## 论文信息

- **arXiv ID**: 2604.14004
- **发表日期**: 2026-04-15
- **作者**: Kangsan Kim, Minki Kang, Taeil Kim, Yanlai Yang, Mengye Ren, Sung Ju Hwang
- **类别**: cs.AI / cs.CL
- **链接**: https://arxiv.org/abs/2604.14004 | https://memorytransfer.github.io/

## 摘要

Memory-based self-evolution 已成为 Coding Agents 的重要范式。然而，现有方法通常将记忆利用限制在同构任务域中，无法利用跨不同现实世界编程问题存在的共享基础设施基础（如运行时环境、编程语言）。本文提出 **Memory Transfer Learning (MTL)**，通过异构域的统一记忆池来实现跨域记忆迁移。在 6 个编程基准上使用四种记忆表示（从具体执行迹到抽象洞察）进行评估，实验表明跨域记忆平均提升性能 3.7%，主要通过迁移元知识（如验证例程）而非任务特定代码。更重要的是，研究发现**抽象程度决定迁移效果**：高层洞察泛化能力强，而低层执行迹因过度具体化常导致负迁移。此外，记忆迁移效果与记忆池规模正相关，且记忆可在不同模型之间迁移。本文为将记忆利用扩展到单域边界之外提供了实证设计原则。

## 核心贡献

### 1. Memory Transfer Learning (MTL) 框架
提出首个跨异构域的记忆迁移学习框架，将记忆利用从同构任务扩展到跨编程语言、运行时环境的多样化场景。

### 2. 抽象层次决定迁移性
- **高层抽象洞察**（如验证模式、算法策略）→ 泛化性好，跨域迁移有效
- **低层执行迹**（如具体代码片段、调试路径）→ 因过度具体化，常导致负迁移

### 3. 记忆池规模效应
迁移效果随记忆池规模增长，说明构建大规模多样化记忆库的重要性。

### 4. 跨模型记忆迁移
记忆可以在不同底座模型之间迁移，暗示记忆表示的模型无关性潜力。

## 关键发现

| 发现 | 含义 |
|------|------|
| 跨域记忆 +3.7% 性能提升 | 异构域共享的元知识（验证例程）是迁移的有效内容 |
| 抽象度 ↑ = 迁移性 ↑ | 记忆压缩/抽象化对跨域利用至关重要 |
| 记忆池规模正相关 | 大规模多样化记忆库价值高 |
| 跨模型迁移可行 | 记忆表示可独立于底座模型 |

## 为什么重要

1. **突破单域边界**：现有 agent memory 大多困在单一任务域，MTL 证明了跨域记忆的可能性
2. **记忆抽象化的实践指导**：提示 agent memory 系统应优先存储高层策略/模式，而非具体执行细节
3. **多语言/多环境 agent 的基础**：为异构编程环境中的 agent 记忆共享提供理论基础

## 与移动端/端侧相关性

- **端侧部署**：移动端编程 agent（如手机上的代码助手）可受益于跨语言记忆迁移
- **隐私友好**：跨模型迁移意味着记忆可在设备间共享而不暴露具体代码
- **记忆压缩**：研究暗示高层抽象记忆比低层细节更有迁移价值 → 对端侧存储有限场景有指导意义
