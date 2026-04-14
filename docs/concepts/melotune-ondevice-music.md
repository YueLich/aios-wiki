---
type: concept
tags: [on-device, ios, music, agent, affective-computing, privacy]
related: [[gemma-4-google]], [[edge-ai-agents]], [[privacy-preserving-ml]]
sources:
  - http://arxiv.org/abs/2604.10815v1
created: 2026-04-14
---

# MeloTune：端侧情感感知音乐推荐

iPhone 端侧部署的音乐 Agent，通过情感学习实现主动音乐推荐。

## 核心技术
- **Mesh Memory Protocol (MMP)**：设备间协作协议
- **Symbolic-Vector Attention Fusion (SVAF)**：符号-向量融合注意力
- **Closed-form Continuous-time (CfC) 网络**：两个 CfC 网络分别运行在设备端
  - 私有 CfC：预测用户情感轨迹（Russell 环形模型）
  - 共享 mesh-runtime CfC：整合共听用户的认知记忆块（CMB）

## 隐私设计
- **CfC 隐藏状态不跨设备传输**
- 仅传输结构化的 CMB（认知记忆块）
- 端到端保持情感数据在设备本地

## 为什么重要
MeloTune 代表了 [[端侧 Agent]] 的一个新范式：
1. **Agent + 端侧推理**：不只是模型推理，而是完整的 Agent 协作系统在端侧运行
2. **P2P 情感耦合**：多设备间的情感同步无需云端中介
3. **隐私优先架构**：用数学保证（隐藏状态不出设备）替代隐私政策承诺
4. **实用化系统**：在 iPhone 上实际部署运行

这预示着端侧 AI Agent 正从简单的工具调用进化为复杂的协作系统。
