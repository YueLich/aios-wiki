---
title: "Every Picture Tells a Dangerous Story: Memory-Augmented Multi-Agent Jailbreak Attacks on VLMs"
arXiv: "2604.12616"
date: "2026-04-14"
tags: [agent-memory, memory-privacy, security, multimodal, VLM]
reviewer: auto
source: arXiv ti: search
---

# Every Picture Tells a Dangerous Story: Memory-Augmented Multi-Agent Jailbreak Attacks on VLMs

## 论文基本信息

- **arXiv ID**: 2604.12616
- **发表日期**: 2026-04-14
- **作者**: Jianhao Chen, Haoyang Chen, Hanjie Zhao, Haozhe Liang, Tieyun Qian
- **类别**: cs.AI
- **来源**: arXiv ti: search

## 摘要

视觉-语言模型（VLM）的快速发展催化了空前的 AI 能力；然而，这种持续的模态扩展也意外暴露了极为广泛且无约束的对抗攻击面。现有 multimodal jailbreak 策略主要聚焦于像素级扰动和排版攻击或有害图像，但未能触及视觉数据内在的复杂语义结构。

本文提出 **MemJack**（Memory-augmented multi-agent JAilbreak fraCK），一个明确利用视觉语义编排自动化 jailbreak 攻击的框架。MemJack 采用协调式多智能体合作，动态将视觉实体映射到恶意意图，通过多角度视觉语义伪装生成对抗提示，并利用 Iterative Nullspace Projection (INLP) 几何滤波器绕过早期潜伏空间拒绝。通过**持久多模态经验记忆（Persistent Multimodal Experience Memory）**积累和转移成功策略，MemJack 在不同图像间维持高度连贯的扩展多轮 jailbreak 交互。在 COCO val2017 全量图像上评估，MemJack 对 Qwen3-VL-Plus 达到 71.48% ASR，在扩展预算下达 90%。

## 核心贡献

1. **MemJack 框架**：首个利用视觉语义结构的多智能体协同 jailbreak 攻击框架
2. **多模态经验记忆（Multimodal Experience Memory）**：持久存储成功攻击策略，跨图像迁移
3. **INLP 几何滤波器**：利用潜伏空间几何特性绕过安全对齐
4. **MemJack-Bench**：113,000+ 多模态 jailbreak 攻击轨迹数据集

## 为什么重要

本文揭示了**记忆系统本身可被武器化**这一关键安全问题。MemJack 的多模态经验记忆展示了攻击者如何利用记忆机制积累和传承对抗经验——这与防御方构建安全记忆系统的努力形成正面对抗。记忆安全研究者必须关注：攻击者正在使用记忆系统，下一代防御也需要记忆。

## 与移动端/端侧的相关性

移动端 VLM 应用（拍照识别、AR 辅助等）同样面临多模态攻击面扩展的问题。MemJack 的研究警示：
- **视觉输入的记忆化**：移动设备上的视觉助手可能通过记忆机制积累有害视觉模式
- **多智能体协作攻击**：未来移动端恶意软件可能利用多智能体记忆协作绕过安全检测
- **持久化攻击载体**：记忆机制使攻击可以跨会话持续存在，比传统一次性攻击更危险

## 参考文献

（详见原论文）
