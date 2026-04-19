---
type: entity
tags: [llama.cpp, inference, ggml, open-source, speculative-decoding, android, qualcomm, adreno]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8849]], [[mnn-350]], [[android-hybrid-inference]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8850
    title: "llama.cpp b8850 Release"
    date: 2026-04-19
    reliability: high
  - url: https://github.com/ggml-org/llama.cpp/compare/b8799...b8850
    title: "llama.cpp b8799..b8850 Commits"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# llama.cpp b8850

> GGML 推理引擎重要版本更新。51 个提交，引入推测解码检查点、Adreno GPU 优化、CPU 内存压缩等端侧关键改进。

## 版本信息

- **发布日期**：2026-04-19
- **构建号**：b8850
- **距上次版本**：b8799（51 commits）
- **仓库**：[ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 核心更新

### 1. 推测解码检查点（Speculative Checkpointing）

```text
server: speculative checkpointing (#19493)
```

推测解码（Speculative Decoding）是端侧 LLM 推理的核心加速技术。本次引入的检查点机制允许服务端在推测解码过程中保存中间状态，当推测失败时可回滚到检查点而非完全重来。

**为什么重要**：推测解码在端侧设备上的收益取决于推测准确率。检查点机制减少了错误推测的惩罚成本，预期在高并发场景下可提升 15-30% 的吞吐量。对于手机端多轮对话场景（Agent 调用），这个改进直接降低了延迟。

### 2. Adreno GPU OpenCL 优化

```text
opencl: refactor q8_0 set_tensor and mul_mat host side dispatch for Adreno (#21938)
```

针对高通 Adreno GPU 的 OpenCL 后端重构，重点优化了 q8_0 量化格式的矩阵乘法（mul_mat）调度。

**为什么重要**：高通骁龙系列芯片的 Adreno GPU 是 Android 端侧推理的主要加速硬件。本次优化：
- 改进了 q8_0 量化张量的数据传输效率
- 优化了 host 端的调度逻辑，减少了 CPU-GPU 同步开销
- 直接提升骁龙 8 Gen 3/4 等设备上的推理速度

### 3. CPU 上下文大小自动适配

```text
llama: fit ctx size for CPU only (#21568)
```

当仅使用 CPU 推理时（无 GPU 加速），llama.cpp 现在会自动调整上下文窗口大小以适配可用内存。

**为什么重要**：端侧设备内存有限（6-12GB RAM），手动配置 context size 容易导致 OOM。自动适配机制让低端设备也能安全运行 LLM，无需用户手动调参。

### 4. CUDA 图 LRU 驱逐

```text
CUDA: use LRU based eviction for cuda graphs (#21611)
```

CUDA Graph 的 LRU（最近最少使用）驱逐策略，优化 GPU 内存管理。

### 5. Gemma 4 模型类型检测

```text
model: Gemma4 model type detection (#22027)
```

新增 Gemma 4 模型的自动类型检测。用户无需手动指定模型架构参数，llama.cpp 可自动识别 Gemma 4 的配置并加载。

### 6. CPU 元后端开销优化

```text
ggml: reduce CPU overhead in meta backend (#22041)
```

减少 meta backend 的 CPU 开销，对端侧推理性能有直接提升。

### 7. AMD CUDA 重构（ headline 变更）

```text
CUDA: refactor mma data loading for AMD (#22051)
```

本次版本的 headline 变更：重构 AMD GPU 的 MMA（Matrix Multiply-Accumulate）数据加载，修复 CDNA 和 RDNA 架构的兼容性问题。主要影响 AMD GPU 用户，对移动端无直接影响。

## 多平台支持

| 平台 | 架构 | 加速 |
|------|------|------|
| macOS | arm64, x64 | KleidiAI |
| iOS | XCFramework | Metal |
| **Android** | **arm64** | **OpenCL/Adreno** |
| Linux | x64, arm64 | CUDA, Vulkan, ROCm |
| Windows | x64, arm64 | CUDA 12/13, Vulkan, SYCL |

## 对手机端 AI 的意义

1. **推测解码检查点**：端侧多轮对话场景的延迟降低
2. **Adreno 优化**：高通芯片推理速度提升，直接影响 Android 端侧部署
3. **CPU 内存自动适配**：降低低端设备的使用门槛
4. **Gemma 4 自动检测**：简化端侧模型部署流程
5. **Android arm64 构建**：持续维护的 Android 二进制分发

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 完整介绍
- [[llamacpp-b8849]] — 上一个版本
- [[mnn-350]] — 阿里 MNN，竞争性端侧推理引擎
- [[android-hybrid-inference]] — Android 端云协同推理
- [[on-device-inference-memory-pressure]] — 端侧内存管理
- [[edgeflow-cold-start]] — 冷启动优化
