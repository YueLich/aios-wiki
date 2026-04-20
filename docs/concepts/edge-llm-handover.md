---
type: concept
tags: [edge-llm, handover, kv-cache, mobile, 5g, inference, latency, streaming, on-device]
related: [[kv-cache-quantization-ondevice]], [[edgeflow-cold-start]], [[llamacpp]], [[mnn-350]]
sources:
  - url: https://arxiv.org/abs/2603.28018
    title: "Low-Latency Edge LLM Handover via Joint KV Cache Transfer and Token Prefill"
    date: 2026-03-17
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Edge LLM Handover: 联合 KV 缓存传输与 Token Prefill 的低延迟切换方案

> 解决移动用户在基站间切换时 Edge LLM 服务中断的问题，提出 ctHO 联合优化框架最小化最差用户切换延迟。来自 Seunghun Lee, Jihong Park, Ce Zheng。

## 核心问题

Edge LLM（边缘部署的大型语言模型）为移动用户提供低延迟 token 流式服务，但当用户在基站（BS）之间移动并触发切换（Handover, HO）时，目标基站没有该用户的 KV 缓存，无法立即恢复解码上下文，导致服务中断。

现有两种方案各有缺陷：
- **token-based HO (tHO)**：将已解码 token 转发给目标基站，重新执行 prefill 重建 KV 缓存。问题：prefill 计算密集，产生大的 TTFT（Time-To-First-Token）延迟，且多用户同时切换时批处理 prefill 的最差用户延迟成为瓶颈。
- **cache-based HO (cHO)**：通过回传链路直接传输 KV 缓存。问题：KV 缓存体量巨大（十亿参数模型约 GB 级），受限的回传带宽在多用户同时切换时成为瓶颈。

## 方法/架构

### ctHO 联合框架

提出 **ctHO (cache-token HO)** 联合方案，同时利用 token-based prefill 和 KV 缓存直接传输：

```
源基站 ──[token转发]──→ 目标基站 → prefill 重建部分 KV
     └──[KV缓存传输 over backhaul]──→ 目标基站 → 获取剩余 KV
                                    ↓
                           取两者最大值 = HO 延迟
```

**关键优化**：
1. **Prefill 长度 L 优化**：决定对多少 token 执行 prefill（vs 直接传输 KV 缓存）。所有用户的 batch prefill 共享一个公共前缀长度 L。
2. **回传带宽分配**：在 K 个用户之间分配回传带宽 R_bh，最小化最差用户的 HO 延迟。
3. **分步求解**：将联合优化问题分解为：
   - 给定 L，优化带宽分配（凸优化）
   - 搜索最优 L（离散搜索）

### 系统模型

- 多用户场景（K=4 UEs）
- 1D 线性网络模型：源基站 x=0，目标基站 x=300m，切换边界 x=150m
- 用户速度 v=20m/s，从 x₀∈[120,130]m 出发
- 每 token KV 缓存大小：s_KV = 2·N_ℓ·N_kv·d_h·q bits

### 实验结果

使用 **Qwen2.5-7B-Instruct**（N_ℓ=28, N_kv=4, d_h=128, q=16bit），每 token KV 缓存 458,752 bits，3072 token 时总缓存约 **176 MB**。

| 参数 | ctHO 优势 |
|------|----------|
| 回传速率 R_bh | 在所有 R_bh 下 ctHO 均优于 tHO 和 cHO |
| Prefill 速度 | ctHO 对 prefill 速度变化不敏感（因联合优化可调节 L） |
| 最大缓存大小 C_max | C_max 越大，cHO 越差（传输量增大），ctHO 通过部分 prefill 保持低延迟 |
| 用户数 K | 用户越多，ctHO 相对优势越大（批 prefill 效率 + 带宽分配优化） |

**核心结论**：ctHO 在所有仿真设置下一致优于纯 tHO 和纯 cHO，通过联合优化 prefill 长度和回传带宽分配，最小化最差用户的 HO 延迟。

## 关键洞察

1. **端侧 LLM 的移动性是被忽视的系统挑战**：现有研究聚焦单基站推理优化，但真实移动场景中用户跨基站移动是常态。切换时的 KV 缓存迁移直接影响用户体验连续性。

2. **Batch prefill 的双刃剑**：批处理 prefill 可以共享计算，但强制所有用户使用相同的前缀长度 L，可能对 token 数少的用户造成浪费（零填充）。ctHO 的核心创新在于找到最优 L 平衡各方。

3. **KV 缓存传输 vs 重新计算的权衡**：本质上是"传输数据"vs"本地计算"的经典 trade-off，与 MEC（移动边缘计算）中的 offloading 问题一脉相承。

4. **未来方向**：论文提出向 soft HO 扩展——目标基站预计算（pre-computation）+ 源基站继续解码，实现更无缝的服务连续性。这对 6G 网络中的 AI-native 架构设计有重要参考价值。

## 为什么重要

随着 ChatGPT、Gemini 等 LLM 服务在移动端的普及（数十亿用户），edge LLM 成为 5G/6G 网络的关键应用。但 **移动性管理** 是 edge LLM 落地的核心障碍之一：

- 云 LLM 依赖远端数据中心，切换影响小（用户始终连接同一云端）
- Edge LLM 将模型部署在基站侧，切换意味着 KV 缓存丢失
- 如果不能解决切换延迟，edge LLM 的低延迟优势将被移动性破坏

本论文首次系统地建模和优化 edge LLM 切换问题，为运营商和设备厂商的 edge LLM 部署提供了理论基础和实用方案。

## 关联
- [[kv-cache-quantization-ondevice]] — KV 缓存量化可减小传输数据量，降低 cHO 的回传带宽需求
- [[edgeflow-cold-start]] — Edge LLM 冷启动问题，切换场景是冷启动的变体
- [[llamacpp]] — llama.cpp 的端侧推理能力是 Edge LLM 部署的基础
- [[mnn-350]] — MNN 作为竞争方案，同样面临移动性挑战
