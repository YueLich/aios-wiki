---
title: "Memory-Efficient Looped Transformer: Decoupling Compute from Memory in Looped Language Models"
arXiv: 2605.07721
date: 2026-05-08
authors: ["Victor Conchello Vendrell", "Arnau Padres Masdemont", "Niccolò Grillo", "Jordi Ros-Giralt", "Arash Behboodi", "Fabio Valerio Massoli"]
tags: [agent-memory, memory-compression, KV-cache, loop-transformer]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2605.07721
- **作者**: Victor Conchello Vendrell, Arnau Padres Masermont, Niccolò Grillo, Jordi Ros-Giralt, Arash Behboodi, Fabio Valerio Massoli
- **提交日期**: 2026-05-08
- **方向**: 记忆压缩 / KV Cache 优化 / 循环语言模型
- **类别**: cs.CL

## 摘要

循环 LLM 架构作为提升推理能力的方向受到广泛关注，它们能够在嵌入空间内执行多步计算而无需生成中间 token。以 Ouro 为代表的模型通过迭代更新内部表示来进行推理，同时在每次迭代中保留标准 Key-Value (KV) Cache，导致内存消耗随推理深度线性增长。因此，增加推理迭代次数会带来难以承受的内存使用，限制了这类架构的实际扩展性。

本文提出 **Memory-Efficient Looped Transformer (MELT)**，一种将推理深度与内存消耗解耦的新型架构。MELT 不再每层每迭代维护独立的标准 KV Cache，而是维护一个跨所有迭代共享的单一 KV Cache，并辅以轻量级"草稿本"(scratchpad) 机制处理中间计算。这一设计在保持推理能力的同时大幅降低了内存开销。

## 核心贡献

1. **架构解耦**：将计算状态与记忆状态分离，使无界推理步数成为可能，同时避免线性增长的内存开销

2. **单一共享 KV Cache**：在所有循环迭代中维护一个持久化缓存，草稿本负责临时计算
   - 传统循环模型：每迭代 × 每层 = O(n × L) 内存
   - MELT：O(L) 内存（与迭代次数无关）

3. **理论分析**：证明 MELT 在显著降低内存的同时保持了与标准循环 Transformer 等效的表达能力

4. **实验验证**：MELT 在保持相当推理性能的同时，峰值内存使用降低了最高 10 倍

5. **与 Agent 记忆系统的直接关联**：
   - 解决 Agent 多步推理时 KV Cache 持续膨胀的问题
   - 支持更深层的思考链而不受内存约束
   - 草稿本机制为 Agent 的工作记忆与长期记忆分离提供了架构参考

## 为什么重要

当前 Agent 系统的核心瓶颈之一是 KV Cache 的内存成本。随着 Agent 需要处理更长的对话历史、更复杂的推理链条，KV Cache 的线性增长严重限制了系统的实际可用深度。

MELT 通过解耦计算与记忆状态，为这一问题提供了架构级解决方案。这一思路对 Agent 记忆系统的设计有重要启示：
- **动态内存管理**：不是所有中间状态都需要保留在注意力缓存中
- **分层记忆架构**：草稿本（计算状态）与共享 KV Cache（记忆状态）的分离，类似于 Agent 的工作记忆与长期记忆的分离
- **端侧可行性**：10 倍内存降低使复杂推理在边缘设备上成为可能

## 与端侧/移动端的相关性

1. **内存受限设备**：移动端/边缘设备的 KV Cache 容量有限，MELT 的常数级内存占用直接解决了这一问题
2. **可穿戴/IoT Agent**：对内存极其敏感的可穿戴 AI 助手场景，MELT 提供了在有限硬件上运行深度推理的可能性
3. **能效优化**：内存访问是 AI 芯片的主要能耗来源之一，10 倍内存降低意味着显著的能效提升
4. **实时响应**：降低内存占用的同时保持推理能力，支持更快的响应速度

## 参考文献

- Ouro (循环 LLM 推理架构)
- Standard KV Cache 机制
- Memory-compressed attention
