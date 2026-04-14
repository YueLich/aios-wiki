---
type: concept
tags: [gui-agent, benchmark, humanization, mobile, evaluation]
related: [[pspa-bench-gui-agent]], [[secagent-mobile-gui]], [[clawmobile-agentic]]
sources:
  - "[arXiv] Turing Test on Screen: A Benchmark for Mobile GUI Agent Humanization"
created: 2026-04-14
---

# Turing Test on Screen: A Benchmark for Mobile GUI Agent Humanization

## 核心问题

The rise of autonomous GUI agents has triggered adversarial countermeasures from digital platforms, yet existing research prioritizes utility and robustness over the critical dimension of anti-detection.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- We argue that for agents to survive in human-centric ecosystems, they must evolve Humanization capabilities.
- We introduce the ``Turing Test on Screen,'' formally modeling the interaction as a MinMax optimization problem between a detector and an agent aiming to minimize behavioral divergence.
- We then collect a new high-fidelity dataset of mobile touch dynamics, and conduct our analysis that vanilla LMM-based agents are easily detectable due to unnatural kinematics.

## 实验结果

论文报告了以下主要实验结果：

- Consequently, we establish the Agent Humanization Benchmark (AHB) and detection metrics to quantify the trade-off between imitability and utility.
- Finally, we propose methods ranging from heuristic noise to data-driven behavioral matching, demonstrating that agents can achieve high imitability theoretically and empirically without sacrificing performance.
- This work shifts the paradigm from whether an agent can perform a task to how it performs it within a human-centric ecosystem, laying the groundwork for seamless coexistence in adversarial digital environments.

## 为什么重要

该研究的重要性体现在：

- 提供了高质量的数据集，为相关研究提供宝贵资源
- 建立了标准化的评估基准，推动领域发展

## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [pspa-bench-gui-agent

## 参考资源

- 论文原文：https://arxiv.org/abs/2604.09574