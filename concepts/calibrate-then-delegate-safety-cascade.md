---
type: concept
tags: [model-cascade, safety-monitoring, edge-cloud, llm-safety, delegation, 模型级联]
related: [[comllm-mec-offloading]], [[edge-cloud-offloading]], [[rpra-llm-judge-inference]], [[e-grm-efficient-generative-reward-modeling]], [[agentopt-client-side-optimization]]
sources:
  - url: https://arxiv.org/abs/2604.14251
    title: "Calibrate-Then-Delegate: Safety Monitoring with Risk and Budget Guarantees via Model Cascades"
    date: 2026-04-18
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Calibrate-Then-Delegate: 基于模型级联的安全监控

> 提出校准-委托框架，用廉价的潜空间探针做初筛、将高风险 case 委托给专家模型——为端侧 LLM 安全监控提供了成本可控的解决方案。

## 核心问题

大规模部署 LLM 时，安全监控面临**成本-精度权衡**：
- 完全用大模型做安全审查：成本高、延迟大
- 完全用小模型/探针：漏检率高，无法处理复杂攻击
- 现有级联方法基于不确定性委托，但不确定性≠委托收益——高不确定性 case 不一定是真正需要专家的 case

## 方法/架构

**Calibrate-Then-Delegate** 框架的核心创新：

1. **校准阶段**：对廉价探针（如潜空间分类器）进行校准，使其输出可靠的风险概率
2. **委托决策**：不是基于"探针不确定"来委托，而是基于"委托给专家后能获得多少额外收益"来决定
3. **风险保证**：在给定的预算约束下，保证整体风险控制在阈值内
4. **预算感知**：支持动态调整委托策略，在 API 成本和安全性之间取得最优平衡

与传统模型级联的关键区别：传统方法委托的是"不确定"的 case，本方法委托的是"专家能带来最大收益"的 case。

## 实验结果

- 在 LLM 安全监控任务上，相比固定阈值委托减少 30-50% 的专家调用
- 在相同预算下，安全监控精度提升 15-25%
- 支持风险和预算的双约束优化

## 关键洞察

1. **不确定性 ≠ 价值**：传统级联用不确定性做委托决策，但这不是最优策略。探针"不确定"的 case 专家可能也帮不上忙
2. **校准是前提**：只有校准后的探针才能提供可靠的概率估计，进而做出合理的委托决策
3. **预算约束是现实需求**：端侧部署的 API 预算有限，需要在精度和成本之间智能分配

## 为什么重要

手机端 LLM 部署面临严格的计算和成本约束。当端侧模型（如 Gemma、MiniCPM）处理用户请求时，需要一个高效的安全监控层：
- **端侧初筛**：用轻量探针做第一层安全检查（几乎零成本）
- **选择性上报**：只将高风险 case 委托给云端大模型
- **成本可控**：在预算约束内最大化安全覆盖

这对端云协同架构中的安全层设计有直接参考价值。

## 关联
- [[comllm-mec-offloading]] — 边缘卸载中的任务分发策略
- [[edge-cloud-offloading]] — 端云协同的基础架构
- [[rpra-llm-judge-inference]] — LLM-as-Judge 的高效推理
- [[e-grm-efficient-generative-reward-modeling]] — 高效奖励模型
- [[agentopt-client-side-optimization]] — 客户端优化策略
