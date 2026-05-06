---
title: "MEMAUDIT: An Exact Package-Oracle Evaluation Protocol for Budgeted Long-Term LLM Memory Writing"
arXiv: 2605.02199
date: 2026-05-04
tags: [agent-memory, memory-retrieval, memory-evaluation]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **标题**: MEMAUDIT: An Exact Package-Oracle Evaluation Protocol for Budgeted Long-Term LLM Memory Writing
- **arXiv ID**: 2605.02199
- **作者**: Nishant Bhargava, Rodrigo Sobral Barrento
- **发表时间**: 2026-05-04
- **方向**: Agent 记忆系统 · 记忆评估 · 记忆写入

## 摘要

长期 LLM Agent 必须将过去的交互流压缩为持久记忆，以便未来查询使用。现有评估通常测量最终的问答准确率，这会将**记忆写入**与**检索、提示、读者推理**纠缠在一起，无法单独评估记忆写入的质量。

本文提出 **MEMAUDIT**，一个用于预算约束下长期记忆写入的**精确 Package-Oracle 评估协议**。

### 核心思想

MEMAUDIT Package 将以下要素固定：
- 经验流（experience stream）
- 候选记忆表示
- 存储成本
- 语义证据单元
- 未来查询需求
- **预算**

这将写入时的记忆选择转变为一个**可审计的有限优化问题**，具有经认证的分母。

### 技术方案

- 使用**凹过模块化语义覆盖目标**（concave-over-modular semantic coverage objective）
- 在存储和「每经验一个表示」约束下
- 使用**分支定界 + MILP 认证**计算精确 Package 最优解

### 评估结果

在以下场景进行验证：
- 受控精确 Package
- 有效性压力测试
- 人工审计的自然支持切片
- 导出的 Mem0、A-Mem、Letta 存储

**关键发现**: MEMAUDIT 能够分离：
1. 表示质量
2. 有效性状态保持
3. 预算感知选择效果

这些是端到端 QA 无法定位的。

## 核心贡献

| 贡献点 | 具体描述 |
|--------|----------|
| Package-Oracle 协议 | 首次将记忆写入评估形式化为可审计优化问题 |
| MILP 认证求解器 | 提供精确最优解的分支定界算法 |
| 分离分析能力 | 解耦表示质量、有效性保持、预算选择三要素 |
| 真实系统评估 | 支持 Mem0、A-Mem、Letta 存储的评分导出 |

## 技术框架

```
MEMAUDIT Package 构成:
├── Experience Stream (E₁, E₂, ..., Eₙ)
├── Candidate Memory Representations (R₁, R₂, ..., Rₘ)
├── Storage Costs (c₁, c₂, ..., cₘ)
├── Semantic Evidence Units
├── Future Query Requirements
└── Budget B

目标: max Σᵢ wᵢ · v(semantic_coverage(R_selected, Eᵢ))
约束: Σⱼ cⱼ · [Rⱼ ∈ selected] ≤ B
      |selected ∩ Eᵢ| ≤ 1, ∀i
```

## 为什么重要

### 现有评估的问题

当前评估（QA 准确率）的局限性：
- **纠缠效应**: 无法区分记忆写入质量 vs 检索质量 vs 推理质量
- **预算模糊**: 不清楚系统在固定存储预算下的真实表现
- **选择盲区**: 无法评估什么被选择了、什么被遗忘了

### MEMAUDIT 的价值

1. **诊断能力**: 精确定位记忆系统的弱点在写入、存储还是检索
2. **预算可比性**: 不同系统在相同预算下的公平对比
3. **可审计性**: MILP 认证保证结果可复现

## 与移动端/端侧相关性

**高相关性**：
- 预算约束评估对存储受限的端侧设备至关重要
- 分离分析帮助设计高效记忆压缩策略
- 支持离线场景下的记忆管理评估

**应用场景**：
- 智能手表/可穿戴设备的记忆容量规划
- 移动端 Agent 的存储预算分配
- 边缘服务器的内存管理策略

## 开源资源

本文提供：
- 可复用的 Package 生成器
- 认证求解器
- 自然 Package 导出
- 外部系统评分器
- 可重现性元数据缓存

## 相关论文

- Mem0 (2026) — 令牌高效算法
- A-MEM — 重要性感知记忆压缩
- Letta — 记忆管理框架
- LongMemEval — 长期记忆基准

## 参考链接

- arXiv: https://arxiv.org/abs/2605.02199
