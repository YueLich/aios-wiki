---
type: concept
tags: [agent-memory, multimodal, social-robots, embodied-ai, memory-selectivity, perception]
related: [[amc-adaptive-memory-crystallization]], [[agent-persistent-identity]], [[mga-memory-gui-agent]], [[memp-episodic-memory]], [[memory-worth-governance]]
sources:
  - url: https://arxiv.org/abs/2604.12081
    title: "Human-Inspired Context-Selective Multimodal Memory for Social Robots"
    date: 2026-04-16
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# SUMMER: 仿人类上下文选择性多模态记忆框架

> 为社交机器人设计的端到端多模态记忆系统，基于人类记忆选择性原理，实现情感显著性和新颖性驱动的记忆存储与检索。

## 核心问题

当前大多数 Agent 记忆系统存在两个关键缺陷：

1. **非选择性存储**：现有系统（MemoryBank、Memory Sandbox 等）采用文本为主的记忆方式，对所有交互进行无差别存储，导致无关信息淹没关键记忆
2. **模态单一**：视觉记忆通常被转换为文本描述，丢失了原始感知信息的丰富性，限制了机器人在需要视觉细节回忆时的表现

对于在连续多模态感知流中运行的社交机器人和移动 Agent，需要一种**选择性、多模态**的记忆机制来模拟人类如何优先记住情感显著和新颖的经历。

## 方法/架构

SUMMER（**S**electivity **U**nified **M**ultimodal **M**emory for **E**mbodied **R**obots）框架包含三个核心组件：

### 1. 选择性记忆存储模块
- **情感显著性检测**：使用 OpenFace 3.0 进行面部表情分析，识别交互中的情感强度
- **新颖性评估**：基于 CLIP-ViT-L/14 计算当前场景与已有记忆的视觉相似度，相似度低于阈值的场景被视为"新颖"
- **场景复杂度估计**：使用 ICNet 评估视觉场景的信息密度
- 三个信号融合决定是否将当前交互存入长期记忆——类似人类如何根据内在（感知独特性）和外在（情感强度、个人相关性）线索筛选记忆

### 2. 多模态检索模块
- **文本检索**：使用 jina-embeddings-v4 对查询和对话记忆进行编码
- **视觉检索**：使用 SigLIP-so400m-P14 对查询和场景图像进行编码
- **加权融合**：sim_final = α · sim_img_norm + (1-α) · sim_text_norm（α 最优值约 0.7）
- 无额外训练，即插即用

### 3. 支撑模块
- **意图分类器**：LLM 推理判断用户意图（ProfileUpdate / SessionEnd / Continue）
- **用户识别**：Levenshtein 比率（姓名）+ InsightFace buffalo_s（面部）双重验证
- **隐私保护**：记忆操作仅在用户自愿提供姓名后激活，支持永久删除

## 实验结果

### 选择性存储评估
- 自建 81 张社交场景数据集（Sora 生成），25 名人类标注者评分记忆性（1-9 Likert）
- SUMMER 的选择性存储机制与人类记忆性评分高度一致，情感线索和新颖性是主要驱动因素

### 多模态检索评估
在 Flickr8k、Flickr30k、MS COCO 上对比：
| 方法 | 描述 |
|------|------|
| 纯文本检索 | 查询嵌入 vs 文本场景描述 |
| 纯视觉检索 | 查询嵌入 vs 图像嵌入 |
| **多模态融合** | **持续优于两种单模态基线** |

最佳性能出现在 α=0.7（视觉权重较高），跨不同编码器组合均成立。

### 运行时性能
- SUMMER 平均响应时间：**0.87 ± 0.16 秒**（768×512 输入）
- 基线 VLM：约 0.47 秒
- 额外开销仅 0.4 秒用于检索和图像处理
- **远低于人机交互 2 秒响应阈值**，适合实时对话

## 关键洞察

1. **Train-free 设计是关键优势**：不需要额外微调即可集成到不同机器人平台，对移动端 Agent 部署具有重要意义——避免了 GPU 训练需求
2. **情感驱动的记忆选择**比简单的固定间隔快照存储更高效——类比人类不会记住每一刻，而是优先编码有意义的经历
3. **α=0.7 的视觉偏好**揭示了多模态记忆中视觉信息的重要性——移动端 Agent 在屏幕理解和视觉场景回忆中同样需要重视视觉编码
4. **隐私优先设计**：选择性存储+用户可控删除，符合移动端 Agent 对隐私的严格要求

## 为什么重要

SUMMER 对手机端 AIOS 生态的启示：

1. **Agent 记忆架构参考**：选择性+多模态的记忆模式可直接迁移到手机端 AI 助手——不需要记住每一次交互，而是优先记住情感显著和新颖的事件
2. **轻量化部署可行**：Train-free 设计意味着手机端可以集成类似的记忆系统而不需要云端训练
3. **隐私合规**：用户自主控制的记忆管理策略符合 Apple Intelligence、HyperOS 等端侧 AI 的隐私优先理念
4. **与现有端侧记忆工作的互补**：AMC（自适应记忆结晶）、Memp（情景记忆）、Memory Governance 等工作关注不同维度，SUMMER 提供了多模态感知层面的记忆选择机制

## 关联
- [[amc-adaptive-memory-crystallization]] — AMC 关注知识记忆的自适应压缩，SUMMER 关注感知记忆的选择性存储
- [[agent-persistent-identity]] — 用户识别模块与持久化身份架构互补
- [[mga-memory-gui-agent]] — GUI Agent 记忆关注操作轨迹，SUMMER 关注社交/情感记忆
- [[memp-episodic-memory]] — Memp 是纯文本情景记忆，SUMMER 扩展到多模态
- [[memory-worth-governance]] — 记忆价值治理可为 SUMMER 的选择性阈值提供策略指导
- [[derm3r-multimodal-agent]] — 同为多模态 Agent，Derm-3R 在医疗领域应用类似的记忆检索思路
