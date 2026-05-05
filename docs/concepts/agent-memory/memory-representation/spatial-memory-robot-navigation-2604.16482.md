---
title: "A Survey of Spatial Memory Representations for Efficient Robot Navigation"
arXiv: 2604.16482
date: 2026-04-13
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# A Survey of Spatial Memory Representations for Efficient Robot Navigation

## 论文基本信息

- **作者**: Ma. Madecheen S. Pangaliman, Steven S. Sison, Erwin P. Quilloy, Rowel Atienza
- **arXiv**: https://arxiv.org/abs/2604.16482
- **领域**: cs.CV
- **备注**: Accepted at the Women in Computer Vision (WiCV) Workshop at CVPR 2026

## 摘要

As vision-based robots navigate larger environments, their spatial memory grows without bound, eventually exhausting computational resources, particularly on embedded platforms (8-16GB shared memory, $&lt;$30W) where adding hardware is not an option. This survey examines the spatial memory efficiency problem across 88 references spanning 52 systems (1989-2025), from occupancy grids to neural implicit representations. We introduce the $α= M_{\text{peak}} / M_{\text{map}}$, the ratio of peak runtime memory (the total RAM or GPU memory consumed during operation) to saved map size (the persistent checkpoint written to disk), exposing the gap between published map sizes and actual deployment cost. Independent profiling on an NVIDIA A100 GPU reveals that $α$ spans two orders of magnitude within neural methods alone, ranging from 2.3 (Point-SLAM) to 215 (NICE-SLAM, whose 47,MB map requires 10GB at runtime), showing that memory architecture, not paradigm label, determines deployment feasibility. We propose a standardized evaluation protocol comprising memory growth rate, query latency, memory-completeness curves, and throughput degradation, none of which current benchmarks capture. Through a Pareto frontier analysis with explicit benchmark separation, we show that no single paradigm dominates within its evaluation regime: 3DGS methods achieve the best absolute accuracy at 90-254,MB map size on Replica, while scene graphs provide semantic abstraction at predictable cost. We provide the first independently measured $α$ reference values and an $α$-aware budgeting algorithm enabling practitioners to assess deployment feasibility on target hardware prior to implementation.

## 核心贡献

1. （待补充：基于摘要提炼 3-5 条核心贡献）
2. 
3. 

## 研究背景与问题

（待补充：论文要解决的核心问题是什么？为什么这个问题重要？）

## 核心方法

（待补充：论文的核心方法/技术方案）

## 为什么重要

（待补充：论文的主要贡献和意义）

## 与移动端/端侧相关性

（待补充：该研究与端侧/移动端 Agent 记忆系统的关联）
