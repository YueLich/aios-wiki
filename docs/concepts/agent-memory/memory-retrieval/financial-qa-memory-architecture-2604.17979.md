---
title: "Architecture Matters More Than Scale: A Comparative Study of Retrieval and Memory Augmentation for Financial QA Under SME Compute Constraints"
arXiv: "2604.17979"
date: "2026-04-20"
tags: [agent-memory, memory-retrieval, memory-representation, financial-ai]
reviewer: auto
source: arXiv RSS/API
---

# Architecture Matters More Than Scale: A Comparative Study of Retrieval and Memory Augmentation for Financial QA Under SME Compute Constraints

## 摘要

AI 和 LLM 正在通过自然语言界面革新金融分析，但中小企业（SME）在基础设施方面面临严重限制——缺乏云 GPU 预算、专职 AI 团队和 API 级推理能力。本研究引入 SME 约束评估设置，使用本地托管的 8B 参数指令微调模型，在 FinQA 和 ConvFinQA 基准上系统比较四种推理架构：基线 LLM、检索增强生成（RAG）、结构化长期记忆和记忆增强会话推理。研究发现一致的架构反转：结构化记忆提高确定性任务的精度，而检索方法在会话隐式引用场景中优于记忆中心方法。

## 核心贡献

1. **SME 约束评估框架**：首个明确针对中小企业计算约束的金融 QA 评估设置

2. **架构对比系统研究**：在真实部署环境下隔离架构选择的影响，而非单纯追求模型规模

3. **架构反转发现**：
   - 结构化记忆：更适合确定性、显式操作数任务（数值推理）
   - 检索方法：更适合会话式、隐式引用场景（对话理解）

4. **混合部署框架**：提出动态选择推理策略的混合框架，平衡数值精度、可审计性和基础设施效率

## 为什么重要

这项研究直接回应了 AI 落地中的核心问题：中小企业如何在大模型时代利用 AI？研究发现模型规模不是唯一决定因素，架构选择对特定任务类型有显著影响。这为资源受限的组织提供了切实可行的部署策略，而非盲目追求最大的模型。

## 与移动端/端侧相关性

1. **端侧部署友好**：8B 参数模型可在消费级 GPU 上运行，适合端侧
2. **架构效率优先**：研究证明架构选择比模型规模更重要，为端侧优化指明方向
3. **混合记忆策略**：动态选择记忆/检索策略适配不同任务类型
4. **隐私保护**：本地部署避免了敏感金融数据上传云端

## 相关论文

- Memanto (2604.22085) 面向长期 Agent 的类型化语义记忆
- GraphPlanner (2604.23626) 图记忆增强的 Agent 路由
- TiMem (2601.02845) 时间层次记忆树
