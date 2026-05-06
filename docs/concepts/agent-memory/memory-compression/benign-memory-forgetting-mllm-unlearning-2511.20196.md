---
title: "Towards Benign Memory Forgetting for Selective Multimodal Large Language Model Unlearning"
arXiv: 2511.20196
date: 2025-11-25
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Towards Benign Memory Forgetting for Selective Multimodal Large Language Model Unlearning

## 论文基本信息

- **作者**: Zhen Zeng, Leijiang Gu, Zhangling Duan, Feng Li, Zenglin Shi 等
- **arXiv**: https://arxiv.org/abs/2511.20196
- **领域**: cs.AI, cs.LG

## 摘要

多模态大语言模型（MLLM）功能强大，但可能无意中记忆隐私敏感信息。虽然现有遗忘方法可以删除此类知识，但往往损害模型的一般图像理解能力，导致"良性遗忘"无法实现。SMFA（Sculpted Memory Forgetting Adapter）将遗忘限制在目标记忆区域，同时保留整体能力。SMFA 先微调模型将敏感响应替换为拒绝回答，生成记忆遗忘适配器，再应用保留锚引导的掩码机制，防止干扰无关知识和理解能力。在 S-MLLMUn Bench 上，SMFA 实现了精确可控的遗忘，同时保持模型的基础图像理解能力。

## 核心贡献

1. **SMFA 框架**: 首个实现选择性 MLLM 遗忘的框架，确保"良性遗忘"
2. **Targeted Memory Forgetting**: 将遗忘限制在目标记忆区域，不损害通用能力
3. **Retaining Anchor Guidance**: 保留锚引导的掩码机制，保护无关知识
4. **S-MLLMUn Bench**: 首个联合评估敏感知识删除和通用视觉理解保持的基准
5. **Precision Unlearning**: 遗忘精度达到目标知识级别，而非模型整体级别

## 研究背景与问题

MLLM 可能记忆训练数据中的隐私信息（如人脸、财务记录）。标准遗忘方法会导致模型整体能力下降，无法实现"删除隐私知识但不损害能力"的良性遗忘目标。

## 核心方法

1. **Memory Region Identification**: 识别模型中存储目标隐私知识的参数区域
2. **Forgetting Adapter Fine-tuning**: 训练遗忘适配器，将敏感响应替换为拒绝
3. **Retaining Anchor Masking**: 应用保留锚掩码，保护与遗忘目标无关的参数
4. **Capability Preservation Check**: 验证遗忘后模型在通用视觉理解上的能力保持
5. **Selective vs Complete**: 区分选择性遗忘（只删特定记忆）和完全遗忘（删除所有相关知识）

## 为什么重要

SMFA 在隐私保护和模型能力之间取得了前所未有的平衡。对于需要在设备上存储用户隐私记忆的 Agent 系统，良性遗忘能力是用户隐私保护的核心技术保障。

## 与移动端/端侧相关性

1. **本地隐私保护**: 遗忘在本地执行，无需上传敏感数据
2. **用户可控遗忘**: 用户可选择性地要求模型遗忘特定记忆
3. **不损害基础能力**: 遗忘后模型基础能力保持，不影响其他功能
4. **合规性**: 满足 GDPR 等数据保护法规的"被遗忘权"要求
