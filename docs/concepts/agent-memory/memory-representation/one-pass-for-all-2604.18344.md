---
title: "One Pass for All: A Discrete Diffusion Model for Knowledge Graph Triple Set Prediction"
arXiv: 2604.18344
date: 2026-04-20
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# One Pass for All: A Discrete Diffusion Model for Knowledge Graph Triple Set Prediction

## 论文基本信息

- **作者**: ADMIS-TONGJI 团队
- **arXiv**: https://arxiv.org/abs/2604.18344
- **代码**: https://github.com/ADMIS-TONGJI/DiffTSP

## 摘要

知识图谱由三元组组成，知识图谱补全旨在推断缺失的三元组。传统 KGC 任务在给定一个或两个元素时预测三元组的缺失元素。作为更现实的任务，三元组集合预测（TSP）仅基于观测到的知识图谱推断缺失三元组集合，不假设任何关于缺失三元组的部分信息。现有 TSP 方法逐三元组预测，无法捕捉预测三元组之间的依赖关系以确保一致性。DiffTSP 将 TSP 视为生成任务，通过离散扩散过程处理。在推理时，DiffTSP 一次性生成完整三元组集合，确保预测三元组之间的一致性。

## 核心贡献

1. **DiffTSP**: 首个将离散扩散用于知识图谱三元组集合预测的模型
2. **One-pass Generation**: 一次性生成完整三元组集合，保证依赖一致性
3. **Structure-aware Denoising Network**: 结构感知去噪网络，整合关系上下文编码器和关系图扩散 Transformer
4. **State-of-the-art**: 在三个公开数据集上达到最优性能
5. **Set-level Prediction**: 集合级预测，而非逐三元组预测

## 研究背景与问题

传统 KGC 假设缺失三元组的信息是部分已知的（如头实体+关系→预测尾实体），但现实中常需要在完全不知道缺失信息的情况下预测可能的三元组集合。TSP 更符合真实应用场景。

## 核心方法

1. **Discrete Diffusion Process**: 通过离散扩散过程在 KG 上添加噪声（掩码关系边）
2. **Reverse Process**: 反向过程逐步恢复完整 KG，条件是输入的不完整图
3. **Structure-aware Denoising Network**: 关系上下文编码器 + 关系图扩散 Transformer
4. **Set-level Loss**: 集合级损失函数，确保一次性生成所有相关三元组

## 为什么重要

DiffTSP 为知识图谱补全提供了一步式生成方案，对 Agent 记忆系统的知识图谱更新有直接价值。一次性生成确保一致性，避免逐三元组预测导致的三元组间冲突。

## 与移动端/端侧相关性

1. **一次性推理**: 减少与远程服务器的交互次数，适合移动端低带宽场景
2. **一致性保证**: Agent 记忆的一致性对决策可靠性至关重要
3. **图结构保留**: 关系图扩散 Transformer 保留记忆的图结构信息
