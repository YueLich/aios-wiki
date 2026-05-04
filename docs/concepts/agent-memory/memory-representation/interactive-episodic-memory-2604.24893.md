---
title: "Interactive Episodic Memory with User Feedback"
arXiv: 2604.24893
date: 2026-04-27
authors: "Nikesh Subedi (University of Utah)"
tags: [agent-memory, episodic-memory, vision-language, user-feedback, egocentric-video]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv**: 2604.24893v1
- **发表**: 2026-04-27
- **作者**: Nikesh Subedi (University of Utah)
- **方向**: 多模态情景记忆 / 人机交互
- **开源**: 待确认

---

## 任务定义

**Episodic Memory with Natural Language Queries (EM-NLQ)**

用户用自然语言提问：
> "Where did I place the mug?"
> "Why did the task fail?"

系统需要在**长时间自我中心视频（egocentric video）** 中搜索答案。

### 挑战

- 视频时间跨度长，记忆稀疏
- 自然语言查询的语义与视频内容匹配困难
- 需要理解空间位置、时间顺序、因果关系

---

## 方法

### 1. User Feedback Generation Recipe

将人类反馈纳入记忆检索循环：

1. **Reference Span Sampling** — 从视频中采样参考片段
2. **Response Captioning and Explanation Generation** — 生成对响应的描述和解释
3. **Feedback Generation** — 基于参考生成反馈信号

### 2. EM-QnF Dataset

**Episodic Memory with Question and Feedback** — 包含用户反馈的情景记忆数据集

### 3. FALM: Feedback ALignment Module

**核心架构创新：**

- **FALM Architecture** — 反馈对齐模块
- **Alignment Supervision** — 对齐监督信号
- **FALM Training Objective** — 训练目标
- **ReFocus: FALM Integration** — 将FALM集成到主模型中
- **Multi-Turn Feedback Extension** — 多轮反馈扩展

---

## 关键洞察

### 用户反馈能显著改善检索质量

初始检索可能不准确，但通过多轮用户反馈：
- 模型学会关注正确的视频片段
- 错误反馈帮助模型排除不相关区域
- 逐步收敛到正确记忆

### ReFocus 机制

FALM通过反馈信号重新调整模型注意力权重，将"关注错误区域"纠正为"关注正确区域"。

---

## 为什么重要

首次系统性地将**用户反馈**作为主动学习信号引入情景记忆检索。这是记忆系统从"被动存储-查找"到"主动交互-校正"的重要一步。

### 与移动端/端侧的相关性

- **可穿戴设备（smartwatch/AR glasses）**：第一人称视频记忆 + 即时用户反馈是自然交互范式
- **家庭机器人**：用户通过自然语言纠正机器人记忆
- **端侧隐私**：反馈学习不需要将原始视频上传云端
