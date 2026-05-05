---
title: "Novel Memory Forgetting Techniques for Autonomous AI Agents: Balancing Relevance and Efficiency"
arXiv: 2604.02280
date: 2026-04-02
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Novel Memory Forgetting Techniques for Autonomous AI Agents: Balancing Relevance and Efficiency

## 论文基本信息

- **作者**: Payal Fofadiya, Sunil Tiwari
- **arXiv**: https://arxiv.org/abs/2604.02280
- **领域**: cs.AI, cs.CV
- **类别**: 记忆压缩 → 自主 AI Agent → 自适应遗忘框架

## 摘要（翻译）

长程对话智能体需要持久记忆以保持连贯推理，但不受控制的记忆积累会导致时间衰减和错误记忆传播。Benchmarks 如 LOCOMO 和 LOCCO 报告性能从 0.455 降至 0.05，MultiWOZ 在持久保留下显示 78.2% 准确率但有 6.8% 错误记忆率。本文提出一种**自适应预算遗忘框架**（adaptive budgeted forgetting framework），通过相关性引导评分和有界优化来调节记忆。该方法整合了**时效性、频率和语义对齐**三个维度来维持约束上下文下的稳定性。对比分析表明，该方法在长程 F1 上超越 0.583 基线水平，保持更高的记忆一致性，并减少了错误记忆行为，同时不增加上下文使用量。

## 核心贡献

1. **自适应预算遗忘框架**：提出首个显式建模"遗忘价值"的 Agent 记忆管理框架，而非被动保留所有记忆。
2. **多维度相关性评分**：整合 recency（时效性）、frequency（频率）、semantic alignment（语义对齐）三个维度评估记忆单元的保留价值。
3. **有界优化保证**：将记忆管理建模为有约束的优化问题，在记忆预算内最大化整体相关性。
4. **错误记忆抑制**：显著降低错误记忆传播（从 6.8% 下降），提升 Agent 在长程交互中的可靠性。
5. **上下文效率不降低**：在不增加上下文使用量的情况下改善了记忆质量。

## 研究背景与问题

### 长程 Agent 的记忆困境
现代 LLM Agent 通常配备记忆模块来存储历史交互，但随着对话长度增加，记忆面临两个核心挑战：
- **时间衰减**（Temporal Decay）：旧记忆对当前任务的相关性自然下降，但简单截断会导致重要上下文丢失
- **错误记忆传播**（False Memory Propagation）：模型在生成时可能混淆记忆与虚构内容，尤其在记忆高度冗余时

Benchmark 数据说明问题严重性：LOCOMO 和 LOCCO 报告性能从初始的 0.455 降至 0.05（下降 89%），MultiWOZ 显示 6.8% 的错误记忆率——意味着每 15 次交互就有 1 次记忆错误。

### 为什么简单截断不够
- 固定窗口截断（Fixed Window）：丢弃最旧的记忆，但可能丢失关键上下文（如用户的长期偏好、跨会话的约束条件）
- 基于重要性的截断：需要预先定义重要性函数，实际中很难准确评估

### 本文方法的核心洞察
遗忘不应是被动的、均匀的，而应是**主动的、有策略的**——每个记忆单元都应该竞争有限的记忆预算，而竞争的成功与否取决于其综合相关性评分。

## 核心方法

### 三维度相关性评分
每个记忆单元 $m_i$ 计算综合评分：
$$Score(m_i) = \alpha \cdot Recency(m_i) + \beta \cdot Frequency(m_i) + \gamma \cdot SemanticAlign(m_i)$$

- **Recency** $R(m_i)$：时间衰减函数，通常为指数衰减，衡量记忆对当前时刻的相关性
- **Frequency** $F(m_i)$：历史访问频率，多次被召回的记忆更有价值
- **Semantic Alignment** $S(m_i)$：与当前对话上下文的语义相似度，用嵌入向量余弦相似度衡量

权重 $\alpha, \beta, \gamma$ 可通过验证集自动学习。

### 有界优化框架
在记忆预算 $B$（如最大记忆条目数或 token 限制）下，最大化总相关性：
$$\max \sum_i Score(m_i) \quad \text{s.t.} \quad \sum_i Cost(m_i) \leq B$$

这是一个背包问题（knapsack problem），作者采用贪心近似求解以保证实时性。

### 遗忘触发机制
- **被动触发**：新记忆进入时，若超出预算，触发遗忘
- **主动刷新**：定期重新评估所有记忆的相关性，动态调整保留策略

## 实验结果

- 长程 F1 达到 0.583 以上（超越基线）
- 错误记忆率显著降低
- 上下文 token 使用量不增加（记忆质量提升但总量不变）
- 在 MultiWOZ 和 LOCOMO 数据集上验证

## 为什么重要

1. **首个显式遗忘框架**：将记忆管理从被动保留转变为主动选择遗忘
2. **多维度评估更全面**：仅考虑 recency 的方法（如 LRU）会丢失长期偏好信息；本文方法同时捕获 recency + frequency + semantic relevance
3. **错误记忆问题直接解决**：错误记忆传播是长程 Agent 的核心信任问题，本文通过遗忘机制抑制了这个问题

## 与移动端/端侧相关性

**高度相关**：

- **移动端 Agent 的核心挑战**：移动端 AI 助手需要在有限内存中运行长程任务（如健康管理、个人助手），本文方法直接解决内存约束问题
- **错误记忆在端侧更危险**：端侧 Agent 通常处理敏感个人信息（如健康、财务），错误记忆可能导致误导性建议
- **计算开销低**：贪心近似在推理时计算量极小，适合实时移动端部署
- **与 RAG 互补**：本文管理 Agent 内部记忆，RAG 管理外部知识库，两者结合可构建完整的端侧记忆系统

**关键词**：选择性遗忘、记忆预算、长程对话 Agent、错误记忆抑制、相关性评分、移动端记忆管理
