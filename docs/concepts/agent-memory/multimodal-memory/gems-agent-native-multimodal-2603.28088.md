---
title: "GEMS: Agent-Native Multimodal Generation with Memory and Skills"
arXiv: "2603.28088"
date: "2026-03-30"
tags: [agent-memory, multimodal-memory, generation, skill-management]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **作者**: Zefeng He, Siyuan Huang, Xiaoye Qu
- **方向**: 多模态生成、Agent 原生框架
- **应用**: 视觉生成、跨模态创作

## 研究背景与问题

近期多模态生成模型在通用生成任务上取得了显著进展，但在处理复杂指令和下游专业任务时仍存在局限性。现有方法依赖基础模型的固有能力，缺乏有效的记忆和技能机制来支持长期、专业的生成任务。

## 核心方法：GEMS

GEMS（Agent-Native Multimodal Generation with Memory and Skills）提出了一个 Agent 原生的多模态生成框架：

1. **记忆机制**：为多模态生成引入外部记忆，支持跨生成会话的信息保持
2. **技能库**：整合可复用的专业技能，提升复杂任务的处理能力
3. **Agent 化设计**：借鉴 Claude Code 等先进 Agent 框架的设计理念

## 核心贡献

1. **首个 Agent 原生的多模态生成框架**：将记忆和技能机制深度融入生成过程
2. **跨任务泛化能力**：在通用和下游任务上都展现出先进性能
3. **可扩展架构**：支持灵活扩展新的记忆和技能模块

## 为什么重要

GEMS 证明了将 Agent 框架（记忆+技能）引入多模态生成能有效突破基础模型的能力上限。这对构建能处理复杂专业任务的多模态 Agent 系统具有重要参考价值。

## 与端侧/移动端的相关性

端侧多模态生成应用（如移动端图像编辑）可从 GEMS 的技能机制中受益，在端侧设备上实现专业级的多模态内容生成能力。

## 参考文献

- 原文: [arXiv:2603.28088](https://arxiv.org/abs/2603.28088)
