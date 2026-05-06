---
title: "StreamMeCo: Streaming Memory Compression for Video Understanding Agents"
arXiv: 2604.09000
date: 2026-04-11
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# StreamMeCo: Streaming Memory Compression for Video Understanding Agents

## 论文基本信息

- **作者**: Junnan Liu, Chi Wang, Yongchao Jin, Yu Liu, Xianglong Liu
- **arXiv**: https://arxiv.org/abs/2604.09000
- **领域**: cs.CV, cs.AI

## 摘要

视频理解 Agent 需要处理长视频流，但视频数据量巨大导致记忆存储成为瓶颈。StreamMeCo 提出面向视频流的在线记忆压缩框架，在视频帧进入记忆时就判断其价值并动态压缩或丢弃。该方法结合视觉语义重要性（哪些帧包含关键事件）和时序冗余性（哪些帧可被后续帧替代），实现自适应的记忆管理。在长视频理解任务上，StreamMeCo 在保持 94% 准确率的同时，将视频记忆存储减少 78%。

## 核心贡献

1. **Streaming Memory Compression**: 首个面向视频流的在线记忆压缩框架
2. **双重要性评估**: 结合语义重要性 + 时序冗余性双重判断记忆价值
3. **78% 存储减少**: 在保持 94% 准确率下实现显著存储节省
4. **Online Operation**: 无需离线批处理，视频帧实时处理并更新记忆
5. **视频理解通用**: 可与任何视频理解模型集成，适用于视频 Agent

## 研究背景与问题

视频 Agent（如监控分析、自动驾驶记录、机器人视觉）需要处理连续视频流，1 分钟视频可能包含 1800 帧（30fps），远超任何 LLM 的上下文窗口。传统方法依赖离线批处理压缩，但视频 Agent 需要实时决策，无法等待离线处理。

## 核心方法

1. **Semantic Importance Score**: 评估每帧的语义重要性（事件检测、异常检测）
2. **Temporal Redundancy Score**: 评估每帧与已存储帧的时序冗余度
3. **Adaptive Compression Policy**: 结合双重评分决定：保留 / 轻压缩 / 重压缩 / 丢弃
4. **Memory Budget Scheduler**: 根据可用存储动态调整压缩率，保证记忆总量不超标
5. **Key-frame Memory Bank**: 维护一个关键帧记忆库，确保核心视觉信息不丢失

## 为什么重要

StreamMeCo 将在线记忆压缩引入视频理解 Agent，解决了视频流实时处理的记忆瓶颈问题。78% 存储减少和 94% 准确率保持的组合，使其成为视频 Agent 实用化的重要一步。

## 与移动端/端侧相关性

1. **实时流处理**: 在线压缩对车载记录仪、监控摄像头等端侧设备至关重要
2. **存储受限环境**: 78% 存储减少使端侧设备可以缓存更长时间的视频记忆
3. **低功耗设计**: 无需 GPU 批处理，适合移动端低功耗推理
4. **与视觉语言模型结合**: 可作为 VLM 的记忆前端，减少输入 token 数量
