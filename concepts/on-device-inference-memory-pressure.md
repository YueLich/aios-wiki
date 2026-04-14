---
type: concept
tags: [inference, memory, on-device, hardware, HBS, chiplet, NPU, 端侧推理, 内存优化]
related: [[edgecim-hardware-codesign]], [[kv-cache-quantization-ondevice]], [[edgeflow-cold-start]], [[llamacpp-b8791]], [[gemma4-ondevice]], [[sustainability-ondevice-intelligence]]
sources:
  - url: https://arxiv.org/abs/2604.11128v1
    title: "Technology solutions targeting the performance of gen-AI inference in resource constrained platforms"
    date: 2026-04-13
    reliability: high
  - url: https://arxiv.org/html/2604.11128v1
    title: "Full HTML version"
    date: 2026-04-13
    reliability: high
created: 2026-04-15
updated: 2026-04-15
---

# 端侧 Gen-AI 推理的内存压力与硬件解决方案

> IMEC 团队用层次化 Roofline 模型评估了两种新兴硬件技术（High Bandwidth Storage 和 SRAM 键合芯粒）对移动设备上 Gen-AI 推理性能的影响，量化了带宽/延迟需求以实现 10 TPS 的交互门槛。

## 核心问题

端侧 LLM 推理面临严峻的内存瓶颈：

- **模型权重**：Llama-7B FP16 需要 ~14GB 内存，超过智能手机标准 DDR 容量
- **KV Cache**：随上下文长度线性增长，多模态输入（图像/视频 token 化）进一步加剧
- **并发推理**：即使低并发度也会增加运行时内存管理复杂度
- **内存墙**：生成阶段 ops/bytes ~ O(1)，数据搬运成为主要瓶颈

现有算法级优化（KV Cache 驱逐、Flash 块访问、稀疏加载）能获得 2-20x 加速，但需要硬件层增强来突破天花板。

## 方法/架构

### 层次化 Roofline 性能分析框架

研究使用经验证的层次化 Roofline 框架，区别于单层内存模型：

```
内存层次：NPU Scratchpad → L2 → DDR → HBS（新增）
```

**核心机制**：将 GEMM/GEMV kernel（注意力计算、MLP 投影等）映射到架构上，通过搜索每个内存层级的最优 tiling 策略计算 kernel 延迟。算术强度（FLOPs/bytes）与硬件拐点比较判定 kernel 是内存受限还是计算受限。

**关键公式**：
```
time = max{ total_FLOPs/compute_throughput, data_traffic_volume/memory_throughput }
```

### 两种硬件方案

**方案一：High Bandwidth Storage（HBS）— 面向大模型（13B）**
- 传统 SSD/Flash 带宽远低于 DDR，HBS 带宽接近 DDR 但容量大几个数量级
- 延迟在微秒级别（vs DDR 的 100ns）
- 16 IO/平面，1-4 Gbps/IO 数据率，通过平面和列结构交错实现高吞吐
- 容量足以容纳模型权重、Q/K/V 矩阵和中间激活值

**方案二：SRAM 键合芯粒 — 面向小模型（1B）**
- 混合键合的 SRAM 缓冲芯粒，直接通过定制接口连接逻辑芯粒上的 NPU
- 灵感来自近存/内存计算研究
- 关键问题：SRAM 有限容量下存储什么最高效

## 实验结果/关键数据

### 实验配置
- 模型：LLaVa1.5-13B（单精度，多模态）
- 计算吞吐：35 TFLOPs（NPU 全部处理单元）
- 上下文长度：200/200、4096/12288、8192/24576
- 目标门槛：**10 TPS**（最低交互性要求）

### 核心结果表

| DDR 带宽 | HBS 带宽 | Q/K/V 存储位置 | 性能（TPS） | 瓶颈位置 | 加速比 |
|----------|---------|---------------|-----------|---------|-------|
| LPDDR6 (173 GB/s) | 16-173 GB/s | HBS | ~4 | HBS | baseline |
| LPDDR6 (173 GB/s) | 16-520 GB/s | HBS | ~5.5 | DDR | 1.4x |
| 3x LPDDR6 (520 GB/s) | 16-520 GB/s | HBS | ~8.9 | HBS | 2.2x |
| 3x LPDDR6 (520 GB/s) | 16-520 GB/s | Q,K,V在DDR | **~12.5** | HBS | **3.1x** |

