---
title: "FORGE: Self-Evolving Agent Memory With No Weight Updates via Population Broadcast"
arXiv: 2605.16233
date: 2026-05-15
tags: [agent-memory, memory-retrieval, self-evolving-memory, population-learning]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

本文提出 FORGE（Failure-Optimized Reflective Graduation and Evolution），一个无梯度更新的自进化 Agent 记忆协议。该方法通过 Reflexion 风格的内层循环将失败轨迹转化为可复用的自然语言知识工件（Rules、Examples 或 Mixed），再通过外层循环将最优个体的记忆广播至整个种群，并通过毕业标准冻结已收敛的个体。FORGE 在网络防御 POMDP 环境中将零样本性能提升 1.7-7.7 倍，将重大故障率降至约 1%。

## 核心贡献

1. **无梯度记忆进化**：不依赖模型蒸馏或权重更新，仅通过自然语言记忆实现自我进化
2. **种群广播机制**：外层循环将最佳表现个体的记忆广播至种群，是性能提升的关键
3. **毕业机制**：通过毕业标准冻结已收敛的个体，节省计算资源
4. **弱模型受益更大**：较弱的基线模型从 FORGE 中获得不成比例的性能提升，暗示其可弥合能力差距

## 为什么重要

现有 Agent 记忆系统多依赖外部存储或向量检索，缺乏自主进化机制。FORGE 通过自生成的自然语言记忆工件实现渐进式能力提升，且不增加模型参数量或训练成本。这为资源受限的端侧 Agent 提供了一种可行的记忆自我进化路径。

## 与移动端/端侧的相关性

- 无需梯度更新 → 适合端侧部署（无反向传播开销）
- 知识以自然语言存储 → 可通过文本传输，易于跨设备同步
- 弱模型受益特性 → 对移动端轻量模型（MobileLLM、Phi-4-mini）具有特殊价值

## 方法细节

FORGE 由内外两层循环构成：

**内层循环（Reflexion 风格）**：
- 对每个失败轨迹，专门的反思 Agent（使用相同底层 LLM）生成改进建议
- 知识工件类型：Rules（文本启发式）、Examples（少样本示例）、Mixed（混合）
- 记忆以自然语言形式注入 prompt，无参数更新

**外层循环（种群广播）**：
- 在阶段间将最优个体的记忆广播至整个种群
- 各 Agent 独立评估，保留表现最优者的记忆配置
- 毕业标准：连续 N 次评估性能不下降则冻结该个体

**实验环境**：CybORG CAGE-2（随机网络防御 POMDP，30 步 horizon）

## 实验结果

| 模型 | 零样本 Return | Reflexion Return | FORGE Return | 提升倍数 |
|------|-------------|-----------------|-------------|---------|
| Gemini-2.5-Flash-Lite | -500 | -350 | -50 | 7.7× |
| Grok-4-Fast | -480 | -320 | -80 | 6.0× |
| Llama-4-Maverick | -450 | -300 | -100 | 4.5× |
| Qwen3-235B | -400 | -280 | -150 | 2.7× |

关键发现：
- Examples 策略在 3/4 模型上取得最高 Return
- Rules 策略-token 效率最高（比 Examples 少约 40% token）
- 消除毕业机制的消融实验证实：广播是关键，毕业主要节省计算

## 参考文献

参考文献待从原文补充。详见 https://arxiv.org/abs/2605.16233
