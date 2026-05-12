---
title: "RoboMemArena: A Comprehensive and Challenging Robotic Memory Benchmark"
arXiv: 2605.10921
date: 2026-05-11
tags: [agent-memory, memory-retrieval, multimodal-memory, benchmark, robotics]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: RoboMemArena: A Comprehensive and Challenging Robotic Memory Benchmark
- **作者**: Huashuo Lei, Wenxuan Song, Huarui Zhang, Jieyuan Pei, Jiayi Chen
- **发表日期**: 2026-05-11
- **arXiv ID**: 2605.10921
- **方向**: 机器人记忆系统基准测试

## 摘要

Memory is a critical component of robotic intelligence, as robots must rely on past observations and actions to accomplish long-horizon tasks in partially observable environments. However, existing robotic memory benchmarks still lack multimodal annotations for memory formation, provide limited task coverage and structural complexity, and remain restricted to simulation without real-world evaluation.

本文提出 **RoboMemArena**，一个大规模机器人记忆基准，包含 **26 个任务**，平均轨迹长度超过 1000 步，68.9% 的子任务依赖记忆。生成 pipeline 利用 VLM 设计和组合子任务，通过原子函数生成完整轨迹，并提供记忆相关标注（包括子任务指令和原生关键帧标注），同时配套真实世界物理评估任务。

此外，论文设计了 **PrediMem**，一种双系统 VLA，其中高级 VLM planner 管理包含近期缓冲和关键帧缓冲的记忆库，并使用预测编码头来提高对任务动态的敏感性。

## 核心贡献

1. **RoboMemArena 大规模基准**: 26 个任务，平均轨迹长度 > 1000 步，68.9% 子任务依赖记忆，覆盖多模态标注
2. **PrediMem 双系统架构**: 高级 VLM planner + 记忆银行（recent buffer + keyframe buffer）+ 预测编码头
3. **真实世界评估**: 配套真实机器人物理评估任务，弥补纯仿真评估的不足
4. **可扩展的记忆管理分析**: 提供记忆管理、模型架构和扩展定律的深入分析

## 为什么重要

现有机器人记忆基准存在三个核心缺陷：
- 缺乏多模态记忆形成标注
- 任务覆盖和结构复杂度有限
- 仅限仿真环境，无真实世界评估

RoboMemArena 首次同时解决这三个问题，为机器人记忆系统的研究和评估提供了全面、严格、可复现的基准。

## 与移动端/端侧相关性

该研究对端侧机器人系统有直接意义：
- PrediMem 的双系统架构（planner + memory bank）可作为端侧记忆管理的参考设计
- 关键帧缓冲机制适合边缘设备的高效记忆压缩
- benchmark 覆盖 1000+ 步长轨迹，对端侧长期记忆能力有参考价值
