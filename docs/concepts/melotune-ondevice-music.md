---
type: concept
tags: [on-device, ios, music, agent, affective-computing, privacy, 端侧推理, 个性化]
related: [[gemma4-ondevice]], [[agent-persistent-identity]], [[apple-intelligence]]
sources:
  - url: https://arxiv.org/abs/2604.10815
    title: "MeloTune: On-Device Arousal Learning and Peer-to-Peer Mood Coupling for Proactive Music Curation"
    date: 2026-04-14
    reliability: high
created: 2026-04-14
updated: 2026-04-21
---

# MeloTune: 端侧唤醒度学习与点对点情绪耦合的主动音乐推荐

> 在设备端学习用户情绪状态并进行个性化音乐推荐，无需云端。来源：arXiv 2604.10815

## 核心问题
现有音乐推荐系统依赖用户历史行为和云端模型，无法实时感知用户情绪变化。在移动端场景中，用户期望音乐播放器能"读懂心情"并主动调整播放列表，但传统方法要么延迟高（云端推理），要么精度低（规则匹配）。

## 方法/架构
MeloTune 是一个部署在 iPhone 上的音乐 Agent，基于两个核心组件：

- **Mesh Memory Protocol (MMP)**：设备间共享认知记忆块（Cognitive Memory Blocks, CMBs）的协议。原始隐藏状态不出设备，只有结构化的认知摘要参与协作
- **Symbolic-Vector Attention Fusion (SVAF)**：融合多模态信号（传感器、音频特征、交互模式）的注意力机制
- **双 CfC 网络**：
  - 私有 CfC：在 Russell 环形模型上预测短期情感轨迹，驱动主动推荐
  - 共享 CfC：MMP Layer 6 运行，整合来自共听同伴的 CMB

关键设计：CfC 隐藏状态永远不离开设备，只有结构化 CMB 参与点对点通信。端侧模型 < 5MB，推理延迟 < 100ms。

## 实验结果
- 在 200 用户 A/B 测试中，推荐点击率比传统方法高 23%
- 用户满意度评分提升 18%（5 分制从 3.2 到 3.8）
- 端侧推理功耗 < 10mW
- 冷启动场景（新用户）表现优于协同过滤 35%

## 关键洞察
情绪感知不需要复杂的 NLP——传感器数据 + 轻量级时序模型就能捕获足够的信号。MeloTune 的关键发现是：端侧模型虽然参数少，但因为能实时访问传感器上下文，反而比大模型的推荐更准确。此外，点对点情绪耦合（不共享原始数据，只共享认知摘要）是隐私保护推荐的新范式。

## 为什么重要
展示了端侧 AI 在用户体验优化上的独特优势：(1) 低延迟实时推荐；(2) 隐私保护（敏感的情绪数据不出设备）；(3) 个性化（适应每个用户的独特模式）。对手机 AIOS 的智能助理和媒体体验有直接启示。

## 关联
- [[agent-persistent-identity]] — Agent 个性化与用户建模
- [[on-device-inference-memory-pressure]] — 端侧推理的资源约束
- [[gemma4-ondevice]] — 端侧模型的实际应用
- [[apple-intelligence]] — Apple 生态中的端侧 AI 应用
