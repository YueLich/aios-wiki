---
title: "MementoGUI: Learning Agentic Multimodal Memory Control for Long-Horizon GUI Agents"
arXiv: 2605.18652
date: 2026-05-18
tags: [agent-memory, multimodal-memory, gui-agent, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: 多机构合作

**核心问题**: 现有 GUI agent 在长时序任务中难以维持任务状态——跨多个界面转换时，早期的关键操作上下文会被后续步骤稀释，导致任务失败或效率下降。

**方法**: MementoGUI 提出一种 agentic 多模态记忆控制框架，将 GUI 交互过程中的视觉、文本、动作序列统一建模为多模态记忆，并在检索时实现动态压缩与优先级调度。

### 多模态记忆架构

1. **多模态记忆编码**：将屏幕截图（视觉）、可访问性树文本（结构化）、动作历史（时序）统一编码为混合向量表示
2. **任务感知压缩**：根据当前子目标动态决定哪些记忆需要保持高精度、哪些可以压缩
3. **层次化检索**：两层检索——高层任务目标匹配 + 低层操作细节回溯

## 核心贡献

1. **首个 GUI agent 多模态记忆框架**：统一建模视觉、文本、动作三种模态的记忆表示
2. **任务感知压缩机制**：在记忆受限的端侧场景下实现按需压缩，保证关键细节不丢失
3. **长时序任务 SOTA**：在 MobileEbench、GAIA 基准上相较基线平均提升 23% 任务完成率
4. **对未见应用的零样本泛化**：多模态记忆编码使 agent 能处理训练集中未见的应用界面

## 为什么重要

GUI automation 是端侧智能的核心场景（手机操控、桌面自动化、车载信息娱乐）。MementoGUI 解决了这一领域长期存在的"长时序上下文丢失"痛点，其多模态记忆架构为多模态 LLM agent 在资源受限设备上的部署提供了可行方案。

## 与移动端/端侧的相关性

GUI Agent 是端侧智能的核心应用之一（手机操控、桌面自动化）。MementoGUI 的多模态记忆架构意味着可以在本地设备上维护一个压缩的多模态状态记忆，在保护用户隐私的同时实现个性化（设备特定）的 GUI 自动化。论文方法对移动端和桌面端部署均有直接参考价值。

## 参考文献

- Zeng, Z., et al. (2026). MementoGUI: Learning Agentic Multimodal Memory Control for Long-Horizon GUI Agents. arXiv:2605.18652.
