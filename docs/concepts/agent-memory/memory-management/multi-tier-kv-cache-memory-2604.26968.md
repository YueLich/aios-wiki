---
title: "Predictive Multi-Tier Memory Management for KV Cache in Large-Scale GPU Inference"
arXiv: 2604.26968
date: 2026-04-19
tags: [agent-memory, memory-management, kv-cache, inference-optimization]
reviewer: auto
source: arXiv API
---

## 核心贡献

本文解决大规模 GPU 推理中 **KV Cache 内存管理**这一核心瓶颈。当前系统存在三重低效：

1. **统一 KV Cache  sizing 缺失**：多-head 潜在注意力（MLA）等架构不支持，导致高达 57x 内存过度配置
2. **单内存层限制**：KV Cache 仅限 GPU HBM，未利用丰富层次（CPU DRAM、CXL、NVMe、RDMA、并行文件系统）
3. **反应式驱逐策略**：丢弃可重用状态，强制重新计算

**核心方案：**
- **架构感知 sizing 引擎**：精确计算每种注意力类型的内存需求，支持 MLA，最高 7.4x batch size 提升
- **六层内存层次结构**：KV Cache 有效容量从 40GB 扩展至 38TB+，热条目 TTFT 保持亚毫秒级
- **贝叶斯重用预测器**：16 种（块类型 × 转换类型）配对的 Beta 共轭先验，70-84% 缓存命中率

## 为什么重要

KV Cache 是大规模 GPU 推理服务中限制吞吐量和成本效率的主要瓶颈。随着 Agent  workloads 增长，内存管理优化直接决定系统能力上限。

## 与端侧/移动端相关性

- **成本降低 47%**：分析投影显示相比 SOTA 基线成本显著降低
- **TTFT 降低 1.4-2.1x**：首 token 时间改善对交互式应用至关重要
- **吞吐提升 1.7-2.9x**：更高效率利用硬件资源

## 技术细节

### 多-tier 内存管理
| 层级 | 容量 | 延迟 | 适用场景 |
|-----|------|-----|---------|
| GPU HBM | 40GB | 微秒 | 热数据 |
| CPU DRAM | TB级 | 亚毫秒 | 温数据 |
| CXL | 10TB+ | 毫秒 | 冷数据 |
| NVMe | 100TB+ | 十毫秒 | 归档 |

### 预测性驱逐
- Beta 共轭先验建模重用模式
- EMA-scored head-granular 驱逐
- RoPE-aware 预取

## 参考文献

（参考文献待从原文补充）
