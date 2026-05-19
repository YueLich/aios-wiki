---
title: "AtlasVA: Self-Evolving Visual Skill Memory for Teacher-Free VLM Agents"
arXiv: 2605.17933
date: 2026-05-18
tags: [agent-memory, multimodal-memory, visual-memory, self-evolving]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: 多机构合作

**核心问题**: VLM (Vision-Language Model) agent 在多轮任务中依赖记忆系统复用经验，但现有方法将视觉记忆存储为文本描述（通过 VLM captioning），导致大量视觉细节丢失，且需要人工"教师"（teacher）标注何时创建/更新记忆。

**方法**: AtlasVA 提出无教师（teacher-free）的自进化视觉技能记忆系统，让 VLM agent 自主决定何时将当前视觉经验存入记忆、如何在记忆中组织技能结构。

### 核心设计

1. **视觉技能图谱（Visual Skill Graph）**：以图结构而非扁平列表组织视觉记忆，节点表示视觉概念（如"红色按钮"、"左侧菜单"），边表示概念间的空间/功能关系
2. **自进化插入机制**：agent 在每轮交互后自主判断是否创建新记忆节点或更新已有节点，无需外部监督信号
3. **跨任务技能迁移**：当新任务涉及与已有技能图谱中相似节点时，agent 自动激活相关路径进行快速适配

## 核心贡献

1. **首个 Teacher-Free 视觉技能记忆框架**：无需人工标注记忆创建/更新时机
2. **图结构视觉记忆表示**：比扁平文本列表保留更丰富的空间和功能关系信息
3. **跨任务技能迁移**：在从未见过的任务上，利用已有技能图谱实现 67% 的零样本任务完成率
4. **显著降低 token 消耗**：相比文本记忆方案，AtlasVA 在保持相同任务性能的同时减少 52% 的记忆检索 token

## 为什么重要

视觉记忆的 captioning 范式存在严重的信息瓶颈——将连续视觉空间强制离散化为文本描述会丢失大量细节。AtlasVA 的图结构方法首次实现了"原生视觉记忆"，保留了视觉输入的空间结构和细节，对需要精细视觉理解的 agent（如机器人操控、GUI 自动化）意义重大。

## 与移动端/端侧的相关性

AtlasVA 的技能图谱结构天然适合端侧部署——图节点可以增量存储、按需加载，不需要每次都将完整记忆描述加载到上下文。其 teacher-free 特性也意味着端侧 agent 能够在用户使用过程中自动建立个性化视觉记忆，无需用户显式"训练"agent。

## 参考文献

- Wang, P., et al. (2026). AtlasVA: Self-Evolving Visual Skill Memory for Teacher-Free VLM Agents. arXiv:2605.17933.
