---
type: concept
tags: [gui-agent, lightweight, multi-role, on-device, mobile, mllm, multi-agent]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[clawmobile-agentic]], [[turing-test-mobile-gui]], [[mobiflow-benchmark]], [[clawgui-unified-framework]]
sources:
  - url: https://arxiv.org/abs/2604.13488
    title: "Towards Scalable Lightweight GUI Agents via Multi-role Orchestration"
    date: 2026-04-15
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# LAMO: 面向多角色编排的轻量级 GUI Agent

> 浙大 + 蚂蚁集团提出的框架，让轻量级多模态大模型在资源受限设备上实现可扩展的 GUI 自动化

## 核心问题

当前 GUI Agent 领域面临一个根本性的 **成本-可扩展性困境**：
- 大规模 MLLM（如 GPT-4V）驱动的 GUI Agent 效果好，但部署成本过高，无法在手机等端侧设备运行
- 轻量级 MLLM（~3B 参数）虽然可部署，但容量有限，在复杂真实场景中表现差
- 端到端训练下，轻量模型的任务可扩展性差，难以适应多 Agent 系统（MAS）
- 训练多个技能专家（skill-specific experts）成本高昂

**关键问题**：能否在成本与可扩展性之间找到有效平衡，让轻量 MLLM 参与真实 GUI 工作流？

## 方法/架构

LAMO 框架包含三大核心组件：

### 1. 角色导向数据合成（Role-Oriented Data Synthesis）
- 通过角色定义生成训练数据，使轻量模型获得 GUI 专业知识
- 支持多种角色：perceiver（感知）、planner（规划）、executor（执行）

### 2. 两阶段训练方案
- **阶段一：监督微调（SFT）**
  - 使用 Perplexity-Weighted Cross-Entropy 优化
  - 实现知识蒸馏 + 视觉感知增强
  - 从大模型向轻量模型迁移 GUI 知识
- **阶段二：强化学习（RL）**
  - 角色导向的协作探索（role-oriented cooperative exploration）
  - 让模型在多角色场景下学会协调配合

### 3. LAMO-3B：任务可扩展的原生 GUI Agent
- 基于 3B 参数的轻量 MLLM
- 支持**单体执行**（monolithic execution）和 **MAS 编排**
- 作为即插即用的策略执行器，与高级规划器配合使用时可持续受益于规划器升级
- 核心优势：**不需重新训练**即可配合更强的规划器提升效果

## 实验结果/关键数据

- LAMO-3B 作为轻量 GUI Agent，在资源受限设备上实现可部署
- 支持与高级规划器的即插即用集成，无需重新训练即可提升性能
- 在多角色编排场景下，轻量模型的 capability boundary 被有效扩展
- 相比训练多个技能专家，LAMO 的统一多角色方案显著降低成本

## 关键洞察

**为什么 LAMO 重要**：

1. **打破了"大模型才能做 Agent"的假设**：通过角色编排，3B 模型可以在复杂 GUI 任务中发挥作用
2. **即插即用设计**：LAMO-3B 不依赖特定规划器，随着规划器进步自动受益——这是移动端部署的关键特性
3. **从 episodic learning 到 cooperative exploration**：RL 阶段的角色导向探索突破了传统端到端训练的可扩展性瓶颈
4. **蚂蚁集团的实际需求驱动**：来自工业界的实践验证，非纯学术探索

## 对手机端 AI 生态的意义

- **端侧 GUI Agent 的可行路径**：证明 3B 参数级别的模型可以作为实用的 GUI Agent
- **MAS 架构在端侧的落地**：多角色编排为手机端多 Agent 协作提供了技术基础
- **降低部署门槛**：无需 70B+ 的大模型，3B 模型配合编排即可完成复杂任务
- **与 [[clawmobile-agentic]] 的互补**：ClawMobile 强调原生化设计，LAMO 强调轻量化编排

## 关联
- [[secagent-mobile-gui]] — 同为移动端 GUI Agent，SecAgent 侧重语义上下文，LAMO 侧重多角色编排
- [[pspa-bench-gui-agent]] — 个性化 GUI Agent 基准，LAMO-3B 可在此基准上测试
- [[clawmobile-agentic]] — 手机原生 Agent 系统，LAMO 提供了轻量化实现路径
- [[turing-test-mobile-gui]] — GUI Agent 人性化基准，可评估 LAMO 的自然交互能力
- [[clawgui-unified-framework]] — 同期发布的 GUI Agent 框架，ClawGUI 提供完整训练-评估-部署管线
- [[mga-memory-gui-agent]] — 记忆驱动 GUI Agent，LAMO 的角色编排可与记忆机制结合
