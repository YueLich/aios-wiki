---
title: "StreamMeCo: Long-Term Agent Memory Compression for Efficient Streaming Video Understanding"
arXiv: 2604.09000
date: 2026-04-10
tags: [agent-memory, memory-compression, video]
reviewer: auto
source: arXiv RSS/API
---

# StreamMeCo: Long-Term Agent Memory Compression for Efficient Streaming Video Understanding

## 论文基本信息

- **作者**: Junxi Wang, Te Sun, Jiayi Zhu, Junxian Li, Haowen Xu, Zichen Wen, Xuming Hu, Zhiyu Li, Linfeng Zhang
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2604.09000
- **代码**: https://github.com/Celina-love-sweet/StreamMeCo

## 核心贡献

1. **StreamMeCo 框架**: 提出高效流式 Agent 记忆压缩框架 StreamMeCo。
2. **边无关 minmax 采样**: 针对孤立节点提出边无关 minmax 采样。
3. **边感知权重剪枝**: 针对连通节点提出边感知权重剪枝，在保持准确性的同时移除冗余记忆节点。
4. **时间衰减记忆检索**: 引入时间衰减记忆检索机制，进一步消除记忆压缩带来的性能下降。
5. **70% 压缩下 1.87 倍加速**: 在 70% 记忆图压缩下，记忆检索加速 1.87 倍，平均准确率提升 1.0%。

## 研究背景与问题

视觉 Agent 记忆在流式视频理解中显示出显著的有效性。然而，存储视频记忆带来巨大的内存开销，导致存储和计算成本高昂。

## 核心方法

**StreamMeCo 三板斧**：

### 1. 边无关 minmax 采样（Isolated Nodes）
对记忆图中的孤立节点使用边无关 minmax 采样。

### 2. 边感知权重剪枝（Connected Nodes）
对连通节点使用边感知权重剪枝，在保持准确性的同时移除冗余记忆节点。

### 3. 时间衰减记忆检索
引入时间衰减机制——越久远的记忆在检索时权重越低——进一步消除压缩带来的性能下降。

## 实验结果

- 在 70% 记忆图压缩下实现 **1.87 倍记忆检索加速**
- 平均准确率提升 **1.0%**
- 基准数据集：M3-Bench-robot, M3-Bench-web, Video-MME-Long

## 为什么重要

这是专门针对视频 Agent 记忆压缩的工作，提出了结合图结构（连通性）的压缩策略。视频理解是 Agent 系统的重要场景，StreamMeCo 的方法在保持关键信息的同时实现了高压缩率，对实时视频处理 Agent 有直接价值。

## 与移动端/端侧相关性

视频流理解在端侧（机器人、自动驾驶眼镜）有重要应用，但视频记忆的存储成本极高。StreamMeCo 在 70% 压缩率下仍能提升准确率，对端侧视频 Agent 系统的内存管理有直接参考价值。
