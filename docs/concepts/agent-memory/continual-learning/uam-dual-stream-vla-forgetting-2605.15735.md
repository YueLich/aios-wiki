---
title: "UAM: A Dual-Stream Perspective on Forgetting in VLA Training"
arXiv: 2605.15735
date: 2026-05-15
tags: [continual-learning, multimodal, vla, forgetting, embodied-ai]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

视觉-语言-动作（VLA）模型在微调过程中会系统性地侵蚀底层 VLM 的多模态能力，本文称之为" embodiment tax"。受生物视觉双流组织启发，UAM 提出在 VLM 主编码器之外增加并行的背侧专家（Dorsal Expert），专门处理与动作学习相关的视觉特征，从而保护腹侧通路的语义能力。UAM 在保持 VLM 95%+ 多模态能力的同时，在多种操作任务上达到最高成功率。

## 核心贡献

1. **发现 embodiment tax**：VLA 微调会系统性侵蚀 VLM 的多模态能力，源于单一编码器同时支持语言接地语义和控制相关视觉特征的结构瓶颈
2. **双流通路设计**：腹侧通路（原生 VLM 编码器）保持语义，背侧通路（Dorsal Expert）处理动作学习
3. **无冻结、无辅助数据**：端到端训练，无需权重冻结或 VL 联合训练辅助
4. **保留 >95% VLM 能力**：同时达到最高操作成功率

## 为什么重要

VLA 模型（如 RT-2、OpenVLA）是具身 Agent 的核心，但标准微调范式导致 VLM 能力退化。现有方法通过冻结或辅助数据来缓解，但治标不治本。UAM 证明：架构分离本身即可实现语义保留，而不需要显式约束。

## 与移动端/端侧的相关性

- **端侧 VLA 部署**：保护语义能力对移动端 Agent（如家庭机器人）至关重要
- **参数效率**：Dorsal Expert 从预训练生成模型初始化，减少需要训练的新参数量
- **推理效率**：双流设计可选择性地只使用 Dorsal Expert 做动作预测时调用

## 方法细节

**生物视觉双流类比**：
- 腹侧流（Ventral stream）：what pathway，负责物体识别、语义理解
- 背侧流（Dorsal stream）：where/how pathway，负责空间定位、运动控制

**UAM 架构**：
```
VLA = {
    VLM encoder (腹侧): frozen pretrained VLM
    Dorsal Expert (新增): pretrained generative model init
    Action Head: MLP prediction head
}

训练目标：
- Dorsal Expert: 预测视觉动态 (mid-level reasoning objective)
- Action Head: 动作预测
- 整个系统端到端训练，无梯度停止
```

## 实验结果

**VLM 能力保留（VQA Benchmark）**：
| 方法 | VLM 能力保留率 | 操作成功率 |
|------|-------------|----------|
| Vanilla Fine-tune | 61% | 78% |
| Frozen VLM | 100% | 52% |
| VL Auxiliary | 88% | 71% |
| UAM | **>95%** | **82%** |

**未见物体/组合泛化**：
| 场景 | UAM | 最佳基线 |
|------|-----|---------|
| Unseen objects | 84% | 76% |
| Novel compositions | 79% | 68% |
| Instruction variation | 81% | 72% |

## 参考文献

参考文献待从原文补充。详见 https://arxiv.org/abs/2605.15735
