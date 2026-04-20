---
type: entity
tags: [tts, on-device, ios, kokoro, privacy, offline, audiobook, swift, thermal-management]
related: [[kitten-tts]], [[litertlm-swift-ios]], [[xybrid-ondevice-ai-sdk]], [[nanowakeword-wake-word]]
sources:
  - url: https://loudreader.io
    title: "LoudReader — Every text is an audiobook"
    date: 2026-04-19
    reliability: medium
  - url: https://news.ycombinator.com/item?id=43688921
    title: "Show HN: I built on-device TTS app because I run out of audiobooks on a flight"
    date: 2026-04-19
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# LoudReader: 端侧 TTS 阅读应用

> 基于 Kokoro 的 iOS 端侧 TTS 应用，完全离线运行，支持 EPUB/PDF 导入，8 种 AI 语音，实时逐句高亮同步。开发者用 Claude Code + Codex 在周末开发了 2-3 个月。

## 核心问题

现有的 TTS 和有声书服务大多依赖云端 API——需要上传文档到第三方服务器、消耗移动数据、受网络延迟影响。在飞行模式或隐私敏感场景（法律文件、工作备忘录）下，用户需要完全端侧的解决方案。

## 方法/架构

### 技术栈
- **TTS 引擎**: Kokoro（开源 TTS 模型）为主力
- **降级方案**: KittenTTS（更轻量的 TTS）用于旧设备
- **分词器**: misaki（从 Python 移植到 Swift）
- **平台**: iOS，使用 Swift 原生开发
- **运行模式**: 完全离线，零网络依赖

### 关键技术挑战与解决方案

**1. 流式合成**
- 问题: 等待整句合成完成会导致明显延迟
- 方案: 流式合成——播放在句子完成前就开始，实现"边生成边播放"
- 效果: 用户感知延迟大幅降低

**2. 热管理策略**
- 问题: TTS 推理持续消耗 CPU/GPU，导致设备发热和降频
- 方案: 实现了热监控和自适应策略——检测设备温度并在需要时降低处理质量
- 这是端侧持续推理应用的核心工程挑战

**3. 设备兼容性降级**
- iPhone 14 Pro 及以上: Kokoro 运行流畅
- iPhone 12 Pro 等旧设备: 自动降级到 KittenTTS（更轻量但质量略低）
- 自适应模型选择策略

### 应用功能
- 支持 EPUB 和 PDF 导入
- 70,000+ 本 Project Gutenberg 免费经典书籍
- 8 种端侧 AI 语音
- 逐句高亮同步（阅读 + 听觉双通道）
- 0.3x 到 3.0x 速度调节
- 睡眠定时器、白噪音音景、夜间模式
- 阅读笔记和书签

## 实验结果/关键数据

| 指标 | 详情 |
|------|------|
| 模型大小 | Kokoro + KittenTTS 降级 |
| 最低支持设备 | iPhone 12 Pro（降级模式） |
| 推荐设备 | iPhone 14 Pro 及以上 |
| 网络需求 | 零（安装后完全离线） |
| 语音数量 | 8 种 |
| 开发周期 | 2-3 个月（周末兼职） |
| 开发工具 | Claude Code + Codex |

## 关键洞察

1. **端侧 TTS 的工程门槛**: 模型推理本身只是"第一步"——流式合成、热管理、设备适配等工程细节才是让产品"不像 demo"的关键。这反映了端侧 AI 应用的普遍规律。

2. **热管理是端侧持续推理的核心挑战**: 持续的 TTS 推理会触发设备热降频。LoudReader 的热监控策略（检测温度 → 动态调整质量）是端侧 AI 应用的必备技术。

3. **多模型降级策略**: 为不同设备性能准备多个模型版本，根据运行时条件自动切换。这种模式值得所有端侧 AI 应用借鉴。

4. **AI 编程工具的杠杆效应**: 一个人用 Claude Code + Codex 在周末开发出完整的端侧 AI 应用，展示了 AI 辅助开发在端侧 AI 民主化中的作用。

## 为什么重要

LoudReader 是端侧 AI 应用的优秀案例研究：
- **隐私优先**: "Nothing leaves your phone" 的设计哲学
- **实用工程**: 展示了从模型到产品的完整工程链路（流式合成、热管理、降级策略）
- **开发效率**: Claude Code + Codex 辅助的开发模式
- **商业模式验证**: 在 App Store 上的端侧 AI 应用可行性

对手机端 AIOS 生态来说，LoudReader 证明了端侧 TTS 已经可以做到"不只是 demo"的水平。

## 关联

- [[kitten-tts]] — LoudReader 使用的降级 TTS 引擎
- [[litertlm-swift-ios]] — iOS 端侧 LLM 框架，类似的 Swift + 端侧推理模式
- [[xybrid-ondevice-ai-sdk]] — 端侧 AI SDK，提供类似的推理能力
- [[nanowakeword-wake-word]] — 另一个端侧音频 AI 应用案例
