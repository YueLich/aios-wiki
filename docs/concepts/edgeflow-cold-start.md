---
type: concept
tags: [inference, mobile, optimization, cold-start, llm, 优化技术]
related: [[on-device-inference]], [[edge-cloud-collaboration]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://arxiv.org/abs/2604.09083v1
    title: "EdgeFlow: Fast Cold Starts for LLMs on Mobile Devices"
    date: 2026-04
created: 2026-04-14
---

# EdgeFlow: Fast Cold Starts for LLMs on Mobile Devices

## 概述

EdgeFlow 是一个专门解决移动设备上 LLM 冷启动延迟的系统。冷启动是指模型从零开始加载到内存并完成首次推理的过程，在移动端这一过程可能耗时数秒，严重影响用户体验。

## 核心问题

移动设备上的 LLM 面临独特的冷启动挑战：
- **内存限制**：手机 RAM 有限（通常 6-12GB），模型需要精心调度
- **存储 I/O 瓶颈**：从闪存加载多 GB 模型权重耗时较长
- **热管理**：持续高负载会触发温度节流

## 为什么重要

冷启动延迟是移动 AI 体验的「最后一公里」问题。用户期望语音助手和 AI 功能即时响应，但目前大多数端侧 LLM 方案在首次调用时有明显延迟。EdgeFlow 的方向直接影响 [[apple-intelligence]] 和 [[xiaomi-hyperai]] 等产品的用户体验竞争力。

## 技术方向

- 智能预加载策略
- 高效内存管理与模型分片
- 与 [[edge-cloud-collaboration]] 架构的协同设计

## 关联实体

- [[llama.cpp]] — 通用推理引擎
- [[mnn]] — 阿里巴巴移动推理框架
