---
title: "When Continual Learning Moves to Memory: A Study of Experience Reuse in LLM Agents"
arXiv: 2604.27003
date: 2026-04-29
authors: "Qisheng Hu, Quanyu Long, Wenya Wang (Nanyang Technological University)"
tags: [agent-memory, continual-learning, memory-retrieval, experience-reuse]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv**: 2604.27003v1
- **发表**: 2026-04-29
- **作者**: Qisheng Hu, Quanyu Long, Wenya Wang (NTU)
- **方向**: 持续学习 / 记忆-学习交叉
- **开源**: CC BY-NC-SA 4.0

---

## 核心发现

记忆增强LLM Agent看似回避了参数学习的稳定性-可塑性困境，但这个挑战在**记忆层面重现了**：

> Under a limited context window, old and new experiences compete during retrieval, relocating the continual-learning bottleneck from parameter updates to memory access.

在有限上下文窗口下，新旧经验在检索时竞争，**持续学习的瓶颈从参数更新转移到记忆访问**。

---

## (k,v) 框架：记忆设计的两个正交轴

### 轴1：经验如何表示（Representation）

- **Raw Trajectories**（原始轨迹）：完整的历史交互记录
- **Abstract Procedures**（抽象程序）：提炼出的程序性知识

### 轴2：经验如何组织以供检索（Organization）

- **Aggregate**（聚合）：将相似经验打包存储
- **Individual**（独立）：每个经验独立存储

### 组合出4种记忆配置

| | Aggregate | Individual |
|---|---|---|
| **Raw** | Raw-Agg | Raw-Ind |
| **Abstract** | Abst-Agg | Abst-Ind |

---

## 研究1：记忆表示的影响

### 关键发现

**抽象程序记忆比详细轨迹更可靠地转移**

1. **负面转移集中发生在困难案例上** — 容易案例即使原始轨迹也能正确迁移
2. **任务内优势不能预测跨任务收益** — 在任务A上表现好不代表能迁移到任务B
3. **抽象减少遗忘（Backward Transfer）** — 抽象表征对权重变化的敏感性更低

### 启示

> Raw trajectories hurt when they pollute retrieval — abstraction filters out noisy details

---

## 研究2：记忆组织的影响

### BabyAI 结果

- 多样化且同质的源记忆表现不同
- 独立存储在多样化环境下更好

### ALFWorld 结果

- Bundling（聚合）仍然是更安全的选择
- 任务间有共享阶段模式时，聚合能提供更好的记忆覆盖

### 细粒度组织并非普遍有益

**关键发现**：产生强正向转移的设计可能同时诱发**检索多样性崩溃**（retrieval diversity collapse）——Agent只召回最相似的记忆，忽略真正有用的远距离记忆。

---

## 对端侧/移动端的意义

| 场景 | 建议 |
|---|---|
| **受限上下文窗口** | 优先抽象记忆表示，减少原始轨迹存储 |
| **多任务Agent | 任务间相似性高时用聚合，低时用独立 |
| **资源受限设备** | 抽象+聚合的组合最小化记忆 footprint |

---

## 为什么重要

首次系统性地在**记忆层面**研究持续学习问题，将CL的核心指标（Forward Transfer, Backward Transfer, Representation-Pair分析）应用到外部记忆设计空间。为"记忆增强Agent如何真正实现持续学习"提供了第一个系统的实验框架。
