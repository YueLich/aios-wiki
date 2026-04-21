---
type: concept
tags: [Agent, 强化学习, 微调, GRM, rubric, coding-agent, RLHF, DPO]
related: [[groupdpo-memory-efficient-preference-optimization]], [[agent-persistent-identity]], [[memp-agent-procedural-memory]], [[obfuscation-free-rlhf]]
sources:
  - url: https://arxiv.org/abs/2604.16335
    title: "Beyond Verifiable Rewards: Rubric-Based GRM for Reinforced Fine-Tuning SWE Agents"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# Beyond Verifiable Rewards: 基于评分标准的 Agent 强化微调

> 传统强化微调依赖"可验证奖励"（如代码能否编译通过），但真实 Agent 任务往往无法简单二分。本文提出 Rubric-Based GRM（奖励模型），用细粒度评分标准替代二值奖励，使 SWE Agent 能在更复杂的任务上获得有效强化信号。

## 核心问题

LLM Agent（尤其是编程 Agent）的强化微调面临一个根本矛盾：

1. **可验证奖励太粗糙**：代码要么通过测试（+1），要么失败（-1），无法区分"部分正确"和"完全错误"
2. **真实任务复杂度远超二值判断**：SWE 任务涉及代码风格、架构选择、边界处理等多个维度
3. **稀疏奖励导致学习效率极低**：Agent 几乎无法从单一的 PASS/FAIL 信号中学习中间策略

## 方法/架构

**Rubric-Based GRM** 的核心思路：

1. **多维评分标准（Rubric）**：将 SWE 任务分解为多个评估维度（正确性、代码质量、测试覆盖、边界处理等），每个维度给出 0-5 分
2. **GRM（Generative Reward Model）**：训练一个专门的奖励模型，根据 Agent 提交的代码和评分标准，自动生成多维度打分
3. **强化微调（Reinforced Fine-Tuning, RFT）**：用 GRM 生成的细粒度奖励信号代替二值信号，通过 policy gradient 优化 Agent

**技术细节**：
- 基础模型：seed-OSS-36B（经 SFT 后的基础能力）
- GRM 基于 seed-1.6 系列模型
- 评分标准涵盖：功能性、可读性、效率、鲁棒性

## 实验结果

| 方法 | SWE-Bench Verified | 通过率 | 平均 rubric 分 |
|------|-------------------|--------|---------------|
| SFT 基线 | 28.3% | 28.3% | 3.12 |
| 标准 RFT（二值奖励） | 31.7% | 31.7% | 3.35 |
| **Rubric-Based GRM RFT** | **36.2%** | **36.2%** | **3.78** |

关键发现：
- Rubric-Based 方法在通过率上提升 4.5 个百分点
- 更显著的是平均 rubric 分提升（3.12 → 3.78），表明 Agent 在"部分正确"的任务上也有大幅改善
- 在困难任务（需要多文件修改）上优势尤为明显

## 关键洞察

1. **稀疏奖励是 Agent 微调的瓶颈**：二值通过/失败信号无法指导 Agent 学习中间策略，rubric 提供了稠密的梯度信号
2. **GRM 质量决定上限**：奖励模型的评分准确性直接决定 Agent 能学到什么
3. **对移动端 Agent 的启示**：虽然本文聚焦编程 Agent，但 rubric-based 方法可以推广到任何 Agent 任务（手机操作、设置调整等），为端侧 Agent 微调提供了新范式

## 为什么重要

- **Agent 微调范式转变**：从"能否完成"到"完成质量如何"的多维度评估
- **适用于移动 AIOS Agent**：手机端 Agent（如 [[secagent-mobile-gui-agent]]、[[clawmobile-agentic]]）的操作任务同样需要多维度评估（操作正确性、效率、用户体验）
- **与 DPO/GRPO 互补**：rubric-based 奖励可以与 [[groupdpo-memory-efficient-preference-optimization]] 等方法结合

## 关联
- [[groupdpo-memory-efficient-preference-optimization]] — 另一种偏好优化方法
- [[agent-persistent-identity]] — Agent 能力的长期演化
- [[memp-agent-procedural-memory]] — Agent 从经验中学习
- [[obfuscation-free-rlhf]] — RLHF 方法论
