---
title: "Lightweight LLM Agent Memory with Small Language Models"
arXiv: 2604.07798
date: 2026-04-09
authors: ["Jiaquan Zhang et al."]
tags: [agent-memory, memory-retrieval, small-language-models, on-device, memory-system]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.07798
- **作者**: Jiaquan Zhang, Chaoning Zhang, Shuxu Chen et al.
- **提交日期**: 2026-04-09
- **方向**: 轻量记忆 / 小语言模型 / 端侧 Agent

## 摘要（全文翻译）

LLM Agent 可以利用工具完成复杂任务，但需要记忆来维持跨轮一致性并在长期交互中积累可复用信息。然而，基于检索的外部记忆系统在线开销低，但因查询构建和候选过滤能力有限而准确率不稳定。多数系统在在线记忆操作中使用重复的大型模型调用，提高了准确率但在长期交互中累积延迟。

本文提出 **LightMem**，一个由小语言模型（SLM）驱动的轻量级 Agent 记忆系统。LightMem 将记忆检索、写入和长期整合模块化，并分离在线处理和离线整合，在不同时条件下实现高效记忆调用。

## 核心贡献

1. **SLM 驱动的记忆系统**：用小语言模型替代大型 LLM 做记忆操作
2. **模块化架构**：检索/写入/整合分离，各模块独立优化
3. **在线-离线分离**：在线处理低延迟，离线整合保证质量
4. **无需重型 LLM**：整个记忆系统可在端侧运行

## 为什么重要

LightMem 证明了"记忆操作不一定需要大模型"。SLM（如 0.5B-1B 参数）足够完成记忆检索和写入决策，同时大幅降低延迟和计算成本。

## 与端侧/移动端的相关性

**高度相关**。LightMem 的整个记忆系统可以在移动设备上本地运行，不需要云端 LLM 调用。对可穿戴设备和手机助手等场景尤其有价值。
