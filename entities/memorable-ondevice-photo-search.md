---
type: entity
tags: [on-device, iphone, photo-search, apple-neural-engine, privacy, vision]
related: [[coremltools-9]], [[apple-intelligence]], [[gemma4-ondevice]]
sources:
  - url: https://hn.algolia.com/api/v1/items/47791221
    title: "HN: Show HN: Memorable – On-device AI search for iPhone photos"
    date: 2026-04-17
    reliability: medium
  - url: https://apps.apple.com/us/app/memorable-ai-photo-search/id6762152034
    title: "Memorable - AI Photo Search (App Store)"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Memorable: 完全端侧的 iPhone AI 照片搜索

> 利用 Apple Neural Engine 在设备本地构建照片搜索索引，零云端、零追踪、零广告，照片不离开设备。

## 核心问题

iPhone 用户的照片库日益庞大，但系统自带的照片搜索能力有限。用户需要 "找到去年夏天在柏林拍的照片" 这样的语义级搜索，而非简单的日期/相册筛选。云方案（如 Google Photos）虽有强大搜索，但意味着照片数据上传云端。

## 方法/架构

### 端到端本地处理

Memorable 的核心设计原则是**完全设备端**：

1. **首次使用**：利用 Apple Neural Engine 处理全部照片，构建私有搜索索引
2. **后续搜索**：即时返回结果，无需网络
3. **零数据外传**：照片不离开设备，不传像素到任何服务器

### 三维度搜索能力

| 搜索维度 | 示例 |
|---------|------|
| **内容** | "狗"、"生日蛋糕"、"红色汽车" |
| **地点** | "柏林"、"圣地亚哥"、"胡佛大坝" |
| **时间** | "去年夏天"、"2024 圣诞节"、"昨天" |
| **组合** | "上周柏林的食物" |

### 隐私架构

- **零账号系统**：无需注册或登录
- **零追踪**：不收集任何分析数据
- **零广告**：无任何广告展示
- **唯一的网络调用**：Apple 内置定位服务（GPS 坐标 → 地名），这是标准 iOS 功能

## 实验结果/关键数据

- 应用体积 **760.4 MB**（AI 模型内嵌）
- 仅支持 iPhone（利用 Apple Neural Engine）
- 免费下载，含内购
- 开发商：BlockDeep Labs

## 关键洞察

**"Privacy First" 的真正含义**：Memorable 的隐私承诺不是 "你的数据在我们这很安全"（privacy theater），而是 "我们永远看不到你的数据"。这是一个重要的产品哲学差异——真正的隐私保护是架构层面的（数据不离开设备），而非信任层面的（相信我们不会看）。

**AI 模型体积 vs 用户体验的 trade-off**：760 MB 的应用体积不小，但换来的是离线即时搜索能力和绝对隐私。对于注重隐私的用户群体，这个 trade-off 是值得的。

**Apple Neural Engine 是端侧 AI 的关键基础设施**：Memorable 证明了 Apple 的 Neural Engine 不仅是营销噱头，而是真正能支撑复杂 AI 推理任务的硬件。这为更多端侧 AI 应用提供了信心。

## 为什么重要

对于手机端 AIOS：
- 证明了 **端侧 AI 搜索** 在消费级 App 中的可行性和用户接受度
- 展示了 **"零云端"** 是一个真实可感知的产品卖点
- Apple Neural Engine + CoreML 的技术栈被充分验证，其他开发者可以复用
- 为手机厂商的端侧 AI 搜索功能提供了参考实现

## 关联

- [[coremltools-9]] — Memorable 可能使用 CoreML 工具链将 AI 模型转换为 Apple Neural Engine 可执行格式
- [[gemma4-ondevice]] — Gemma 4 的端侧多模态能力可与此类应用协同，提供更强大的理解力
- [[edgeflow-cold-start]] — 首次索引构建的冷启动优化是此类应用的关键用户体验点
