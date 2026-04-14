---
type: concept
tags: [gui-agent, benchmark, trajectory, mobile, real-world]
related: [[turing-test-mobile-gui]], [[pspa-bench-gui-agent]], [[gui-agent-privacy]]
sources:
  - "[arXiv] MobiFlow: Real-World Mobile Agent Benchmarking through Trajectory Fusion"
created: 2026-04-14
---

# MobiFlow：真实世界移动 Agent 轨迹融合基准

## 概念定义

MobiFlow 是一个通过轨迹融合（Trajectory Fusion）进行真实世界移动 Agent 评估的基准框架。它收集真实用户的操作轨迹，构建多任务、跨应用的评估场景，使测试更贴近实际使用模式。

## 为什么重要

现有基准多在模拟环境中测试，与真实手机使用场景存在较大差距。MobiFlow 的创新在于：
1. **轨迹驱动**：基于真实用户操作数据构建测试用例
2. **跨应用流程**：真实任务往往需要跨越多个 App
3. **融合技术**：将多个简单轨迹组合成复杂任务流

这对评估 Agent 在真实手机环境下的表现至关重要——不再是孤立的单 App 测试，而是端到端的真实工作流。

## 与手机端 AIOS 的关联

手机 AIOS 的 Agent 需要在真实、复杂的多任务场景下工作。MobiFlow 这类基于真实轨迹的基准，对于验证 Agent 在实际手机环境中的可靠性具有指导意义。与 [[gui-agent-privacy]] 结合，轨迹数据的收集也需要考虑隐私保护。

## 相关概念

- [[turing-test-mobile-gui]] — 拟人化评估维度
- [[pspa-bench-gui-agent]] — 个性化基准测试
- [[gui-agent-privacy]] — Agent 操作中的隐私保护
