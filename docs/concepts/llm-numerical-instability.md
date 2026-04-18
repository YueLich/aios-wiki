---
type: concept
tags: [推理可靠性, LLM, 浮点精度, 多Agent, 确定性, 端侧推理]
related: [[on-device-vs-cloud-agentic-tool-calling]], [[agent-persistent-identity]], [[long-horizon-task-mirage]]
sources:
  - url: https://arxiv.org/abs/2604.13206
    title: "Numerical Instability and Chaos: Quantifying the Unpredictability of Large Language Models"
    date: 2026-04-14
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# LLM 数值不稳定性 — 浮点精度引发的不可预测性

> 研究揭示 LLM 的不可预测性根植于浮点表示的有限精度，量化误差在 Transformer 层中传播、放大或消散。在端侧异构硬件上，这一问题尤为突出。

## 核心问题

多 Agent LLM 系统的失败率远超预期：AutoGen 工作流在 23% 的协作任务上无法收敛，MetaGPT 在 31% 的规划任务中产生不可复现输出。这些失败不能归因于算法限制，而是源自浮点运算在异构基础设施上的非确定性。

## 方法/架构

### 混沌雪崩效应

研究发现 Transformer 早期层存在"雪崩效应"——微小扰动触发二元结果：
- **快速放大**：误差在前几层指数级增长
- **完全衰减**：误差被完全吸收

### 三区间模型

| 区间 | 条件 | 行为 |
|------|------|------|
| 稳定区 | 扰动低于输入依赖阈值 | 输出恒定不变 |
| 混沌区 | 舍入误差主导 | 输出发散，不可预测 |
| 信号主导区 | 真实输入变化压过数值噪声 | 输出由真实输入决定 |

### 浮点误差传播追踪

- 追踪浮点舍入误差如何在 Transformer 计算层中传播
- 在注意力机制和 FFN 层中分别分析误差放大模式
- 验证跨多个数据集和模型架构的普适性

## 关键洞察

1. **端侧异构硬件放大此问题**：手机端 ARM CPU、NPU、DSP 使用不同的浮点实现和精度，同一模型在不同硬件上可能产生不同输出
2. **固定随机种子不解决根本问题**：即使固定种子，浮点运算的非确定性仍会导致输出差异
3. **对端侧 Agent 的启示**：在端侧部署的 Agent 需要设计容错机制，而非假设确定性执行
4. **量化进一步加剧**：模型量化将浮点精度从 FP32/BF16 降至 INT8/INT4，数值不稳定性会更显著

## 为什么重要

- **端侧推理可靠性的理论基础**：理解为什么同一模型在不同手机上给出不同答案
- **多 Agent 系统的故障模式分析**：23% 和 31% 的失败率数字为端侧多 Agent 系统设计提供风险评估参考
- **量化策略的指导**：理解数值不稳定性有助于设计更鲁棒的量化方案
- **端侧 Agent 容错设计**：Agent 需要检测和恢复数值不稳定性导致的异常行为

## 关联

- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧工具调用的可靠性受数值不稳定性影响
- [[agent-persistent-identity]] — Agent 持久化身份的稳定性受浮点精度约束
- [[long-horizon-task-mirage]] — 长程任务失败可能部分源自数值误差累积
- [[kv-cache-quantization-ondevice]] — KV 缓存量化会加剧数值不稳定性
