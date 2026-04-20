---
type: concept
tags: [llm, inference, optimization, agent, quantization, on-device]
related: [[edgeflow-cold-start]], [[on-device-vs-cloud-agentic-tool-calling]], [[clawmobile-agentic]]
sources:
  - url: https://arxiv.org/abs/2604.09741
    title: "ExecTune: Effective Steering of Black-Box LLMs with Guide Models"
    date: 2026-04-09
    reliability: high
created: 2026-04-15
updated: 2026-04-15
---

# ExecTune：用 Guide 模型高效引导黑盒 LLM

> AWS AI 团队提出的 Guide-Core Policy（GCoP）框架，通过小模型引导大模型推理，在 GSM8K 上提升 9.2% 准确率同时降低 22.4% 推理成本。Haiku-3.5 配合 ExecTune 可超越 Sonnet-3.5。

## 核心问题

黑盒 LLM API 的部署困境：

1. **推理成本高**：重复调用 API 的累积成本远超一次性训练成本
2. **无法定制**：黑盒模型无法直接微调或修改
3. **效率浪费**：现有 prompt 引导和 advisor 模式产生的策略经常"不可执行"——核心模型无法忠实遵循 guide 的意图

**关键洞察**：现有方法优化的是 guide 的"信息量"，但真正决定端到端性能的是 guide 的"可执行性"（executability）——核心模型能多大程度上忠实执行 guide 策略的概率。

## 方法/架构

### GCoP（Guide-Core Policy）框架

将推理分解为两个阶段：

```
Guide（小模型，可训练） → 生成结构化策略 → Core（大模型，黑盒） → 执行策略输出结果
```

形式化目标函数（成本敏感效用）：

$$J^\pi(s_0) = V^\pi(s_0) - \lambda T^\pi(s_0)$$

其中 $V$ 是任务奖励，$T$ 是推理成本，$\lambda$ 是成本-性能权衡系数。

**核心发现**：端到端性能由 **guide 平均可执行性** 决定——策略能被核心模型忠实执行的概率。

### ExecTune 训练配方

两阶段训练：

**阶段 1：初始化**
- **Teacher-guided Acceptance Sampling**：用强 teacher 模型提出策略，再用目标 core 模型验证是否可执行
- **监督微调（SFT）**：用高可执行性策略数据初始化 guide

**阶段 2：结构化强化学习**
- 使用 GRPO（Group Relative Policy Optimization）进行结构感知 RL
- 奖励设计：
  - ✅ 策略格式正确/可解析
  - ✅ 执行成功
  - ✅ 成本效率
  - ❌ 策略缺失、格式错误、偏题

### 模型配置

Guide 模型：Qwen3-1.7B（极小）
Core 模型：Claude Haiku-3.5 / Haiku-3.0（黑盒 API）

## 实验结果/关键数据

### 数学推理（GSM8K，Core = Haiku-3.5）

| 方法 | 准确率 | 相对成本 |
|------|--------|----------|
| Core-only (Haiku-3.5) | 基线 | 1x |
| Prompting | 略有提升 | ~1.2x |
| SFT Guide | 中等提升 | ~1.1x |
| **ExecTune GCoP** | **+9.2%** | **0.776x** |

### 代码生成（KodCode，Core = Haiku-3.0）

- 准确率提升 9.2%，推理成本降低 22.4%
- **Haiku-3.5 + ExecTune 超越 Sonnet-3.5**
- 距离 Sonnet-4 仅差 1.7% 绝对精度，但成本低 38%

### 关键数据点

- Guide 模型仅 1.7B 参数，训练成本极低
- 模块化适配：更新 guide 无需重训 core
- 持续学习、领域适配、定向遗忘均可通过更新 guide 实现

## 关键洞察

1. **可执行性 > 信息量**：传统方法认为 guide 应该"更有信息量"，但 ExecTune 证明"更可执行"更重要。一个简单但可执行的策略，优于一个复杂但难执行的策略。

2. **小模型引导大模型的可行性**：1.7B 的 guide 模型就能有效引导 Haiku 级别的 core 模型，说明"策略生成"是比"任务执行"更轻量的能力。

3. **对端侧推理的启示**：
   - 手机端可以运行小 guide 模型（1-3B），将复杂推理外包给云端大模型
   - Guide 模型可以本地微调，Core 模型保持黑盒
   - 这是一种新型的端云协作模式——不是任务拆分，而是策略引导

4. **模块化适应性**：同一个 Core 模型可以通过更换 Guide 适配不同场景（数学、代码、客服），无需重新训练——这对手机端多场景 Agent 非常有价值。

## 为什么重要

对手机端 AIOS 生态的关键启示：

1. **新型端云协作模式**：传统的端云协作是"任务拆分"（边缘处理简单任务，云端处理复杂任务）。ExecTune 提出了"策略引导"模式——端侧小模型生成策略，云端大模型执行，比传统模式更高效。

2. **降低成本门槛**：Haiku + ExecTune 接近 Sonnet-4 水平但成本低 38%，这意味着手机端 AI 功能的部署成本可以大幅降低。

3. **Guide 模型本地化**：1.7B 的 guide 模型完全可以在手机端运行（如通过 [[mnn-350]] 或 [[llamacpp]] 推理），实现完全本地的策略生成 + 云端执行。

4. **隐私保护**：Guide 模型在本地运行，只有最终策略（不含原始数据）发送到云端，天然提供隐私保护。

## 关联
- [[edgeflow-cold-start]] — ExecTune 可能加速冷启动（guide 本地预热）
- [[on-device-vs-cloud-agentic-tool-calling]] — 新的端云协作范式
- [[clawmobile-agentic]] — 手机 Agent 可采用 GCoP 架构
- [[mnn-350]] — 可作为端侧 Guide 模型的推理引擎
- [[llamacpp]] — 可作为端侧 Guide 模型的推理引擎
- [[septq-post-training-quantization]] — Guide 模型可进一步量化以减小体积
