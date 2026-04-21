---
type: entity
tags: [CMake, CPU优化, GGML, GitHub, Intel GPU, MSVC, RPC, SYCL, WebGPU, activation, adreno, android, apple-silicon, backend, cross-platform, framework, gemma4, ggml, gpu, gpu-acceleration, hexagon, iOS, inference, inference-engine, ios, kleidiai, llama-cpp, llama.cpp, macOS, macos, metal, mobile, model-detection, on-device, open-source, opencl, optimization, qualcomm, quantization, release, speculative-decoding, vulkan, xielu, 子图缓存, 库重构, 开源, 推理优化, 推理引擎, 推理框架, 热修复, 端侧推理, 端侧部署, 跨平台]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[coremltools-9]]
sources:
  - https://github.com/ggml-org/llama.cpp/releases
created: 2026-04-14
updated: 2026-04-2120
---

# llama.cpp 版本追踪

llama.cpp 持续快速迭代，本页汇总各 build 的重要变更。最新版本在最上方。

共追踪 28 个版本（b8791 ~ b8854）。



### Build 8854
## 发布信息

- **版本**: b8854
- **发布日期**: 2026-04-20
- **仓库**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 主要变更

### 服务器重构
- **server: refactor "use checkpoint" logic (#22114)** — 重构服务端的 checkpoint 使用逻辑，使代码结构更清晰，为后续推测解码（speculative decoding）的进一步优化铺路。

### 平台支持

| 平台 | 包格式 |
|------|--------|
| macOS Apple Silicon (arm64) | 原生 + KleidiAI 变体 |
| macOS Intel (x64) | 原生 |
| iOS | XCFramework |
| Linux x64/arm64 | CPU/ROCm |

## 为什么重要

b8854 是一个**代码质量改进**版本，不涉及功能变更但提升了代码可维护性。重构 checkpoint 逻辑使推测解码的错误回滚路径更清晰，降低了后续修改引入 bug 的风险。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 的 GGML 生态
- [[coremltools-9]] — Apple Core ML 工具链
- [[on-device-inference-memory-pressure]] — 推测解码减少推理内存压力


### Build 8853
## 发布信息

- **版本**: b8853
- **发布日期**: 2026-04-20
- **仓库**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 主要变更

### SYCL 修复
- **[SYCL] Fix reorder MMVQ assert on unaligned vocab sizes (#22035)** — 修复 Intel GPU (SYCL) 后端在词表大小不是 16 的倍数时的断言失败。Q4_0, Q8_0, Q4_K, Q6_K 的 reorder mul_mat_vec_q 调度器原先要求 block_num_y 是 16 个子组的倍数，导致 HY-MT 等词表大小为 120818 的模型在加载时崩溃。修复方案：将 assert 改为 padding，block_num_y 向上取整到子组大小的整数倍。对齐词表的模型无性能回退。

### 平台支持

| 平台 | 包格式 |
|------|--------|
| macOS Apple Silicon (arm64) | 原生 + KleidiAI 变体 |
| macOS Intel (x64) | 原生 |
| iOS | XCFramework |
| Linux x64/arm64 | CPU/ROCm |

## 为什么重要

b8853 修复了一个影响**特定模型在 Intel GPU 上运行**的严重 bug。对于使用 SYCL 后端在 Intel Arc/集成显卡上运行 LLM 的用户，某些词表大小非对齐的模型（如 HY-MT，词表 120818）之前会直接崩溃。修复后这些模型可以正常加载和推理。这也体现了 llama.cpp 在跨平台兼容性方面的持续投入——确保不仅是 NVIDIA/AMD GPU，Intel GPU 也能稳定运行端侧推理。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 的 GGML 生态
- [[edge-llm-handover]] — Edge LLM 部署需要稳定的多平台推理后端


### Build 8852
## 发布信息

- **版本**: b8852
- **发布日期**: 2026-04-20
- **仓库**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 主要变更

### 命名规范化
- **server: rename --clear-idle to --cache-idle-slots (#21741)** — 服务器命令行参数重命名，使选项名称更准确地反映其功能（管理空闲缓存槽位而非"清除空闲"）。

### 平台支持

| 平台 | 包格式 |
|------|--------|
| macOS Apple Silicon (arm64) | 原生 + KleidiAI 变体 |
| macOS Intel (x64) | 原生 |
| iOS | XCFramework |
| Linux x64/arm64 | CPU/ROCm |

## 为什么重要

b8852 是一个**API 清理**版本。`--clear-idle` 改名为 `--cache-idle-slots` 使参数语义更明确，对于使用 llama.cpp HTTP 服务器的端侧部署脚本，需要更新启动参数。这是典型的 breaking change 小版本——无性能影响但需注意兼容性。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 的 GGML 生态
- [[mnn-350]] — MNN 也有类似的缓存管理机制


### Build 8851
## 发布信息

- **版本**: b8851
- **发布日期**: 2026-04-19
- **仓库**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 主要变更

### 依赖更新
- **cpp-httplib 升级至 0.42.0** — HTTP 服务器库更新，可能包含安全修复和性能改进。llama.cpp 的内置 HTTP 服务器（用于 API 推理）依赖此库。

### 平台支持

| 平台 | 包格式 |
|------|--------|
| macOS Apple Silicon (arm64) | 原生 + KleidiAI 变体 |
| macOS Intel (x64) | 原生 |
| iOS | XCFramework |
| Linux x64/arm64/s390x | CPU/Vulkan/ROCm/OpenVINO |
| Android | 原生 |

## 为什么重要

b8851 是一个**维护性更新**，核心变化是依赖库版本升级。cpp-httplib 0.42.0 的更新可能修复了 HTTP 处理中的边缘情况或安全问题，对于运行 llama.cpp HTTP 推理服务的生产环境有实际价值。

对于手机端 AIOS，llama.cpp 持续保持每周 2-3 个版本的迭代速度，表明端侧 LLM 推理生态的活跃度。b8851 距离 b8850 仅一天，说明项目采用**持续集成 + 频繁发布**的策略，新功能和修复能够快速到达用户手中。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 的 GGML 生态和 HuggingFace 集成
- [[coremltools-9]] — Apple 平台的 Core ML 工具链与 llama.cpp iOS 部署互补
- [[mnn-350]] — Alibaba 的端侧推理引擎，与 llama.cpp 在移动端形成竞争
- [[edgeflow-cold-start]] — llama.cpp 的快速加载能力支持冷启动优化
- [[on-device-inference-memory-pressure]] — llama.cpp 的量化能力直接缓解内存压力


### Build 8850
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
- [[llamacpp]] — 上一个版本
- [[mnn-350]] — 阿里 MNN，竞争性端侧推理引擎
- [[android-hybrid-inference]] — Android 端云协同推理
- [[on-device-inference-memory-pressure]] — 端侧内存管理
- [[edgeflow-cold-start]] — 冷启动优化


### Build 8849
## 版本信息

- **发布日期**：2026-04-19
- **构建号**：b8849
- **仓库**：[ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 本次更新

```
common/autoparser: allow space after tool call (#22073)
```

这是一个小幅改进版本，主要修复了 tool call 解析中空格处理的问题。在 Agent 系统中，LLM 输出的 tool call 格式可能存在尾随空格，此修复提升了工具调用的鲁棒性。

## 多平台支持

llama.cpp 持续为端侧推理提供最广泛的平台覆盖：

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | arm64, x64 | Apple Silicon + Intel |
| iOS | XCFramework | 移动端完整支持 |
| Android | arm64 | 手机端推理核心 |
| Linux | x64, arm64, s390x | 服务器/边缘 |
| Windows | x64, arm64 | CUDA 12/13, Vulkan, SYCL |
| openEuler | x86 | 310p, 910b ACL Graph |

### 硬件加速选项
- **CUDA**: 12.4, 13.1
- **Vulkan**: 跨平台 GPU 推理
- **ROCm 7.2**: AMD GPU
- **OpenVINO**: Intel 推理优化
- **KleidiAI**: macOS ARM 优化
- **SYCL**: Intel oneAPI
- **HIP**: AMD Radeon

## 对手机端 AI 的意义

1. **Android arm64 构建**：直接可用于 Android 端侧 LLM 部署
2. **iOS XCFramework**：Swift/SwiftUI 项目可直接集成
3. **Tool Call 改进**：Agent 系统中工具调用的可靠性提升，对端侧 Agent 至关重要
4. **KleidiAI 支持**：Apple Silicon 上的推理加速，对 macOS/iOS 端侧部署有直接影响

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 的完整介绍和使用指南
- [[mnn-350]] — 阿里 MNN，另一个端侧推理引擎
- [[minicpm-242]] — MiniCPM 模型可使用 llama.cpp 推理
- [[on-device-inference-memory-pressure]] — 端侧推理的内存压力管理
- [[edgeflow-cold-start]] — 端侧推理引擎的冷启动优化


### Build 8846
## 核心优化

### 子图分裂缓存（#22041）

当连续使用相同的 `ggml_cgraph` 时，`ggml_backend_meta_graph_compute` 中的子图构建是重复且不必要的开销。b8846 引入了缓存机制：

- **缓存子图分裂结果**：当 `cgraph` 未变化时，跳过逐次的子图构建
- **UID 分配**：为每个子图分配唯一标识符，使 CUDA 的快速 UID 检查路径也能命中
- **对端侧推理的意义**：减少 CPU 开销直接降低手机端推理延迟和功耗

### 为什么重要

GGML meta backend 是 llama.cpp 在 CPU（包括手机和嵌入式设备）上运行时的核心调度层。每次推理调用的子图构建带来固定 CPU 开销，即使计算图完全相同。这个优化在批量推理或连续对话场景中效果尤为明显——计算图不变时，开销趋近于零。

对端侧部署而言，这意味着：
- 手机 CPU 推理的吞吐量提升
- 功耗敏感场景（后台推理、长对话）的电池续航改善
- 为后续更多 meta backend 优化铺路（批量调度、异构加速）

## 相关变更

- 代码评审后进行了多次重构：重命名 `last_uid` 和 `last_n_subgraphs` 字段，移除 `last_max_tmp_size`
- 合作者：Johannes Gäßler

## 构建版本

- macOS Apple Silicon (arm64) + KleidiAI 变体
- iOS XCFramework
- Linux Ubuntu x64/arm64
- Windows x64

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 的核心技术栈（GGML + HuggingFace 生态）
- [[mnn-350]] — 阿里端侧推理框架，同类竞品
- [[on-device-inference-memory-pressure]] — 端侧推理的内存压力管理
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化，互补优化方向


### Build 8843
## 修复内容

- **#21630 的副作用**：添加 CMP0194 NEW 策略消除 CMake 4.1+ 警告，但在 Windows runner 上导致 MinGW 工具链被优先选择
- **修复方式**：仅回滚 CMP0194 策略块，保留 #21630 的其他改进
- **权衡**：CMake 4.1+ 警告回归，但仅是外观问题，不破坏任何平台

## 可用构建

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | Apple Silicon (arm64) | 含 KleidiAI 版本 |
| macOS | Intel (x64) | — |
| iOS | XCFramework | — |
| Linux | x64/arm64/s390x | CPU/Vulkan/ROCm/OpenVINO |
| Android | arm64 | CPU |
| Windows | x64/arm64 | CPU/CUDA 12/CUDA 13/Vulkan/SYCL |

## 为什么重要

llama.cpp 是端侧 LLM 推理的基础设施级项目，Windows 构建失败直接影响大量开发者。b8843 作为热修复确保了跨平台可用性。连续的构建发布（b8841→b8842→b8843 在同一天内）也反映了项目对 Windows 生态的重视。

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 的 GGUF 生态全貌
- [[mnn-350]] — 阿里 MNN 是另一个端侧推理引擎选项
- [[coremltools-9]] — Apple Core ML 工具链与 iOS XCFramework 构建互补


### Build 8841
## 核心变更

本次更新聚焦于 **RPC（远程过程调用）传输层的架构重构**，主要改动：

1. **传输层解耦**：将所有 RPC 传输相关代码移入独立文件 `rpc-transport.cpp/.h`，实现关注点分离
2. **Socket 抽象**：引入 `socket_t` 接口封装底层 socket 操作，隐藏平台实现细节（POSIX/Win32）
3. **跨平台兼容**：修复了 Win32 平台下的 socket 处理问题

### 技术意义

RPC 是 llama.cpp 实现 **分布式推理** 的核心组件——允许将模型推理任务分发到远程设备执行。对于移动端 AI 场景，这意味着：

- **手机作为 RPC 客户端**：手机端可将大型模型推理请求发送到边缘服务器或本地 GPU 设备
- **多设备协同**：重构后的架构更易于支持新传输协议（如 BLE、WiFi Direct）
- **架构可维护性**：`socket_t` 抽象为未来支持 QUIC、WebRTC 等现代传输协议铺平道路

## 可用构建

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | arm64 / x64 | 含 KleidiAI 启用版本 |
| iOS | XCFramework | 移动端推理核心构建 |
| Android | arm64 | 端侧推理关键构建 |
| Ubuntu | x64 / arm64 / s390x | CPU/Vulkan/ROCm/OpenVINO 变体 |
| Windows | x64 | CPU/CUDA/Vulkan 变体 |

## 为什么重要

虽然本次变更主要是内部重构而非功能更新，但它反映了 llama.cpp 团队在 **生产级工程质量** 上的持续投入。对于依赖 llama.cpp 作为端侧推理后端的项目（MNN 集成、Core ML bridge、Android 部署），稳定的传输层是分布式推理可靠性的基础保障。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 上游项目概述与 GGUF 格式介绍
- [[mnn-350]] — 阿里 MNN 推理框架，同为端侧推理选择
- [[coremltools-9]] — Apple Core ML 工具链，iOS 端 llama.cpp 的替代/互补方案
- [[on-device-inference-memory-pressure]] — 端侧推理的内存管理挑战


### Build 8840
## 核心更新

- **服务器 API**: 在 `/props` 端点暴露 `media_tag` 字段（PR #22028），增强了多媒体模型支持的元数据查询能力

## 平台支持

- **macOS**: Apple Silicon (arm64) + KleidiAI 加速变体、Intel x64
- **iOS**: XCFramework 包
- **Linux**: Ubuntu x64/arm64/s390x、Vulkan、ROCm 7.2、OpenVINO

## 为什么重要

b8840 虽然是小幅更新，但 `media_tag` 的暴露意味着 llama.cpp 正在加强对多模态模型（视觉+语言）的服务端支持。对于依赖 llama.cpp 做端侧推理的移动应用来说，多模态能力的完善是关键里程碑。

从 b8783 到 b8840（过去几周内 20+ 个版本），项目保持了极高的迭代速度，持续优化端侧推理性能。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 的 GGML 格式背景与量化体系
- [[mnn-350]] — 阿里 MNN，另一个主流端侧推理框架
- [[coremltools-9]] — Apple Core ML 工具链，与 llama.cpp iOS 部署互补


### Build 8839
## 核心变更

- **模型层重构 (#22079)**: 重构 bias tensor 变量命名，统一 jina-bert-v2 等模型中 `create_tensor_qkv` 的使用方式。这是纯内部重构，不改变 API 或推理行为，但提升了代码可维护性。

## 平台支持

本版本继续提供完整的跨平台构建：

| 平台 | 构建 |
|------|------|
| macOS/iOS | arm64, x64, KleidiAI, XCFramework |
| Linux | x64/arm64/s390x CPU, Vulkan, ROCm 7.2, OpenVINO |
| Android | arm64 CPU |
| Windows | x64/arm64 CPU, CUDA 12/13, Vulkan, SYCL, HIP |
| openEuler | 310p, 910B |

## 关键洞察

llama.cpp 保持极高的迭代频率（从 b8838 到 b8839 仅 1 个 commit），说明项目处于活跃维护状态。对于移动端 AIOS 开发者而言：

1. **iOS XCFramework**: 持续提供 iOS 原生集成支持，是 Core ML 之外的重要端侧推理选项
2. **Android arm64**: 直接可用的 Android 预编译二进制，降低端侧部署门槛
3. **KleidiAI 构建**: 针对 ARM 架构优化的推理路径，对移动端性能至关重要

## 为什么重要

llama.cpp 是端侧 LLM 推理的事实标准引擎。本版本虽为小幅重构，但体现了：
- 代码质量持续优化（变量命名规范化）
- 全平台覆盖无死角（iOS/Android/Linux/Windows 均有预编译包）
- 生态系统稳定（MNN、coremltools 等竞品/互补方案也在同步迭代）

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 主页与生态概述
- [[llamacpp]] — 前一版本，主要包含模型支持更新
- [[mnn-350]] — 阿里 MNN，另一端侧推理框架
- [[coremltools-9]] — Apple Core ML 工具链，llama.cpp XCFramework 的替代/互补方案


### Build 8838
## 版本概要

b8838 是 b8836 的增量更新，主要包含两项改进：

### 1. Android 构建模块化 (#22076)

将 Android 端的 `libcommon` 库重构为独立的 `libllama-common`。这一改动的核心意义在于：

- **解耦公共依赖**：Android 端推理库的公共代码（日志、配置、内存管理等）现在作为独立模块编译，避免与主推理库（libllama）的链接冲突
- **减小 APK 体积**：多个 Android 应用可以共享同一个 `libllama-common`，减少重复代码
- **简化集成流程**：开发者在 Android 项目中集成 llama.cpp 时，依赖关系更清晰

这对[[mnn-350]]等其他端侧推理框架的 Android 集成方案具有参考价值——模块化构建是大规模跨平台项目持续维护的基础。

### 2. 后端多段张量读取 (#22063)

`ggml-backend-meta` 新增 `get_tensor` 的多段读取（multi-segment read）支持。技术细节：

- 允许单次 `get_tensor` 调用从多个非连续内存段读取数据
- 适用于张量在内存中分段存储的场景（如碎片化的模型文件、分布式加载）
- 对端侧推理的内存优化有潜在价值——支持更灵活的内存布局

## 平台支持

b8838 继续提供全平台预编译二进制：
- **macOS**：Apple Silicon (arm64)、Intel (x64)、KleidiAI 增强版
- **Linux**：Ubuntu x64/arm64/s390x、Vulkan、ROCm 7.2、OpenVINO
- **Android**：arm64 (CPU)
- **iOS**：XCFramework
- **Windows**：x64/arm64 (CPU)、CUDA 12

## 为什么重要

虽然 b8838 是增量版本，但 Android 构建模块化体现了 llama.cpp 在移动端持续投入的信号。随着[[ggml-llamacpp-hf]]生态的成熟，构建系统的工程化质量直接影响第三方应用的采纳速度。

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 生态概览
- [[llamacpp]] — 上一版本
- [[mnn-350]] — 阿里 MNN 端侧推理框架
- [[vllm-mlx-apple-silicon]] — vLLM + MLX Apple Silicon 方案


### Build 8837
## 基本信息

- **项目**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)
- **版本**: b8837
- **类型**: 推理框架构建版本
- **关键变更**: ggml-backend-meta 多段读取支持

## 主要更新

### ggml-backend-meta: 多段读取支持

此版本在 `ggml-backend-meta` 中新增了 `get_tensor` 的多段读取（multi-segment read）支持（PR #22063）。

这改进了元数据后端的张量获取机制，允许从多个数据段中读取张量数据，对于分段存储的模型文件更加高效。

## 可用构建

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | Apple Silicon (arm64) | 标准构建 |
| macOS | Apple Silicon (arm64) | KleidiAI 启用 |
| macOS | Intel (x64) | — |
| iOS | XCFramework | 移动端集成 |
| Linux | x64 (CPU) | — |
| Linux | arm64 (CPU) | — |

## 版本关系

- 前序版本: [b8836](llamacpp-b8836.md), [b8833](llamacpp-b8833.md)
- 后续版本: b8838, b8839
- 项目主页: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 对端侧部署的意义

持续的后端改进确保了 llama.cpp 在各种平台（特别是 iOS/Android）上的模型加载效率。多段读取支持对于移动设备上常见的分段下载/存储策略尤其有价值。

## 参考链接

- [GitHub Release](https://github.com/ggml-org/llama.cpp/releases/tag/b8837)
- [PR #22063](https://github.com/ggml-org/llama.cpp/pull/22063)


### Build 8836
## 版本概要

b8836 是一个维护性版本，变更内容集中在 CI/CD 流程：

- **核心变更**：释放 ROCm 发布流程中的磁盘空间（#22012）
- 无功能性代码变更

## 平台支持

延续全平台预编译策略：

| 平台 | 变体 |
|------|------|
| macOS Apple Silicon | CPU, KleidiAI 加速 |
| macOS Intel | CPU |
| iOS | XCFramework |
| Linux x64 | CPU, Vulkan, ROCm 7.2, OpenVINO |
| Linux arm64 | CPU, Vulkan |
| Linux s390x | CPU |
| Android arm64 | CPU |
| Windows x64 | CPU, CUDA 12 |
| Windows arm64 | CPU |

## 关键洞察

**持续高频迭代**：从 b8831 到 b8836 仅 5 个构建版本，体现了 llama.cpp 的极高迭代频率。这种日级发布节奏保证了端侧推理引擎能快速吸收社区贡献。

**ROCm 7.2 支持**：AMD ROCm 7.2 预编译版本的提供，意味着 AMD GPU 推理生态在 llama.cpp 中的成熟度提升，为 Linux 端侧推理提供了更多硬件选择。

## 为什么重要

llama.cpp 作为端侧 LLM 推理的核心引擎，每个版本都确保了最新模型的快速适配。对手机端 AIOS 而言，iOS XCFramework 和 Android arm64 的持续预编译保证了端侧部署的可用性。

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 的生态整合
- [[llamacpp]], [[llamacpp]] — 近期版本对比
- [[mnn-350]] — 阿里 MNN 推理引擎，同为端侧推理竞争者
- [[vllm-mlx-apple-silicon]] — vLLM-MLX 在 Apple Silicon 的高性能推理


### Build 8833
## 核心问题
llama.cpp 的 WebGPU 后端存在编译器警告和 FlashAttention 精度问题，影响在浏览器和跨平台环境下的推理稳定性。

## 方法/架构

### 主要变更
1. **ggml-webgpu 编译器修复**: 消除参数类型转换警告，重构代码结构
2. **FlashAttention 重构**: 
   - 修复 soft_max 精度问题
   - 将 reg_tile 累积升级到 f32 精度以改善数值稳定性
   - 重构 FlashAttention 编码逻辑
3. **Vulkan 后端稳定性**: 修复退出时的 segfault 问题
4. **NVIDIA 精度**: 尝试提高除法精度（已回退，待后续修复）

### 跨平台支持
- **macOS**: Apple Silicon (arm64) + KleidiAI 加速版 + Intel x64
- **iOS**: XCFramework 包
- **Linux**: Ubuntu x64/arm64 CPU 版本

## 实验结果
本次更新主要是 bug 修复和精度优化，无新的性能基准。FlashAttention f32 累积精度可能改善长序列推理的数值稳定性。

## 关键洞察

### WebGPU 对端侧的意义
WebGPU 是浏览器端推理的关键后端。llama.cpp 持续维护 WebGPU 后端意味着：
- 在 Chrome/Safari 中运行 LLM 成为可能
- 不需要安装原生应用，网页即可使用 AI
- 这对 Progressive Web App (PWA) 形式的 AI 助手至关重要

### FlashAttention 精度升级
reg_tile 累积从低精度升级到 f32，虽然会略微增加计算量，但能避免：
- 长上下文推理时的数值溢出
- 量化模型 + FlashAttention 组合的精度退化
- 这对端侧运行长上下文模型（如 RAG 场景）很重要

## 为什么重要
llama.cpp 是端侧 LLM 推理的事实标准引擎。每次更新都在改善跨平台兼容性和推理精度，直接影响手机、浏览器、嵌入式设备上的 AI 体验。WebGPU 后端的持续维护让"浏览器即 AI 运行时"成为现实。

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 的 GGML 格式与 HuggingFace 生态
- [[mnn-350]] — 阿里的 MNN 推理框架，llama.cpp 的竞争对手
- [[coremltools-9]] — Apple Core ML 工具链，llama.cpp 的 macOS/iOS 替代方案
- [[qwen36-35b-a3b]] — Qwen3.6 MoE 模型，可用 llama.cpp 运行


### Build 8831
## 核心更新

### Android arm64 官方构建（#21647）
b8831 最重要的变化是 **CI 新增 Android arm64 构建和发布流程**。此前，Android 用户需要自行交叉编译或依赖社区构建。现在可以直接下载预编译的 `llama-b8831-bin-android-arm64.tar.gz`。

这对手机端 AIOS 意义重大：
- **降低部署门槛**：开发者不再需要配置 NDK 交叉编译环境
- **标准化二进制**：官方构建经过 CI 测试，质量有保障
- **持续更新**：每次 release 自动构建，用户始终能获取最新版本

### 全平台支持矩阵

| 平台 | 架构 | 加速后端 |
|------|------|---------|
| macOS | arm64, x64 | Metal, KleidiAI |
| iOS | XCFramework | Metal |
| Linux | x64, arm64, s390x | CPU, Vulkan, ROCm 7.2, OpenVINO |
| **Android** | **arm64** | **CPU** |
| Windows | x64, arm64 | CPU, CUDA 12.4, CUDA 13.1, Vulkan, SYCL, HIP |

### 其他改进
- server: 修复 ignore_eos 标志未被尊重的问题
- pin android-setup actions 到 v4（CI 稳定性）

## 为什么重要

1. **Android 官方支持是信号**：ggml-org 正式将 Android 作为一等公民平台，意味着手机端 LLM 推理从"社区hack"变为"官方支持"
2. **端到端部署路径成熟**：从模型量化（GGUF）→ 二进制下载 → Android App 集成，全链路可用
3. **生态协同**：配合 MNN、CoreML、TensorRT 等其他推理框架，llama.cpp 在 CPU 推理场景（尤其是 ARM 设备）保持领先

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 与 HuggingFace 生态整合
- [[mnn-350]] — 阿里 MNN 推理框架，同为端侧推理选择
- [[minicpm-242]] — MiniCPM 模型可在 llama.cpp 上运行
- [[gemma4-ondevice]] — Gemma 4 等模型的端侧部署


### Build 8829
## 发布信息

- **版本**: b8829
- **发布日期**: 2026-04-17
- **仓库**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 核心变更

### libcommon → libllama-common 重命名

本次发布的主要变更是库重命名重构（#21936）：

- `libcommon` 重命名为 `libllama-common`
- 新增 `libllama-common-base` 子库
- CMake 配置允许共享库构建
- 添加 `-fPIC` 编译标志以支持位置无关代码
- 导出所有符号（export all symbols）
- 添加 `common_log_get_verbosity_thold()` API
- 修复 build_info 导出问题

### KleidiAI 支持

macOS arm64 构建新增 KleidiAI 启用版本，为 Arm 架构提供优化的推理加速。

### 平台支持

- macOS (Apple Silicon arm64 + KleidiAI / Intel x64)
- iOS XCFramework
- Linux (Ubuntu x64/arm64/s390x, Vulkan, ROCm 7.2, OpenVINO)
- Windows (x64/arm64, CPU/CUDA/Vulkan)

## 关键洞察

- 这是一个**重构型发布**，不包含新功能但改善了库结构
- `libllama-common` 的命名更清晰，表明 common 组件正在成为 llama.cpp 生态的正式基础设施
- KleidiAI arm64 构建对 **iPhone/iPad 端侧推理** 有直接价值
- ROCm 7.2 和 OpenVINO 2026.0 支持保持了多硬件后端覆盖

## 为什么重要

库重构虽然不直接影响终端用户，但对下游项目（MNN、MLC-LLM 等）的集成有长期影响。清晰的库边界使 llama.cpp 更适合作为基础推理层被其他框架依赖。

## 关联

- [[ggml-llamacpp-hf]] — GGML 与 HuggingFace 的合作，llama.cpp 生态的整体定位
- [[llamacpp]] — 前一个版本
- [[llamacpp]] — 近期版本系列
- [[gemma-cpp-inference]] — gemma.cpp 基于 GGML 的推理实现


### Build 8828
## 核心更新

本次发布的焦点是 PR #22027：**Gemma4 模型类型检测**。这是一个看似微小但对端侧生态意义重大的修复。

### 技术细节

- **模型类型自动识别**：新增 Gemma4 31B 和 26BA4B（26B 激活参数，4B 模型分片）两种变体的类型检测逻辑
- **纯展示性修复**：不改变推理行为，修正 `llama-bench`、`llama-server` 等工具中 Gemma4 模型的参数量显示
- **代码改动极小**：仅修改 2 个文件，+7/-1 行 — 说明是精准的元数据修补而非大规模重构
- **覆盖两种 Gemma4 变体**：
  - **Gemma4 31B**：完整参数量 31B 的模型
  - **Gemma4 26BA4B**：MoE 风格架构，26B 激活参数，4B 分片大小

### 平台支持

b8828 继续提供全面的跨平台二进制分发，与 b8827 一致：

| 平台 | 变体 |
|------|------|
| macOS | arm64, arm64 KleidiAI, x64 |
| iOS | XCFramework |
| Linux | x64/arm64/s390x CPU, Vulkan, ROCm 7.2, OpenVINO |
| Windows | x64/arm64 CPU, CUDA 12/13, Vulkan, SYCL, HIP |
| openEuler | 310p, 910b ACL Graph |

## 为什么重要

对手机端 AIOS 生态而言：

- **Gemma4 是 Google 端侧 LLM 主力**：Google 正将 Gemma4 作为 on-device AI 核心模型推广，llama.cpp 作为最流行的本地推理框架，Gemma4 支持的完善程度直接影响开发者体验
- **模型类型检测是工具链基础**：错误的参数量显示会导致 benchmark 失真、资源预估错误、量化配置不匹配 — 这些在端侧资源受限的设备上尤为关键
- **26BA4B 的特殊架构需要显式支持**：MoE 风格的 Gemma4 变体在端侧推理时的内存占用和延迟特性与 dense 31B 完全不同，自动检测确保工具链能正确区分
- **从 b8827 的 OpenCL Adreno 到 b8828 的 Gemma4 支持**：llama.cpp 在移动端推理上的迭代速度持续保持高位

## 关联

- [[llamacpp]] — 前一个版本，OpenCL Adreno GPU 调度重构
- [[gemma4-ondevice]] — Gemma4 端侧部署的详细概述
- [[ggml-llamacpp-hf]] — GGML 与 llama.cpp 加入 HuggingFace 的生态概述
- [[gemma-cpp-inference]] — Google 官方的 Gemma C++ 推理实现


### Build 8827
## 核心更新

本次发布的亮点是 PR #21938：**OpenCL q8_0 set_tensor 和 mul_mat 主机端调度重构**，专门针对 Adreno GPU（Qualcomm Snapdragon 系列）。

### 技术细节

- **q8_0 GEMM/GEMV Adreno 调度重构**：重新设计了 q8_0 量化格式在 Adreno GPU 上的矩阵乘法（GEMM）和矩阵向量乘法（GEMV）的主机端分发逻辑
- **set_tensor 优化**：改进了张量数据在 GPU 内存中的布局和传输方式
- **代码质量**：修复空白符问题，提升代码一致性

### 平台支持

b8827 继续提供全面的跨平台二进制分发：

| 平台 | 变体 |
|------|------|
| macOS | arm64, arm64 KleidiAI, x64 |
| iOS | XCFramework |
| Linux | x64/arm64/s390x CPU, Vulkan x64/arm64, ROCm 7.2, OpenVINO |
| Windows | x64/arm64 CPU, CUDA 12 |

## 为什么重要

对手机端 AIOS 生态而言：

- **Qualcomm Adreno 是 Android 主流 GPU**：几乎所有 Snapdragon 芯片都使用 Adreno GPU，此次重构直接影响数十亿 Android 设备的端侧推理性能
- **q8_0 是移动端常用量化格式**：相比 FP16 减半内存占用，同时保持较高精度，是端侧 LLM 推理的主力格式
- **OpenCL 是跨厂商 GPU 标准**：不依赖 Vulkan 或 CUDA，可在 Qualcomm/Mali/PowerVR 等多种移动 GPU 上运行
- **从 b8783 到 b8827 持续迭代**：44 个版本的快速迭代说明 llama.cpp 团队对移动端 GPU 支持的持续投入

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 母项目概述，本次更新是其 OpenCL 移动端能力的延续
- [[mnn-350]] — MNN 同样提供 Adreno GPU 支持，两者在移动端推理领域形成互补
- [[coremltools-9]] — Apple 端侧推理工具链，与 llama.cpp 的 iOS XCFramework 分发形成对比
- [[edgeflow-cold-start]] — 优化后的 OpenCL 后端可减少冷启动时的 GPU 初始化延迟


### Build 8816
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
- [[llamacpp]] — 前一版本
- [[edgeflow-cold-start]] — 冷启动优化，llama.cpp 的快速迭代支持此类上层优化
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化，依赖 ggml 底层改进


### Build 8815
## 更新内容

### Metal: 实现 ROLL 算子 (#21946)
- 在 Metal 后端新增 `ROLL` 操作的 GPU 实现
- 对 Apple Silicon 设备的推理性能有直接提升
- ROLL 操作在张量操作中用于序列位置变换，对注意力机制实现有辅助作用

### Unix: 支持统一 Apple SDK
- 支持 Apple 统一 SDK 架构
- 简化 macOS/iOS/tvOS 跨平台构建流程
- 为 [[coremltools-9]] 集成提供更好的 SDK 兼容性

## 为什么重要

对手机端 AI 生态的意义：

- **Metal 算子库持续完善**：ROLL 算子的 Metal 实现意味着更多底层操作可以在 Apple GPU 上执行，减少 CPU-GPU 数据搬运
- **统一 SDK 降低跨端部署门槛**：构建一次，部署到 iPhone/iPad/Mac，简化端侧模型部署流程
- **与 [[ggml-llamacpp-hf]] 的 HuggingFace 整合形成完整工具链**：从模型获取到端侧推理的全链路优化

## 关联
- [[ggml-llamacpp-hf]] — GGML 与 llama.cpp 加入 HuggingFace
- [[llamacpp]] — 上一版本
- [[llamacpp]] — 历史版本
- [[coremltools-9]] — Apple Core ML 工具链


### Build 8809
## 核心变更

### SYCL Q8_0 重排序修复（#21638）

修复了 Intel GPU (SYCL) 后端的严重 bug：Q8_0 量化权重在重排序优化后，第二次 prompt 处理会产生垃圾输出甚至崩溃。

**根因**：PR #21527 引入的 Q8_0 重排序优化缺少 GEMM 路径的重排感知反量化器。token 生成阶段通过 DMMV/MMVQ 重排了权重（AoS→SoA），但下一次 prompt 处理仍用标准反量化器读取，导致数据错乱。

**修复**：
- 新增 `dequantize_block_q8_0_reorder()` 函数
- 接入 `ggml_get_to_fp16_sycl()` 和 `ggml_get_to_fp32_sycl()`
- 与 Q4_0、Q4_K、Q6_K 已有的重排模式一致

### VRAM 满载时的重排序崩溃修复（#20478）

重排序优化会在设备上分配与权重张量等大的临时缓冲区。当 VRAM 接近满载时（大模型单 GPU 场景），分配失败导致 memcpy 对 NULL 指针崩溃。

**修复**：尝试设备分配 → 回退到主机内存 → 两者都失败则跳过重排回退到未优化内核。
- 设备内存回退到主机内存时，重排序速度从 ~38 t/s 降至 ~21 t/s（Intel Arc Pro B70）
- 但后续推理仍保留优化，仅一次性重排变慢
- 新增 RAII 临时缓冲区类 `sycl_reorder_temp_buffer`，自动清理

### Q4_K 和 Q6_K 的 DMMV 重排支持

Q4_K 和 Q6_K 之前在 MMVQ 和 GEMM 路径有重排支持，但 DMMV 路径遇到重排数据会 abort。新增 DMMV 内核读取 SOA 重排布局。

### 构建选项

新增 `GGML_SYCL_HOST_MEM_FALLBACK` CMake 选项（默认 ON）。设备访问主机内存需要 Linux kernel 6.8+（Ubuntu 26.04+）；旧内核用户可设 OFF 禁用。

## 关键洞察

1. **AI 辅助开发成为常态**：本次修复的代码由 Claude Opus 4.6 协助编写（root cause 调查 + 内核代码），人工审查并在真实硬件上测试。这是 llama.cpp 中明确标注 AI 辅助编码的又一案例。

2. **SYCL 后端持续成熟**：Intel GPU 通过 SYCL 后端的推理支持在稳步改善。Q8_0 重排修复解决了实际部署中的崩溃问题，对于使用 Intel Arc 显卡做推理的用户有直接价值。

3. **重排序优化的权衡**：重排（AoS→SoA）可以提升推理吞吐，但增加了内存管理和错误处理的复杂度。本次修复暴露了三个相关 bug，说明优化路径需要更全面的测试覆盖。

## 为什么重要

llama.cpp 是端侧 LLM 推理的核心引擎，每次更新影响所有下游应用。b8809 修复了可能导致 Intel GPU 推理崩溃的关键 bug，对于使用 SYCL 后端的部署（包括边缘设备和工作站）具有稳定性价值。iOS XCFramework 的持续更新也确保了 Apple 平台的端侧推理可用性。

## 关联

- [[ggml-llamacpp-hf]] — GGML 与 llama.cpp 加入 HuggingFace
- [[llamacpp]] — 上一个版本
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化，Q8_0 是常用量化格式之一
- [[kl-quantization-ssm-transformer]] — 量化敏感度分析


### Build 8808
## 概述

llama.cpp 是端侧 LLM 推理的事实标准框架，基于 GGML 张量库，支持 CPU、Apple Silicon 和消费级 GPU 推理。b8808 继续在性能优化和模型兼容性方面推进。

## 版本追踪

| 版本 | 发布日期 | 距前版间隔 |
|------|----------|-----------|
| b8783 | 2026-04-08 | — |
| b8795 | 2026-04-13 | 5天 |
| b8797 | 2026-04-14 | 1天 |
| b8796 | 2026-04-14 | 同日 |
| **b8808** | **2026-04-16** | **2天** |

开发节奏非常快，几乎每日都有新版本发布。

## 端侧推理生态位置

llama.cpp 在手机端 AIOS 的推理栈中占据核心位置：

- **GGML 格式**是端侧模型分发的事实标准
- 支持多种量化方案 (Q4_0, Q4_1, Q5_0, Q5_1, Q8_0 等)
- 与 [[mnn-350]] (阿里 MNN) 和 CoreML 形成竞争/互补关系
- [[ggml-llamacpp-hf]] 与 HuggingFace 的整合加速了生态发展

## 关联

- [[ggml-llamacpp-hf]] — GGML/llama.cpp 加入 HuggingFace 的背景
- [[llamacpp]] — 前一版本
- [[mnn-350]] — 竞争推理框架
- [[gemma-cpp-inference]] — gemma.cpp 基于 GGML 库
- [[kl-quantization-ssm-transformer]] — 量化技术与 llama.cpp 的量化方案互补


### Build 8807
## 核心更新

b8807 主要聚焦 Vulkan 后端的 im2col 操作优化：

- **改善 im2col 内存写入布局**：优化卷积操作的中间结果存储方式，减少内存带宽瓶颈
- **限制工作组数量**：避免 GPU 资源过度分配导致的调度开销
- **按 vendor_id 而非 subgroup size 进行设备调优**：更通用的设备适配策略，subgroup size 在不同 GPU 上差异大，vendor_id 更稳定

## 支持平台

- macOS Apple Silicon (arm64) + KleidiAI 变体
- macOS Intel (x64)
- iOS XCFramework
- Linux: Ubuntu x64/arm64/s390x, Vulkan, ROCm 7.2, OpenVINO 2026.0
- Windows: x64/arm64 CPU, CUDA 12.4

## 为什么重要

im2col 是卷积神经网络推理的核心操作，视觉模型（图像分类、目标检测、OCR）大量使用。Vulkan 后端覆盖了大部分 Android 设备和 Linux 桌面 GPU。这次优化直接改善端侧视觉模型的推理性能——对手机端 Agent 的屏幕理解、图像识别等场景尤为重要。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 的背景
- [[llamacpp]] — 上一个已记录版本
- [[gemma-cpp-inference]] — llama.cpp 推理生态
- [[edgeflow-cold-start]] — 端侧推理冷启动优化


### Build 8797
## 核心问题

Qualcomm Hexagon DSP 拥有 HMX（Hexagon Matrix eXtension）硬件矩阵乘法单元，但在之前的 llama.cpp 实现中，HMX 调用是同步的——主线程发出 matmul 请求后必须等待 HMX 计算完成才能继续，导致 HVX（向量单元）的反量化和 DMA 数据传输阶段被阻塞。这种串行执行模式无法充分利用 Hexagon DSP 的异构计算能力。

## 方法/架构

b8797 引入了三项核心技术改进：

### 1. 异步 HMX Worker（hmx-worker → hmx-queue）
- **原始方案**：同步 HMX 调用，主线程阻塞等待 matmul 完成
- **新方案**：引入专用的 hmx-worker 线程，将 HMX 计算与 HVX 反量化/DMA 传输流水线化
- **架构演化**：从 hmx-worker 进一步简化为 hmx-queue，复用 dma-queue 接口，减少线程唤醒往返次数
- **效果**：HMX matmul 与 HVX dequant/DMA 三个阶段真正并行执行

### 2. Cost-based VTCM Chunk Search
- 针对 out-stationary matmul 模式，实现了基于代价的 VTCM（Vector Tightly Coupled Memory）分块搜索
- VTCM 是 Hexagon DSP 的片上高速缓存，合理分块可最大化数据局部性

### 3. 其他优化
- **Scatter/Transpose 优化**：使用 HMX 内联函数替代通用实现
- **VTCM 内存限制调整**：在 v73 架构上将 vmem 上限调至略低于 3GB
- **竞态修复**：修复 hmx_worker_drain 中的 futex 竞态条件，通过局部变量存储避免重复原子加载

## 实验结果/关键数据

| 优化项 | 影响 |
|--------|------|
| 异步 HMX worker | HVX 与 HMX 并行，吞吐量提升 |
| hmx-queue 接口 | 减少线程唤醒开销 |
| VTCM chunk search | 改善数据局部性 |
| vmem limit 调整 | 支持更大模型 |

本次发布同时包含 iOS XCFramework 构建，表明 llama.cpp 在 Apple 生态（CoreML 对比路径）和 Qualcomm 生态上同步推进。

## 关键洞察

**Hexagon DSP 正成为移动端 LLM 推理的关键战场。** Qualcomm 的 HMX 单元类似 Apple 的 AMX/ANE，是专门为矩阵运算设计的硬件加速器。llama.cpp 的这次优化意味着：

1. **骁龙设备的 LLM 推理差距在缩小**：之前 Hexagon DSP 的利用率不高，这次优化后有望显著提升 tokens/s
2. **Qualcomm 的开源投入在加深**：PR 由 Qualcomm 工程师（@qti.qualcomm.com）主导提交，表明 Qualcomm 在积极支持 llama.cpp 生态
3. **异步流水线是移动端推理的通用优化模式**：类似 Apple ANE+GPU 的异构调度思路

## 为什么重要

对手机端 AI 生态的意义：
- **直接利好骁龙 8 Gen 4/8s Gen 4 设备**：这些芯片的 Hexagon DSP 拥有更强的 HMX 能力
- **缩小与 Apple Silicon 的差距**：llama.cpp 在 iOS/macOS 上已有成熟的 CoreML 路径，现在 Qualcomm 路径也在快速追赶
- **为端侧 Agent 提供更低延迟的推理基础**：异步流水线减少了首 token 延迟

## 关联
- [[llamacpp]] — 前序版本，对比优化趋势
- [[llamacpp]] — 更早的版本，可观察迭代方向
- [[ggml-llamacpp-hf]] — GGML 与 HuggingFace 合并后的生态基础
- [[mnn-350]] — 阿里 MNN 同样在 Qualcomm 平台上竞争
- [[edgecim-hardware-codesign]] — 硬件软件协同设计的端侧推理趋势
- [[rl-asic-exploration]] — 从 LLM 到芯片的 RL 驱动架构探索


### Build 8795
## 核心变更

### b8795: Metal FlashAttention 修复
- **修复 FA 支持逻辑** (#21898)：修复 Apple Metal 后端的 FlashAttention 支持判断逻辑
- 对 iOS/macOS 端侧推理至关重要——FlashAttention 是移动端 Transformer 推理的关键加速手段
- 修复前可能导致某些设备上 FA 回退到慢速路径，严重影响推理延迟

### b8794: 多模态 API 扩展
- **新增 `mtmd_image_tokens_get_decoder_pos()` API** (#21851)：为多模态推理提供图像 token 解码位置查询
- 这是 llama.cpp 多模态能力（图像理解）的关键 API 补充
- 允许开发者精确控制图像 token 在序列中的位置，对手机端多模态应用（拍照问答、屏幕理解等）至关重要

### b8793: Vulkan 精度修复
- **Vulkan shader RoundingModeRTE** (#21572)：在设备支持时自动为所有 Vulkan shader 添加 RoundingModeRTE
- 使用 FetchContent 获取 SPIRV-Headers
- 修复 Vulkan 后端的数值精度问题，影响 Android 设备上的推理正确性

## 为什么重要

**对手机端 AI 生态的关键信号**：

1. **Metal FA 修复**直接提升 iPhone/iPad 端侧推理性能。FlashAttention 是 3B-7B 模型在移动设备上达到可用延迟（<500ms TTFT）的核心技术。

2. **多模态 API** 持续完善，说明 llama.cpp 正从纯文本推理引擎演变为多模态推理框架——这与 Apple Intelligence、Gemini Nano 等端侧多模态战略一致。

3. **Vulkan 精度修复**保障 Android 设备推理正确性。Vulkan 是 Android GPU 推理的主要后端，精度问题会导致模型输出错误。

4. **一天三版本**的发布频率反映了社区对移动端推理的极高关注度和活跃开发节奏。

## 平台支持

| 平台 | 变体 |
|------|------|
| macOS/iOS | arm64, arm64-KleidiAI, x64, iOS XCFramework |
| Linux | x64, arm64, s390x, Vulkan x64/arm64, ROCm 7.2, OpenVINO |
| Windows | x64, arm64, CUDA 12/13, Vulkan, SYCL, HIP |
| openEuler | 310p, 910b ACL Graph |

## 关联
- [[llamacpp]] — 前一版本，Vulkan 精度修复
- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 的背景
- [[gemma4-ondevice]] — 多模态模型，依赖此类推理框架
- [[coremltools-9]] — Apple 端侧推理工具链的另一条路径
- [[mnn-350]] — 阿里端侧推理框架，竞品对比


### Build 8793
## 核心问题
在移动和边缘设备上使用 Vulkan 后端运行 LLM 推理时，浮点舍入模式的不一致会导致数值精度问题，影响模型输出的准确性和可复现性。不同 GPU 驱动对 IEEE 754 舍入模式的支持程度不同，手动管理不可行。

## 方法/架构
本次更新的核心改动：**程序化地为所有 shader 添加 RoundingModeRTE（Round to Nearest, Ties to Even）支持**。

- **自动检测**：运行时检测设备是否支持 RoundingModeRTE 扩展
- **Shader 注入**：若支持，自动在所有计算 shader 中插入对应的 SPIR-V 修饰符
- **依赖管理**：使用 FetchContent 获取 SPIRV-Headers（后续切换为系统安装依赖）

技术细节：
- RTE（Round to Nearest, Ties to Even）是 IEEE 754 默认舍入模式
- 之前 Vulkan shader 使用的舍入模式取决于驱动实现，不同设备结果不一致
- PR 通过 VK_KHR_shader_rounding_instruct_float16 和 float32 扩展实现
- 构建系统：移除 FetchContent，依赖已安装的 SPIRV-Headers

## 跨平台二进制发布
本次发布包含完整的多平台二进制：

| 平台 | 后端 | 备注 |
|------|------|------|
| macOS arm64 | CPU + KleidiAI | Apple Silicon 优化 |
| iOS | XCFramework | 移动端部署 |
| Ubuntu x64/arm64 | CPU / Vulkan / ROCm 7.2 / OpenVINO | 多后端选择 |
| Windows x64/arm64 | CPU / CUDA 12.4 / CUDA 13.1 / Vulkan / SYCL / HIP | 最广泛的 GPU 支持 |
| openEuler | 昇腾 310p | 国产 AI 芯片支持 |

## 关键洞察
- **Vulkan 精度一致性**：这个改动看似小（一个 shader 修饰符），但解决了跨设备数值不可复现的根本问题。对 mobile AIOS 尤其重要——不同厂商的 GPU 驱动实现差异极大
- **KleidiAI 集成**：macOS arm64 版本提供 KleidiAI 启用版本，这是 ARM 针对 AI 工作负载的优化库，对移动端推理性能有直接提升
- **openEuler + 昇腾支持**：持续扩展国产 AI 芯片生态，对小米/华为等国内厂商的端侧部署方案有重要意义
- **多 CUDA 版本并行**：同时提供 CUDA 12.4 和 13.1 二进制，说明用户生态正在分裂，llama.cpp 选择兼容而非强制升级

## 为什么重要
llama.cpp 是手机端 AI 推理的基石项目。Vulkan 后端的精度修复直接影响：
- **跨设备一致性**：确保同一模型在不同手机 GPU 上产生相同输出
- **量化精度**：配合 GGUF 量化格式，RTE 舍入保证量化后模型的数值正确性
- **开发信任度**：开发者可以信任 Vulkan 后端的数值行为，降低调试成本

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 后的持续演进
- [[llamacpp]] — 前一个版本，连续迭代
- [[edgecim-hardware-codesign]] — 硬件-软件协同设计趋势
- [[on-device-inference-memory-pressure]] — 内存管理优化方向


### Build 8791
## 本次更新要点

### Metal: XIELU 一元运算符
- 在 Metal 后端新增 **XIELU (eXponential Identity Linear Unit)** 激活函数
- XIELU 是一种新型激活函数，结合了指数特性和线性特性，在某些场景下比 SiLU/Swish 表现更好
- 这意味着 **iOS/macOS 端侧推理** 可以使用更高效的激活函数，减少内存和计算开销
- 与 [[coremltools-9]] 的 CoreML 转换路径互补 — llama.cpp 走的是直接 Metal kernel 路线

### ARM NEON nvfp4 点积修复
- 修复了 ARM NEON 后端在 non-dotprod 目标上的 nvfp4 (NVIDIA FP4) 点积计算
- 对 Qualcomm Snapdragon 和 MediaTek 等无 dotprod 指令集的 ARM SoC 至关重要
- 确保低精度推理在更多移动芯片上正确运行

### 其他
- WebGPU 矩阵乘法改用 f32 累加（精度提升）
- BoringSSL 更新到 0.20260413.0
- Windows MSVC CMake 警告修复

## 为什么重要

XIELU on Metal 是端侧 LLM 推理优化的又一突破。传统的激活函数（ReLU, GELU, SiLU）在 Metal shader 中已有优化实现，XIELU 作为更新的激活函数被纳入 Metal kernel 后，使用 XIELU 架构的模型在 iPhone/Mac 上的推理效率将显著提升。结合 nvfp4 的 ARM 修复，llama.cpp 在移动芯片上的低精度推理能力持续增强。



### Build b8855 (2026-04-20)

**发布日期**: 2026-04-20

**主要修复**:
- 修复 GLM-DSA 在 `llama-tokenize` 使用 `vocab_only` 时的崩溃问题 (#22102)
- 简化 `print_info` 中 GLM-DSA 的处理逻辑
- 代码审查反馈修正

**二进制发布**:
- macOS Apple Silicon (arm64) — 标准版和 KleidiAI 启用版
- iOS (arm64) — 移动端推理二进制
- 多平台预编译包

**端侧意义**: GLM-DSA 是智谱 AI 的模型格式，此修复确保在使用 `vocab_only` 模式（仅加载词表用于 tokenize，不加载模型权重）时不会崩溃。`vocab_only` 模式在端侧常用于快速 tokenization 预处理和模型格式检测，是一个重要的轻量级操作模式。



### Build b8860 (2026-04-20)

**主要更新**: 修复 Gemma-4 MoE 模型的 Tensor Parallel AllReduce 延迟问题

**技术细节**:
- 修复 Gemma-4 MoE 架构在 tensor-parallel 模式下的延迟 AllReduce 问题 (PR #22129)
- 跳过不消费当前节点的前向节点，允许 MUL 链式执行
- 在跳过节点前检查所有 source 节点，确保依赖完整性
- 多平台构建：macOS arm64/x64、Linux (CPU/Vulkan/ROCm/OpenVINO)、Android arm64、Windows (CPU/CUDA 12/13/Vulkan/SYCL/HIP)

**对移动端的意义**: Gemma-4 是 Google 最新的端侧多模态模型，MoE 架构需要高效的 tensor parallel 支持。
此修复确保 Gemma-4 在 Android arm64 设备上运行时不会因 AllReduce 延迟导致推理瓶颈。
对于在手机端部署 Gemma-4 MoE 模型的场景至关重要。

**关联**: [[gemma4-ondevice]], [[mnn-350]], [[coremltools-9]]

---

## 相关
- [[llamacpp]] — 上一个版本，含更多架构更新
- [[mnn-350]] — 阿里端侧推理引擎，竞争方案
- [[coremltools-9]] — Apple 官方模型转换工具链
### Build b8857 (2026-04-20)

**主要更新**: ggml-webgpu 更新矩阵-向量乘法（mat-vec）

**技术细节**:
- 重写 mat-vec kernel，新的 float 路径实现
- 完整移植 k-quants 到新 mat-vec 实现
- 清理旧 shader 和遗留常量
- 修复 q3_K 和 q5_K 在 u32 索引下的性能问题

**WebGPU 意义**: 这个 build 使 llama.cpp 的 WebGPU 后端更加成熟，
矩阵-向量乘法是 LLM 推理的核心操作，优化后能显著提升浏览器端和
跨平台推理性能。对于移动端 WebView 内嵌 AI 能力有直接价值。

**关联**: [[mnn-350]], [[coremltools-9]]

---


### Build b8862 (2026-04-20)

**发布日期**: 2026-04-20
**主要变更**:
- **mtmd 模块修复**: 修正 `get_n_pos` / `get_decoder_pos` 逻辑 (PR #22175)。多模态处理中的位置计算错误可能导致图像 token 与文本 token 对齐偏差，修复后提升多模态推理的准确性。
- 继续提供 macOS/iOS、Linux (Vulkan/ROCm/OpenVINO)、Android arm64、Windows (CUDA/CPU) 全平台二进制。

**对移动端意义**: mtmd 修复对 iOS XCFramework 和 Android arm64 构建尤为重要——这两个平台是 llama.cpp 移动端部署的主要目标。多模态推理的位置计算正确性直接影响视觉语言模型 (VLM) 在手机上的表现。

**下载**: [GitHub Releases](https://github.com/ggml-org/llama.cpp/releases/tag/b8862)

### Build b8863

**发布日期**: 2026-04-20
**类型**: 补丁版本

**主要变更**:
- `ggml-cuda`: 修复 OOM 时 legacy memory pool 未释放的问题，添加显式同步和析构函数清理
- 修复 MUSA 宏兼容性（摩尔线程 GPU 支持）
- 继续优化 CUDA 后端的内存管理稳定性

**为什么重要**: 这个版本解决了 CUDA 后端在大模型推理时 OOM 后内存池泄漏的问题。
对于端侧部署（如 Jetson、边缘 GPU 设备）而言，内存管理的稳定性至关重要——
OOM 后无法正确回收内存会导致设备变砖或需要重启推理进程。

**相关**:
- [[edge-inference-memory-pressure]] — 端侧内存压力管理
- [[quantization-mobile-deploy]] — 量化部署中的内存优化
