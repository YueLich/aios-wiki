---
title: "From Verbatim to Gist: Distilling Pyramidal Multimodal Memory via Semantic Information Bottleneck"
arXiv: 2603.01455
date: 2026-03-02
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

# MM-Mem: From Verbatim to Gist — Distilling Pyramidal Multimodal Memory via Semantic Information Bottleneck

## 论文基本信息

- **作者**: Niu Lian, Yuting Wang, Hanshu Yao, Jinpeng Wang, Bin Chen, Yaowei Wang, Min Zhang, Shu-Tao Xia
- **arXiv**: https://arxiv.org/abs/2603.01455
- **代码**: https://github.com/EliSpectre/MM-Mem

## 摘要

虽然多模态大语言模型展示了令人印象深刻的短期推理能力，但它们在长程视频理解上仍有困难，原因在于有限的上下文窗口和静态记忆机制无法匹配人类认知效率。现有范式通常走向两个极端：视觉中心方法通过密集视觉累积产生高延迟和冗余，文本中心方法通过激进字幕化导致细节丢失和幻觉。MM-Mem 提出受模糊痕迹理论启发的金字塔 multimodal 记忆架构，将记忆分层为感官缓冲区、情景流和符号模式，实现从细粒度感知痕迹（字面）到高层语义模式（图式）的渐进蒸馏。此外，论文推导出语义信息瓶颈目标，引入 SIB-GRPO 优化记忆压缩与任务相关信息保留之间的权衡。推理时，设计熵驱动自上而下记忆检索策略。在 4 个基准上的广泛实验确认 MM-Mem 在离线和流式任务上达到最优性能，展示了鲁棒泛化并验证了认知启发记忆组织的有效性。

## 核心贡献

1. **Pyramidal Multimodal Memory**: 感官缓冲区 → 情景流 → 符号模式三层金字塔架构
2. **Fuzzy-Trace Theory**: 模糊痕迹理论启发的记忆分层设计
3. **Semantic Information Bottleneck**: 语义信息瓶颈目标优化压缩-保留权衡
4. **SIB-GRPO Training**: 优化记忆压缩与任务相关信息保留
5. **Entropy-driven Retrieval**: 熵驱动自上而下记忆检索策略

## 研究背景与问题

现有视频 Agent 记忆要么保留太多细节（高延迟）要么丢失太多细节（幻觉）。MM-Mem 从认知科学中寻找答案——人类自然地将字面细节蒸馏为高层图式。

## 核心方法

1. **Hierarchical Memory Distillation**: 从感官缓冲区到情景流到符号模式的分层蒸馏
2. **Semantic Information Bottleneck**: 语义压缩保留任务相关信息
3. **SIB-GRPO Optimization**: 强化学习优化压缩-保留权衡
4. **Top-down Retrieval**: 自上而下的记忆检索，高熵触发详细回忆，低熵触发抽象回忆
5. **Offline + Streaming**: 支持离线批处理和流式推理

## 为什么重要

MM-Mem 将认知科学理论系统性地引入 multimodal 记忆系统。分层蒸馏和语义信息瓶颈为记忆压缩提供了理论指导，对需要处理长视频的 Agent 系统有重要价值。

## 与移动端/端侧相关性

1. **移动端长视频处理**: 突破移动端上下文限制的长视频记忆方案
2. **信息瓶颈理论**: 端侧可用信息瓶颈指导记忆压缩
3. **认知启发设计**: 借鉴人类记忆机制的端侧记忆架构
4. **流式处理**: 支持移动端实时视频流的增量记忆管理
