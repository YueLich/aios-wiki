---
title: "SleepGate: Sleep-Inspired Memory Consolidation for Resolving Proactive Interference in LLMs"
arXiv: 2603.14517
date: 2026-03-15
authors: ["Ying Xie"]
tags: [agent-memory, memory-compression, proactive-interference, sleep-inspired, KV-cache, continual-learning]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2603.14517
- **发表日期**: 2026-03-15
- **作者**: Ying Xie
- **方向**: 记忆压缩与干扰消除（睡眠启发的记忆巩固）

## 摘要

**背景**：LLM 遭受主动干扰（Proactive Interference, PI）：上下文窗口中的过时信息干扰当前值的检索。随着陈旧关联积累，检索准确率呈对数线性下降，这是无论上下文长度如何都存在的瓶颈，提示工程无法缓解。

**方法**：受生物大脑睡眠依赖的记忆巩固启发——突触 downscaling、选择性重放和针对性遗忘——SleepGate 为基于 Transformer 的 LLM 引入学到的睡眠周期。三个机制：
1. 冲突感知时序标签器：检测新条目何时取代旧条目
2. 轻量遗忘门：选择性地驱逐或压缩陈旧缓存条目
3. 整合模块：将存活条目合并为紧凑摘要

这些组件在推理过程中以睡眠微周期定期激活，由自适应熵触发器控制。

**理论结果**：SleepGate 将干扰范围从 $O(n)$ 降低到 $O(\log n)$

**实验结果**：小规模 Transformer（4 层，793K 参数），PI 深度 5 达到 99.5% 检索准确率，深度 10 达到 97.0%，而 5 个基线（完整 KV cache、滑动窗口、H2O、StreamingLLM、仅 decay）在深度 5 后均低于 18%。

## 核心贡献

1. **生物启发的记忆框架**：首次将睡眠依赖的记忆巩固机制（downscaling + 选择性遗忘 + 整合）形式化为 LLM KV cache 管理
2. **冲突感知标签器**：检测新旧条目冲突，触发遗忘决策
3. **对数干扰界**：理论证明将 PI 范围从线性降到对数，是提示工程无法达到的理论突破
4. **无需架构修改**：作为 KV cache 管理策略，可叠加在任何 LLM 架构上

## 为什么重要

主动干扰是 LLM 记忆系统的核心问题：

- **上下文越长越差**：这与人类记忆系统相反——人类通过遗忘反而能改善检索
- **提示工程无解**：这是架构级问题，需要在记忆管理层解决
- **小模型大效果**：在 4 层 793K 参数的小模型上就能显著超越所有基线，说明方法本身的有效性

## 与端侧/移动端的相关性

SleepGate 对端侧部署有直接影响：

- **KV Cache 管理**：移动端设备内存有限，有限的 KV cache 容量下主动遗忘更重要
- **隐私保护**：选择性地遗忘过时/敏感信息，符合移动端隐私法规
- **能效优化**：通过压缩和驱逐减少内存占用，降低移动端功耗

## 参考文献

- arXiv: 2603.14517 | https://arxiv.org/abs/2603.14517
