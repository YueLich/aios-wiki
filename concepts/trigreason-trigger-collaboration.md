---
type: concept
tags: [推理优化, edge-cloud, small model, speculative reasoning, Agent, 推理框架]
related: [[rpra-llm-judge-inference]], [[on-device-inference-memory-pressure]], [[edge-cloud-offloading]], [[exectune-guide-core-policy]], [[chain-of-modality]], [[clawmobile-agentic]]
sources:
  - url: https://arxiv.org/abs/2604.14847
    title: "TrigReason: Trigger-Based Collaboration between Small and Large Reasoning Models"
    date: 2026-04-16
    reliability: high
  - url: https://github.com/QQQ-yi/TrigReason
    title: "TrigReason GitHub Repository"
    date: 2026-04-16
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# TrigReason: 触发式小大模型推理协作

> 用触发器替代轮询，让小模型跑大部分推理、大模型只在关键时刻介入——edge-cloud 场景下延迟降 43.9%，API 成本降 73.3%

## 核心问题

Large Reasoning Models (LRMs) 如 QwQ-32B 通过扩展思维链 (CoT) 在复杂任务上表现强劲，但自回归生成数千个 thinking tokens 导致推理延迟极高。现有加速方法（RL 长度惩罚、变长 CoT 微调、prompt 工程）通常强制缩减 token 预算，可能跳过关键逻辑步骤或阻止必要的自我纠错。

**核心矛盾**: 如何在保持推理质量的同时大幅降低推理成本？

## 方法/架构

TrigReason 提出**触发式协作推理框架**，用选择性干预替代持续轮询（SpecReason 的方式）。系统将大部分推理委托给 Small Reasoning Model (SRM)，仅在三种特定场景激活 LRM 干预：

### 三大触发器

**1. Strategic Priming Trigger（战略引导触发器）** — 解决 Path Divergence Risk
- SRM 缺乏构建初始规划的战略能力，推理容易偏离最可能路径
- 先让 LRM 生成前 n 个推理步骤（默认 n=20），建立有效推理轨迹
- 然后将控制权交给 SRM 继续推理
- 减少 n 从 20 到 0 会导致 25.4% 的绝对准确率下降

**2. Cognitive Offload Trigger（认知卸载触发器）** — 解决 Cognitive Overload Risk
- 利用 SRM 的 "overconfidence" 作为早期预警信号
- 定义 token 级困惑度 PPL(t)，当某个推理步骤的 PPL 异常低时（SRM 过于自信），触发 LRM 介入
- 阈值 ρ 是模型相关的：DeepSeek-R1-1.5B 最优 ρ=0.85，Qwen3-0.6B 最优 ρ=0.75
- 禁用此触发器会导致准确率显著下降

**3. Intervention Request Trigger（干预请求触发器）** — 解决 Recovery Inability Risk
- SRM 缺乏强健的自反思和纠错机制
- 当推理陷入无产出循环时，触发 LRM 接管

### 架构流程
```
输入问题 x
    ↓
[Strategic Priming] LRM 生成前 n 步 → 建立推理方向
    ↓
[SRM Execution] SRM 接管后续推理
    ↓
[Cognitive Offload] 检测 PPL 异常 → LRM 干预
    ↓
[Intervention Request] 检测推理循环 → LRM 接管
    ↓
输出最终答案
```

## 实验结果

### 模型配置
| 角色 | 模型 | 参数量 |
|------|------|--------|
| LRM | QwQ-32B (dense) | 32B |
| LRM | Qwen3-30B-A3B-Thinking-2507 (MoE) | 30B, 3B active |
| SRM | DeepSeek-R1-1.5B | 1.5B |
| SRM | Qwen3-0.6B | 0.6B |

### 准确率（相对 LRM 全量推理的比例）
| Benchmark | TrigReason (平均) | 备注 |
|-----------|-------------------|------|
| AIME24 | 105.8% | 最高 119.3% (Qwen3-0.6B + Qwen3-30B) |
| AIME25 | 104.7% | 部分配置超越 LRM baseline |
| GPQA Diamond | 99.6% | 研究生级多选题 |

### 效率提升
- **SRM token 占比**: 相比 SpecReason 提升 **1.70× ~ 4.79×**（四种组合均显著）
- **Edge-Cloud 部署** (SRM 本地 + LRM 通过 DeepSeek API):
  - 延迟降低 **43.9%**
  - API 成本降低 **73.3%**
  - 59.4% 推理 token 卸载到 SRM，仅 2.49% 绝对准确率下降

### 对比 SpecReason 的关键差异
SpecReason 使用 LRM 作为验证器（verifier）接受/拒绝 SRM 推理步骤，但发现 DeepSeek-V3.1 作为验证器时会受自身归纳偏见影响，给语义薄弱的 SRM 步骤打高分 → 错误传播 → 最终解题错误。TrigReason 用触发器替代验证器，避免了这一问题。

## 关键洞察

1. **Overconfidence 是信号而非噪声**: TrigReason 的核心发现是 SRM 的异常低困惑度（overconfidence）可以作为 "需要大模型介入" 的可靠信号。这与直觉相反——通常我们认为高困惑度（不确定）才需要帮助。

2. **战略规划比逐步验证更重要**: Strategic Priming Trigger（仅 n=20 步的 LRM 引导）贡献了最大的准确率提升（25.4%），说明 SRM 的主要瓶颈不是执行能力而是规划能力。这对 mobile agent 架构设计有直接启示。

3. **触发器比轮询更高效**: 相比 SpecReason 的持续轮询验证，TrigReason 的选择性干预在相同准确率下将 SRM 利用率提升了 1.7-4.8 倍。这意味着边缘设备可以承担更多推理负载。

4. **超参数的模型依赖性**: ρ（认知卸载阈值）在不同 SRM 间差异显著（0.75 vs 0.85），反映了不同小模型在平均困惑度和推理可靠性上的内在差异。实际部署需要 per-model 调参。

## 为什么重要

TrigReason 对手机端 AIOS 生态具有直接价值：

1. **端云协同推理**: 框架天然适配 edge-cloud 架构——SRM 在手机本地运行（如 Qwen3-0.6B），LRM 在云端。43.9% 延迟降低 + 73.3% 成本降低直接改善用户体验。

2. **Agent 任务分解启示**: 三类推理风险（路径偏离、认知过载、恢复失败）映射到 mobile agent 的任务分解场景。Strategic Priming 的有效性说明让大模型做规划、小模型做执行是正确分工。

3. **能耗优化**: 将 59.4% 推理 token 转移到本地小模型，大幅减少云端调用，对电池续航敏感的移动设备尤其重要。

4. **与现有推理优化互补**: TrigReason 可以与量化、KV-cache 优化等技术叠加使用——小模型本地推理可以进一步用 [[kv-cache-quantization-ondevice]] 加速。

## 关联

- [[rpra-llm-judge-inference]] — RPRA 用 LLM-Judge 预测最优推理模型，TrigReason 用触发器动态切换，两者互补
- [[on-device-inference-memory-pressure]] — SRM 本地运行面临内存压力问题
- [[edge-cloud-offloading]] — TrigReason 是 edge-cloud 推理卸载的精确实现
- [[exectune-guide-core-policy]] — ExecTune 用 Guide Model 指导黑盒 LLM，TrigReason 类似但聚焦推理场景
- [[chain-of-modality]] — 动态编排思想的多模态扩展
- [[clawmobile-agentic]] — Mobile agent 架构中 SRM+LRM 协作的潜在应用
