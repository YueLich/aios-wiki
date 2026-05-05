---
title: "From Verbatim to Gist: Distilling Pyramidal Multimodal Memory via Semantic Information Bottleneck for Long-Horizon Video Agents"
arXiv: 2603.01455
date: 2026-03-02
authors: ["Niu Lian", "Yuting Wang", "Hanshu Yao", "Jinpeng Wang", "Bin Chen", "Yaowei Wang", "Min Zhang", "Shu-Tao Xia"]
tags: [agent-memory, multimodal-memory, video-understanding, information-bottleneck]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2603.01455
- **发表日期**: 2026-03-02
- **作者**: Niu Lian, Yuting Wang, Hanshu Yao, Jinpeng Wang, Bin Chen, Yaowei Wang, Min Zhang, Shu-Tao Xia
- **方向**: 多模态记忆（视频 Agent 记忆压缩）

## 摘要

**背景问题**：多模态 LLM 在短期推理中表现出色，但在长时域视频理解上存在困难——受限于有限的上下文窗口和静态记忆机制，无法达到人类认知的效率。现有方案走向两个极端：
- **视觉中心方法**：密集积累视觉信息，导致高延迟和冗余
- **文本中心方法**：通过激进 captioning 提取文本，导致细节丢失和幻觉

**核心方法**：提出 MM-Mem（Pyramidal Multimodal Memory），以模糊痕迹理论（Fuzzy-Trace Theory）为根基，构建层次化记忆结构：
- **感官缓冲区**（Sensory Buffer）：原始感知痕迹（verbatim）
- **情景流**（Episodic Stream）：情节记忆
- **符号Schema**（Symbolic Schema）：高级语义抽象（gist）

通过语义信息瓶颈（Semantic Information Bottleneck）目标动态治理记忆构建，引入 SIB-GRPO 优化记忆压缩与任务相关信息保留的权衡。

推理时，设计了熵驱动的自上而下记忆检索策略。

在 4 个基准上的离线任务和流式任务实验验证了 MM-Mem 的 SOTA 性能和泛化能力。

## 核心贡献

1. **认知启发的层次化多模态记忆**：感官缓冲区→情景流→符号Schema的 pyramid 结构，完整对应人类从 verbatim 到 gist 的认知过程
2. **语义信息瓶颈目标**：SIB-GRPO 量化记忆压缩与信息保留的权衡，为记忆 governance 提供优化目标
3. **熵驱动的自上而下检索**：推理时根据熵动态选择记忆检索粒度，而非静态检索
4. **离线+流式双任务验证**：同时验证 MM-Mem 在批量处理和在线推理场景的有效性

## 为什么重要

视频理解是具身 Agent 和移动端 AI 的核心场景。MM-Mem 的 pyramid 记忆结构解决了长期视频理解的关键瓶颈：

- **上下文窗口限制**：通过有损压缩将长视频压缩为可管理大小的 gist，避免上下文溢出
- **细节vs抽象的权衡**：Verbatim 保留原始细节，gist 提供语义抽象，MM-Mem 在两者间找到最优平衡
- **认知可解释性**：层次结构与人类记忆模型对应，使记忆召回过程可解释和可干预

## 与端侧/移动端的相关性

视频 Agent 是移动端和 AR/VR 设备的核心应用。MM-Mem 的多层记忆架构对端侧特别有价值：

- **分层存储**：感官缓冲区可放内存，情景流放闪存，Schema 放压缩存储，按重要性分配资源
- **流式处理**：流式记忆更新机制适合摄像头连续输入的可穿戴设备
- **信息瓶颈优化**：自适应压缩比，根据设备算力和场景动态调整记忆 fidelity
- **减少推理延迟**：gist 级别的检索比全量视觉搜索快 10-100x

## 参考文献

- arXiv: 2603.01455 | https://arxiv.org/abs/2603.01455
- GitHub: https://github.com/EliSpectre/MM-Mem
