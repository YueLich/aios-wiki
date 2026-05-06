---
title: "MEM: Multi-Scale Embodied Memory for Vision Language Action Models"
arXiv: 2603.03596
date: 2026-03-04
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

# MEM: Multi-Scale Embodied Memory for Vision Language Action Models

## 论文基本信息

- **作者**: Marcel Torne, Karl Pertsch, Homer Walke, Kyle Vedder, Suraj Nair, Brian Ichter, Allen Z. Ren, Haohuan Wang, Jiaming Tang, Kyle Stachowicz, Karan Dhabalia, Michael Equi, Quan Vuong, Jost Tobias Springenberg, Sergey Levine, Chelsea Finn, Danny Driess
- **arXiv**: https://arxiv.org/abs/2603.03596
- **领域**: cs.RO, cs.AI

## 摘要

传统上，端到端机器人学习中的记忆涉及将过去观察序列输入学得策略。然而，在复杂多阶段真实世界任务中，机器人记忆必须在多个粒度级别表示过去事件：从捕获抽象语义概念（如机器人做晚餐应记住菜谱已完成阶段）的长期记忆，到捕获最近事件并补偿遮挡的短期记忆（如机器人记住一旦手臂遮挡就想抓取的物体）。论文的主要见解是，有效的长程机器人控制记忆架构应结合多种模态来捕获这些不同抽象级别。MEM 提出混合模态长程记忆的机器人策略方法。MEM 结合视频压缩的短程记忆（通过视频编码器）和基于文本的长期记忆，共同使机器人策略能够执行持续达十五分钟的任务（如清理厨房或准备烤芝士三明治）。此外，发现记忆使 MEM 策略能够智能地在上下文中调整操作策略。

## 核心贡献

1. **Multi-scale Embodied Memory**: 首个多尺度具身记忆架构
2. **Video + Text Mixed Modal**: 视频编码短程记忆 + 文本长期记忆
3. **15-minute Tasks**: 支持长达十五分钟的长程任务
4. **In-context Strategy Adaptation**: 记忆使策略能在上下文中智能调整
5. **Real-world Robot Validation**: 真实机器人验证

## 研究背景与问题

机器人在长程任务中需要多层次记忆：长期语义概念和短期细节。现有方法用单一模态无法有效捕获这两种需求。

## 核心方法

1. **Video-based Short-horizon Memory**: 视频编码器压缩近期观察
2. **Text-based Long-horizon Memory**: 文本编码器维护高层任务状态
3. **Mixed-modal Fusion**: 视频和文本记忆的混合模态融合
4. **Long-horizon Task Benchmark**: 15 分钟真实机器人任务基准
5. **In-context Adaptation**: 记忆条件下的策略上下文适应

## 为什么重要

MEM 首次系统解决了机器人长程记忆的多模态问题，为具身 Agent 的记忆架构提供了重要参考。视频+文本的混合方案对移动端机器人有直接价值。

## 与移动端/端侧相关性

1. **移动机器人**: 家庭机器人、服务机器人的核心能力
2. **长程任务**: 15 分钟任务覆盖大多数日常家务
3. **视频编码效率**: 视频编码器可在端侧高效运行
4. **上下文适应**: 移动端需要快速适应新任务/环境
