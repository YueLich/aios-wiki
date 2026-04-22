---
type: concept
tags: [agent-memory, reinforcement-learning, GRPO, memory-augmented, training-framework, inference-framework, modular, LLM, agent, memory-rl, on-device, 端侧推理, Agent记忆]
related: [[agent-persistent-identity]], [[mga-memory-gui-agent]], [[memory-worth-governance]], [[summer-memory-benchmark]]
sources:
  - url: https://arxiv.org/abs/2603.29493
    title: "MemFactory: Unified Inference & Training Framework for Agent Memory"
    date: 2026-03-31
    reliability: high
created: 2026-04-22
updated: 2026-04-22
---

# MemFactory: Agent 记忆的统一推理与训练框架

> 首个将 Memory-RL 的训练、评估和推理统一的模块化框架，类似 LLaMA-Factory 但面向 Agent 记忆系统。arXiv 2603.29493。

## 核心问题

当前记忆增强 Agent 研究高度碎片化——Memory-R1、MemAgent、RMM 等各自实现，代码互不兼容，复现困难。研究者想在不同记忆策略之间切换（比如把 Memory-R1 的检索模块换成 LRM-based 重排器）需要大量重复工程工作。缺少类似 LLaMA-Factory 在 LLM 微调领域那样的统一基础设施。

## 方法架构

### 三层架构设计

MemFactory 借鉴 LLaMA-Factory 的 "Lego-like" 模块化理念，将记忆生命周期拆解为三个原子操作：

1. **Extractor（提取层）**：从对话历史、环境观察中提取有价值的记忆单元
2. **Updater（更新层）**：管理记忆库的写入、合并、冲突消解
3. **Retriever（检索层）**：根据当前上下文从记忆库中检索相关记忆

通过 **Agent Layer** 编排这三个原子模块，研究者可以自由组合。框架原生支持 GRPO（Group Relative Policy Optimization）进行记忆管理策略的 RL 微调，基于多维度环境奖励驱动。

### 支持的 SOTA 范式

- **Memory-R1**：基于 RL 的记忆推理优化
- **MemAgent**：记忆驱动的 Agent 架构
- **RMM**：前瞻-回顾记忆管理

## 实验结果

在开源 MemAgent 架构上使用内置 GRPO pipeline 进行验证：

- 评估集上平均性能优于对应基座模型
- 相对增益最高达 **14.8%**
- 跨主任务和 out-of-distribution 评估集均显示一致性提升

## 关键洞察

1. **Memory-RL 类比 PEFT**：正如 LoRA/QLoRA 让微调变得民主化，Memory-RL 的统一框架将让记忆优化研究民主化。当前每个团队都在从头实现记忆管道，MemFactory 消除了这个障碍。

2. **原子模块化 vs 整体架构**：将记忆拆成 Extract/Update/Retrieve 三个正交操作是关键设计决策。这意味着你可以独立替换任何一个模块而不需要重写整个管道。对端侧部署特别有价值——移动端可以使用轻量级 Extractor 但高质量 Retriever。

3. **GRPO 驱动的记忆策略**：用 RL 而非启发式规则来决定 "什么时候提取/更新/检索记忆" 是核心创新。Agent 在运行中学习最优的记忆管理策略，而不是依赖固定规则。

4. **端侧相关性**：对移动端 AIOS 来说，记忆管理是 Agent 持久化的核心瓶颈。端侧 Agent 需要在有限内存和计算资源下高效管理记忆。MemFactory 提供的模块化设计使得可以针对端侧约束定制各模块的实现（如量化记忆存储、轻量级检索）。

## 为什么重要

对手机端 AI 生态的意义：

- **降低研究门槛**：像 LLaMA-Factory 降低了 LLM 微调门槛一样，MemFactory 降低了 Memory-RL 研究门槛
- **端侧记忆优化**：模块化设计允许针对移动设备的内存/计算约束定制记忆管道
- **Agent 持久化**：是构建真正有长期记忆的移动端 Agent 的关键基础设施
- **GRPO 集成**：RL 驱动的记忆管理策略在端侧比启发式规则更高效，能根据实际使用模式自适应

## 关联

- [[agent-persistent-identity]] — 记忆是 Agent 持久化身份的底层支撑
- [[mga-memory-gui-agent]] — MGA 同样关注记忆驱动的 GUI Agent，MemFactory 提供了其训练框架
- [[memory-worth-governance]] — 记忆价值治理需要类似 MemFactory 的模块化评估管道
- [[summer-memory-benchmark]] — SUMMER 评估 Agent 短期记忆，MemFactory 是其可能的优化框架
