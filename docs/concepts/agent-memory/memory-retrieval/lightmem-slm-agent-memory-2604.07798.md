---
title: "LightMem: Lightweight LLM Agent Memory with Small Language Models"
arXiv: 2604.07798
date: 2026-04-09
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# LightMem: Lightweight LLM Agent Memory with Small Language Models

## 论文基本信息

- **作者**: Xinyu Wang, Wei Fan, Yue Wang, Haibo Liu, Junzhou Luo
- **arXiv**: https://arxiv.org/abs/2604.07798
- **领域**: cs.AI, cs.CL

## 摘要

LLM Agent 的记忆系统面临效率与效果的矛盾：完整记忆需要大量 token 上下文，而压缩又会丢失关键信息。LightMem 提出用小型语言模型（SLM）作为专用记忆模型，在端侧实现高效记忆存储与检索。与直接用 LLM 记忆相比，LightMem 使用 1.3B-3B 参数的 SLM 作为记忆编码器/检索器，实现 85% 的 token 减少，同时在下游任务上保持 92% 的效果。实验在多个 Agent 基准上验证，包括复杂对话、任务规划和推理任务。

## 核心贡献

1. **SLM-based Memory Architecture**: 首个使用小型语言模型作为专用记忆编码器/检索器的框架
2. **记忆解耦设计**: 将记忆存储和检索任务从主 LLM 解耦，由轻量级 SLM 专门处理
3. **85% Token 减少**: 通过知识蒸馏和记忆压缩，在端侧实现显著 token 节省
4. **92% 效果保持**: 在多个 Agent 基准上保持接近完整 LLM 记忆的效果
5. **隐私保护**: 敏感记忆可完全在本地 SLM 中处理，无需上传云端 LLM

## 研究背景与问题

LLM Agent 需要维护长交互历史，但上下文窗口有限且推理成本随 token 数量线性增长。传统方案（摘要、压缩、向量检索）都有信息丢失或检索质量下降的问题。如何在端侧设备上实现高效且有效的 Agent 记忆，是移动端部署的核心挑战。

## 核心方法

1. **Memory Distillation**: 从大 LLM 记忆中蒸馏关键信息到 SLM 记忆模块
2. **Hierarchical Memory Index**: 多层级记忆索引（事件→场景→细节），支持细粒度检索
3. **SLM Retriever**: 用微调 SLM 做记忆检索，比向量相似度更语义化
4. **Adaptive Memory Update**: 根据交互重要性动态决定是否更新记忆
5. **端侧部署优化**: INT4 量化 + KV Cache 压缩，支持移动端实时推理

## 为什么重要

LightMem 首次系统性地用 SLM 替代 LLM 处理记忆任务，为端侧 Agent 记忆提供了可行方案。记忆解耦设计让主 LLM 更专注推理，SLM 专管记忆——这是模块化 Agent 架构的重要参考。85% token 减少意味着移动端可以在有限上下文内维护更长的有效记忆。

## 与移动端/端侧相关性

1. **端侧友好**: 1.3B-3B SLM 可在手机/车载设备上运行，适合移动端部署
2. **INT4 量化**: 完整支持量化推理，内存占用 < 2GB
3. **隐私原生**: 所有记忆处理在本地完成，不依赖云端 API
4. **长上下文移动场景**: 车载导航、机器人等需要长记忆但计算资源受限的场景
