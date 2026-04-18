---
type: concept
tags: [on-device, ios, music, agent, affective-computing, privacy, 平台]
related: [[gemma4-ondevice]], , 
sources:
  - http://arxiv.org/abs/2604.10815v1
created: 2026-04-14
---

## 核心问题

MeloTune is an iPhone-deployed music agent that instantiates the Mesh Memory Protocol (MMP) and Symbolic-Vector Attention Fusion (SVAF) as a production system for affect-aware music curation with peer-to-peer mood coupling. Each device runs two closed-form continuous-time (CfC) networks: a private listener-level CfC that predicts a short-horizon affective trajectory on Russell's circumplex and drives proactive curation, and a shared mesh-runtime CfC at MMP Layer 6 that integrates Cognitive Memory Blocks (CMBs) from co-listening peers. CfC hidden states never cross the wire; only structured CMB

## 论文信息

- **标题**: MeloTune: On-Device Arousal Learning and Peer-to-Peer Mood Coupling for Proactive Music Curation
- **作者**: Hongwei Xu
- **来源**: arXiv

## 方法/架构

详细方法论待补充。参考原始论文获取完整技术细节。

## 为什么重要

作为手机端 AIOS 生态的一部分，MeloTune：端侧情感感知音乐推荐 对推动端侧 AI 落地具有重要意义。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[kv-cache-quantization-ondevice]] — 内存优化
