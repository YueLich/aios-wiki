---
title: "PASK: Toward Intent-Aware Proactive Agents with Long-Term Memory"
arXiv: "2604.08000"
date: "2026-04-09"
tags: [agent-memory, long-term-memory, proactive-agents]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

主动性是通用人工智能的核心期望。现有研究大多停留在实验室场景，在真实世界的主动性 Agent 方面存在明显差距：深度、复杂性、歧义性、精确性和实时约束等挑战。本文研究在延迟和长视野约束下，从持续上下文推断潜在需求并在演化的用户记忆中落地行动的场景。提出 **DD-MM-PAS**（需求检测、记忆建模、主动性 Agent 系统）作为流式主动性 AI Agent 通用范式，并在 Pask 系统中实例化，包含用于 DD 的流式 IntentFlow 模型、用于长期 MM 的混合记忆（工作空间、用户、全局），以及 PAS 基础设施框架。引入 **LatentNeeds-Bench** 基准，从用户授权数据构建并经数千轮人工编辑精炼。实验表明，IntentFlow 在延迟约束下达到 Gemini3-Flash 模型的领先水平，同时识别更深层用户意图。

## 核心贡献

1. **DD-MM-PAS 通用范式**：提出 Demand Detection、Memory Modeling、Proactive Agent System 三层架构，为流式主动性 AI Agent 提供统一框架
2. **Pask 系统实例化**：混合记忆模块包含工作空间记忆（短期任务上下文）、用户记忆（长期偏好）、全局记忆（共享知识）
3. **IntentFlow 模型**：流式需求检测模型，在延迟约束下达到 Gemini3-Flash 同等性能，同时识别更深层用户意图
4. **LatentNeeds-Bench 基准**：首个从真实用户授权数据构建的主动性 Agent 评测基准，经数千轮人工编辑确保质量
5. **主动干预闭合回路**：各组件形成闭环——检测到潜在需求 → 查用户记忆 → 主动生成干预

## 为什么重要

现有 Agent 多为被动响应式，而真实世界需要主动预见用户需求。PASK 将记忆系统从"被动存储"升级为"主动推断"，结合混合记忆架构解决了三个关键问题：(1) 如何从噪声流式输入中检测真实需求；(2) 如何利用多层次记忆支持长期偏好理解；(3) 如何在严格延迟约束下完成实时推理。

## 与端侧/移动端的相关性

- **流式处理**：IntentFlow 模型专为低延迟场景设计，适合手机、AR 眼镜等实时交互设备
- **混合记忆分层**：工作空间/用户/全局三层分离，用户隐私数据可完全保留在本地
- **边缘友好**：主动干预决策可在云端完成，记忆查询和恢复在边缘侧执行
- **隐私授权数据**：LatentNeeds-Bench 基于真实用户数据构建，确保benchmark 反映实际场景

## 参考文献

- DD-MM-PAS 范式：需求检测、记忆建模、主动性 Agent 系统
- LatentNeeds-Bench：用户授权数据，2000+ 轮人工编辑
- IntentFlow：延迟约束下对标 Gemini3-Flash
