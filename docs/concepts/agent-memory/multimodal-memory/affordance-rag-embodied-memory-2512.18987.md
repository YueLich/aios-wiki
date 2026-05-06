---
title: "Affordance RAG: Hierarchical Multimodal Retrieval with Affordance-Aware Embodied Memory for Mobile Manipulation"
arXiv: 2512.18987
date: 2025-12-22
tags: [agent-memory, embodied-memory, affordance, mobile-robot, multimodal-RAG]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Ryosuke Korekata, Quanting Xie, Yonatan Bisk, Komei Sugiura
- **提交日期**: 2025-12-22
- **方向**: 具身记忆 / 移动操作 / Affordance感知

## 摘要

本研究解决了开放词汇移动操作问题——机器人需要根据自由形式的自然语言指令，将各种物体运送到容器中。该任务涉及理解视觉语义和操作动作的affordance，具有很大挑战性。

为此，Affordance RAG提出了一种**零样本层次化多模态检索框架**，从预探索图像构建Affordance感知的具身记忆。模型基于区域和视觉语义检索候选目标，用affordance分数重排序，使机器人能够识别在真实世界中可能执行的操作选项。

## 核心贡献

1. **Affordance感知具身记忆**：从预探索图像中构建，存储场景中可执行操作的知识
2. **层次化多模态检索**：区域级+语义级双重检索，提高召回精度
3. **Affordance分数重排序**：不仅考虑视觉相似性，还考虑动作可行性
4. **零样本泛化**：无需在目标环境进行额外训练
5. **85%任务成功率**：在真实机器人移动操作实验中验证有效

## 方法详解

### 问题背景
移动操作机器人需要：
- 理解自然语言指令（如"把桌子上的杯子拿过来"）
- 在未知环境中定位目标物体
- 判断机器人能否实际执行该操作（affordance）

### 核心方法
1. **预探索阶段**：机器人在新环境中自主探索，建立场景图像数据库
2. **具身记忆构建**：从预探索图像中提取affordance知识——哪些物体可以被抓取、放置到哪些位置
3. **层次化检索**：先检索图像候选，再在区域内进行细粒度匹配
4. **Affordance重排序**：综合视觉语义相似性和动作可行性评分

### 与移动端/端侧的相关性
对于移动端部署的视觉记忆系统，Affordance RAG的预探索+检索两阶段框架非常适合：
- 预探索阶段可以离线完成，建立本地场景记忆
- 运行时只需进行高效检索，无需重推理
- 零样本能力减少了在线计算负担

## 为什么重要

Affordance RAG将**物理可执行性**引入记忆检索，突破了纯视觉相似的局限。对于家庭机器人、服务机器人等需要在真实物理环境中长期运行的Agent，知道"能做什么"和知道"是什么"同样重要。

## 参考文献

- 相关项目: 基于大规模室内环境的移动操作实验
