---
type: entity
tags: [推理框架, 移动推理, 端侧AI, 混合云, YC]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[coremltools-9]], [[minicpm-242]]
sources:
  - url: https://github.com/cactus-compute/cactus
    title: "Cactus Compute GitHub"
    date: 2026-04-20
    reliability: high
  - url: https://cactuscompute.com
    title: "Cactus Compute Official Website"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Cactus — 移动端 AI 推理引擎

> 由 Y Combinator W25 孵化的 Cactus Compute 推出的端侧 AI 推理引擎，专注智能手机、笔记本和边缘设备，主打超低延迟与自动云端降级。

## 核心问题

端侧 AI 推理面临三大挑战：
1. **延迟瓶颈**：云端推理延迟 >1s，用户体验差
2. **隐私顾虑**：数据上传至云服务存在泄露风险
3. **成本压力**：大规模调用 API 费用高昂

## 架构设计

Cactus 采用三层架构：

| 层 | 功能 | 特点 |
|---|---|---|
| **Cactus Engine** | 上层 API | OpenAI 兼容接口，支持 Chat/Vision/STT/RAG/Tool Call |
| **Cactus Graph** | 计算图 | 零拷贝计算图，类 PyTorch for mobile，支持自定义模型 |
| **Cactus Kernels** | 底层算子 | ARM SIMD 优化内核，支持 Apple/Snapdragon/Exynos 等 |

## 关键技术特性

- **ARM CPU 最快推理**：自研 SIMD 内核，针对各大 ARM 平台优化
- **10x 更低 RAM**：零拷贝内存映射，大幅减少内存占用
- **多模态统一 SDK**：语音（STT）、视觉（Vision）、语言模型共用一套 API
- **自动云端降级**：当端侧模型能力不足时，自动路由至云端模型
- **NPU 加速预填充**：利用硬件 NPU 加速 prefill 阶段
- **KV Cache 量化**：chunked prefill + KV cache 量化减少内存压力

## 性能数据

来自 HN 社区实测（Pixel 9 Pro，Qwen2.5 1.5B Q6_K）：
- Token 生成速率：277 tok（总输出）
- TTFT（首 Token 时间）：1609ms
- 生成速度：9 tok/sec
- RAM 使用：~246 MB（报告）

Cactus 引擎报告参数：
- prefill_tps: 1621.89 tok/s
- decode_tps: 168.42 tok/s
- ram_usage_mb: 245.67

## HN 社区反应

- **123 points**，属于高质量 YC Launch HN 帖
- 用户反馈：已使用数月，"Makes it really easy to plug and play different models on my phone"
- 关注点：App 打包体积、商业模式

## 为什么重要

Cactus 的定位值得关注：
1. **YC S25 背书**：YC 选择在手机端 AI 领域投资，印证该赛道成熟度
2. **混合云降级**是端侧 AI 落地的关键能力——模型太小就自动切云端，无需开发者手动处理
3. **OpenAI 兼容 API**降低迁移成本，开发者可零改动切换端侧/云端
4. **多模态统一**：语音+视觉+语言一个 SDK，减少集成复杂度

对手机端 AI 生态：与 [[ggml-llamacpp-hf]]（通用端侧推理）和 [[mnn-350]]（阿里系端侧框架）形成竞争格局。Cactus 的差异化在于「移动端优先」设计和自动云降级。

## 关联

- [[ggml-llamacpp-hf]] — 通用端侧推理引擎，Cactus 的主要竞品
- [[mnn-350]] — 阿里巴巴端侧推理框架，同赛道竞品
- [[coremltools-9]] — Apple 端侧工具链，Cactus 在 iOS 端可能基于此
- [[minicpm-242]] — 端侧语言模型，Cactus 引擎可加载的典型模型
- [[on-device-inference-memory-pressure]] — 端侧推理的内存优化方法论
- [[edgeflow-cold-start]] — 端侧模型冷启动优化，Cactus 的 TTFT 性能相关
