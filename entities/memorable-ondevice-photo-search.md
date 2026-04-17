---
type: entity
tags: [on-device, iphone, photo-search, neural-engine, privacy, apple, multimodal, edge-ai]
related: [[anylanguagemodel-apple]], [[iphone-17e]], [[secagent-mobile-gui]]
sources:
  - url: https://apps.apple.com/us/app/memorable-ai-photo-search/id6762152034
    title: "Memorable - AI Photo Search (App Store)"
    date: 2026-04-17
    reliability: high
  - url: https://hn.algolia.com/api/v1/search?query=memorable+on-device+ai+iphone+photos&tags=story
    title: "Show HN: Memorable – On-device AI search for iPhone photos"
    date: 2026-04-17
    reliability: medium
created: 2026-04-17
updated: 2026-04-17
---

# Memorable: 端侧 AI 照片搜索

> 一款完全在 iPhone Neural Engine 上运行的 AI 照片搜索应用——零云端、零账号、零数据外传。

## 核心问题

iPhone 用户拥有成千上万张照片，但 iOS 原生搜索能力有限（主要依赖元数据和基础标签）。云端 AI 照片搜索方案（如 Google Photos）需要上传照片到服务器，存在隐私风险。Memorable 提出了一个极端隐私优先的方案：所有 AI 推理完全在设备端完成。

## 架构与实现

### 技术架构

- **推理引擎**：Apple Neural Engine（ANE），利用 iPhone 的专用 NPU
- **索引构建**：首次打开时，离线处理全部照片库建立私有搜索索引
- **搜索维度**：
  - 内容搜索："dog"、"birthday cake"、"red car"
  - 地点搜索："Berlin"、"San Diego"（利用 GPS 坐标→Apple 位置服务转换）
  - 时间搜索："last summer"、"Christmas 2024"
  - 组合搜索："food in Berlin last week"
- **推理延迟**：首次索引后，每次搜索即时返回

### 隐私设计

这是一个值得研究的隐私架构：

1. **零网络请求**（除 Apple 内置位置服务）：应用唯一的网络调用是将 GPS 坐标转为地名，这是 iOS 系统级功能
2. **无账号系统**：不需要注册或登录
3. **无追踪/广告**：不收集任何分析数据
4. **无像素外传**：照片数据不离开设备，"Not even a single pixel"

### 规模与商业

- 应用大小：760.4 MB（包含 AI 模型权重）
- 免费起步 + 内购模式
- 仅支持 iPhone（利用 Neural Engine）
- 开发商：BlockDeep Labs

## 关键洞察

### 端侧多模态 AI 的产品化验证

Memorable 证明了几个重要趋势：

1. **完整的多模态模型可以在手机端运行**：视觉理解 + 语义搜索 + 时间推理，全部在 A 系列芯片的 Neural Engine 上完成
2. **760MB 的模型大小是可接受的**：对于一个离线索引应用，用户愿意用存储换隐私
3. **"隐私即卖点" 的商业模型可行**：不需要用数据换免费服务

### 对手机端 AIOS 的启示

- **搜索是端侧 AI 的杀手级应用**：不需要实时响应、不需要最新知识、不需要多轮对话——照片搜索是端侧推理的完美场景
- **ANE 的能力边界在扩展**：之前 ANE 主要用于 Face ID 和相机处理，现在可以运行完整的多模态搜索模型
- **与 Apple Intelligence 的互补**：Memorable 填补了 Apple 自有方案在照片语义搜索上的空白

## 关联

- [[anylanguagemodel-apple]] — Apple 端侧模型生态
- [[iphone-17e]] — iPhone 硬件与端侧 AI 能力
- [[secagent-mobile-gui]] — 移动端 Agent 的屏幕感知
- [[gemma4-ondevice]] — 对比 Android 端的端侧 AI 方案
