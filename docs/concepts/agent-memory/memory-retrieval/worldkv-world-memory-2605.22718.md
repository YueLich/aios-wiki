---
title: "WorldKV: Efficient World Memory with World Retrieval and Compression"
arXiv: 2605.22718
date: 2026-05-21
tags: [agent-memory, memory-retrieval, world-model, kv-cache, embodied-memory]
reviewer: auto
source: arXiv API
---

## 摘要

WorldKV 提出一种无需训练的世界记忆框架，解决视频扩散模型中持久世界一致性与实时推理的矛盾。核心挑战：全 KV-Cache 注意力保持一致性但内存开销随 rollout 长度线性增长，滑动窗口恢复吞吐量但丢失长期一致性。WorldKV 由两部分组成：**World Retrieval** 将被驱逐的 KV-Cache 分块存储在 GPU/CPU 内存中，通过摄像机/动作对应关系选择性检索场景相关分块，无需重编码即可重新插入原生注意力窗口；**World Compression** 通过关键帧相似度剪枝每个分块内的冗余 token，将每分块存储减半，在固定预算下容纳 2 倍历史。在 Matrix-Game-2.0 和 LingBot-World-Fast 上，WorldKV 以约 2 倍吞吐量达到全 KV 记忆保真度，且无需任何微调即可与记忆训练基线竞争。

## 核心贡献

1. **World Retrieval**：被驱逐的 KV-Cache 分块存储在分层 GPU/CPU 记忆中，通过摄像机位姿和动作对应关系选择性检索相关场景，无需重编码
2. **World Compression**：基于关键帧相似度剪枝分块内冗余 token，存储减半而信息保留
3. **训练-free 框架**：无需微调即可部署，与记忆训练基线性能相当
4. **2 倍吞吐量提升**同时保持与全 KV-Cache 相近的世界一致性

## 为什么重要

视频生成与具身 AI 的核心挑战之一是维护跨时间的视觉一致性。传统方法在"保持记忆"和"实时推理"之间被迫取舍。WorldKV 通过将记忆组织为可按需检索的分块（类似人类的情景记忆），同时用压缩减少存储负担，为世界模型提供了一种实用的记忆架构。这一思路对端侧部署尤为重要：移动机器人无法持续保留完整 KV-Cache，必须选择性存储和检索。

## 与端侧/移动端的相关性

- **分层记忆架构**：GPU/CPU 分层存储对应移动端 DRAM + NVM 分层
- **无需微调**：可直接部署在现有视频生成 pipeline，降低端侧部署门槛
- **计算可控**：选择性检索避免全量重计算，适合边缘设备资源约束
- **论文来自 KAUST CVLab**，有开源项目页

## 参考文献

（参考文献待从原文补充）
