---
type: concept
tags: [agent-memory, benchmark, gamified-evaluation, long-term-memory, LLM评估]
related: [[amc-adaptive-memory-crystallization]], [[memory-worth-governance]], [[agent-persistent-identity]], [[mga-memory-gui-agent]]
sources:
  - url: https://arxiv.org/abs/2604.14158
    title: "MemGround: Long-Term Memory Evaluation Kit for Large Language Models in Gamified Scenarios"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# MemGround: 基于游戏化场景的 LLM 长期记忆评估框架

> 三层分级记忆评估基准，通过 RPG 游戏场景测试 LLM 的状态追踪、时序关联和推理记忆能力

## 核心问题

现有 LLM 记忆评估方法本质是静态的——过度关注简单检索和短上下文推断，忽略了复杂记忆系统的多面性，如连续交互中的动态状态追踪和层级推理。这导致我们无法准确衡量 Agent 在长期交互中真正"记住"了什么。

## 方法/架构

MemGround 提出**三层分级记忆评估框架**，每层对应一个游戏化场景：

| 层级 | 记忆类型 | 游戏场景 | 评估维度 |
|------|---------|---------|---------|
| L1 | Surface State Memory（表面状态记忆） | TRPG（桌游RPG） | 追踪实体属性和状态变化 |
| L2 | Temporal Associative Memory（时序关联记忆） | No Case Should Remain Unsolved（侦探推理） | 关联跨时间的事件线索 |
| L3 | Reasoning-Based Memory（推理记忆） | Type Help（交互式求助） | 基于历史推理上下文做出决策 |

每个场景设计了多维度评估指标：
- **QA Overall**：问答正确率
- **MFCO**（Memory-Faithful Chain-of-Thought）：记忆忠实的推理链
- **MFU**（Memory Faithful Utilization）：记忆利用率

## 实验结果

在多个 SOTA 模型上的测试结果揭示了显著差异：

| 模型 | TRPG QA↑ | No Case QA↑ | Type Help QA↑ |
|------|----------|-------------|---------------|
| GPT-5.2 | **51.51%** | 28.56% | 23.61% |
| Claude-Opus-4.6 | 38.07% | **47.76%** | 23.81% |
| A-MEM (agent) | **53.79%** | 41.72% | 21.80% |
| Gemini-3-Pro-Preview | 26.28% | 41.61% | 28.62% |
| DeepSeek-V3.2 | 31.41% | 37.58% | 27.98% |
| Qwen3-VL-32B (open) | 25.78% | 13.03% | 14.02% |

**关键发现**：
- 即使是最强模型（GPT-5.2 在 TRPG 达到 51.51%），整体表现仍远低于人类水平
- 专门的记忆增强 Agent（A-MEM, Mem0）在某些场景超越了原始 LLM
- 开源模型（Qwen3-32B）在记忆任务上显著落后于闭源模型
- Claude-Opus-4.6 在推理密集的侦探场景表现最佳（47.76%），展示了推理与记忆的协同

## 关键洞察

**游戏化评估比传统 QA 更能暴露记忆缺陷**：在 TRPG 场景中，模型需要持续追踪多个实体的状态变化——这在静态 QA 中完全无法测试。结果表明，当前 LLM 的"长期记忆"更多是上下文窗口内的被动保留，而非主动的记忆管理。

**对移动端 Agent 的启示**：手机端 Agent 需要在多天甚至多周的使用中记住用户偏好、操作习惯和上下文。MemGround 的三层框架可以直接转化为移动端 Agent 的记忆能力评估标准。

## 为什么重要

MemGround 填补了 Agent 记忆评估的关键空白。对于手机端 AIOS 而言：
- 提供了评估端侧 Agent 记忆能力的标准化框架
- 游戏化场景天然适合测试持续交互场景下的记忆保持
- 三层分级直接对应 Agent 从"记住状态"到"利用记忆推理"的能力梯度
- 结果表明现有模型在记忆任务上仍有巨大提升空间，这正是端侧 Agent 需要突破的方向

## 关联
- [[amc-adaptive-memory-crystallization]] — 自适应记忆结晶化与 MemGround 的 L3 推理记忆层互补
- [[memory-worth-governance]] — 记忆治理需要 MemGround 这样的评估框架来衡量治理效果
- [[agent-persistent-identity]] — Agent 持久化身份依赖长期记忆，MemGround 评估了基础能力
- [[mga-memory-gui-agent]] — MGA 的 GUI Agent 记忆机制可以用 MemGround 框架评估
