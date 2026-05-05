---
title: "MMA: Multimodal Memory Agent"
arXiv: 2602.16493
date: 2026-02-19
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Yihao Lu, Wanru Cheng, Zeyu Zhang, Hao Tang
- **提交日期**: 2026-02-19

## 摘要

Long-horizon multimodal agents depend on external memory; however, similarity-based retrieval often surfaces stale, low-credibility, or conflicting items, which can trigger overconfident errors. We propose Multimodal Memory Agent (MMA), which assigns each retrieved memory item a dynamic reliability score. MMA stores memories with multimodal evidence: raw observations, derived annotations, and source credibility signals. During retrieval, rather than returning a flat list sorted by similarity, MMA returns memories annotated with reliability-weighted relevance scores. Reliability is computed from source freshness (was this observation recent?), source consistency (do other sources corroborate?), and retrieval history (has this memory been useful before?). Conflicting memories are explicitly flagged rather than silently averaged.

## 核心贡献

1. **可靠性评分记忆**: 每条记忆项附带动态可靠性分数
2. **多模态证据存储**: 原始观测、派生注释、来源可信度信号
3. **冲突记忆显式标记**: 不静默平均，而是显式标记冲突

## 为什么重要

解决了多模态记忆检索中置信度估计缺失的问题，显著降低了长期视觉-语言导航任务的错误率。

## 与端侧/移动端的相关性

**高度端侧相关**：可靠性加权机制减少了对过时或冲突记忆的依赖，在资源受限的移动感知场景中特别有价值。
