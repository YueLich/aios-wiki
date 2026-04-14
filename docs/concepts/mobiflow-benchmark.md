---
type: concept
tags: [gui-agent, benchmark, trajectory, mobile, real-world]
related: [[turing-test-mobile-gui]], [[pspa-bench-gui-agent]], [[gui-agent-privacy]]
sources:
  - "[arXiv] MobiFlow: Real-World Mobile Agent Benchmarking through Trajectory Fusion"
created: 2026-04-14
---

# MobiFlow: Real-World Mobile Agent Benchmarking through Trajectory Fusion

## 核心问题

Mobile agents can autonomously complete user-assigned tasks through GUI interactions.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- In real-world mobile-agent scenarios, however, many third-party applications do not expose system-level APIs to determine whether a task has succeeded, leading to a mismatch between benchmarks and real-world usage and making it difficult to evaluate model performance accurately.
- To address these issues, we propose MobiFlow, an evaluation framework built on tasks drawn from arbitrary third-party applications.

## 实验结果

论文报告了以下主要实验结果：

- Using an efficient graph-construction algorithm based on multi-trajectory fusion, MobiFlow can effectively compress the state space, support dynamic interaction, and better align with real-world third-party application scenarios.
- MobiFlow covers 20 widely used third-party applications and comprises 240 diverse real-world tasks, with enriched evaluation metrics.
- Compared with AndroidWorld, MobiFlow's evaluation results show higher alignment with human assessments and can guide the training of future GUI-based models under real workloads.

## 为什么重要

该研究的重要性体现在：

- 建立了标准化的评估基准，推动领域发展
- 提升了计算效率，使实际部署更加可行

## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [turing-test-mobile-gui

## 参考资源

- 论文原文：https://arxiv.org/abs/2604.09587