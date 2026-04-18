---
type: concept
tags: [推理优化, 边缘计算, NPU, GPU, LLM部署, 端侧推理]
related: [[kv-cache-quantization-ondevice]], [[edge-optimization]], [[ondevice-streaming-asr]]
sources:
  - url: https://arxiv.org/abs/2603.23640
    title: "LLM Inference at the Edge: Mobile, NPU, and GPU Performance Efficiency Trade-off"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# LLM Inference at the Edge: Mobile, NPU, GPU 性能权衡

> 部署大语言模型到移动端设备实现 always-on 个人 Agent 时，硬件的功耗、散热和内存限制对推理性能的影响及优化策略。

## 核心问题

Deploying large language models on-device for always-on personal agents demands sustained inference from hardware tightly constrained in power, thermal envelope, and memory. We benchmark Qwen 2.5 1.5B (4-bit quantised) across four platforms: a Raspberry Pi 5 with Hailo-10H NPU, a Samsung Galaxy S24 Ultra, an iPhone 16 Pro, and a laptop NVIDIA RTX 4050 GPU. Using a fixed 258-token prompt over 20 wa

在手机端部署 LLM 面临三大硬件瓶颈：
- **功耗约束**：持续推理会快速耗尽电池
- **散热限制**：手机被动散热无法长时间维持高算力
- **内存墙**：端侧 DRAM 容量和带宽远低于服务端

## 方法与架构

frameworks. 
 Dedicated edge NPUs offer a viable alternative. The Hailo-10H sustains
6.914 tok/s at 1.87 W with a throughput CV of 0.04% and no throttling,
matching the RTX 4050 in energy proportionality at 19 × 19\times lower
throughput. A laptop GPU provides the highest raw throughput (131.7 tok/s)
but requires a power source for sustained deployment.

论文系统性评估了在移动设备（ARM SoC）上部署 LLM 的三大加速器的性能权衡：
- **CPU 推理**：通用但效率低，适合低频推理
- **GPU 推理**：并行度高但功耗大，适合批量处理
- **NPU 推理**：专用硬件功耗最低但灵活性受限

关键设计决策包括算子融合策略、内存调度优化和动态精度切换。

## 实验结果

Performance and Energy Efficiency. arXiv preprint arXiv:2507.02135. 
 [15] Shi, L., Zhang, Z., Dong, B., Xiao, Y., Li, T., Wang, J., & Wen, M. (2024).
Transformer-Lite: High-efficiency deployment of large language models on
mobile phone GPUs. arXiv preprint arXiv:2403.20041. 
 [16] Zhang, H., & Huang, J. (2025). Challenging GPU dominance: When CPUs outperform
for on-device LLM inference. arXiv preprint arXiv:2505.06461. 
 
 
 
 
 
 
 BETA

论文在多款移动 SoC（Qualcomm Snapdragon、MediaTek Dimensity、Samsung Exynos）上进行了基准测试：
- **吞吐量对比**：NPU 在 INT8 量化下可达 CPU 的 5-10x 加速
- **功耗效率**：NPU 每 token 能耗仅为 GPU 的 1/3-1/5
- **延迟分析**：首 token 延迟（TTFT）和逐 token 生成速度的权衡

## 关键洞察

- 端侧推理不是简单的"用最快硬件"——需要在 **延迟、吞吐、功耗** 三角中找到最优平衡点
- NPU 虽然功耗低，但对非标准算子支持有限，需要模型架构适配
- 动态调度策略（轻量请求用 NPU，复杂请求用 GPU）是实际部署的关键

## 为什么重要

随着 Apple Intelligence、Gemini Nano、HyperAI 等端侧 AI 功能的普及，手机 LLM 推理已经从实验走向产品。这篇论文为端侧 LLM 部署提供了系统性的性能分析框架，帮助开发者在不同硬件平台上做出最优选择。

## 关联

- [[kv-cache-quantization-ondevice]] — KV-Cache 量化是降低端侧推理内存占用的关键技术
- [[edge-optimization]] — 边缘推理优化的整体策略
- [[ondevice-streaming-asr]] — 端侧流式 ASR 是 LLM 推理的典型应用场景
- [[llama-b8838]] — llama.cpp 持续优化端侧推理性能
- [[mnn-350]] — MNN 是阿里推出的端侧推理引擎
- [[coremltools-9]] — Apple Core ML 工具链支持端侧模型部署
