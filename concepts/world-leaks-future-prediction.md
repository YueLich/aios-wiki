---
type: concept
tags: [agent-architecture, prediction, evolutionary, llm-agent, reasoning]
related: [[agent-persistent-identity]], [[clawmobile-agentic]], [[exectune-guide-core-policy]]
sources:
  - url: https://arxiv.org/abs/2604.15719
    title: "The World Leaks the Future: Harness Evolution for Future Prediction Agents"
    date: 2026-04-17
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# The World Leaks the Future: Harness Evolution for Future Prediction Agents

> 提出 Milkyway 框架，利用演化信号（时间序列中的模式演变）来增强 LLM Agent 的未来预测能力。在 FutureX 和 FutureWorld 基准上显著超越 GPT-5.4 等强基线。

## 核心问题

未来预测（Future Prediction）是一个独特的 Agent 任务：Agent 必须在目标结果尚未发生时，仅基于当前可获取的公开信息做出预测。这与传统 QA 任务（答案已存在）本质不同——证据是部分的、动态演化的，且需要等待未来才能验证正确性。

传统方法的局限：
- **单次证据采集**：Agent 获取一次信息后做出预测，无法捕捉随时间演化的信号
- **缺乏演化建模**：忽略"世界正在泄漏未来"这一关键直觉——当前事件的模式往往隐含未来走向

## 方法/架构：Milkyway

Milkyway 引入 **Harness Evolution（驾驭演化）** 机制：

### 三阶段迭代框架
1. **初始预测**：基于当前证据形成基线预测
2. **演化信号采集**：在多轮迭代中，系统地追踪时间序列模式的演变——不只是"发生了什么"，而是"变化的趋势是什么"
3. **预测修正**：利用演化信号修正先前预测，持续迭代直到收敛

### 核心设计决策
- 将演化信号建模为可操作的观测变量，而非噪声
- 引入 external experience-reuse 机制，允许从历史预测案例中学习
- 架构兼容通用 Agent 能力——禁用 harness-evolution 后在 GAIA 和 HLE 上仍保持竞争力

## 实验结果

### FutureX 基准（2026年3月第3周切片）

| 方法 | L1 | L2 | L3 | L4 | Overall |
|------|-----|-----|-----|-----|---------|
| GPT-5.4 (web search) | 62.14 | 59.80 | 44.24 | 31.57 | 44.07 |
| MiroFlow† | 64.29 | 72.82 | 59.45 | 46.80 | 58.84 |
| Flash-Searcher | 86.8 | 81.4 | 73.1 | — | 81.8 |
| **Milkyway** | — | — | — | — | **最优** |

### FutureWorld 基准（2026年3月30日-4月3日，100题）
- Milkyway: 62.22 ± 2.79（GPT-5.4 对比基线）
- 五天日均窗口结果稳定

### 通用 Agent 能力（GAIA / HLE）
| 方法 | GAIA Lvl1 | Lvl2 | Lvl3 | Overall | HLE |
|------|-----------|------|------|---------|-----|
| MiroFlow | 90.6 | 83.7 | 72.5 | 84.2 | 41.2 |
| Flash-Searcher | 86.8 | 81.4 | 73.1 | 81.8 | 44.8 |
| **Milkyway** | 88.7 | 80.2 | 76.9 | 82.4 | 43.9 |

Milkyway 在 Level 3 最难任务上达到 76.9%（MiroFlow 72.5%），表明演化信号对复杂推理尤其有效。

## 关键洞察

1. **"世界在泄漏未来"是一个深刻直觉**：当前事件的演化模式（趋势、节奏、关联变化）包含预测信号，远超单次快照的信息量
2. **演化建模是 Agent 架构的通用组件**：不仅限于预测任务，任何需要跟踪时间动态的 Agent（用户行为预测、系统状态预判）都可以借鉴
3. **与移动端 Agent 的关联**：手机端 Agent 持续感知用户行为模式，本质上也是在做"未来预测"——下一个意图、下一个 App、下一个位置。Milkyway 的演化信号采集机制可以类比迁移到端侧行为预测

## 为什么重要

Milkyway 展示了 Agent 不仅仅是"回答问题"，而是可以主动建模世界动态。这对手机端 AIOS 的 Agent 架构设计有直接启示：
- **意图预测**：通过追踪用户交互模式的演化来预判下一步操作
- **资源预分配**：基于使用模式演化预加载 App、预热模型
- **上下文感知**：环境变化（位置、时间、社交场景）的演化信号可用于主动服务

## 关联

- [[agent-persistent-identity]] — Agent 持久身份可集成演化信号记忆
- [[clawmobile-agentic]] — 原生 Agent 架构可嵌入演化预测模块
- [[exectune-guide-core-policy]] — Guide Model 的策略可基于演化信号动态调整
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent 可利用演化模式提升预测准确性
- [[edgeflow-cold-start]] — 冷启动优化可利用演化信号预加载资源
