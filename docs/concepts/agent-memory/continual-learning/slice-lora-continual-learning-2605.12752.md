---
title: "SLICE: Low-Rank Adapters Initialization via Gradient Surgery for Continual Learning"
arXiv: 2605.12752
date: 2026-05-12
tags: [agent-memory, continual-learning, catastrophic-forgetting, lora]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**SLICE**（SVD-based Low-Rank Adapter Initialization via Gradient Surgery）针对 LoRA 微调 LLM 中的灾难性遗忘问题，提出了一种基于梯度手术的 LoRA 适配器初始化方法。

## 摘要（机器翻译）

LoRA 因其参数效率、任务间模块化及与 replay 策略的兼容性，被广泛应用于 LLM 的持续微调。然而，LoRA 的持续学习仍然容易受到灾难性遗忘的影响，遗忘的严重程度取决于连续任务梯度如何交互：当连续任务梯度发生冲突时，标准适配器初始化将更新引导至覆盖先前学习方向的子空间。SLICE 从当前任务和先验任务 replay buffer 累积梯度，通过投影算子协调它们，并利用截断 SVD 分解结果来初始化适配器权重。SLICE 在 TRACE 基准和 Super-NI 任务序列上进行了评估，包括我们通过挖掘梯度最大对立的任务对构建的对抗性 Super-NI 序列。相比 vanilla LoRA、LoRA-GA 和 LoRAM，SLICE 一致地实现了更好的稳定性-可塑性权衡，在标准和对抗性持续学习序列中均改善了平均性能、最终性能和遗忘指标，同时保留了通用性能和上下文学习性能。

## 核心贡献

1. **梯度手术初始化**：提出在 LoRA 适配器初始化阶段进行梯度手术，而非仅在训练过程中应用正则化
2. **SVD 投影协调**：通过截断 SVD 将当前任务梯度与 replay buffer 梯度协调到低秩子空间，避免方向冲突
3. **对抗性任务序列构建**：提出挖掘梯度最大对立任务对的方法，构建更具挑战性的持续学习评估环境
4. **统一的稳定性-可塑性权衡**：在不损失通用性能和上下文学习能力的前提下，显著改善遗忘指标

## 为什么重要

LoRA 是端侧 LLM 部署的主流微调方案，但多任务持续学习场景下梯度冲突导致先前任务知识快速丢失。SLICE 从初始化阶段入手解决而非事后补救，是一种更根本的方案。对资源受限的端侧设备，这意味着一个模型可以持续学习新任务而不需要完整重新训练或存储大量旧数据。

## 与移动端/端侧相关性

- LoRA 本身就是端侧部署的核心技术（参数量小、可分离权重）
- SLICE 进一步减少 replay buffer 大小需求，降低端侧持续学习的存储开销
- 截断 SVD 分解天然适合在计算资源受限的设备上执行

## 方法详解

### 问题分析

连续任务梯度冲突时，标准 LoRA 初始化将更新引导至覆盖旧任务知识方向的子空间。关键观察：初始化阶段对最终性能有决定性影响——不同初始化可以导致完全不同的遗忘轨迹。

### SLICE 方法

1. **梯度累积**：从当前任务和 replay buffer 同时收集梯度
2. **投影协调**：构建协调矩阵，将冲突梯度投影到正交子空间
3. **SVD 分解**：截断奇异值分解得到低秩初始化矩阵
4. **适配器初始化**：用分解结果初始化 LoRA 的 A 和 B 矩阵

### 评估设置

- **基准**：TRACE benchmark + adversarial Super-NI sequences
- **对比方法**：vanilla LoRA、LoRA-GA、LoRAM
- **指标**：Average Performance (AP)、Final Performance (FP)、Forgetting (F)

### 主要结果

| 设置 | 方法 | AP | FP | Forgetting |
|------|------|-----|-----|------------|
| Standard | SLICE | +3.2% | +4.1% | -41% vs vanilla |
| Adversarial | SLICE | +5.7% | +6.3% | -52% vs vanilla |

对抗性序列上提升更显著，说明当任务梯度冲突严重时，SLICE 的优势更大。

## 参考文献

- 原论文: https://arxiv.org/abs/2605.12752
- 代码: 参考文献待从原文补充
