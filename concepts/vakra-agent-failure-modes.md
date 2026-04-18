---
type: concept
tags: [Agent, 基准测试, 失败模式, 推理, 工具使用, IBM]
related: [[secagent-mobile-gui]], [[clawmobile-agentic]], [[mga-memory-gui-agent]], [[pspa-bench-gui-agent]]
sources:
  - url: https://huggingface.co/blog/ibm-research/vakra-benchmark-analysis
    title: "Inside VAKRA: Reasoning, Tool Use, and Failure Modes of Agents"
    date: 2026-04-15
    reliability: high
  - url: https://github.com/ibm-research/VAKRA
    title: "VAKRA GitHub Repository"
    date: 2026-04-15
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# VAKRA: Agent 推理与工具使用的失败模式分析

> IBM Research 推出的 Agent 基准测试，深入分析 Agent 在推理、工具使用中的系统性失败模式，而非仅测量成功率。提供详细的 failure taxonomy 以指导 Agent 架构改进。

## 核心问题
现有 Agent 基准（如 SWE-Bench、WebArena）主要测量任务成功率，但不回答关键问题：**Agent 为什么失败？** 同样的 30% 失败率可能来自完全不同的原因——推理缺陷、工具调用错误、规划偏差或记忆丢失。没有失败模式分析，就无法有针对性地改进 Agent 架构。

## 方法架构

VAKRA 不仅测量 Agent 性能，还系统分类失败模式：

**失败模式分类体系**：
1. **推理失败**：逻辑错误、假设矛盾、遗漏约束
2. **工具使用失败**：错误的 API 调用、参数错误、工具选择错误
3. **规划失败**：任务分解不当、步骤遗漏、死循环
4. **上下文失败**：丢失历史信息、误解用户意图、幻觉

### 评测维度
- **推理准确性**：逻辑推理、数学推理、常识推理
- **工具使用熟练度**：API 发现、参数构造、错误处理
- **失败恢复能力**：Agent 能否从错误中恢复

## 关键洞察

1. **失败模式比成功率更重要**：两个 Agent 可能有相同的 70% 成功率，但一个主要在工具调用上失败（可通过更好的 API schema 修复），另一个主要在推理上失败（需要更根本的架构改进）。VAKRA 的 taxonomy 让开发者知道该改进什么。

2. **端侧 Agent 的失败模式可能不同**：端侧 Agent（如手机 GUI Agent）面临的额外挑战——屏幕信息有限、操作延迟、功耗约束——可能导致不同分布的失败模式。将 VAKRA 的 taxonomy 扩展到端侧场景是一个有价值的研究方向。

3. **与 GUI Agent 基准的互补**：[[pspa-bench-gui-agent]] 测量 GUI Agent 的任务成功率，VAKRA 提供失败模式分析方法论。两者结合可以更全面地评估和改进端侧 Agent。

## 为什么重要

- **Agent 开发的诊断工具**：不再盲目试错，而是通过失败模式分析精确改进
- **为端侧 Agent 提供参考**：VAKRA 的 taxonomy 可以扩展到 mobile GUI Agent 场景
- **指导模型选择**：不同模型在不同失败模式上表现不同，帮助选择适合端侧部署的模型

## 关联
- [[secagent-mobile-gui]] — GUI Agent 的安全性与失败模式
- [[clawmobile-agentic]] — 移动端 Agent 架构设计
- [[pspa-bench-gui-agent]] — GUI Agent 基准测试
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent（减少上下文失败）
