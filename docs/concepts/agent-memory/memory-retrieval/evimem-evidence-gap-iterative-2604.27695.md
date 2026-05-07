---
title: "EviMem: Evidence-Gap-Driven Iterative Retrieval for Long-Term Conversational Memory"
arXiv: 2604.27695
date: 2026-04-30
tags: [agent-memory, memory-retrieval, iterative-retrieval, conversational-memory]
reviewer: auto
source: arXiv RSS/API
---

# EviMem: Evidence-Gap-Driven Iterative Retrieval for Long-Term Conversational Memory

## 论文信息

- **arXiv ID**: 2604.27695
- **作者**: Yuyang Li, Yime He, Zeyu Zhang, Dong Gong
- **发表日期**: 2026-04-30
- **方向**: 记忆的检索与利用
- **代码**: https://github.com/AIGeeksGroup/EviMem

## 摘要（翻译）

长期对话记忆需要检索分散在多个会话中的证据，但单次检索在时间和多跳问题上失败。现有迭代方法通过生成内容或文档级信号细化查询，但没有系统诊断证据缺口——即当前累积检索集中缺少什么——导致查询细化缺乏目标。

EviMem 结合了：
- **IRIS**（Iterative Retrieval via Insufficiency Signals）：通过充分性评估检测证据缺口、诊断缺少的内容、并驱动有针对性的查询细化
- **LaceMem**（Layered Architecture for Conversational Evidence Memory）：支持细粒度缺口诊断的粗到细记忆层次结构

在 LoCoMo 上，EviMem 在时间问题上将 Judge Accuracy 从 73.3% 提升到 81.6%，在多跳问题上从 65.9% 提升到 85.2%，延迟降低 4.5 倍。

## 核心贡献

### 1. IRIS：证据缺口驱动的迭代检索

核心洞察：**迭代检索的关键不是生成更多内容，而是诊断还缺什么**

IRIS 四步闭环：
1. **充分性评估**：判断当前累积证据是否足够回答查询
2. **缺口诊断**：如果不足，具体指出缺少什么类型的证据
3. **查询细化**：根据缺口生成更有针对性的查询
4. **迭代**：重复直到充分或达到最大迭代次数

### 2. LaceMem：层级对话证据记忆

粗到细的三层记忆结构：

| 层级 | 粒度 | 用途 |
|-----|------|------|
| 会话层 | 完整会话 | 快速定位相关会话 |
| 片段层 | 会话内片段 | 精确定位相关段落 |
| 证据层 | 单个事实/引用 | 最细粒度的证据提取 |

### 3. 证据缺口量化

EviMem 引入证据覆盖率的量化指标：
- 明确计算当前检索集对查询的覆盖率
- 覆盖率 < 阈值时触发迭代
- 诊断结果直接指导查询重写

## 实验结果

| 问题类型 | MIRIX | EviMem | 提升 |
|---------|-------|--------|-----|
| 时间推理 | 73.3% | 81.6% | +8.3pp |
| 多跳推理 | 65.9% | 85.2% | +19.3pp |
| 延迟 | 基准 | 0.22x | 4.5x 降低 |

## 为什么重要

EviMem 解决了长期对话记忆检索的一个根本性问题：**单次检索无法处理跨会话的复杂查询**。

关键贡献：
1. **证据缺口诊断**：首次在迭代检索中引入明确的缺口检测，而非盲目生成
2. **多跳推理大幅提升**：85.2% 的多跳准确率说明层次结构和迭代策略的有效性
3. **4.5x 延迟降低**：高效的实现来自精确的检索而非穷举

## 与端侧/移动端相关性

1. **多跳推理能力**：移动端 Agent 常需要跨会话推理（"上次我提到的那个项目怎么样了"）
2. **延迟优化**：4.5x 延迟降低对移动端用户体验至关重要
3. **分层结构**：粗到细的层次结构适合移动端的资源分级利用
