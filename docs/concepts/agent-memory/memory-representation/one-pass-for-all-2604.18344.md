---
title: "One Pass for All: A Discrete Diffusion Model for Knowledge Graph Triple Set Prediction"
arXiv: 2604.18344
date: 2026-04-20
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# One Pass for All: A Discrete Diffusion Model for Knowledge Graph Triple Set Prediction

**作者:** Jihong Guan, Jiaqi Wang, Wengen Li, Hanchen Yang, Yichao Zhang et al.  
**发表:** 2026-04-20

## 摘要

Knowledge Graphs (KGs) are composed of triples, and the goal of Knowledge Graph Completion (KGC) is to infer the missing factual triples. Traditional KGC tasks predict missing elements in a triple given one or two of its elements. As a more realistic task, the Triple Set Prediction (TSP) task aims to infer the set of missing triples conditioned only on the observed knowledge graph, without assuming any partial information about the missing triples. Existing TSP methods predict the set of missing triples in a triple-by-triple manner, falling short in capturing the dependencies among the predicted triples to ensure consistency. To address this issue, we propose a novel discrete diffusion model termed DiffTSP that treats TSP as a generative task. DiffTSP progressively adds noise to the KG through a discrete diffusion process, achieved by masking relational edges. The reverse process then gradually recovers the complete KG conditioned on the incomplete graph. To this end, we design a structure-aware denoising network that integrates a relational context encoder with a relational graph diffusion transformer for knowledge graph generation. DiffTSP can generate the complete set of triples in a one-pass manner while ensuring the dependencies among the predicted triples. Our approach achieves state-of-the-art performance on three public datasets. Code: https://github.com/ADMIS-TONGJI/DiffTSP.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
