---
title: "FSFM: A Biologically-Inspired Framework for Selective Forgetting of Agent Memory"
arXiv: 2604.20300
date: 2026-04-22
authors: ["Yingjie Gu", "Wenjian Xiong", "Liqiang Wang", "Pengcheng Ren", "Chao Li", "Xiaojing Zhang", "Yijuan Guo", "Qi Sun", "Jingyao Ma", "Shidang Shi"]
tags: [agent-memory, memory-compression, selective-forgetting, neuro-inspired, privacy]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.20300
- **发表日期**: 2026-04-22
- **作者**: Yingjie Gu, Wenjian Xiong, Liqiang Wang, Pengcheng Ren, Chao Li, Xiaojing Zhang, Yijuan Guo, Qi Sun, Jingyao Ma, Shidang Shi
- **方向**: 记忆压缩与遗忘（选择性遗忘）

## 摘要

**背景**：当前 LLM Agent 研究大多聚焦于记忆的"保留"（retention），而对选择性遗忘（selective forgetting）——受人类认知过程（海马索引/记忆巩固理论和艾宾浩斯遗忘曲线）启发的机制——探索不足。

**核心论点**：在资源受限环境中，精心设计的遗忘机制与记忆本身同样重要，在三个维度带来收益：

1. **效率**：通过智能记忆剪枝降低存储和检索开销
2. **质量**：动态更新过时偏好和上下文，提升输出质量
3. **安全**：主动遗忘恶意输入、敏感数据和隐私侵害内容

**方法**：FSFM 建立遗忘机制taxonomy：被动衰减型、主动删除型、安全触发型、自适应增强型。基于 LLM Agent 架构和向量数据库的进展，提出详细规格、实现策略和受控实验验证。

**实验结果**：访问效率 +8.49%，内容质量（信噪比）+29.2%，安全风险 100% 消除。

## 核心贡献

1. **遗忘机制taxonomy**：首次系统分类 Agent 记忆的选择性遗忘机制（被动/主动/安全触发/自适应）
2. **认知科学理论基础**：将海马索引理论、记忆巩固机制和艾宾浩斯遗忘曲线形式化引入 AI 遗忘建模
3. **三维评估框架**：从效率、质量、安全三个维度量化遗忘机制收益
4. **神经科学与 AI 的桥梁**：为实际部署提供认知可行的遗忘策略，同时满足伦理和合规要求

## 为什么重要

选择性遗忘是真正智能 Agent 系统的必备能力——人类大脑并非记录所有经历，而是通过遗忘保留关键信息、清除过时/有害数据。FSFM 首次从系统化角度论证了这一能力：

- **隐私合规**：GDPR 等法规要求"被遗忘权"，FSFM 提供技术实现路径
- **资源效率**：端侧设备存储有限，主动遗忘比被动积累更可持续
- **安全防护**：防止记忆中的恶意提示词注入（prompt injection）和隐私泄露

## 与端侧/移动端的相关性

FSFM 的遗忘机制对端侧 Agent 至关重要：

- **隐私保护**：可穿戴设备和智能手机上的 Agent 需要即时遗忘敏感上下文（如位置、健康数据）
- **能效优化**：遗忘比积累后再压缩更节能，适合低功耗场景
- **法规合规**：移动端 AI 面临更严格的隐私法规，被遗忘权是刚需

## 参考文献

- arXiv: 2604.20300 | https://arxiv.org/abs/2604.20300
