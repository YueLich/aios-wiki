---
type: concept
tags: [privacy, gui-agent, personalization, mobile, preference-optimization]
related: [[mobile-agent-framework]], [[pspa-bench-gui-agent]], [[sustainability-ondevice-intelligence]]
sources:
  - url: https://arxiv.org/abs/2604.11259v1
    title: "Mobile GUI Agent Privacy Personalization with Trajectory Induced Preference Optimization"
    date: 2026-04
created: 2026-04-14
---

# Mobile GUI Agent Privacy Personalization with Trajectory Induced Preference Optimization

## 核心问题

Mobile GUI agents powered by Multimodal Large Language Models (MLLMs) can execute complex tasks on mobile devices.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- Despite this progress, most existing systems still optimize task success or efficiency, neglecting users' privacy personalization.
- In this paper, we study the often-overlooked problem of agent personalization.
- We observe that personalization can induce systematic structural heterogeneity in execution trajectories.

## 实验结果

论文报告了以下主要实验结果：

- For example, privacy-first users often prefer protective actions, e.g., refusing permissions, logging out, and minimizing exposure, leading to logically different execution trajectories from utility-first users.
- Such variable-length and structurally different trajectories make standard preference optimization unstable and less informative.
- To address this issue, we propose Trajectory Induced Preference Optimization (TIPO), which uses preference-intensity weighting to emphasize key privacy-related steps and padding gating to suppress alignment noise.

## 为什么重要

该研究的重要性体现在：

- Results on our Privacy Preference Dataset show that TIPO improves persona alignment and distinction while preserving strong task executability, achieving 65.60% SR, 46.22 Compliance, and 66.67% PD, outperforming existing optimization methods across various GUI tasks.
- The code and dataset will be publicly released at https://github.com/Zhixin-L/TIPO.

## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [mobile-agent-framework

## 参考资源

- 论文原文：https://arxiv.org/abs/2604.11259