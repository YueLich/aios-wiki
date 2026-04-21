---
type: concept
tags: [mllm, token-compression, visual-optimization, oppo, inference-acceleration, mobile-ai, 视觉token压缩]
related: [[gemma4-ondevice]], [[on-device-inference-memory-pressure]], [[kv-cache-quantization-ondevice]], [[edgeflow-cold-start]]
sources:
  - url: https://arxiv.org/abs/2604.17087
    title: "EvoComp: Learning Visual Token Compression for Multimodal Large Language Models via Semantic-Guided Evolutionary Labeling"
    date: 2026-04-18
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# EvoComp: OPPO 视觉 Token 压缩框架

> OPPO CTG 团队提出 EvoComp，通过语义引导的进化标注策略训练视觉 token 压缩器，在保持 MLLM 任务精度的同时大幅减少视觉 token 数量，对端侧多模态推理有直接意义。arXiv: 2604.17087

## 核心问题

多模态大语言模型 (MLLM) 在视觉语言理解任务上表现优异，但大量视觉 token 严重拖累推理效率——特别是高分辨率或多图场景下。在手机端运行 MLLM 时，视觉 token 的数量直接决定了：
- KV-Cache 内存占用（与 token 数量线性相关）
- 推理延迟（注意力计算复杂度 O(n²)）
- 功耗（计算量越大越耗电）

## 方法/架构

### EvoComp 框架
1. **轻量级编码器压缩器**: 基于 encoder-only transformer 的 token 选择器，通过联合考虑视觉和文本上下文，选出信息量最大且最不冗余的视觉 token
2. **进化标注策略 (Evolutionary Labeling)**: 不需要人工标注，而是通过搜索最小化 MLLM 输出损失的 token 子集，同时通过词汇表分组强制语义多样性
3. **定制损失函数**: 
   - **GHM 损失**: 缓解类别和难度不平衡
   - **余弦相似度正则化**: 鼓励保留 token 和丢弃 token 之间的语义分离

### 核心思想
- 压缩器在视觉 token 之后、LLM 之前插入
- 选择哪些 token 保留，哪些丢弃
- 通过进化搜索找到最优的 token 选择策略
- 将搜索结果作为压缩器训练的监督信号

## 实验结果/关键数据

- 在多个视觉语言基准上评估（VQA、图像描述、多模态推理等）
- 大幅减少视觉 token 数量的同时保持任务精度
- OPPO 作为手机厂商的直接参与，表明该技术有端侧部署的工程考量

## 关键洞察

1. **OPPO 直接下场**: 作为中国主要手机厂商之一，OPPO 直接投入 MLLM 视觉 token 压缩研究，表明端侧多模态推理已经是手机厂商的核心技术布局

2. **进化搜索 > 直接训练**: 用进化算法搜索最优 token 选择策略，比端到端直接训练压缩器效果更好——因为直接训练的梯度信号在"选择"操作上是不可导的

3. **语义多样性约束**: 不只是选择"信息量最大"的 token，还要保证所选 token 的语义多样性——避免选择冗余的相似 token

4. **对端侧部署的价值**: 视觉 token 压缩直接减少 KV-Cache 内存和注意力计算量，是端侧 MLLM 推理的关键优化手段

## 为什么重要

对手机端 AIOS 的核心意义：
- **端侧多模态推理的必需品**: 手机上的摄像头、屏幕截图等视觉输入需要 MLLM 处理，但有限的内存和计算能力要求必须压缩视觉 token
- **手机厂商的技术竞争**: OPPO 发布此研究，表明小米、vivo 等其他厂商也在进行类似工作——视觉 token 压缩将成为手机 AI 的标配技术
- **与量化协同**: token 压缩 + 量化 + 推测解码可以叠加效果，三者结合可能是端侧 MLLM 的最优部署方案
- **实时应用支持**: 压缩后延迟降低，使得实时摄像头场景理解等应用成为可能

## 关联
- [[gemma4-ondevice]] — 端侧多模态模型，视觉 token 压缩的直接应用场景
- [[on-device-inference-memory-pressure]] — 视觉 token 压缩减轻内存压力
- [[kv-cache-quantization-ondevice]] — 与 KV-Cache 量化协同优化
- [[edgeflow-cold-start]] — 端云协同中的视觉处理优化
- [[ggml-llamacpp-hf]] — llama.cpp 对多模态模型的支持