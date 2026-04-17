---
type: entity
tags: [模型, MoE, 端侧推理, agentic-coding, 阿里, 开源模型]
related: [[gemma4-ondevice]], [[llamacpp-b8833]], [[minicpm-242]], [[qwen3]]
sources:
  - url: https://the-decoder.com/alibabas-open-model-qwen3-6-leads-googles-gemma-4-across-agentic-coding-benchmarks/
    title: "Alibaba's open model Qwen3.6 leads Google's Gemma 4 across agentic coding benchmarks"
    date: 2026-04-17
    reliability: high
  - url: https://huggingface.co/Qwen/Qwen3.6-35B-A3B
    title: "Qwen3.6-35B-A3B on HuggingFace"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Qwen3.6-35B-A3B

> 阿里发布新一代开源 MoE 模型 Qwen3.6-35B-A3B，仅激活 35B 参数中的 3B，在 agentic coding 基准上全面超越 Gemma 4

## 核心问题
开源模型在端侧部署面临质量-效率权衡：大模型能力强但推理成本高，小模型效率高但能力不足。Qwen3.6 采用 MoE 架构试图两全——35B 总参数保证容量，每次仅激活 3B 以控制推理成本。

## 方法/架构

### 模型架构
- **总参数**: 35B（350 亿）
- **激活参数**: 3B（每次推理仅激活 35B 中的 3B）
- **架构**: Mixture-of-Experts (MoE)
- **模式**: 支持 thinking（深度推理）和 non-thinking（快速响应）双模式
- **多模态**: 支持图像和视频理解任务

### 部署方式
- **Qwen Studio**: 在线体验平台
- **API**: 阿里云 Model Studio 提供 Qwen3.6 Flash API
- **开源权重**: HuggingFace 和 ModelScope 可下载
- **量化友好**: 3B 激活参数量适合 4-bit 量化后在手机端运行

## 实验结果

### 与 Gemma 4-31B 对比（核心基准）

| 基准 | Qwen3.6-35B-A3B | Gemma 4-31B | 差距 |
|------|-----------------|-------------|------|
| SWE-bench Verified | 73.4 | 52.0 | +21.4 |
| Terminal-Bench 2.0 | 51.5 | 42.9 | +8.6 |
| GPQA（推理） | 86.0 | 84.3 | +1.7 |
| AIME26（数学） | 92.7 | 89.2 | +3.5 |

### 与前代 Qwen3.5 对比
- 在 agentic coding 任务上"显著超越"前代 Qwen3.5-35B-A3B
- Alibaba 声称在图像和视频任务上可与 Claude Sonnet 4.5 匹敌

## 关键洞察

### 为什么 MoE 对端侧重要
MoE 架构的激活参数量远小于总参数量，这意味着：
1. **内存效率**: 推理时只需加载活跃专家的权重，不是全部 35B
2. **计算效率**: 3B 激活参数量意味着推理 FLOPs 接近 3B 密集模型
3. **量化空间**: 3B 激活参数 4-bit 量化后仅需 ~1.5GB，手机可行

### Agentic Coding 的端侧意义
SWE-bench 和 Terminal-Bench 测试的是 Agent 在代码仓库中自主完成任务的能力。Qwen3.6 在这些基准上的大幅领先（+21.4 SWE-bench）表明：
- 更强的代码理解和修改能力 → 端侧编程助手更实用
- 更好的多步骤推理 → Agent 任务分解更可靠
- 这对 Android Studio Agent Mode、GitHub Copilot 等端侧编码工具是重大利好

### MoE 路由的端侧挑战
- 专家路由需要额外的内存带宽（加载不同专家权重）
- 手机端 DRAM 带宽有限，频繁切换专家可能导致延迟抖动
- 需要智能缓存策略：预加载高频专家，LRU 淘汰低频专家

## 为什么重要
Qwen3.6-35B-A3B 证明了 MoE 架构在端侧部署的可行性——用 3B 的计算成本获得接近 35B 的能力。这对移动 AIOS 的 Agent 系统至关重要：更强的模型意味着更可靠的 Agent 行为，而 MoE 的效率特性让端侧部署成为可能。与 Gemma 4 的竞争也推动了整个开源端侧模型生态的进步。

## 关联
- [[gemma4-ondevice]] — Qwen3.6 的主要竞争对手，Google 的端侧开源模型
- [[minicpm-242]] — 另一个端侧高效模型，Qwen3.6 的 MoE 路线不同
- [[llamacpp-b8833]] — llama.cpp 是运行 Qwen3.6 的主要推理引擎之一
- [[mnn-350]] — 阿里自研的推理框架 MNN，可能优先适配 Qwen3.6
