---
type: concept
tags: [memory, agent-memory, persistent-memory, knowledge-graph, vector-database, 持久化, 智能体记忆]
related: [[mga-memory-gui-agent]], [[agent-persistent-identity]], [[experience-compression-spectrum]], [[memory-worth-governance]], [[kv-cache-quantization-ondevice]], [[edge-cloud-offloading]]
sources:
  - url: https://arxiv.org/abs/2604.18478
    title: "WorldDB: A Vector Graph-of-Worlds Memory Engine with Ontology-Aware Write-Time Reconciliation"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# WorldDB：向量图-世界记忆引擎

> 一种基于递归世界、内容寻址不可变性和边写时程序的持久记忆引擎，在 LongMemEval-s 上达到 96.40%，超越 Hydra DB SOTA 5.6 个百分点。arXiv 2604.18478

## 核心问题

长运行 Agent（持续数天或数月交互）面临记忆层的三重结构缺陷：

1. **语义碎片化**：朴素分块破坏跨段依赖。实体在一个 chunk 中引入、在另一个 chunk 中更新，检索时各自独立返回，产生"遗漏幻觉"
2. **时间停滞**：扁平向量存储无时序区分能力。"我现在住在奥斯汀"和"我2022年住在奥斯汀"被同等返回，LLM 需要自行消解矛盾
3. **身份漂移**：标准嵌入将"Sarah"、"工程负责人"、"我的经理"放在三个相近但独立的位置，没有显式消解器，跨 session 的实体追踪静默失败

现有方案（Graphiti/Zep、Memento、Hydra DB）在 LongMemEval-s 上表现不一：Hydra DB 90.79%、Supermemory 85.20%、Zep 71.2%、Mem0 仅 29.07%。但它们的图仍然是**扁平的**——边只是标签，不携带可执行语义。

## 方法/架构

WorldDB 基于三个非标准承诺：

### 1. 递归世界（Recursive Worlds）
节点不是一行记录，而是一个**世界**——包含内部子图、自身本体论作用域、组合嵌入和时间范围的容器。世界可以任意深度嵌套。查询世界 W 无法泄漏世界 W' 的节点，除非存在显式 `refers_to` 边。编辑传播不变式是结构性的，不由应用代码保证。

### 2. 内容寻址不可变性（Content-Addressed Immutability）
每个节点 ID 是 `blake3(τ ‖ n ‖ c ‖ sort(C_ids) ‖ sort(E_ids) ‖ t_create)`。叶节点的微小编辑会在叶节点及所有祖先产生新哈希——提供去重、可验证引用和 Merkle 审计追踪。Blob 本身不可变；有效性区间（事实何时为真）存在于节点行的可变列上，关闭时不违反内容寻址。

### 3. 边即写时程序（Edges as Write-Time Programs）
默认本体论的 11 种边类型（contains、refers_to、supersedes、same_as、contradicts、implies、derived_from、instance_of、subtype_of、causes、precedes）各带 `on_insert`/`on_delete`/`on_query_rewrite` 处理器：
- **Supersedes** 处理器在提交时关闭目标的 `t_valid.to`
- **Contradicts** 处理器记录冲突但不删除任何一方
- **SameAs** 暂存合并提案——引擎从不静默折叠身份

### 三通道检索管道
BM25 ∪ HNSW ∪ 实体图遍历，通过 reciprocal rank fusion 融合，无手工路由。

### 内容/组合嵌入分离
参数无关的基于注意力的世界嵌入（类 HAKG），随子图变化增量更新。

### 后台整合器
生成摘要节点、计算 causes 和 subtype_of 的传递闭包，支持"摘要优先"查询——在 1000 叶子节点语料上比全细节遍历快 **6.5 倍**。

## 实验结果

| 指标 | WorldDB | Hydra DB | Supermemory | Zep | Mem0 |
|------|---------|----------|-------------|-----|------|
| LongMemEval-s 总分 | **96.40%** | 90.79% | 85.20% | 71.2% | 29.07% |
| 任务平均 | **97.11%** | 90.8% | — | — | — |
| 对 Hydra DB 提升 | +5.6pp 总分 / +6.3pp 任务平均 | — | — | — | — |

工程基准：
- 1M 节点 + 2.5M 边批量加载：**5,401 writes/s**
- P95 读延迟：13ms (seed) / 97ms (BM25) / 3.1ms (HNSW)
- 协调器模糊测试：2×2,000 随机操作下不变式保持

消融实验：引擎的图贡献为 **+10.7pp** 任务平均分。

## 关键洞察

**世界嵌套是解决记忆粒度的关键**：扁平图中一个"项目"是多个节点和边的集合，但没有封装边界。WorldDB 的递归世界天然支持"这个对话是一个世界、这个项目是一个世界、这个用户是一个世界"的层级组织。这对移动 Agent 尤其重要——手机端的交互上下文天然具有层级结构（应用→对话→任务→子任务）。

**内容寻址 ≠ 版本控制**：不同于 Git 式的版本控制（显式 commit），WorldDB 的不可变性是通过哈希自然涌现的。任何编辑产生新节点，旧节点保留。这与端侧 Agent 的需求匹配——需要审计追踪但不想管理显式版本标签。

**边即程序消除了应用层耦合**：传统知识图谱需要应用代码在每次查询时显式处理"superseeds意味着旧事实无效"。WorldDB 将此逻辑下沉到存储层。移动 Agent 开发者不再需要编写记忆管理逻辑。

## 为什么重要

WorldDB 直接解决了手机端 AIOS Agent 的核心瓶颈：**持久记忆**。当前端侧 Agent 每次启动都从零开始（无状态 chatbot），或依赖简单的键值缓存。WorldDB 提供了一种结构化的、可审计的、支持时间旅行的记忆子系统：

- **端侧适配潜力**：blake3 哈希 + HNSW 检索的组合计算开销可控，适合在 NPU 上运行
- **隐私保护**：内容寻址意味着数据不可篡改，支持差分隐私审计
- **MCP 集成**：论文提供了 Model Context Protocol 表面，暴露 9 个记忆工具，支持 stdio 和 streamable-HTTP 传输——可直接嵌入端侧 Agent 框架
- **与现有方案互补**：可作为 KV-cache 优化的上层抽象，或与联邦学习的记忆聚合层集成

## 关联

- [[mga-memory-gui-agent]] — MGA 同样关注 GUI Agent 的记忆驱动，WorldDB 提供了底层存储引擎
- [[agent-persistent-identity]] — WorldDB 的 same_as 边和身份消解直接支持 Agent 持久身份
- [[experience-compression-spectrum]] — 经验压缩与 WorldDB 的后台整合器/摘要节点互补
- [[memory-worth-governance]] — 记忆价值治理可利用 WorldDB 的有效性区间机制
- [[kv-cache-quantization-ondevice]] — WorldDB 是上层记忆抽象，KV-cache 是底层推理优化
- [[edge-cloud-offloading]] — WorldDB 的 MCP surface 可用于端云记忆同步
