---
title: "Chameleon: Episodic Memory for Long-Horizon Robotic Manipulation"
arXiv: "2603.24576"
date: "2026-03-25"
tags: [agent-memory, episodic-memory, embodied-memory, robotics]
reviewer: auto
source: arXiv RSS
---

## 核心贡献

Chameleon 研究了机器人操作中的情景记忆（episodic memory）问题。论文指出：**当前 embodied agent 通过语义压缩轨迹和相似性检索实现记忆的方法会丢失区分性细粒度感知线索**。

**核心问题**：
- 遮挡和状态变化使得决策时的观察是感知混叠的（perceptually aliased）
- 相同观察可能来自不同的交互历史
- 现有方法（语义压缩+相似性检索）会丢弃决策所需的区分性几何线索
- 可能返回感知相似但决策无关的经历

**Chameleon 方案**：
- 借鉴人类情景记忆，构建几何接地（geometry-grounded）的多模态记忆
- 在记忆中保留细粒度的几何信息
- 支持基于几何相似性的检索，而非仅依赖语义相似性

## 为什么重要

这篇论文揭示了 embodied agent 记忆中一个关键缺陷：纯语义压缩丢失了机器人操作所需的几何细节。Chameleon 提出了将语义记忆与几何记忆结合的方向，对需要长期记忆物体位置、空间关系的机器人系统至关重要。

## 与端侧/移动端的相关性

**高度相关**。移动机器人和具身 AI 是端侧记忆系统的核心应用场景。Chameleon 的几何接地记忆方法直接影响机器人如何在边缘设备上长期记住环境——这对家庭机器人、物流机器人等实际应用场景意义重大。

## 摘要

Robotic manipulation often requires memory: occlusion and state changes can make decision-time observations perceptually aliased, making action selection non-Markovian at the observation level because the same observation may arise from different interaction histories. Most embodied agents implement memory via semantically compressed traces and similarity-based retrieval, which discards disambiguating fine-grained perceptual cues and can return perceptually similar but decision-irrelevant episodes. Inspired by human episodic memory, we propose Chameleon, which writes geometry-grounded multimodal memories.

## 参考文献

待补充
