---
title: "MedMemoryBench: Benchmarking Agent Memory in Personalized Healthcare"
arXiv: 2605.11814
date: 2026-05-12
tags: [agent-memory, memory-retrieval, benchmark, healthcare]
reviewer: auto
source: arXiv RSS/API
---

# MedMemoryBench: Benchmarking Agent Memory in Personalized Healthcare

## 论文概览

| 字段 | 内容 |
|------|------|
| 标题 | MedMemoryBench: Benchmarking Agent Memory in Personalized Healthcare |
| 作者 | Yihao Wang, Haoran Xu, Renjie Gu, Yixuan Ye, Xinyi Chen, Xinyu Mu, Yuan Gao, Chunxiao Guo, Peng Wei, Jinjie Gu, Huan Li, Ke Chen, Lidan Shou |
| 提交日期 | 2026-05-12 |
| 类别 | cs.AI |
| 论文简介 | 为个性化医疗Agent记忆系统建立基准测试，包含约2000会话和16000交互轮次 |

## 核心贡献

### 1. 医疗轨迹数据集
- 基于临床 grounded、合成患者原型，构建高度真实的长时域医疗轨迹
- 包含约 **2,000 会话** 和 **16,000 交互轮次**
- 人-Agent 协作 pipeline 合成数据

### 2. "Evaluate-while-Constructing" 流式评估协议
- 区别于传统静态评估
- 精确模拟生产环境的动态记忆积累过程
- 支持流式评估协议

### 3. 记忆饱和（Memory Saturation）现象形式化
- 研究持续信息流入主动降低检索和推理鲁棒性的关键现象
- 系统性调查记忆饱和问题

### 4. 主流架构瓶颈揭示
- 复杂医疗推理能力不足
- 噪声鲁棒性差
- 为生产级医疗Agent开发提供重要基础

## 为什么重要

现有基准测试主要聚焦于日常开放域对话，无法捕捉真实医疗应用的高风险复杂性。本工作源自服务于数千万活跃用户的行业领先健康管理Agent的生产级需求，直接针对：

1. **精确性要求**：医疗场景对记忆精度要求极高
2. **安全性要求**：医疗决策关乎生命安全
3. **长期追踪能力**：需要跨时间跨事件的临床记忆

## 与移动端/端侧的相关性

医疗Agent需要在边缘设备（如移动端、可穿戴设备）上运行，以实现：
- 实时健康监测
- 本地化隐私保护（医疗数据不离设备）
- 低延迟响应

记忆饱和问题的研究对端侧资源受限环境尤为重要——端侧设备无法无限存储记忆，必须决定何时遗忘或压缩。

## 关键发现

主流架构在以下方面存在严重瓶颈：
- **复杂医疗推理能力**
- **噪声鲁棒性**（医疗数据常含噪声）

## 参考

- GitHub: （待补充）
- arXiv: https://arxiv.org/abs/2605.11814
