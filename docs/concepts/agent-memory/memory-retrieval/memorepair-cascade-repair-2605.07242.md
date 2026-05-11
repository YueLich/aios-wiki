---
title: "MEMOREPAIR: Barrier-First Cascade Repair in Agentic Memory"
arXiv: 2605.07242
date: 2026-05-08
tags: [agent-memory, memory-retrieval, memory-maintenance]
reviewer: auto
source: arXiv API
---

## 摘要

Agentic Memory 在跨任务演化中形成持久派生物（summaries、cached outputs、embeddings、learned skills、executable tool procedures）。当源 artifacts 被删除、修正或因工具/API 迁移失效时，由此派生的 descendants 可能仍然可见并以陈旧依据 steering 未来行为。本文将这种失效模式形式化为**级联更新问题（Cascade Update Problem）**，repair 目标是记忆存储的可见派生状态（visible derived state）。本文提出 MemoRepair，一种 barrier-first 级联修复合约。修复事件从失效后代状态到经验证后继状态触发受控转换：受影响后代在修复前撤回，后继从 retained support 构建并在当前接口下 staged repaired predecessors，publication 限制为经验证的 predecessor-closed successors。该合约导出固定修复成本权衡的标量化修复选择问题。在 ToolBench 和 MemoryArena 上的实验表明：MemoRepair 将无级联修复系统的失效记忆暴露从 69.8-94.3% 降至 0%；相较于穷举 Repair-all，在降低标准化修复操作成本（1.00→0.57-0.76）的同时恢复了 91.1-94.3% 的经验证后继。

## 核心贡献

1. **级联更新问题形式化**：将源 artifact 失效导致的后代可见状态问题建模为级联更新问题
2. **MemoRepair 合约**：barrier-first 级联修复三步流程（撤回→构建→发布）
3. **publication 限制策略**：仅允许经验证的 predecessor-closed successors 重新发布
4. **最优化求解**：修复选择问题可归约为最大权重前驱闭包，通过单次 s-t min-cut 精确求解
5. **实验验证**：ToolBench 和 MemoryArena 上显著降低失效记忆暴露和修复成本

## 为什么重要

真实世界的 Agent 记忆不是静态快照，而是不断演化的派生关系网络。当底层信息变化（API 更新、知识修正、工具迁移），整个派生链都可能受影响。现有系统没有处理这个问题的机制，导致 Agent 继续基于陈旧信息做决策。MemoRepair 首次系统解决了这个问题，并给出了可证明最优的修复策略。

## 与移动端/端侧相关性

端侧 Agent 的记忆存储同样面临底层信息频繁变化的问题（如本地文件修改、App 版本更新、用户偏好变化），MemoRepair 的 barrier-first 策略和成本优化思路对轻量级级联修复有借鉴意义。其标量化修复选择问题也适用于资源受限的端侧环境。
