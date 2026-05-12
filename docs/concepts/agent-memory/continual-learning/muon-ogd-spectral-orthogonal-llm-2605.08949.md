---
title: "Muon-OGD: Muon-based Spectral Orthogonal Gradient Projection for LLM Continual Learning"
arXiv: 2605.08949
date: 2026-05-09
tags: [agent-memory, continual-learning, LLM, orthogonal-gradient]
reviewer: auto
source: arXiv API
---

# Muon-OGD: Muon-based Spectral Orthogonal Gradient Projection for LLM Continual Learning

## 论文信息

- **arXiv ID**: 2605.08949
- **发表日期**: 2026-05-09
- **作者**: Binghang Lu, Zheyuan Deng, Runyu Zhang et al.
- **方向**: 持续学习 / LLM / 正交梯度
- **开源**: 待确认

## 摘要（英译中）

大语言模型持续学习的核心挑战是灾难性遗忘。现有基于投影的方法通过将参数更新限制在与先前任务相关方向的正交子空间来减轻干扰，但这些方法通常在欧几里得参数几何下制定，更新幅度和投影由 Frobenius 范数控制。

Muon 优化器的近期实证成功——它应用正交化矩阵更新并承认谱范数解释——表明对于矩阵值 LLM 参数，Frobenius 几何可能不是最优选择。

作者提出 **Muon-OGD**，将 Muon 风格的算子范数几何与正交投影约束集成。方法将每个更新表述为带有线性非干扰约束的谱范数约束优化问题，并通过对偶迭代和 Newton-Schulz 矩阵符号近似高效求解。通过应用避开与先前任务相关保护方向的正交化动量更新，Muon-OGD 旨在改善顺序 LLM 适应中的稳定性-可塑性权衡。

在 TRACE 和领域特定 Coding-Math-Medical 课程上评估，使用编码器-解码器和仅解码器架构，Muon-OGD 在顺序微调和其他正交梯度基线上持续改进，同时保持计算可扩展性。这些结果表明，谱范数感知的更新几何为 LLM 持续学习提供了一种实用且有效的 Frobenius 范数投影替代方案。

## 核心贡献

1. **谱范数几何**：将 Muon 的谱范数解释引入正交投影持续学习
2. **对偶迭代求解**：高效求解谱范数约束优化问题
3. **Newton-Schulz 近似**：矩阵符号近似的计算高效实现
4. **多架构验证**：编码器-解码器和仅解码器架构均有效
5. **计算可扩展**：保持正交投影好处的同时计算开销可控

## 关键洞察

> Frobenius 几何可能不是 LLM 持续学习中正交投影的最优选择，谱范数几何提供了更合适的更新空间解释。

Muon 优化器的成功暗示了谱范数几何对矩阵参数更自然。持续学习中的正交投影约束在这种几何下能更好地保持先前任务的表示结构。

## 为什么重要

- **几何改进**：从 Frobenius 到谱范数几何的范式转换
- **实证验证**：在多个基准和架构上持续优于基线
- **理论动机**：Muon 优化器的成功提供了实证基础

## 与端侧/移动端的相关性

- LLM 持续学习是端侧个性化助手的关键能力
- 计算可扩展性适合资源受限环境
- 无需存储训练数据的正交投影方法对隐私友好

## 参考文献

- 原论文: https://arxiv.org/abs/2605.08949
