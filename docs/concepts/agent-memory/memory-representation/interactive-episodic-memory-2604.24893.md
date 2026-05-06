---
title: "Interactive Episodic Memory with User Feedback"
arXiv: 2604.24893
date: 2026-04-27
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# Interactive Episodic Memory with User Feedback

**作者:** Nikesh Subedi, Loris Bazzani, Ziad Al-Halah
**发表:** 2026-04-27
**备注:** Accepted to CVPR 2026. Project Page: https://nsubedi11.github.io/refocus

## 摘要

In episodic memory with natural language queries (EM-NLQ), a user may ask a question (e.g., "Where did I place the mug?") that requires searching a long egocentric video, captured from the user's perspective, to find the moment that answers it. However, queries can be ambiguous or incomplete, leading to incorrect responses. Current methods ignore this key aspect and address EM-NLQ in a one-shot setup, limiting their applicability in real-world scenarios. In this work, we address this gap and introduce the Episodic Memory with Questions and Feedback task (EM-QnF). Here, the user can provide feedback on the model's initial prediction or add more information (e.g., "Before this. I'm looking for the big blue mug not the white one"), helping the model refine its predictions interactively.

## 核心贡献

1. **EM-QnF 任务定义**: 首次定义 Episodic Memory with Questions and Feedback 任务，支持用户通过反馈迭代式精化预测
2. **FALM 模块 (Feedback ALignment Module)**: 即插即用的反馈对齐模块，使现有 EM-NLQ 模型能够有效整合用户反馈
3. **轻量训练方案**: 避免昂贵的序列优化，提出了一个高效的反馈整合训练方案
4. **CVPR 2026 接收**: 在三个挑战性基准上显著超越 SOTA，与商用大规模视觉-语言模型相当但更高效

## 为什么重要

现有情景记忆方法假设查询是完整且明确的，但现实世界的查询往往是模糊或不完整的。这篇论文首次系统研究了用户反馈对情景记忆检索的影响，并提出了一个即插即用的解决方案。CVPR 2026 接收表明该方向获得计算机视觉领域顶级会议的认可。

## 与端侧/移动端的相关性

第一人称视角视频记忆在智能眼镜、AR 头显等移动设备上有直接应用。FALM 的即插即用特性使其易于集成到端侧应用中。轻量训练方案也适合在资源受限的移动设备上运行。
