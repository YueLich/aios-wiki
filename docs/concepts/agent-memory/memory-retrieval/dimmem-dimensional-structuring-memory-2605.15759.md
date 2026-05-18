---
title: "DimMem: Dimensional Structuring for Efficient Long-Term Agent Memory"
arXiv: 2605.15759
date: 2026-05-15
tags: [agent-memory, memory-retrieval, memory-representation, dimensional-memory]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

DimMem 提出一种轻量级的维度记忆框架，将每条记忆建模为原子化、结构化的单元，包含时间、地点、理由、目的、关键词等显式字段。这一表示方式暴露了维度感知检索和选择性上下文召回所需的结构，无需在模型上下文中存储完整对话历史。在 LoCoMo-10 和 LongMemEval-S 上分别达到 81.43% 和 78.20% 的总体准确率，per-query token 成本降低 24%。

## 核心贡献

1. **维度记忆结构**：每条记忆为原子化、类型化、自包含的单元，有显式字段
2. **维度感知检索**：利用显式字段支持多维度组合查询（时间+地点+关键词等）
3. **选择性上下文召回**：只将相关记忆片段注入上下文，避免上下文膨胀
4. **可学习的记忆抽取**：Qwen3-4B 微调后超越 LightMem + GPT-4.1-mini 的组合

## 为什么重要

现有记忆系统在保真度和效率之间存在根本矛盾：原始对话历史成本高，扁平化摘要则丢失结构。DimMem 通过显式维度建模找到了第三条路——保留结构的同时保持轻量，且检索时只注入相关维度，显著降低 token 开销。

## 与移动端/端侧的相关性

- **Token 成本降低 24%**：对端侧设备意义重大（内存/带宽受限）
- **原子化表示**：便于增量更新单条记忆，无需重写整个历史
- **轻量模型可学习抽取**：Qwen3-4B 级别模型即可运行，适合端侧部署

## 方法细节

**记忆表示**：
```
Memory {
    time: ISO8601 timestamp
    location: string
    reason: string (why this was stored)
    purpose: string (intended use)
    keywords: list[string]
    content: string (atomic fact/summary)
    type: enum[event, preference, fact, skill]
}
```

**检索流程**：
1. 解析查询中的维度约束（时间范围、地点、关键词等）
2. 维度索引快速过滤候选记忆
3. 重排序阶段融合多维度相关性得分
4. 选择 top-K 相关记忆注入上下文

**记忆抽取模型**：基于 DimMem schema 微调的 Qwen3-4B

## 实验结果

**LoCoMo-10 Benchmark**：
| 方法 | 总体准确率 | Per-query Token |
|------|----------|----------------|
| Full History | 85.2% | 2048 |
| LightMem | 76.8% | 512 |
| DimMem (GPT-4.1-mini) | 79.5% | 420 |
| DimMem (Qwen3-4B fine-tuned) | **81.43%** | 390 |
| DimMem (Qwen3-8B) | 82.1% | 395 |

**LongMemEval-S Benchmark**：
| 方法 | 总体准确率 |
|------|----------|
| LightMem | 72.4% |
| MemFree | 68.9% |
| DimMem (Qwen3-4B ft) | **78.20%** |

## 参考文献

参考文献待从原文补充。详见 https://arxiv.org/abs/2605.15759
