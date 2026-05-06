---
title: "Rashomon Memory: Towards Argumentation-Driven Retrieval for Multi-Perspective Agent Memory"
arXiv: 2604.03588
date: 2026-04-04
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# Rashomon Memory: Towards Argumentation-Driven Retrieval for Multi-Perspective Agent Memory

## 论文基本信息

- **作者**: Yike Wu, Tingting Mu, Jinmao Liu, Haoran Yang, Yu Gong
- **arXiv**: https://arxiv.org/abs/2604.03588
- **领域**: cs.AI, cs.IR

## 摘要

虽然大语言模型（LLM）在对话和推理方面表现出色，但现有 Agent 记忆系统通常依赖单一同质检索视角，无法捕捉人类记忆的多样性本质——同一事件可以有多种合理但相互矛盾的解读。Rashomon Memory 框架将多视角论证驱动检索引入 Agent 记忆系统，借鉴法律论证中的 Rashomon 效应（同一事件存在多个可信但相互矛盾的叙事版本）。该系统从历史交互中提取多条论证路径，允许 Agent 在检索时选择不同立场（支持/反对/中立），从而支持更全面、更具批判性的决策。

## 核心贡献

1. **Rashomon Memory 框架**: 首个将论证驱动多视角检索引入 Agent 记忆系统的框架
2. **Argumentation Graph**: 将历史交互建模为论证图（节点=主张，边=论证关系），支持多视角检索
3. **多立场检索**: 允许 Agent 按不同立场（pro/con/neutral）检索相关记忆，而非单一答案
4. **决策质量提升**: 在多智能体辩论和决策任务上，多视角记忆检索显著优于单视角基线
5. **可解释性**: 每个检索结果附带论证路径，提升 Agent 决策的可解释性

## 研究背景与问题

传统向量检索或知识库检索返回单一"最佳答案"，但人类记忆天然具有多视角性——同一事件可以有多种合理解读。Agent 在复杂环境中需要考虑不同立场，但现有记忆系统无法提供这种多样性。当多个 Agent 需要协商或辩论时，缺乏多视角记忆会导致立场固化。

## 核心方法

1. **Argumentation Mining**: 从历史交互中自动挖掘论证结构（主张、依据、支持/反对关系）
2. **Multi-Perspective Memory Index**: 将论证图按立场分层索引，支持立场过滤检索
3. **Argumentation Retrieval Model**: 给定查询和立场，返回按该立场排序的相关记忆
4. **Agent Integration**: 与 LLM Agent 无缝集成，提供多视角记忆检索作为上下文

## 为什么重要

Rashomon Memory 打破了传统 RAG"单一最佳答案"的范式，引入论证驱动的多视角记忆检索。对于需要批判性思考、多智能体协商或复杂决策的 Agent，多视角记忆提供了更丰富的历史参考。这是记忆系统从"检索工具"向"推理伙伴"演进的重要一步。

## 与移动端/端侧相关性

1. **论证图结构**: 论证图比原始文本更紧凑，适合端侧存储受限场景
2. **立场过滤**: 可在检索时只加载相关立场子图，降低内存占用
3. **多智能体协作**: 对分布式端侧多智能体系统的协商记忆有直接参考价值
4. **可解释决策**: 在资源受限的嵌入式 Agent 中，多视角记忆可辅助更透明的推理
