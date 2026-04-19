---
type: concept
tags: [on-device, llm, social-media, feed-curation, privacy, personalization]
related: [[huoziime-ondevice-ime]], [[gemma4-ondevice]], [[agent-persistent-identity]]
sources:
  - url: https://imbue.com/product/bouncer/
    title: "Bouncer: Heal your feed - Imbue"
    date: 2026-04-08
    reliability: high
  - url: https://news.ycombinator.com/item?id=47706293
    title: "HN: Control your X/Twitter feed using a small on-device LLM"
    date: 2026-04-09
    reliability: medium
created: 2026-04-19
updated: 2026-04-19
---

# Bouncer: 端侧 LLM 治理社交信息流

> Imbue 推出 Bouncer——用端侧小模型对抗平台算法，让用户夺回 Twitter 信息流的控制权。

## 核心问题

社交平台的推荐算法以**成瘾性而非愉悦感**为优化目标，用户被动接受算法"投喂"的内容，丧失了对信息消费的主动权。传统"关闭推荐"方案让用户失去了发现有价值内容的能力。

## 解决方案

Bouncer 在设备本地运行一个小 LLM，作为信息流的"守门人"：

- **端侧推理** — 所有数据处理在设备上完成，不发送到云端
- **内容过滤** — 识别并过滤低质量、操纵性、情绪激化的内容
- **保留价值** — 保留实时信息、本地政治、兴趣发现等高价值内容
- **用户主权** — 用户定义自己的标准，而非接受平台优化

## 技术路线

- 使用小参数模型（具体大小未公开，但定位为"small on-device LLM"）
- 在设备上完成推理，零数据外传
- 与 Twitter/X 的信息流集成

## 为什么重要

Bouncer 开创了一个新的端侧 AI 应用范式：**算法对抗 Agent**。

传统思路是"让平台提供更好的算法"，Bouncer 的思路是"让用户部署自己的算法"。这需要：
1. 足够小的模型以在端侧实时运行
2. 足够智能以理解内容质量和用户偏好
3. 完全在本地以保护隐私

这种模式可以推广到任何推荐系统——YouTube、TikTok、新闻 App 等。端侧 Agent 不仅是"执行任务"，还可以成为用户与算法之间的**中介层**。

HN 上获得 15 点关注，反映社区对"算法自主权"议题的共鸣。

## 关联

- [[huoziime-ondevice-ime]] — 端侧 LLM 的个性化应用
- [[gemma4-ondevice]] — 端侧模型能力参考
- [[agent-persistent-identity]] — Agent 如何持续学习用户偏好
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧推理的能力边界
