---
title: "Learning, Fast and Slow: Towards LLMs That Adapt Continually"
arXiv: "2605.12484"
date: "2026-05-12"
tags: [agent-memory, continual-learning, catastrophic-forgetting, fast-slow-learning, LLM-adaptation]
reviewer: auto
source: arXiv API
---

# Learning, Fast and Slow: Towards LLMs That Adapt Continually

## 论文信息

| 字段 | 内容 |
|------|------|
| **作者** | Rishabh Tiwari, Kusha Sareen, Lakshya A Agrawal, Joseph E. Gonzalez, Matei Zaharia, Kurt Keutzer, Inderjit S Dhillon, Rishabh Agarwal, Devvrit Khatri |
| **发表日期** | 2026-05-12 |
| **arXiv ID** | 2605.12484 |
| **类别** | cs.LG |
| **标签** | agent-memory, continual-learning, catastrophic-forgetting, fast-slow-learning, LLM-adaptation |

## 摘要（翻译）

大语言模型（LLMs）通过更新参数（如通过强化学习）来训练下游任务。然而更新参数会迫使模型吸收任务特定信息，可能导致灾难性遗忘和塑性丧失。相比之下，上下文学习（in-context learning）可以在固定LLM参数下廉价快速地适应任务特定需求（如提示优化），但通常无法达到更新LLM参数所能获得的性能增益。学习不应该仅限于上下文或权重层面。此外，人类也可能以不同时间尺度学习（如系统1与系统2）。为此，本文为LLMs引入了一种快-慢学习框架，将模型参数作为"慢"权重，优化后的上下文作为"快"权重。这些快"权重"可以从文本反馈中学习以吸收任务特定信息，同时让慢权重更接近基础模型并保持通用推理能力。Fast-Slow Training（FST）在推理任务上比纯慢学习（RL）样本效率提高3倍，同时持续达到或超越更高的性能渐近线。此外，FST训练的模型更接近基础LLM（KL散度减少达70%），导致比RL训练更少的灾难性遗忘。这种减少的漂移也保持了塑性：在训练一个任务后，FST训练模型比纯参数训练的模型更能有效地适应后续任务。在任务领域不断变化的持续学习场景中，FST继续获取每个新任务，而纯参数RL则停滞不前。

## 核心贡献

1. **Fast-Slow Learning框架**：将模型参数作为"慢"权重，上下文作为"快"权重，首次将快慢学习思想引入LLM适应

2. **Fast-Slow Training（FST）**：
   - 快权重从文本反馈中学习，吸收任务特定信息
   - 慢权重保持接近基础模型，持续通用推理能力
   - 样本效率提升3倍

3. **减轻灾难性遗忘**：FST训练的模型比纯参数RL训练遗忘更少（KL散度减少达70%）

4. **保持塑性**：训练一个任务后，FST模型比纯参数训练模型更能有效适应后续任务

5. **持续学习验证**：在任务领域不断变化的场景中，FST持续获取新任务而RL停滞

## 为什么重要

LLM的持续适应是构建长期记忆Agent的核心挑战。本文提出的Fast-Slow框架优雅地解决了灾难性遗忘与适应能力之间的张力：快权重负责吸收新任务信息（类似工作记忆），慢权重保持通用能力（类似长期记忆）。这种设计对Agent记忆系统有重要启示——或许Agent也需要类似的双重记忆机制，一个用于快速适应当前任务，一个用于保持通用能力。

## 技术细节

### 核心框架

```
Fast-Slow Learning for LLMs：

  快权重（Fast Weights）= 优化后的上下文
  └─ 从文本反馈学习
  └─ 吸收任务特定信息
  └─ 位于上下文窗口内

  慢权重（Slow Weights）= 模型参数
  └─ 保持接近基础模型
  └─ 持续通用推理能力
  └─ 通过RL更新（但更新幅度受控）

训练信号：文本反馈 → 快权重 + 慢权重联合优化
```

### 关键设计

- **快权重 = 上下文**：不需要额外参数，通过文本反馈在线学习
- **慢权重正则化**：通过KL散度约束保持接近基础模型
- **样本效率**：3x样本效率提升（相比纯参数RL）
- **塑性保持**：训练后仍能有效适应新任务

## 实验结果

| 方法 | 样本效率 | KL散度（vs基础） | 持续学习性能 |
|------|---------|-----------------|-------------|
| RL (慢权重) | 1x | 高漂移 | 停滞 |
| FST (快+慢) | 3x | 减少70% | 持续提升 |

## 与移动端/端侧的相关性

1. **端侧LLM适应**：快权重机制适合在边缘设备上部署，不需要大量参数更新
2. **低资源场景**：3x样本效率意味着更少的训练数据需求
3. **隐私保护**：在本地通过上下文快学习，无需上传参数
4. **持续个性化**：用户特定适应可以存储在快权重中，本地维护

## 参考

- arXiv: https://arxiv.org/abs/2605.12484
