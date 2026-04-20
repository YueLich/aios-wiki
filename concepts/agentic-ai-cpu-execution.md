---
type: concept
tags: [agentic-ai, cpu-optimization, on-device-inference, execution-pipeline, edge-computing, tool-processing, latency, energy]
related: [[edge-cloud-offloading]], [[agent-persistent-identity]], [[clawmobile-agentic]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://arxiv.org/abs/2511.00739
    title: "Towards Understanding, Analyzing, and Optimizing Agentic AI Execution: A CPU-Centric Perspective"
    date: 2026-04-17
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Agentic AI CPU 执行优化

> 从 CPU 视角系统性分析 Agentic AI 工作负载的性能瓶颈，发现工具处理占总延迟 90.6%，CPU 动态能耗占总量 44%。

## 核心问题

Agentic AI 框架在 LLM 推理之上叠加了决策编排器（orchestrator）和外部工具调用（Python 执行、Web 搜索、数据库查询等）。现有 AI 效率研究几乎全部聚焦 GPU 内核和 KV-cache 调度，而 **CPU 在 agentic 工作流中的角色被严重忽视**。

对于手机端 Agent 而言，这个问题尤为致命——移动设备的 CPU 性能和功耗预算远低于服务器，而 Agent 系统的工具调用、状态管理、决策循环全部运行在 CPU 上。

## 方法/架构

论文系统性地分析了 5 种 agentic AI 工作负载：
- **Haystack RAG** — 检索增强生成
- **Toolformer** — 工具使用推理
- **ChemCrow** — 化学领域工具调用
- **LangChain** — 通用 Agent 框架
- **SWE-Agent** — 软件工程 Agent

从三个维度进行 profiling：
1. **延迟分解**：LLM 推理 vs 工具处理 vs 编排决策
2. **吞吐量瓶颈**：CPU 一致性/同步/核过订阅 vs GPU 显存
3. **能耗分析**：CPU 动态能耗在总能耗中的占比

## 实验结果/关键数据

| 指标 | 发现 |
|------|------|
| 工具处理延迟占比 | 最高 **90.6%** 的总延迟来自 CPU 上的工具处理 |
| CPU 动态能耗占比 | 大 batch 下 CPU 动态能耗占总能耗 **44%** |
| 吞吐量瓶颈源 | CPU 侧：核一致性、同步、过订阅；GPU 侧：显存容量和带宽 |
| ReAct vs 单体 LLM | ALFWorld 成功率高 **27%**，WebShop 高 **34%** |

基于 profiling 发现，论文提出两项优化：

### 1. CGAM (CPU and GPU-Aware Micro-batching)
CPU/GPU 感知的微批处理策略，根据编排器和推理路径的动态特性自适应调整 batch 大小。

### 2. MAWS (Mixed Agentic Workload Scheduling)
针对异构 agentic 工作负载的混合调度，将同质和异质 agent 任务分别优化。实测 P50 延迟分别获得 **1.47×** 和 **1.41×** 加速。

## 关键洞察

**1. Agent 工作流是 CPU-bound，不是 GPU-bound**

传统 LLM 优化假设瓶颈在 GPU 推理。但 Agent 系统中，工具处理（Python 执行、搜索、数据库查询）占了绝大部分延迟。这意味着对于手机端 Agent，优化 CPU 端的工具执行流水线比优化 GPU 推理更重要。

**2. 工具调用的重复性决定了系统效率**

论文发现 agentic flow 的"执行路径动态性和重复性"直接影响系统级性能。手机端 Agent 场景中，用户行为模式相对固定（查天气、设闹钟、发消息），工具调用具有高度可预测性——这为预缓存和流水线化提供了机会。

**3. SLM 可以胜任 Agent 编排**

论文指出，在工具使用和检索可以外化计算和事实回忆的设置下，SLM（如 GPT-J 6B）可以保持任务性能。这对手机端部署意义重大——不需要端侧运行大模型，小模型 + 高效工具链即可。

**4. 能耗优化是移动端的生死线**

CPU 动态能耗占 44% 意味着，即使 GPU 推理完全异步化，Agent 系统仍然会因为 CPU 上的工具处理而严重消耗电量。手机端需要针对性的 CPU 功耗调度策略。

## 为什么重要

这篇论文为手机端 AIOS 的 Agent 系统设计提供了关键的系统级洞察：

- **工具链优化优先于模型优化**：与其压缩端侧 LLM，不如优化工具调用的 CPU 执行效率
- **SLM + 工具链 > 大模型单体**：手机端不需要运行 70B 模型，小模型 + 高效编排器即可
- **能耗预算需要重新分配**：传统的"推理能耗"视角不够，需要考虑整个 Agent 工作流的 CPU 能耗
- **微批处理和调度策略对移动端有直接参考价值**

## 关联

- [[edge-cloud-offloading]] — 边缘-云协同卸载与 CPU 执行优化的互补关系
- [[clawmobile-agentic]] — ClawMobile 原生 Agent 架构中的工具调用设计
- [[agent-persistent-identity]] — Agent 持久化身份管理的 CPU 开销
- [[kv-cache-quantization-ondevice]] — 端侧 KV-cache 优化减少 GPU 负载，间接影响 CPU/GPU 平衡
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端工具调用的延迟/能耗权衡
