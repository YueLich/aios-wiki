---
title: "AutoSearch: Adaptive Search Depth for Efficient Agentic RAG via Reinforcement Learning"
arXiv: 2604.17337
date: 2026-04-19
tags: [agent-memory, memory-retrieval, agentic-rag, rl]
reviewer: auto
source: arXiv RSS/API
---

# AutoSearch: Adaptive Search Depth for Efficient Agentic RAG

## 论文基本信息

- **标题**: AutoSearch: Adaptive Search Depth for Efficient Agentic RAG via Reinforcement Learning
- **arXiv ID**: 2604.17337
- **发表日期**: 2026-04-19
- **作者**: Jingbo Sun, Wenyue Chong, Songjun Tu, Qichao Zhang, Yaocheng Zhang, Jiajun Chai, Xiaohan Wang, Wei Lin, Guojun Yin, Dongbin Zhao
- **方向**: 记忆检索 · Agentic RAG
- **类别**: cs.AI

## 摘要（原文翻译）

Agentic RAG 系统使大语言模型（LLM）能够通过多步交互与外部检索工具协作解决复杂任务。然而，这种多步交互涉及冗余搜索步骤，产生大量计算成本和延迟。先前工作限制搜索深度（即搜索步数）以降低成本，但这往往导致对复杂问题的探索不足。为解决这一问题，本文首先研究搜索深度如何影响准确率，发现一个定义准确率-效率权衡的最小充分搜索深度——它由问题复杂度和智能体能力共同决定。此外，本文提出 AutoSearch，一个强化学习（RL）框架，通过自生成 critique 信号评估每个搜索步骤的价值，从而自适应地决定何时停止搜索。

## 核心贡献

1. **最小充分搜索深度发现**：通过分析搜索深度与准确率的关系，发现存在一个由问题复杂度和智能体能力共同决定的最小充分搜索深度
2. **自批评信号评估**：AutoSearch 使用 RL 让智能体对自己的每步搜索进行自评估，无需人工设计停止规则
3. **准确率-效率自适应平衡**：根据问题复杂度动态调整搜索步数，避免简单问题过度搜索、复杂问题探索不足

## 为什么重要

记忆检索的搜索深度直接影响答案质量——太浅导致信息不完整，太深则引入不必要的延迟和噪声。AutoSearch 通过强化学习自适应学习何时停止，这对于持续运行、记忆不断增长的智能体系统至关重要。与固定搜索深度相比，AutoSearch 可以将简单查询的延迟降低 50%+，同时保证复杂查询的准确率。

## 与移动端/端侧的相关性

- **高相关性**：移动端设备算力有限，自适应搜索深度可减少不必要的计算
- **边缘部署**：边缘设备上的记忆系统可受益于提前停止策略，降低能耗
- **实时应用**：对于需要快速响应的移动端场景（如 AR 辅助），自适应搜索可保证响应时间

## 参考文献

- 原论文: https://arxiv.org/abs/2604.17337
