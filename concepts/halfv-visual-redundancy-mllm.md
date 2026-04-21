---
type: concept
tags: [视觉Token压缩, MLLM, 推理加速, 多模态, token pruning, 端侧推理, Qwen2.5-VL]
related: [[evocomp-visual-token-compression-mllm]], [[token-compression-vit-acceleration]], [[multimodal-edge-pruning]], [[imp-mobile-lmm]], [[topovlm-layer-pruning]], [[essen-compact-vlm-training]]
sources:
  - url: https://arxiv.org/abs/2604.16462
    title: "From Inheritance to Saturation: Disentangling the Evolution of Visual Redundancy for Architecture-Aware MLLM Inference Acceleration"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# HalfV: 视觉冗余生命周期与 MLLM 推理加速

> 发现 MLLM 视觉 token 存在通用三阶段冗余生命周期（模态对齐→全局聚合→视觉饱和），提出基于截断矩阵熵的架构感知加速框架 HalfV——在 Qwen25-VL 上保留 96.8% 性能的同时实现 4.1× FLOPs 加速。

## 核心问题

多模态大语言模型（MLLM）在高分辨率设置下，视觉 Transformer 编码的视觉 token 数量爆炸，自注意力的 O(N²) 复杂度导致 prefill 阶段成为延迟瓶颈。现有加速方法（token-level 剪枝、layer-level 稀疏化）存在严重的**骨干网络依赖**——在 Vicuna/Mistral 上过拟合的方法迁移到 Qwen2.5 架构时性能下降 5.7%-22.4%。

## 方法架构

### 三阶段视觉冗余生命周期

通过截断矩阵熵（Truncated Matrix Entropy）追踪不同层的冗余演化，发现所有骨干网络的视觉 token 都经历三个阶段：

| 阶段 | 层范围 | 冗余特征 | 适合的加速策略 |
|------|--------|---------|--------------|
| **模态对齐** | 早期层 | 冗余继承自 ViT，token 高度相似 | token-level 剪枝 |
| **全局聚合** | 中间层 | token 开始差异化，冗余动态变化 | 需要动态策略 |
| **视觉饱和** | 后期层 | 信息吸收完毕，冗余稳定高 | layer-level 稀疏化 |

### HalfV 框架

**两步加速框架**，根据冗余生命周期的不同阶段适配不同的加速策略：

1. **截断矩阵熵**：作为统一探针追踪跨层冗余
   - 计算每个 transformer 层的 token 表示矩阵的 Gram 矩阵
   - 保留 top-k 特征值（肘点之前）抑制噪声
   - 截断矩阵熵 = 归一化截断迹，衡量当前层的冗余程度

2. **架构感知加速**：
   - 早期层（模态对齐）：token-level 剪枝
   - 后期层（视觉饱和）：layer-level 稀疏化
   - 中间层：根据冗余度动态调整

### 与现有方法的对比

| 方法 | 策略 | 骨架依赖 | Qwen2.5 性能 |
|------|------|---------|-------------|
| HoloV | Token-level 剪枝 | 高（Vicuna 过拟合） | -5.7%~-22.4% |
| DART | Token-level 剪枝 | 高 | -5.7%~-22.4% |
| ShortV | Layer-level 稀疏 | 中 | 有退化 |
| **HalfV** | **两阶段混合** | **低** | **-3.2% (保留96.8%)** |

## 实验结果

在 Qwen25-VL 上的关键结果：

- **性能保留：** 96.8%（仅下降 3.2%）
- **计算加速：** 4.1× FLOPs
- **评估基准：** POPE、MME、MMBench、SQA 平均

**核心发现：** 不同骨干网络的视觉冗余演化遵循相同的三阶段模式，但冗余分布的具体层位置和程度不同。基于生命周期阶段适配策略（而非一刀切）是跨架构泛化的关键。

## 关键洞察

1. **统一探针优于手工规则：** 截断矩阵熵提供了无监督的冗余度量，不需要针对特定架构调参
2. **阶段混合策略是关键：** token-level 和 layer-level 方法各有最佳适用阶段，混合使用效果远超单一策略
3. **从 Vicuna 到 Qwen 的泛化：** 这是首个系统解决视觉 token 加速方法跨骨干迁移问题的工作
4. **端侧 MLLM 部署的意义：** 4.1× 加速 + 96.8% 性能保留 = 使高分辨率多模态推理在手机端变得可行

## 为什么重要

对手机端 AI 生态的意义：
- **端侧 MLLM 可行性：** 高分辨率视觉理解是端侧 AI 的核心需求（拍照识物、屏幕理解、AR），4.1× 加速直接降低计算门槛
- **Qwen2.5-VL 兼容：** Qwen 是端侧多模态模型的主力（Qwen 3.5 Small 等），适配 Qwen 架构的方法有直接应用价值
- **框架可复用性：** 截断矩阵熵作为统一探针可应用于任何 MLLM，不需要重新设计
- **与现有优化栈互补：** HalfV 减少 FLOPs，可与 KV-cache 量化、模型量化等技术叠加

## 关联

- [[evocomp-visual-token-compression-mllm]] — OPPO 的视觉 Token 压缩框架
- [[token-compression-vit-acceleration]] — ViT Token 压缩策略重审视
- [[multimodal-edge-pruning]] — 多模态边缘推理的零样本剪枝
- [[imp-mobile-lmm]] — 面向移动设备的高性能大型多模态模型
- [[topovlm-layer-pruning]] — 拓扑感知层剪枝
- [[essen-compact-vlm-training]] — 低资源训练紧凑视觉语言模型
- [[qwen35-small]] — Qwen 3.5 Small 端侧多模态模型系列
