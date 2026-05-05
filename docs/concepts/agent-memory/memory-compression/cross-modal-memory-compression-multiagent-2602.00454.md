---
title: "Cross-Modal Memory Compression for Efficient Multi-Agent Debate"
arXiv: 2602.00454
date: 2026-01-31
tags: [agent-memory, memory-compression, multi-agent]
reviewer: auto
source: arXiv RSS/API
---

# Cross-Modal Memory Compression for Efficient Multi-Agent Debate

## 论文基本信息

- **作者**: Jing Wu, Yue Sun, Tianpei Xie, Suiyao Chen, Jingyuan Bao, Yaopengxiao Xu, Gaoyuan Du, Inseok Heo, Alexander Gutfraind, Xin Wang
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2602.00454
- **代码**: （待补充）

## 核心贡献

1. **DebateOCR 框架**: 提出跨模态压缩框架，将长文本辩论轨迹替换为紧凑的图像表示。
2. **92%+ token 减少**: 压缩通常跨度数万到数十万 token 的辩论历史，减少超过 92% 的输入 token。
3. **理论分析**: 提供理论视角，证明跨 Agent 的多样性支持信息恢复——任何单个压缩历史可能丢弃细节，但多个 Agent 压缩视图的聚合使集体表示能以指数高概率接近信息瓶颈。
4. **更低计算成本**: 在多个基准上实现更低计算成本和更快推理。

## 研究背景与问题

多智能体辩论可以提高推理质量并减少幻觉，但随着辩论轮次和智能体数量增加，上下文快速增长。保留完整文本历史导致 token 使用量超出上下文限制，通常需要重复摘要，引入开销并加剧信息损失。

## 核心方法

**DebateOCR（Cross-Modal Compression for Debate）**:

1. **跨模态转换**: 将长文本辩论轨迹转换为紧凑图像表示
2. **专用视觉编码器**: 通过专用视觉编码器处理压缩后的图像，为后续轮次提供条件
3. **理论保证**: 基于信息瓶颈理论，证明聚合多个 Agent 的压缩视图可以恢复被单个压缩丢弃的信息

## 关键数据

- **Token 减少**: 92%+
- **计算成本**: 显著降低
- **推理速度**: 更快

## 为什么重要

这篇论文将跨模态压缩（文本→图像）应用于多智能体辩论的记忆压缩问题，并提供了理论保证。对于需要长上下文的多智能体 Agent 系统，跨模态压缩是突破上下文限制的有效途径。

## 与移动端/端侧相关性

在端侧部署多智能体系统时，跨 Agent 通信的上下文膨胀是严重瓶颈。DebateOCR 的跨模态压缩思路——将文本转换为视觉表示再压缩——对资源受限环境下的多 Agent 协作有参考价值。
