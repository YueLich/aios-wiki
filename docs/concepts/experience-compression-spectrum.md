---
type: concept
tags: [Agent记忆, 经验压缩, 技能发现, LLM Agent, 高效推理]
related: [[mga-memory-gui-agent]], [[agent-persistent-identity]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://arxiv.org/abs/2604.15877
    title: "Experience Compression Spectrum: Unifying Memory, Skills, and Rules in LLM Agents"
    date: 2026-04-17
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Experience Compression Spectrum

> 统一 LLM Agent 的记忆、技能和规则的压缩框架（arXiv:2604.15877）

## 核心问题

随着 LLM Agent 在长期、多会话部署中积累大量交互数据，如何高效管理这些经验成为关键瓶颈。Agent 记忆系统和技能发现都在解决这个问题——从交互轨迹中提取可重用知识——但通过对 22 篇核心论文中 1,136 条引用的分析发现，两个社区的交叉引用率不到 1%。

## 方法/架构

本文提出 **Experience Compression Spectrum（经验压缩谱）**，将记忆、技能和规则视为沿着单一压缩轴上的点：

| 压缩级别 | 知识类型 | 压缩率 | 上下文消耗 | 检索延迟 |
|---------|---------|--------|-----------|---------|
| Level 0 | 原始轨迹 | 1:1 | 极高 | 极高 |
| Level 1 | 情景记忆 | 5-20x | 中等 | 中等 |
| Level 2 | 程序性技能 | 50-500x | 低 | 低 |
| Level 3 | 声明式规则 | 1,000x+ | 极低 | 极低 |

将 20+ 个系统映射到这个谱上后发现：**每个系统都在固定的、预设的压缩级别上运行**——没有系统支持跨级别的自适应压缩。作者将此称为 **"missing diagonal"（缺失对角线）**。

## 关键洞察

1. **专业化不足**：记忆社区和技能社区独立解决共享子问题，但几乎不交换解决方案
2. **评估方法与压缩级别强耦合**：不同压缩级别需要不同的评估方法
3. **可迁移性与特异性的权衡**：压缩率越高，知识可迁移性越强，但特异性越低
4. **知识生命周期管理被忽视**：知识的创建、使用、更新、淘汰的完整生命周期基本未被研究

## 实验结果

引用分析覆盖 22 篇核心论文、1,136 条引用，发现跨社区引用率低于 1%。映射 20+ 个系统（包括 MemGPT、Reflexion、Voyager、SkillGenie 等）均显示固定压缩级别操作。

## 为什么重要

对手机端 AI Agent 而言，内存和计算资源有限。自适应压缩意味着 Agent 可以在设备上保留更多经验（低压缩），同时快速检索关键规则（高压缩）。这为端侧 Agent 的长期记忆管理提供了理论框架——同一份经验可以根据当前场景在不同压缩级别之间动态切换。

## 关联
- [[mga-memory-gui-agent]] — MGA 的记忆驱动 GUI Agent 可借鉴此框架优化记忆压缩策略
- [[agent-persistent-identity]] — 持久化身份需要跨压缩级别的知识迁移
- [[kv-cache-quantization-ondevice]] — KV Cache 量化也是一种压缩，可与经验压缩谱统一考虑
- [[edgeflow-cold-start]] — 冷启动优化需要高效的知识检索，压缩谱提供了理论基础
