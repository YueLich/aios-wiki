---
type: concept
tags: [多模态, multimodal-fusion, agentic-inference, omnimllm, 动态融合, hallucination-mitigation]
related: [[mma2a-modality-native-routing]], [[multimodal-edge-pruning]], [[summer-multimodal-memory]], [[synergy-agentic-web-agent]], [[edge-cloud-offloading]], [[edgeflow-cold-start]]
sources:
  - url: https://arxiv.org/abs/2604.14520
    title: "Chain of Modality: From Static Fusion to Dynamic Orchestration in Omni-MLLMs"
    date: 2026-04-16
    reliability: high
  - url: https://arxiv.org/html/2604.14520v1
    title: "Chain of Modality (Full Paper HTML)"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Chain of Modality (CoM): 动态多模态融合编排

> 一种 Agentic 框架，将多模态融合从被动拼接转变为动态编排，解决 Omni-MLLM 中静态融合拓扑导致的结构性病理。西北工业大学，arXiv 2026-04-16。

## 核心问题

当前全模态大语言模型（Omni-MLLMs）普遍采用**静态融合拓扑**——无论任务语义如何，都以固定方式拼接不同模态输入。这导致了一个令人困惑的**性能悖论**：在 AVHBench 等基准上，单模态基线模型经常**超越**联合多模态推理模型。多模态融合非但没有产生协同效应，反而引入了系统性干扰。

论文通过实证分析，识别出两个结构性病理：

### 病理 1：位置偏差（Positional Bias）
在顺序输入格式（如 Audio-Visual）中，视觉特征凭借位置邻近性"劫持"注意力分配。即使在音频主导的任务中，深层注意力中视觉 token 的权重仍然与音频相当甚至更高。调换输入顺序会导致性能剧烈波动，证明模型依赖的是**结构邻近性**而非语义内容。

### 病理 2：对齐陷阱（Alignment Trap）
为弥合时序差距而采用的交错格式，通过强制跨模态 token 物理相邻，迫使模型在信号不一致时仍"幻觉"语义一致性。这导致虚警率系统性升高（ErrorV > ErrorA），模型即使在视觉证据误导的情况下也偏向视觉模态。

## 方法/架构：CoM 三组件

CoM 框架将推理分为三个阶段：

### 1. Planner（规划器）- 拓扑感知规划
- **模态选择**：分析任务需求，从可用模态集合中筛选最小充分模态集
- **拓扑选择**：在并行（Parallel）、顺序（Sequential）、交错（Interleaved）三种拓扑中动态选择最优配置
- **执行排序**：确定模态处理的最优顺序

### 2. Reasoner（推理器）- 分析推理
- 根据 Planner 的蓝图，沿选定拓扑从最小模态集提取证据
- 生成各模态的感知推理链

### 3. Decider（决策器）- 最终决策
- 综合理性推理链生成最终响应

## 双路径认知执行

CoM 根据任务复杂度自适应选择执行路径：

| 路径 | 适用场景 | 流程 | 训练需求 |
|------|---------|------|---------|
| **Direct-Decide** (Plan-Decide) | 直觉型任务（音乐问答、场景理解） | 感知 → 直接决策 | 免训练（zero-shot） |
| **Reason-Decide** (Plan-Reason-Decide) | 分析型任务（计数、复杂推理） | 感知 → 分析审计 → 综合决策 | 数据高效 SFT |

关键洞察：Omni-MLLMs 已具备潜在分析能力，只是在标准直接映射中处于休眠状态。PRD 结构作为**结构性催化剂**激活这些能力。

## 实验结果

### 主要性能对比（训练-free Plan-Decide 路径）

| 方法 | Music-AVQA | AVHBench(A-Hal) | AVHBench(V-Hal) | OmniBench | WorldSense |
|------|-----------|-----------------|-----------------|-----------|------------|
| Qwen-Omni-7B | 77.9 | 73.2 | 66.8 | 46.5 | 39.2 |
| **+CoM** | **78.8 (+0.9)** | **78.2 (+5.0)** | **79.7 (+12.9)** | **49.4 (+2.9)** | **41.9 (+2.7)** |
| Ola-7B | 69.6 | 54.2 | 71.3 | 40.2 | 41.1 |
| **+CoM** | 69.3 | **62.6 (+8.4)** | **73.8 (+2.5)** | **42.4 (+2.2)** | 40.0 |

**核心亮点**：在 AVHBench 幻觉基准上，CoM 实现了 **+12.9%（Audio-Hallucination）** 的提升，证明动态拓扑切换能有效抑制跨模态幻觉。

### 分析推理任务（Plan-Reason-Decide 路径）

| 方法 | AV-Odyssey | AV-Counting |
|------|-----------|------------|
| Qwen2.5-Omni-7B | 24.4 | 21.5 |
| +CoM (PD) | 27.0 | 23.6 |
| **+CoM (PRD)** | **31.6 (+7.2)** | **26.9 (+5.4)** |

PRD 路径在分析型任务上取得了更大提升，证明递进式认知深度对复杂推理至关重要。

### 消融实验：拓扑 x 任务协同

不同任务对不同拓扑有明确偏好：
- **并行拓扑**：单模态主导任务表现最佳（快速定位关键模态）
- **顺序拓扑**：需要传递逻辑的任务最佳（空间到音频接地）
- **交错拓扑**：需要细粒度对齐的任务最佳

## 关键洞察

1. **模态编排的物理性与训练同等重要**：优化模态的"物理排列"本身就能解锁 zero-shot 潜力，复杂训练设计不是唯一路径
2. **视觉偏差是结构性的而非语义性的**：模型在深层仍对视觉 token 保持系统性偏好，无论任务是否以视觉为中心
3. **模型已具备休眠的分析能力**：PRD 结构不需要新知识，只需激活已有能力——这对端侧部署极其有利
4. **训练-free 也能战胜重型 RL 优化模型**：架构驱动的方法在 7 个基准上与密集 SFT/RL 模型持平或超越

## 对手机端 AI 的意义

CoM 框架对端侧多模态 AI 有直接指导价值：
- **计算效率**：动态模态选择避免处理冗余模态，节省端侧算力和能耗
- **自适应深度**：简单查询走 Direct-Decide 路径（快速响应），复杂查询走 Reason-Decide 路径（深度分析），天然适配移动端延迟-精度权衡
- **免训练部署**：训练-free 设置适合端侧持续学习场景，无需频繁更新权重
- **幻觉抑制**：动态拓扑切换可减少端侧多模态推理中的跨模态干扰，提升可靠性

## 关联
- [[mma2a-modality-native-routing]] — CoM 的模态选择与路由机制互补，两者都在解决多模态信息流的最优配置问题
- [[multimodal-edge-pruning]] — CoM 的最小充分模态集与剪枝策略目标一致：只处理必要信息
- [[summer-multimodal-memory]] — 多模态推理需要持久化记忆来跨轮次保持上下文一致性
- [[synergy-agentic-web-agent]] — CoM 的 agentic 编排范式可推广到 Agent 间协作
- [[edge-cloud-offloading]] — CoM 的拓扑选择可与端云卸载决策联合优化
- [[edgeflow-cold-start]] — Direct-Decide 路径的免训练特性有利于冷启动场景
