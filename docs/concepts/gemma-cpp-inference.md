---
type: concept
tags: [inference, on-device, cpp, google, gemma, cpu, lightweight]
related: [[llama-cpp]], [[mnn]], [[gemma-4-google]], [[gemma4-ondevice]]
sources:
  - url: https://github.com/google/gemma.cpp/releases/tag/v0.1.4
    title: "gemma.cpp v0.1.4 release"
    date: 2025-03-25
created: 2026-04-14
---

# gemma.cpp — Google Gemma 轻量级 C++ 推理引擎

## 概述

gemma.cpp 是 Google 推出的 Gemma 模型专用 C++ 推理实现，设计目标是极简依赖、直接高效地运行 Gemma 系列模型。与 [[llama-cpp]] 的通用性不同，gemma.cpp 专注于 Gemma 架构的极致优化。

## v0.1.4 更新内容

- **Gemma 构造函数重构**：改进 NUMA 内存池支持，优化多核 CPU 场景下的推理性能
- **修复 Gemma3-1B 提示词包装**：小模型的 prompt 处理更准确
- **辅助 EOS token 支持**：支持 Gemma2 的 secondary EOS token，提升生成终止精度
- **注意力长度与 SFP 说明文档**

## 技术特点

1. **零依赖设计**：不依赖 PyTorch/TensorFlow，纯 C++ 实现
2. **NUMA 优化**：针对服务器和高端工作站的多 NUMA 节点内存架构做了优化
3. **KleidiAI 集成**：macOS 版本支持 ARM KleidiAI 加速
4. **Gemma 全系列支持**：Gemma 1/2/3 均可推理

## 为什么重要

gemma.cpp 是端侧 Gemma 推理的"原生"方案：
- Google 官方维护，保证与 Gemma 模型演进同步
- 极小的二进制体积，适合嵌入式和移动场景
- 与 [[llama-cpp]] 形成互补：llama.cpp 胜在通用性，gemma.cpp 胜在 Gemma 专用优化
- 是构建 [[mobile-aios-overview]] 中轻量推理层的重要候选方案

## 关联

- [[llama-cpp]] — 竞争/互补方案，通用性更强
- [[mnn]] — 阿里巴巴的端侧推理框架
- [[gemma4-ondevice]] — 可通过 gemma.cpp 推理的端侧模型
- [[edgeflow-cold-start]] — 冷启动优化与推理框架紧密相关
