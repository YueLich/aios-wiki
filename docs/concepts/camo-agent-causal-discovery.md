---
type: concept
tags: [multi-agent, causal-discovery, agent-simulation, emergence, LLM-agent, 理论框架]
related: [[agent-persistent-identity]], [[emommas-emotion-aware-multi-agent]], [[memento-skills-agent-design]], [[memory-as-metabolism-companion-ks]], [[gaat-agent-governance]]
sources:
  - url: https://arxiv.org/abs/2604.14691
    title: "CAMO: An Agentic Framework for Automated Causal Discovery from Micro Behaviors to Macro Emergence in LLM Agent Simulations"
    date: 2026-04-18
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# CAMO: 多 Agent 因果发现框架

> 多智能体因果发现框架，自动从微观 agent 行为中发现宏观涌现的因果机制。论文首次提出用 LLM agent 团队来做因果发现，而非用传统统计方法。

## 核心问题

LLM 驱动的多 agent 模拟被广泛用于研究社会涌现现象（协调、规范形成、极化），但现有方法只能**观察**涌现行为，无法解释**为什么**会涌现。从微观 agent 交互到宏观结果的因果机制仍然是个黑箱。这导致对 prompt、agent 策略或交互设置的干预只能靠启发式猜测，难以泛化。

核心问题：给定一个 LLM agent 模拟，如何自动恢复微观行为和中观交互到宏观涌现结果 Y 的因果机制？

## 方法/架构

### 五 Agent 协作框架

CAMO 由 5 个 LLM agent 组成协作团队，分为两个循环：

**快速精化循环（Fast Refinement Loop）**：
- **A1: Worldview Parser** — 将非结构化领域知识转换为结构化的因果假设，自动提取候选变量并标记微观/中观/宏观层级
- **A2: Worldview Integrator** — 对齐多视角世界观为统一可计算表示，为计算因子分配规范构建规则
- **A3: Causal Cartographer** — 核心因果分析 agent，通过 add-prune 精化过程测试每个计算因子的信息增益 ΔÎ(Z)，构建局部因果模型
- **A4: Simulation Scriptwright** — 将优先化的模糊边转换为可执行干预脚本
- **A5: Counterfactual Adjudicator** — 执行配对干预（do(X=x) vs do(X=x')）验证因果假设

**慢速修订循环（Slow Revision Loop）**：当干预证据与假设矛盾时触发，更新或移除世界观假设。

### 关键创新

1. **最小充分因果接口**：不试图恢复完整因果 DAG，而是找到目标 Y 的 Markov 边界 MB^ℋ(Y) + 最小解释子图 E_Y
2. **诱导因子空间 ℋ**：引入超出日志可观测量的可计算非线性变换变量（比率、滚动统计、图度量）
3. **反事实验证**：通过模拟器内部的反事实探测来定向模糊边并修订假设

## 实验结果/关键数据

### 因果结构恢复（O2O 外卖模拟）

| 方法 | MB-Prec | MB-Rec | MB-F1 | Anc-F1 |
|------|---------|--------|-------|--------|
| Single-round (Text-only) | 0.00 | 0.00 | 0.00 | 0.27 |
| Single-round (Data-grounded) | 0.20 | 0.50 | 0.29 | 0.35 |
| Single-round (CoT) | 0.00 | 0.00 | 0.00 | 0.32 |
| Multi-round (No causal feedback) | 0.00 | 0.00 | 0.00 | 0.33 |
| **CAMO (Ours)** | **1.00** | **1.00** | **1.00** | **0.98** |

关键发现：
- 所有 baseline 在 Markov 边界恢复上完全失败（F1=0.00~0.29），CAMO 达到完美 1.00
- 在四个涌现场景（O2O 外卖、Schelling 隔离、信息扩散、规范涌现）上一致有效
- 跨 LLM backbone（Qwen3-235B、DeepSeek-V3.2、GPT-5 mini、Gemma3-27B）稳定工作

### Add-Prune 动态

- Prune 步骤主导压缩（去除无关因子），Add 步骤引入少量必要修正
- Markov 边界大小逐步收敛到真实值（2），候选集被有效压缩到更小规模
- 这种"压缩-修正"机制防止早期过度剪枝同时保持紧凑性

### 干预排名

在无真实因果图的情况下，CAMO 的干预排名 Precision@5 和 MAP@5 在 Smallville（协调）和 AgentSociety（极化/煽动）场景中均显著优于 baseline。

## 关键洞察

1. **因果发现需要 agent 协作，不是单轮 prompt**：单轮方法（text-only、data-grounded、CoT）在因果发现上完全失败，说明因果理解需要多 agent 的迭代精化和反事实验证
2. **计算因子空间是关键**：仅用日志变量无法发现因果结构，必须引入非线性组合变量（比率、图度量等）
3. **局部接口优于全局 DAG**：在复杂 agent 系统中，恢复完整因果 DAG 既不可行也不必要；找到目标的 Markov 边界 + 最小解释子图就够用了
4. **干预排名可操作**：即使没有真实因果图，CAMO 的干预排名也能指导对模拟的修改

## 为什么重要

对手机端 AIOS 的意义：

- **Agent 行为理解**：移动 Agent 系统（如 [[clawmobile-agentic]]）的涌现行为（用户偏好学习、自适应策略）需要因果理解，而非仅观察
- **多 Agent 调试**：当多 Agent 协作（如 [[emommas-emotion-aware-multi-agent]]）出现问题时，因果发现可以定位根因
- **个性化 Agent 的可解释性**：端侧 Agent 的个性化决策需要因果解释，而非黑箱（如 [[agent-persistent-identity]] 中的持久化身份管理）
- **模拟驱动的 Agent 设计**：可用 CAMO 在部署前通过模拟发现因果机制，优化 Agent 策略

## 关联

- [[agent-persistent-identity]] — Agent 持久化身份管理，CAMO 可用于理解身份如何因果地影响决策
- [[emommas-emotion-aware-multi-agent]] — 多 Agent 情感协商，CAMO 的因果发现可用于分析协商结果的涌现机制
- [[memento-skills-agent-design]] — Agent 技能设计，CAMO 的干预排名可指导技能配置优化
- [[memory-as-metabolism-companion-ks]] — 伴随知识系统，因果发现可帮助理解知识如何影响 Agent 行为
- [[gaat-agent-governance]] — Agent 治理遥测，CAMO 提供从微观治理行为到宏观治理效果的因果解释
