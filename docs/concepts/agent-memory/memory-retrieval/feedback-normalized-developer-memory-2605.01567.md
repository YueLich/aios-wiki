---
title: "Feedback-Normalized Developer Memory for Reinforcement-Learning Coding Agents: A Safety-Gated MCP Architecture"
arXiv: 2605.01567
date: 2026-05-12
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Mehmet Iscan
- **提交日期**: 2026-05-12

## 摘要

LLM coding agents operate over repositories, terminals, tests, and execution traces across long software-engineering episodes. Persistent memory is useful but existing approaches store all interactions uniformly, leading to memory bloat and retrieval pollution. This paper proposes Feedback-Normalized Developer Memory (FNDM), where the signal for what to store comes from downstream feedback (test results, build success/failure, code review outcomes) rather than the agent itself. FNDM introduces a Safety-Gated Memory Controller that only writes to persistent memory when an action receives positive feedback—passing tests, successful builds, or approved reviews. Negative feedback implicitly suggests the underlying assumption was wrong and should not be reinforced. This creates a self-curating memory that naturally prioritizes successful strategies. The Memory Communication Protocol (MCP) architecture enables safe memory sharing across agent sessions. Evaluated on SWE-bench-like tasks, FNDM reduces memory size by 60% while improving task success rate by 12% compared to uniform memory storage.

## 核心贡献

1. **反馈驱动记忆写入**: 只在下游反馈正面时（测试通过、构建成功）才写入记忆
2. **安全门控记忆控制器**: 负面反馈隐含假设错误，不应被强化
3. **自清理记忆**: 自然优先排序成功策略，内存占用减少 60%

## 为什么重要

解决了统一记忆存储导致的内存膨胀和检索污染问题。通过引入下游反馈信号，记忆系统能够自清理、自我优化。

## 与端侧/移动端的相关性

记忆压缩 60% 的效果对端侧资源受限环境特别有价值。MCP 架构支持跨会话安全共享记忆，可在边缘设备间协作。
