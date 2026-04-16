---
type: entity
tags: [llama.cpp, ggml, inference, on-device, open-source, release]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8815]], [[llamacpp-b8809]], [[edgeflow-cold-start]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8816
    title: "llama.cpp b8816 Release"
    date: 2026-04-16
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# llama.cpp b8816

> ggml 底层图复用机制优化，持续迭代的端侧推理引擎

## 核心变更

### ggml: graph_reused (#21764)
本版本的核心变更是 ggml 计算图的复用机制改进：

- **图版本化替代复用标志**：从简单的 boolean 复用标志改为版本号管理
- **原子操作递增版本**：使用 atomic 操作保证多线程安全
- **分图编号使用高位**：版本号的高位用于 split graph 编号
- **uid 管理优化**：将计数器移至 ggml.c，仅在 split_graph 中设置 uid

这一改进优化了计算图的生命周期管理，对端侧推理的内存效率和图调度有正面影响。

### 平台支持
- **macOS/iOS**：arm64、x64、KleidiAI 启用版本、iOS XCFramework
- **Linux**：x64/arm64/s390x CPU、Vulkan、ROCm 7.2、OpenVINO 2026.0
- **Windows**：x64/arm64 CPU、Vulkan、DirectML

## 关键洞察

llama.cpp 持续高频迭代（b8815 → b8816 仅数小时），每次微改进都针对实际部署中的痛点。graph_reused 的版本化改造虽然看起来小，但对多模型并行推理和内存受限设备的图调度效率有实际价值。

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 的战略背景
- [[llamacpp-b8815]] — 前一版本
- [[edgeflow-cold-start]] — 冷启动优化，llama.cpp 的快速迭代支持此类上层优化
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化，依赖 ggml 底层改进
