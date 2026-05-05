---
title: "GS-Quant: Granular Semantic and Generative Structural Quantization for Knowledge Graph Completion"
arXiv: 2604.21649
date: 2026-04-24
authors: ["Qizhuo Xie", "Yunhui Liu", "Yu Xing", "Qianzi Hou", "Xudong Jin", "Tao Zheng", "Tieke He"]
tags: [agent-memory, memory-representation, knowledge-graph]
reviewer: auto
source: arXiv API
---

## 摘要

GS-Quant 针对大语言模型知识图谱补全（KGC）任务，提出将连续图嵌入与离散 LLM Token 之间的模态差距进行桥接。通过粒化语义增强模块和生成式结构重建模块，生成语义一致且结构分层的离散编码，遵循从粗到细的语言学逻辑。

## 背景问题

现有量化方法将量化视为平坦的数值压缩，导致语义纠缠的编码，无法反映人类推理的层级特性。

## 核心方法

1. **粒化语义增强模块（Granular Semantic Enhancement）**：将层级知识注入码本，确保早期编码捕获全局语义类别，后期编码细化特定属性
2. **生成式结构重建模块（Generative Structural Reconstruction）**：为编码序列施加因果依赖，将独立离散单元转化为结构化语义描述符
3. **词汇扩展**：通过扩展 LLM 词汇表，使其能够像自然语言生成一样对图结构进行推理

## 核心贡献

1. 提出语义一致且结构分层的离散编码生成框架
2. 粒化语义增强模块实现从粗到细的语义捕获
3. 生成式结构重建实现编码序列的因果依赖建模
4. 在知识图谱补全任务上显著优于文本和嵌入基线方法

## 为什么重要

知识图谱是 Agent 记忆系统的重要表示形式，但如何将结构化知识高效融入 LLM 一直是个难题。GS-Quant 通过分层量化的方式，让 LLM 能够理解和推理层级知识关系，对构建更具结构化记忆能力的 Agent 系统有直接参考价值。

## 端侧相关性

- 量化压缩技术可降低知识图谱存储和推理的内存开销
- 离线知识图谱补全能力对端侧知识库建设有参考价值
