---
title: IdeaForge: A Knowledge Graph-Grounded Multi-Agent Framework for Cross-Methodology Innovation Analysis and Patent Claim Generation
arXiv: 2605.13311
date: 2026-05-13
tags: [agent-memory, memory-representation, knowledge-graph, multi-agent, creativity]
reviewer: auto
source: arXiv RSS/API
---

# IdeaForge: A Knowledge Graph-Grounded Multi-Agent Framework for Cross-Methodology Innovation Analysis and Patent Claim Generation

## 论文信息

- **arXiv**: 2605.13311
- **作者**: Joy Bose
- **发表日期**: 2026-05-13
- **类别**: cs.AI
- **主题**: 知识图谱增强的多 Agent 创新分析框架

## 摘要

IdeaForge 是一个基于知识图谱的多 Agent 框架，用于创新分析和专利声明生成。该框架集成了 TRIZ、Design Thinking 和 SCAMPER 三种创新方法论，通过专业 Agent 在 FalkorDB 知识图谱上协作。每个 Agent 贡献结构化的实体和关系，代表矛盾、发明原理、用户需求、转换、类比和候选声明。核心贡献是跨方法论收敛机制——通过图结构将多种方法论独立支持的声明连接起来（CONVERGENT 关系），从而识别高置信度的创新候选。

## 核心贡献

1. **多方法论集成**：TRIZ、Design Thinking、SCAMPER 三种创新方法论的统一知识图谱表示
2. **跨方法论收敛机制**：通过 CONVERGENT 关系连接多方法论支持的声明，识别高置信度创新候选
3. **InnovationScore 公式**：综合考虑收敛支持度、方法多样性、声明强度和现有技术挑战数量
4. **专利起草 Agent**：基于收敛声明子图生成结构化专利草案，减少对不受约束的 LLM 生成的依赖

## 技术详解

### 问题背景

现有 AI 辅助创新系统的局限：
- 单一方法论，无法融合多种思维框架
- 顺序式 prompt 工作流，不保留中间推理结构
- 缺乏可追溯性和可解释性

### 框架设计

IdeaForge 的核心架构：

1. **知识图谱层**：FalkorDB 持久化存储，实体包括矛盾、发明原理、用户需求、转换、类比、候选声明
2. **专业 Agent**：
   - TRIZ Agent：处理矛盾和发明原理
   - Design Thinking Agent：处理用户需求和转换
   - SCAMPER Agent：处理类比和候选声明
3. **收敛检测**：识别被多种方法论独立支持的声明，建立 CONVERGENT 关系
4. **专利起草**：基于收敛声明子图生成结构化专利草案

### 知识图谱模式

关键实体类型：
- `矛盾（Contradiction）`
- `发明原理（Inventive Principle）`
- `用户需求（User Need）`
- `转换（Transformation）`
- `类比（Analogy）`
- `候选声明（Candidate Claim）`

关键关系类型：
- `SUPPORTED_BY`：声明被某方法论支持
- `CONVERGENT`：声明被多种方法论同时支持

### 性能评估

在法律技术用例上的实验表明：
- 图增强的多方法论综合比单一方法论基线产生更多样化和可追溯的创新候选
- CONVERGENT 声明具有更高的 InnovationScore

## 为什么重要

IdeaForge 展示了知识图谱作为多 Agent 共享记忆的有效性：
- **持久化推理结构**：不像传统 prompt 链，知识图谱保留了完整的中间推理状态
- **跨方法论收敛**：通过图结构自然地融合多种创新方法论
- **可解释性强**：每条声明都有明确的方法论来源和推理路径
- **高质量输出**：InnovationScore 提供系统性的候选评估

## 与端侧/移动端的相关性

- **知识图谱本地存储**：知识图谱可以本地构建和查询，适合端侧部署
- **模块化 Agent 设计**：各专业 Agent 可独立运行，便于在移动端裁剪
- **图遍历计算效率**：相比全上下文输入，图遍历更适合资源受限环境
- **可追溯性**：对于需要审计和解释的应用（医疗、法律）尤为重要
