---
title: "GRID: Graph Representation of Intelligence Data for Security Text Knowledge Graph Construction"
arXiv: 2605.16714
date: 2026-05-15
tags: [agent-memory, memory-representation, knowledge-graph, security]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: GRID: Graph Representation of Intelligence Data for Security Text Knowledge Graph Construction
- **arXiv ID**: 2605.16714
- **发表日期**: 2026-05-15
- **作者**: Liangyi Huang, Zichen Liu, Fei Shao, Shang Ma, Mengshi Zhang, Zihao Chen, Yanfang Ye, Xusheng Xiao
- **方向**: 安全知识图谱、Agent外部记忆、文本图构建
- **类别**: cs.AI / cs.CR（网络安全）

## 摘要

安全知识图谱可为安全Agent提供可计算的外部记忆，但从长篇网络威胁情报（CTI）文档构建知识图谱仍然困难：LLM通常缺乏领域安全知识，且端到端文档到图的训练难以用廉价、稳定的奖励进行监督。

GRID（Graph Representation of Intelligence Data）是一个用于安全文本知识图谱构建的端到端框架。GRID首先通过图提取和知识图谱条件文本修订，从CTI文章创建可追溯的文章-图对齐来构建安全领域监督。然后将文档到图学习转变为脚本化的任务库，结合四项选择题和多选问题与三元组级正则匹配目标，产生比使用LLM评判器重复评分全图输出更稳定的任务特定奖励。

基于该监督流程，训练了两个基于Qwen3-4B-Instruct-2507的4B提取器：主任务的银行奖励模型和辅助的端到端奖励模型。在来自GRID、CASIE、CTINexus、MalKG和SecureNLP的249篇CTI文章上，基于本体引导的GRID提取流程的任务银行奖励模型达到了84.62%的源平均精确率、64.91%的源平均召回率和68.53%的平均F1。

## 核心贡献

1. **可追溯的文章-图对齐**：通过图提取和知识图谱条件文本修订，从CTI文章创建可追溯的对齐监督
2. **任务银行奖励机制**：将文档到图学习转变为可离线构建、跨训练运行复用的稳定任务特定奖励
3. **四选项多选题+正则匹配**：比LLM评判器更稳定的三元组级监督信号
4. **安全领域KG构建完整流程**：从原始CTI文档到可部署的知识图谱

## 为什么重要

安全Agent依赖外部知识图谱作为记忆系统面临三个核心挑战：
- **领域知识不足**：通用LLM缺乏网络安全领域知识
- **训练监督困难**：文档到图的端到端训练缺乏稳定奖励
- **部署成本**：全图LLM评判推理成本过高

GRID通过任务银行奖励和多级监督信号解决了这些问题，对构建面向安全领域的Agent记忆系统有直接参考价值。4B规模的Qwen3模型使端侧部署成为可能。

## 与移动端/端侧相关性

GRID使用Qwen3-4B级别模型，对端侧友好：
- 可在边缘安全Agent中部署轻量级CTI分析
- 任务银行奖励可离线预计算，减少在线推理成本
- 知识图谱本身是紧凑的记忆表示形式，适合资源受限环境

## 参考文献

（参考文献待从原文补充）
