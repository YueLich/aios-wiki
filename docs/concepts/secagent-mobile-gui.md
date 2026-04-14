---
type: concept
tags: [gui-agent, mobile, semantic, automation, efficiency]
related: [[mobile-agent-framework]], [[pspa-bench-gui-agent]], [[clawmobile-agentic]]
sources:
  - url: https://arxiv.org/abs/2603.08533v2
    title: "SecAgent: Efficient Mobile GUI Agent with Semantic Context"
    date: 2026-03
created: 2026-04-14
---

# SecAgent: Efficient Mobile GUI Agent with Semantic Context

## 核心问题

Mobile Graphical User Interface (GUI) agents powered by multimodal large language models have demonstrated promising capabilities in automating complex smartphone tasks.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- To address these challenges, we present SecAgent, an efficient mobile GUI agent at 3B scale.
- We first construct a human-verified Chinese mobile GUI dataset with 18k grounding samples and 121k navigation steps across 44 applications, along with a Chinese navigation benchmark featuring multi-choice action annotations.

## 实验结果

论文报告了以下主要实验结果：

- Building upon this dataset, we propose a semantic context mechanism that distills history screenshots and actions into concise, natural language summaries, significantly reducing computational costs while preserving task-relevant information.
- Through supervised and reinforcement fine-tuning, SecAgent outperforms similar-scale baselines and achieves performance comparable to 7B-8B models on our and public navigation benchmarks.
- Our dataset is available at https://huggingface.co/datasets/alibabagroup/CMGUI.

## 为什么重要

该研究的重要性体现在：

- 提供了高质量的数据集，为相关研究提供宝贵资源
- 建立了标准化的评估基准，推动领域发展
- 提升了计算效率，使实际部署更加可行

## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [mobile-agent-framework

## 参考资源

- 论文原文：https://arxiv.org/abs/2603.08533