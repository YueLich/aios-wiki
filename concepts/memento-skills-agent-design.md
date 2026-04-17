---
type: concept
tags: [agent架构, 技能学习, 持续学习, agent-design, memory-based-RL]
related: [[amc-adaptive-memory-crystallization]], [[agent-persistent-identity]], [[mga-memory-gui-agent]], [[memground-benchmark]]
sources:
  - url: https://arxiv.org/abs/2603.18743
    title: "Memento-Skills: Let Agents Design Agents"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Memento-Skills: 让 Agent 设计 Agent

> 基于记忆的强化学习框架，Agent 通过经验自主构建、适应和改进特定任务的子 Agent

## 核心问题

当前 LLM Agent 系统要么使用固定工具集（ReAct、Toolformer），要么需要人工设计特定任务的 Agent。缺乏一种机制让通用 Agent 从经验中学习，自主演化出任务专属的技能。

## 方法/架构

Memento-Skills 是一个**通用的、可持续学习的 LLM Agent 系统**，核心理念是"Agent 设计 Agent"：

**架构三要素**：
1. **有状态提示（Stateful Prompts）**：技能以结构化 Markdown 文件存储，作为持久演化的记忆
2. **记忆驱动的 RL 框架**：技能编码行为和上下文，使 Agent 跨交互携带知识
3. **读写反思学习（Read-Write Reflective Learning）**：
   - **读阶段**：Agent 读取已有技能，理解任务需求
   - **写阶段**：基于执行结果，创建或修改技能文件

**技能演化路径**：
```
基础技能（Web搜索、终端操作）
    ↓ 经验积累
复合技能（多步骤任务编排）
    ↓ 持续改进
专业化技能（领域特定的高效策略）
```

**关键创新**：技能不是代码，而是结构化 Markdown——包含前置条件、执行步骤、后置条件和学习笔记。这使得技能既人类可读，又可被 Agent 自动修改。

基于 Memento 2 的 Read-Write Reflective Learning 机制，Agent 在每次交互后反思执行结果，将成功经验固化为技能，将失败经验转化为技能的前置条件约束。

## 为什么重要

对于手机端 AIOS Agent：
- **自适应技能学习**：Agent 可以从用户的日常操作中学习，自动生成个性化技能
- **资源高效**：技能以文件形式存储，不需要额外的模型参数
- **可解释性**：Markdown 格式的技能人类可读，便于用户审核和修改
- **持续演化**：Agent 能力随使用时间增长，而非固定不变

这与传统"写死工具集"的 Agent 形成鲜明对比——Memento-Skills 提出了一种**有机增长的 Agent 能力体系**。对于手机端，这意味着 Agent 可以从用户的操作模式中学习，逐渐成为真正个性化的助手。

## 关联
- [[amc-adaptive-memory-crystallization]] — AMC 的记忆结晶化与 Memento-Skills 的技能学习互补
- [[agent-persistent-identity]] — Agent 持久化身份需要技能作为能力载体
- [[mga-memory-gui-agent]] — MGA 的 GUI Agent 可以用 Memento-Skills 框架学习交互技能
- [[memground-benchmark]] — MemGround 可以评估 Memento-Skills 的记忆能力
