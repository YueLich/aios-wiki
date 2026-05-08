---
title: "STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?"
arXiv: 2605.06527
date: 2026-05-07
tags: [agent-memory, memory-retrieval, memory-governance, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?
- **作者**: Hanxiang Chao, Yihan Bai, Rui Sheng, Tianle Li, Yushi Sun
- **发表**: 2026-05-07
- **方向**: Agent 记忆有效性 / 记忆更新 / 记忆治理

## 核心问题

LLM Agent 被期望维护长期记忆，但现有基准主要评测静态事实检索，**忽略了记忆"过时"后的 Belief Revision 能力**。当新观察到的信息使旧记忆失效（而非显式否定）时，Agent 需要通过上下文推理和常识来判断记忆是否过时——这一能力此前几乎未被系统研究。

## 核心贡献

### 1. 识别关键失败模式：Implicit Conflict

论文定义了 **Implicit Conflict**（隐式冲突）：后续观察在未明确否定旧记忆的情况下使其失效，需要 Agent 通过语境推理和常识来检测。这种失效模式在现实场景中极为常见，例如：

- 用户搬家后，原地址记忆仍然"正确"但已过时
- 医生读取的历史病历与最新检查结果矛盾
- 项目进展中，之前的决策在新信息出现后需要重新评估

### 2. STALE 基准

构建了 **STALE 基准**，包含：
- 400 个专家验证的冲突场景
- 1200 个评估查询，分布在三个维度
- 覆盖 100+ 日常生活主题
- 上下文最长 150K tokens

### 3. 三维探测框架

| 维度 | 含义 | 评测内容 |
|------|------|---------|
| **State Resolution** | 状态解析 | 检测先前信念是否已过时 |
| **Premise Resistance** | 前提抵抗 | 拒绝错误预设过时状态的问题 |
| **Implicit Policy Adaptation** | 隐式策略适应 | 在下游行为中主动应用更新后的状态 |

### 4. CUPMem 基线系统

提出 **CUPMem**（Contextual Update Propagation Memory）原型，通过以下机制实现状态感知的记忆写入：
- **Structured State Consolidation**：结构化状态整合
- **Propagation-Aware Search**：传播感知搜索
- 强调显式状态判决（explicit state adjudication）是构建稳健 Agent 记忆的有前景方向

## 实验发现

对前沿 LLM 和专门记忆框架的系统评测揭示了普遍差距：

- 最佳模型在 STALE 总体准确率仅 **55.2%**
- 模型经常接受嵌入用户问题中的过时假设
- 模型难以识别一个方面的状态变化何时应该使相关记忆失效
- 即使能检索到更新证据，模型也难以据此行动

## 为什么重要

1. **填补空白**：首次系统研究 LLM Agent 的 Belief Revision 能力
2. **现实意义**：Implicit Conflict 比显式否定更常见，更贴近真实世界记忆失效模式
3. **可行动方向**：CUPMem 证明了显式状态判决的有效性，为未来记忆治理研究提供新思路

## 与移动端/端侧的相关性

记忆有效性判断直接影响端侧记忆系统的可靠性。STALE 揭示的 55.2% 准确率意味着当前系统有近一半场景无法正确处理记忆过时问题。对边缘部署尤为重要——端侧 Agent 需要在有限计算资源下完成复杂的上下文推理来判断记忆有效性。

## 参考

- GitHub: (未公开)
- arXiv: https://arxiv.org/abs/2605.06527
