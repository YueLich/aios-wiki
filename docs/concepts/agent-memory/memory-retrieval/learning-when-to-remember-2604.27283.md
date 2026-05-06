---
title: "Learning When to Remember: Risk-Sensitive Contextual Bandits for Abstention-Aware Memory Retrieval in LLM-Based Coding Agents"
arXiv: 2604.27283
date: 2026-04-30
tags: [agent-memory, memory-retrieval, risk-sensitive, coding-agents]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Mehmet Iscan (Yildiz Technical University, PythaLab)
- **提交日期**: 2026-04-30
- **方向**: 记忆检索 / 风险敏感决策 / 选择性遗忘

## 摘要

基于LLM的编程Agent越来越依赖外部记忆来复用先前的调试经验、修复轨迹和仓库本地操作知识。然而，检索到的记忆只有在当前失败与之前的失败真正兼容时才有价值——栈跟踪、终端错误、路径或配置症状的表面相似性可能导致不安全的记忆注入。

本文将记忆使用重新定义为选择性、风险敏感的控制问题，而非单纯的Top-k检索问题。提出RSCB-MC（风险敏感上下文多臂老虎机记忆控制器），决定Agent是使用无记忆、注入最佳方案、总结多个候选、执行高精度或高召回检索、选择 abstain，还是请求反馈。

## 核心贡献

1. **风险敏感记忆控制**：将记忆使用重新定义为选择性控制问题，而非Top-k检索
2. **RSCB-MC框架**：16维上下文状态特征，包括相关性、不确定性、结构兼容性、反馈历史、假阳性风险、延迟、token成本
3. **pattern-variant-episode模式**：存储可重用的issue知识
4. **abstention作为安全动作**：非注入和abstention是一等安全行为（奖励设计对假阳性注入的惩罚强于错失复用）
5. **零假阳性率**：在确定性smoke-scale artifacts上保持0.0%假阳性率

## 方法详解

**记忆控制器决策空间**：
- 无记忆（No Memory）
- 注入最佳方案（Inject Top Resolution）
- 总结多个候选（Summarize Candidates）
- 高精度检索（High-Precision Retrieval）
- 高召回检索（High-Recall Retrieval）
- Abstain（选择不检索）
- 请求反馈（Ask for Feedback）

**16维状态特征**：
1. 相关性得分（retrieval relevance）
2. 不确定性（uncertainty）
3. 结构兼容性（structural compatibility）
4. 反馈历史（feedback history）
5. 假阳性风险（false-positive risk）
6. 延迟（latency）
7. Token成本（token cost）
8-16. 其他上下文特征（任务类型、Agent类型等）

**奖励设计**：
```
R = 成功复用×奖励 - 假阳性注入×高惩罚 - 延迟成本 - token成本
```
假阳性惩罚 >> 错失复用惩罚，使得"不检索"成为合理选项。

**pattern-variant-episode模式**：
- **Pattern**：问题类型的通用结构（如"NullPointerException in method X"）
- **Variant**：具体变体（如具体的类名、方法名）
- **Episode**：完整的调试历史（尝试过的修复、失败原因）

## 为什么重要

对于编程Agent记忆，核心问题不仅是"哪个记忆最相似"，而是"检索到的记忆是否安全到足以影响调试轨迹"。这个视角转变对于在真实代码库中安全部署记忆增强Agent至关重要。零假阳性率的设计在生产环境中有直接价值。

## 与端侧/移动端的相关性

- **高度端侧相关**：微秒级决策延迟（p95=331μs），可在实时推理中部署
- 16维特征适合轻量级模型预测
- Token成本优化对资源受限设备有价值
- 隐私敏感的代码记忆（不向云端暴露内部实现细节）

## 实验结果

**确定性smoke-scale artifacts**：
- RSCB-MC非预言重放成功率：62.5%（最强）
- 假阳性率：0.0%（安全保证）

**200-case hot-path验证**：
- 代理成功率：60.5%
- 假阳性率：0.0%
- p95决策延迟：331微秒

## 核心洞察

> "对于编程Agent记忆，核心问题不仅是哪个记忆最相似，而是检索到的记忆是否安全到足以影响调试轨迹。"

这个重新定义对记忆系统的设计有根本性启示：
1. 不是"找到越多越好"而是"找错了不如不找"
2. Abstention是一种应该被主动学习的策略，而非被迫选项
3. 假阳性代价远高于假阴性——安全比召回更重要
