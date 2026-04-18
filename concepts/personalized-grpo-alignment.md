---
type: concept
tags: [对齐, GRPO, 个性化, 偏好学习, 端侧微调, RLHF]
related: [[gemma4-aicore]], [[agent-persistent-identity]], [[secagent-mobile-gui]]
sources:
  - url: https://machinelearning.apple.com/research/personalized-group
    title: "Personalized Group Relative Policy Optimization for Heterogenous Preference Alignment"
    date: 2026-04
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# P-GRPO: 个性化偏好对齐的优化框架

> Apple 研究团队提出 Personalized GRPO，解决了标准 GRPO 在个性化场景中的系统性偏差问题——通过按偏好组独立归一化优势估计，保留少数偏好信号，实现异构偏好对齐。

## 核心问题
标准 RLHF/GRPO 方法优化一个全局目标，假设所有用户偏好一致。但实际场景中，不同用户有截然不同的偏好（如正式 vs 随意、简洁 vs 详细）。GRPO 的 group-based 归一化隐含假设所有样本可交换，导致：
- **主导偏好压制少数信号**：batch 内多数用户的偏好主导优势估计
- **少数用户偏好被忽略**：异构偏好被平均化，失去对比信号

## 方法架构

P-GRPO 的核心创新是**解耦优势估计与即时 batch 统计量**：

```
标准 GRPO: Â = (r - μ_batch) / σ_batch
P-GRPO:   Â = (r - μ_group) / σ_group
```

其中 μ_group 和 σ_group 是**偏好组特定的历史奖励统计量**，而非当前 batch 的统计量。

### 关键设计

1. **偏好组识别**：根据用户反馈历史将样本分组
2. **组级归一化**：每个偏好组独立维护奖励历史，优势估计相对于组内历史而非当前 batch
3. **对比信号保留**：不同组之间的差异不会被 batch 归一化平均掉

## 实验结果

- 在多样化任务上一致收敛更快
- 奖励更高（相比标准 GRPO）
- 成功恢复并学习异构偏好信号
- 不牺牲通用能力

## 关键洞察

1. **端侧个性化的核心问题**：当端侧 Agent（如 Android 助手）需要适应个人用户的使用习惯时，偏好对齐至关重要。P-GRPO 提供了在端侧保持通用能力的同时学习个人偏好的方法论。

2. **与端侧微调的结合**：P-GRPO 的组级归一化机制计算开销极小（只维护组级统计量），适合在端侧设备上进行偏好微调。结合 Gemma 4 的 on-device fine-tuning 能力，可实现"千人千面"的端侧 AI。

3. **Agent 持久化身份的对齐基础**：在 [[agent-persistent-identity]] 框架中，Agent 的个性化身份需要偏好对齐作为底层支撑。P-GRPO 为每个用户维护独立的偏好模型，这正是 Agent 个性化所需的。

## 为什么重要

- **端侧 AI 个性化**：为 on-device Agent 提供偏好对齐方法论，实现真正的个性化
- **Apple 端侧对齐研究**：反映 Apple 在 CoreML/ANE 上实现用户级个性化的技术方向
- **对 Android Agent 的启示**：AICore 集成的 Gemma 4 可以使用类似方法实现端侧个性化

## 关联
- [[gemma4-aicore]] — Gemma 4 支持端侧微调，P-GRPO 可作为对齐方法
- [[agent-persistent-identity]] — Agent 持久化身份需要个性化偏好对齐
- [[secagent-mobile-gui]] — GUI Agent 的用户适配需要偏好学习
- [[lacy-small-model-token-selection]] — Apple 的另一项小模型优化研究
