---
title: "CMT: A Memory Compression Method for Continual Knowledge Learning of Large Language Models"
arXiv: 2412.07393
date: 2024-12-09
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# CMT: A Memory Compression Method for Continual Knowledge Learning of Large Language Models

## 论文基本信息

- **作者**: Dongfang Li, Zetian Sun, Xinshuo Hu
- **arXiv**: https://arxiv.org/abs/2412.07393
- **领域**: cs.CL, cs.AI

## 摘要

大语言模型需要适应数据、任务和用户偏好的持续变化，但模型规模巨大且训练成本高昂，频繁重训练不现实。CMT 提出压缩记忆训练（Compression Memory Training），将新知识以压缩记忆的形式整合到模型中，而不改变模型主参数。压缩记忆存储新知识的紧凑表示，推理时通过记忆增强生成。在持续知识学习任务上，CMT 在保持主模型能力的同时，高效吸收新知识。

## 核心贡献

1. **Compression Memory Training**: 新知识以压缩记忆存储，不改主模型参数
2. **Memory-augmented Generation**: 推理时通过记忆增强生成，整合压缩知识
3. **持续学习框架**: 支持新知识的持续整合，不遗忘旧知识
4. **参数高效**: 不需要全量微调，训练成本显著降低
5. **知识隔离**: 新旧知识在记忆层面分离，便于管理

## 研究背景与问题

LLM 部署后需要适应新知识，但全量微调成本高且有遗忘风险。增量学习方案（adapter、prompt tuning）虽参数高效，但知识整合质量不如全量微调。CMT 提出用压缩记忆作为知识整合的中间载体，在参数效率和知识质量间取得平衡。

## 核心方法

1. **Knowledge Compression**: 将新知识压缩为密集向量表示（压缩记忆）
2. **Memory Index**: 压缩记忆存储在可学习的记忆索引中
3. **Memory-augmented Inference**: 推理时检索相关压缩记忆，增强主模型生成
4. **Contrastive Memory Training**: 用对比学习确保压缩记忆与原始知识语义对齐
5. **Selective Memory Activation**: 只激活与当前查询相关的记忆子集

## 为什么重要

CMT 将"记忆压缩"和"持续学习"两个方向结合，提出了一种参数高效的持续学习方案。对需要在部署后不断吸收新知识的 Agent 系统有重要参考价值。

## 与移动端/端侧相关性

1. **参数高效**: 不改变主模型参数，适合移动端受限的微调资源
2. **记忆模块化**: 压缩记忆可独立更新，移动端可增量下载新记忆模块
3. **本地个性化**: 用户特定知识可存储为本地压缩记忆，保护隐私
4. **知识版本管理**: 不同压缩记忆对应不同知识版本，便于回滚和管理
