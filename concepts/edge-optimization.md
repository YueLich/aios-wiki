---
type: concept
tags: [edge-ai, optimization, 推理优化, 端侧部署]
related: []
created: 2026-04-18
updated: 2026-04-18
---

# 端侧推理优化技术

> 概念页面 — 从多个相关页面的 wikilink 引用自动创建

端侧推理优化是在手机、IoT 设备等资源受限环境中高效运行 AI 模型的技术集合。

## 核心技术

- **模型量化**: 将 FP32 权重压缩到 INT8/INT4，减少内存和计算量
- **模型剪枝**: 移除不重要的神经元和连接
- **知识蒸馏**: 用大模型教小模型，在保持精度的同时缩小模型
- **硬件特化**: 针对 NPU/GPU/DSP 指令集优化算子

## 关键挑战

| 挑战 | 解决方案 |
|------|----------|
| 内存不足 | KV-Cache 量化、动态批处理 |
| 启动延迟 | 模型预热、EdgeFlow 冷启动优化 |
| 功耗限制 | DVFS 动态调频、算子融合 |
| 多模型切换 | 模型路由、缓存策略 |

## 关联

- [[septq-post-training-quantization]] — 后训练量化
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化
- [[edgeflow-cold-start]] — 冷启动优化
- [[on-device-inference-memory-pressure]] — 内存压力
- [[dancemoe-distributed-moe-edge]] — 分布式 MoE