### 关键发现

1. **HBS 延迟的隐藏影响**：即使 HBS 带宽略高于 DDR，微秒级延迟仍使其成为性能瓶颈。HBS 带宽需要至少 **40% 高于 DDR 带宽**才能让瓶颈转移到 DDR。

2. **Q/K/V 缓存策略**：将 Q、K、V 矩阵限制在 DDR 中传输（而非经过 HBS）可显著提升注意力执行时间（占总 GEMM 时间的 31-69%），使 10μs 延迟下仍能达到 10 TPS 目标。

3. **上下文长度影响**：类似趋势在 8192/24576 长上下文下仍然成立，但绝对 TPS 更低。

4. **小模型的芯粒策略**：对于 1B 参数模型，缓存 Q/K/V 的性能收益有限；**缓存 MLP 和投影层的权重矩阵**才是更高效的芯粒利用方式。

## 关键洞察

### 从算法到硬件的协同优化逻辑

这项研究揭示了端侧推理优化的层次化思路：

- **算法层**（已有）：KV Cache 驱逐、量化、稀疏注意力 → 2-20x
- **中间件层**（已有）：调度优化、异构 SoC 感知批处理 → 1.6-4.8x
- **硬件层**（本文）：HBS + 键合芯粒 → 突破内存墙

三层叠加是端侧部署 7B+ 模型的现实路径。

### HBS 的工程可行性

HBS 不需要全新的存储技术，而是将现有 Flash SSD 接口从 PCIe Gen5/6（16-32 GB/s）扩展到更高 IO 密度的平面架构。这在制造工艺上比 HBM 更容易实现，因为不需要 3D 堆叠，成本更接近传统 SSD。

### 大小模型的不同优化方向

| 维度 | 大模型（13B） | 小模型（1B） |
|------|-------------|------------|
| 主要瓶颈 | KV Cache 容量 | 计算效率 |
| 推荐方案 | HBS + DDR 分层 | SRAM 键合芯粒 |
| 关键优化 | Q/K/V 放 DDR，权重放 HBS | MLP 权重放芯粒 |
| 交互门槛 | 需要 3x LPDDR6 | DDR 单独即可 |

## 为什么重要

1. **端侧部署的硬件路线图**：首次系统量化了端侧 LLM 推理对下一代内存技术的带宽/延迟需求，为芯片设计提供了具体目标（HBS 带宽 > 40% LPDDR6）

2. **多模态推理的内存挑战**：LLaVa1.5-13B 的实验表明，多模态输入带来的长上下文使 KV Cache 压力远超纯文本场景，这对 Gemma 4、MiniCPM-V 等端侧多模态模型的部署有直接指导意义

3. **与现有优化的互补性**：KV Cache 量化（已有页面）、HBS 硬件增强可以叠加使用，量化减少容量需求，HBS 提供更大容量和带宽

4. **来自 IMEC 的权威性**：IMEC 是全球领先的半导体研究机构，其分析具有产业前瞻性

## 关联

- [[edgecim-hardware-codesign]] — EdgeCIM 从 CIM 角度解决端侧推理加速，本文从内存层次角度，两者互补
- [[kv-cache-quantization-ondevice]] — KV Cache 量化减少容量需求，与 HBS 方案可以叠加
- [[edgeflow-cold-start]] — EdgeFlow 解决冷启动延迟，本文解决稳态推理带宽
- [[llamacpp-b8791]] — llama.cpp 作为实际推理框架，其优化（如 Metal XIELU）可与硬件方案协同
- [[gemma4-ondevice]] — Gemma 4 作为端侧多模态模型代表，其部署直接受本文研究结果影响
- [[sustainability-ondevice-intelligence]] — 内存优化直接影响端侧推理的能耗，与性能-能耗权衡主题呼应
