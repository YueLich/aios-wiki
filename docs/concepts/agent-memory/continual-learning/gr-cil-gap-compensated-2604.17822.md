---
title: "GR4CIL: Gap-compensated Routing for CLIP-based Class Incremental Learning"
arXiv: 2604.17822
date: 2026-04-20
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# GR4CIL: Gap-compensated Routing for CLIP-based Class Incremental Learning

## 论文基本信息

- **作者**: Tianqi Wang, Jingcai Guo
- **arXiv**: https://arxiv.org/abs/2604.17822
- **领域**: cs.CV, cs.LG

## 摘要

类别增量学习（CIL）旨在持续获取新类别同时保留已学知识。CLIP 等预训练模型因强大泛化能力在 CIL 中展现潜力，但现有方法仍面临两个关键挑战：共享参数适应容易导致旧知识漂移，以及任务边界未知时难以确定推理时使用哪个分类头。GR4CIL 提出间隙补偿路由，通过在 CLIP 特征空间中识别和补偿类别间的表示间隙，解决旧知识漂移和任务边界问题。

## 核心贡献

1. **Gap-compensated Routing**: 补偿 CLIP 特征空间中类别间表示间隙的路由机制
2. **Old Knowledge Drift 解决**: 系统解决共享参数适应中的旧知识漂移问题
3. **Task Boundary Unknown 处理**: 推理时无需明确任务边界
4. **CLIP-based CIL 优化**: 针对 CLIP 预训练模型的增量学习优化
5. **多基准验证**: 在多个 CIL 基准上验证有效性

## 研究背景与问题

CLIP 的强大泛化能力使其成为 CIL 的有力基础，但增量学习场景下共享参数适应容易破坏 CLIP 已建立的表示空间，导致旧知识漂移。

## 核心方法

1. **Feature Space Gap Analysis**: 分析 CLIP 特征空间中类别间的表示间隙
2. **Compensated Routing**: 在推理时补偿已识别间隙，减少旧类别干扰
3. **Dual-head Design**: 新旧类别分别处理，但通过路由机制协调
4. **Continual Pre-training**: 在增量学习过程中持续微调 CLIP 表示

## 为什么重要

GR4CIL 为基于 CLIP 的增量学习提供了新思路，对需要持续学习新类别的 Agent 视觉记忆系统有参考价值。

## 与移动端/端侧相关性

1. **端侧视觉识别**: CLIP 模型可在端侧运行，支持移动端增量视觉学习
2. **隐私保护**: 增量学习允许本地学习新类别，无需上传原始数据
3. **资源受限场景**: 路由机制比完整重训练更高效
