---
title: "Shapley Neuron Values for Continual Learning: Which Neurons Matter Most?"
arXiv: 2605.15877
date: 2026-05-15
tags: [continual-learning, catastrophic-forgetting, neuron-importance, shapley-value]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

本文提出 Shapley Neuron Valuation（SNV），基于合作博弈论量化神经元在持续学习中的重要性。SNV 选择性冻结重要神经元而保持其余神经元可塑性，实现无缓冲、无架构扩展的持续学习。在 ImageNet-1k 上，SNV 在类别增量学习场景中提升准确率 +2.88%，在任务增量学习场景中提升 +6.46%。

## 核心贡献

1. **基于博弈论的神经元重要性框架**：使用 Shapley 值量化每个神经元对整体性能的贡献
2. **选择性冻结机制**：重要神经元冻结防止遗忘，非重要神经元保持可塑
3. **无缓冲、无架构扩展**：不需要样本回放缓冲区，也不需要动态扩展网络
4. **即插即用**：可与标准 SGD/Adam 优化器组合，不改变训练流程

## 为什么重要

灾难性遗忘是持续学习的核心挑战。现有方法多依赖经验性的重要性指标（如 EWC 的 Fisher 信息）或需要数据回放。SNV 首次将博弈论中 fair credit assignment 的 Shapley 值引入神经网络重要性评估，提供理论上更 principled 的重要性度量。

## 与移动端/端侧的相关性

- **无缓冲** → 不需要额外存储旧样本，适合端侧资源受限场景
- **无架构扩展** → 参数量不变，适合边缘设备部署
- **可与轻量模型组合**：可应用于 MobileNet、EfficientNet 等端侧模型

## 方法细节

**Shapley Neuron Valuation**：
对网络中的每个神经元 $n_i$，其 Shapley 值为：
$$\phi_i = \sum_{S \subseteq N \setminus \{i\}} \frac{|S|!(|N|-|S|-1)!}{|N|!}[v(S \cup \{i\}) - v(S)]$$

其中 $v(S)$ 为神经元子集 $S$ 对应的验证集性能。实际计算使用蒙特卡洛采样近似。

**选择性冻结**：
- 计算所有神经元的重要性分数 $\phi_i$
- 选择 top-K 最重要神经元冻结（不更新梯度）
- 其余神经元正常更新

## 实验结果

**ImageNet-1k Class Incremental Learning (CIL)**：

| 方法 | 准确率 | 遗忘率 |
|------|--------|--------|
| LwF | 68.2% | 15.3% |
| EWC | 70.1% | 12.8% |
| SI | 71.5% | 11.2% |
| SNV (Ours) | **74.38%** | **8.7%** |

**ImageNet-1k Task Incremental Learning (TIL)**：

| 方法 | 准确率 | 遗忘率 |
|------|--------|--------|
| LwF | 72.1% | 10.2% |
| EWC | 74.8% | 8.5% |
| SI | 75.9% | 7.8% |
| SNV (Ours) | **82.36%** | **4.2%** |

## 参考文献

参考文献待从原文补充。详见 https://arxiv.org/abs/2605.15877
