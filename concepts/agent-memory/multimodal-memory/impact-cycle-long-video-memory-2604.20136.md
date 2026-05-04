---
title: "IMPACT-CYCLE: A Contract-Based Multi-Agent System for Claim-Level Supervisory Correction of Long-Video Semantic Memory"
arXiv: 2604.20136
date: 2026-04-22
tags: [agent-memory, semantic-memory, multi-agent, long-video, supervision]
reviewer: auto
source: arXiv RSS/API
---

# IMPACT-CYCLE: A Contract-Based Multi-Agent System for Claim-Level Supervisory Correction of Long-Video Semantic Memory

## 论文基本信息

- **arXiv ID**: 2604.20136
- **作者**: (From paper)
- **提交日期**: 2026-04-22
- **类别**: cs.AI, cs.CV, cs.MA

## 摘要

Correcting errors in long-video understanding is disproportionately costly: existing multimodal pipelines produce opaque, end-to-end outputs that expose no intermediate state for inspection, forcing annotators to revisit raw video and reconstruct temporal logic from scratch. The core bottleneck is not generation quality alone, but the absence of a supervisory interface through which human effort can be proportional to the scope of each error. We present IMPACT-CYCLE, a supervisory multi-agent system that reformulates long-video understanding as iterative claim-level maintenance of a shared semantic memory -- a structured, versioned state encoding typed claims, a claim dependency graph, and a provenance log. Role-specialized agents operating under explicit authority contracts decompose verification into local object-relation correctness, cross-temporal consistency, and global semantic coherence, with corrections confined to structurally dependent claims. When automated evidence is insufficient, the system escalates to human arbitration as the supervisory authority with final override rights; dependency-closure re-verification then ensures correction cost remains proportional to error scope. Experiments on VidOR show substantially improved downstream reasoning (VQA: 0.71 to 0.79) and a 4.8x reduction in human arbitration cost.

## 核心贡献

1. **声明级语义记忆维护**：将长视频理解重新定义为共享语义记忆的迭代声明级维护。
2. **结构化版本化状态**：编码类型化声明、声明依赖图和溯源日志。
3. **角色专业化 Agent**：在显式权限合约下运行，分解为局部对象关系正确性、跨时间一致性和全局语义一致性验证。
4. **成本比例校正机制**：依赖闭包再验证确保校正成本与错误范围成比例。

## 为什么重要

长视频理解中的错误修正成本极高——现有流程迫使注释者从头重新审视原始视频。IMPACT-CYCLE 通过声明级语义记忆维护将监督成本与错误范围成比例，将 VQA 准确率从 0.71 提升到 0.79，同时将人工仲裁成本降低 4.8 倍。这对需要处理大量视频数据的移动端 Agent 场景（如视频摘要、视频搜索）有直接价值。

## 与移动端/端侧相关性

- 移动端视频应用（相册、视频摘要）需要处理用户的大量视频数据
- 4.8x 人工成本降低对需要用户反馈的端侧应用（如视频自动标注）非常重要
- 声明级记忆与移动端传感器数据（摄像头、麦克风）的结构化组织方式契合
- 分层验证（局部/跨时间/全局）对移动端有限计算资源下的高效推理有启发
