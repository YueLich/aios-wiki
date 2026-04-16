---
type: concept
tags: [agent memory, memory governance, lifelong learning, 端侧推理, memory quality]
related: [[memory-as-metabolism-companion-ks]], [[memp-agent-procedural-memory]], [[agent-persistent-identity]], [[memory-driven-gui-agent]], [[memory-worth-governance]], [[lcsb-finetuning-ondevice]]
sources:
  - url: https://arxiv.org/abs/2604.12007
    title: "When to Forget: A Memory Governance Primitive"
    date: 2026-04-16
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# Memory Worth: 记忆治理原语

> 提出 Memory Worth (MW) — 一个轻量级的双计数器记忆质量评估信号，用于 Agent 记忆的过时检测、检索抑制和弃用决策。arXiv:2604.12007

## 核心问题

Agent 记忆系统持续积累经验，但缺乏一个原则性的操作度量来管理记忆质量——决定哪些记忆值得信任、哪些应该抑制或弃用。现有系统依赖写入时的重要性评分（静态）或 LLM 判断（昂贵且不稳定），而非基于结果反馈的动态评估。当 Agent 的任务分布发生变化时，过时的记忆继续被当作可信知识使用，导致推理质量下降。

## 方法/架构

### Memory Worth 定义

MW 是一个每个记忆单元的在线信号，定义为加权检索计数的比率：

**MW_T(m) = hits⁺_T(m) / (hits⁺_T(m) + hits⁻_T(m))**

其中：
- **hits⁺_T(m)**：记忆 m 被检索且任务成功的加权累计次数
- **hits⁻_T(m)**：记忆 m 被检索且任务失败的加权累计次数
- **检索权重 w_t(m)**：反映记忆对行动的影响程度（均匀/分数比例/Oracle 三种策略）

当无检索记录时，MW 设为 0.5（无信息先验）。整个估计器**每个记忆只需两个标量计数器**，可以无缝添加到已有的检索和结果日志架构中。

### 双计数器的必要性

单一比率会隐藏关键信息。例如两个记忆的 MW 都是 0.80：
- m_A: hits⁺=80, hits⁻=20 → 高证据，可靠
- m_B: hits⁺=8, hits⁻=2 → 低证据，不确定

双计数器保留了证据量信息，支持证据感知的分类决策（θ_H=0.60, θ_L=0.40, V_min=10 检索阈值）。

### 检索权重策略

- **均匀权重**：w_t(m) = 1/k，无需额外信息
- **分数比例**：w_t(m) ∝ score(m, q_t)，基于检索评分函数
- **Oracle**：w_t(m) ∝ U*(m)，真实效用（仅实验可用）

三种策略在长期稳态下收敛到相同值，区别主要在收敛速度和非平稳环境中的表现。

## 实验结果

### 实验 1：受控环境校准（10,000 episodes, 20 seeds）

| 方法 | ρ @2k | ρ @5k | ρ @10k |
|------|-------|-------|--------|
| 无反馈基线 | 0.00±.00 | 0.00±.00 | 0.00±.00 |
| 均匀权重 | 0.66±.06 | 0.81±.03 | **0.89±.02** |
| 分数比例 | 0.66±.06 | 0.81±.04 | **0.89±.02** |
| Oracle | 0.67±.06 | 0.82±.04 | **0.90±.02** |

MW 在 10,000 episodes 后 Spearman 等级相关达到 ρ=0.89±0.02，而无反馈基线始终为 0.00——差距高达 0.89。

### 实验 4：共检索混淆

当两个记忆（U*=0.90 的锚点和 U*=0.05 的搭便车者）总是一起被检索时，MW 无法区分它们（都收敛到 ≈0.49）。只有当 ≥30% 的检索场景打破共检索配对时，有意义的分离才开始出现。

**关键启示**：检索多样性是 MW 区分混淆记忆与真正高质量记忆的必要条件。

### 实验 5：真实文本检索（all-MiniLM-L6-v2, 3,000 episodes）

使用真实文本记忆和神经嵌入检索（而非合成效用数字）：
- 过时记忆在 episode 300 时 MW 跨越 θ_L=0.40 阈值
- 最终稳定在 MW=0.17
- 专家记忆稳定在 MW=0.77

确认 MW 信号在现代语义检索下依然有效。

## 关键洞察

1. **关联 ≠ 因果**：MW 测量的是记忆与结果的共现关联概率 p⁺(m) = Pr[y_t=+1 | m∈M_t]，而非因果贡献。但作为操作信号仍然有用——与真实效用的 Spearman ρ 达到 0.89。

2. **最小可操作原语**：MW 不是完整的记忆治理系统，而是这类系统所需的最小操作原语。可以从它构建过时检测、检索抑制、不确定性感知排序和弃用决策。

3. **共检索是系统性瓶颈**：在移动 Agent 场景中，如果 GUI Agent 始终检索同一组视觉-动作记忆，MW 无法区分真正有效的记忆和搭便车者。需要设计检索多样性机制。

4. **对端侧 Agent 的意义**：MW 仅需两个标量计数器/记忆，内存开销极小，适合资源受限的移动设备。可以作为端侧 Agent 记忆生命周期管理的基础组件。

## 为什么重要

对于手机端 AIOS 的 Agent 系统，记忆质量治理是尚未解决的关键问题。随着 Agent 在设备上积累越来越多的交互经验，需要机制来：
- 自动淘汰过时知识（如应用界面更新后旧的 UI 操作记忆）
- 抑制低质量记忆的检索
- 在有限的设备内存中保留最有价值的经验

MW 提供了一个理论上收敛、实操轻量的解决方案，可以直接集成到 [[memory-driven-gui-agent]] 和 [[memp-agent-procedural-memory]] 等现有框架中。

## 关联

- [[memory-as-metabolism-companion-ks]] — 伴生知识系统的代谢设计，MW 可作为其记忆淘汰机制
- [[memp-agent-procedural-memory]] — Agent 程序性记忆，MW 可评估程序性记忆的长期有效性
- [[agent-persistent-identity]] — Agent 持久化身份，MW 可用于身份相关记忆的治理
- [[memory-driven-gui-agent]] — 记忆驱动的 GUI Agent，MW 可优化其记忆检索策略
- [[lcsb-finetuning-ondevice]] — 端侧微调，MW 的轻量特性适合端侧部署
- [[sustainability-ondevice-intelligence]] — 端侧智能的可持续性，MW 通过记忆治理减少无效计算
