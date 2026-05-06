---
title: "Chameleon: Episodic Memory for Long-Horizon Robotic Manipulation"
arXiv: "2603.24576"
date: "2026-03-25"
tags: [agent-memory, episodic-memory, embodied-memory, robotics, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **几何接地多模态记忆（Geometry-Grounded Multimodal Memory）**：将语义信息与几何细节统一写入记忆 token，保留用于消歧的细粒度几何信息，而非仅存储语义压缩轨迹。
2. **可微分记忆栈（Differentiable Memory Stack）**：提出一种可端到端训练的回忆机制，支持目标导向（goal-directed）的检索，而非简单的相似度匹配。
3. **Camo-Dataset**：构建了首个覆盖情景回忆、空间跟踪、顺序操作的 real-robot UR5e 数据集，专门评估感知混叠（perceptual aliasing）场景下的记忆表现。

## 方法详解

### 问题背景
机器人操作中，遮挡和状态变化会导致决策时的观察被感知混叠——同一视觉观察可能来自不同的交互历史。现有方法通过语义压缩轨迹（semantically compressed traces）和相似度检索实现记忆，但会丢弃用于消歧的细粒度感知线索。

### Chameleon 方案
- **多模态记忆写入**：将语义 token 与几何接地 token 混合写入记忆，使得记忆同时保留高层语义和低层几何细节。
- **几何相似性检索**：检索时不仅考虑语义相似性，还计算几何相似性，确保返回的回忆在几何层面也与当前任务相关。
- **可微分记忆栈**：通过可微分操作实现端到端训练，梯度可以从检索结果回传到写入策略。

## 为什么重要

这篇论文揭示了 embodied agent 记忆中一个关键缺陷：纯语义压缩丢失了机器人操作所需的几何细节。Chameleon 提出了将语义记忆与几何记忆结合的方向，对需要长期记忆物体位置、空间关系的机器人系统至关重要。

## 与端侧/移动端的相关性

**高度相关**。移动机器人和具身 AI 是端侧记忆系统的核心应用场景。Chameleon 的几何接地记忆方法直接影响机器人如何在边缘设备上长期记住环境——这对家庭机器人、物流机器人等实际应用场景意义重大。

## 摘要

Robotic manipulation often requires memory: occlusion and state changes can make decision-time observations perceptually aliased, making action selection non-Markovian at the observation level because the same observation may arise from different interaction histories. Most embodied agents implement memory via semantically compressed traces and similarity-based retrieval, which discards disambiguating fine-grained perceptual cues and can return perceptually similar but decision-irrelevant episodes. Inspired by human episodic memory, we propose Chameleon, which writes geometry-grounded multimodal tokens to preserve disambiguating context and produces goal-directed recall through a differentiable memory stack. We also introduce Camo-Dataset, a real-robot UR5e dataset spanning episodic recall, spatial tracking, and sequential manipulation under perceptual aliasing. Across tasks, Chameleon consistently improves decision reliability and long-horizon control over strong baselines in perceptually confusable settings.

## 参考文献

- Xinying Guo, Chenxi Jiang, Hyun Bin Kim, Ying Sun, Yang Xiao, Yuhang Han, Jianfei Yang. "Chameleon: Episodic Memory for Long-Horizon Robotic Manipulation." arXiv:2603.24576, 2026.
