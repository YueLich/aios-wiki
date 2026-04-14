# 📱 Mobile AIOS Wiki

> 手机端 AI 操作系统知识库 — 自动化增量更新，追踪端侧 AI 最新进展

## 这是什么

这是一个由 [Hermes Agent](https://github.com/nicepkg/hermes-agent) 自动维护的知识库，专注于**手机端 AI 操作系统 (Mobile AIOS)** 领域。

每小时自动扫描 50+ 来源，筛选、去重、合成后推送到本仓库。

**关注领域：**
- 端侧大模型部署与推理优化
- 手机 AI 助手与 Agent 框架
- AI 原生操作系统（小米 HyperAI、华为 HarmonyOS AI、三星 Galaxy AI 等）
- NPU / 端侧芯片与模型适配
- 端侧多模态（语音、视觉、文本）
- 量化、蒸馏、剪枝等移动端优化技术
- 隐私计算与端云协同

## 目录结构

```
aios-wiki/
├── SCHEMA.md           # 知识图谱 Schema（领域定义、页面格式、去重规则）
├── index.md            # 页面目录（按主题分组）
├── index.json          # 去重索引（已处理标题 + 已知主题）
├── log.md              # 更新日志（每次变更记录）
├── sources.json        # 来源配置（arXiv、RSS、GitHub releases）
├── entities/           # 实体页面 — 公司、产品、模型
├── concepts/           # 概念页面 — 技术、方法、架构
├── comparisons/        # 对比页面 — 产品/技术对比
├── queries/            # 速查页面 — 常见问题
└── raw/                # 原始资料
    ├── articles/       # 文章原文/摘要
    ├── papers/         # 论文摘要
    ├── transcripts/    # 视频/播客转录
    └── assets/         # 图片、图表
```

## 数据来源

| 层级 | 来源 | 说明 |
|------|------|------|
| Tier 1 | arXiv API | 6 组精准搜索（on-device LLM、mobile agent、edge inference 等） |
| Tier 2 | RSS Feeds | Google AI Blog、Android Dev、HuggingFace、The Decoder、arXiv cs.AI/CL/LG 等 |
| Tier 3 | GitHub Releases | llama.cpp、MNN、mlc-llm、MiniCPM、coremltools、TensorRT-LLM |
| Tier 4 | 英文科技媒体 | The Decoder、9to5Mac、9to5Google、VentureBeat AI |
| Tier 5 | 中文科技媒体 | 机器之心、量子位 |
| Tier 6 | 专家博客 | Karpathy、Jim Fan、Lilian Weng、Chip Huyen、Simon Willison |

## 更新频率

- ⏰ **每小时**自动运行
- 🔍 扫描所有来源的最新内容
- 🧹 基于标题去重，跳过已处理内容
- 📝 对新内容创建 wiki 页面（含 YAML frontmatter + wikilinks）
- 📤 自动 commit + push 到本仓库
- 📱 Telegram 推送中文学习摘要

## 页面格式

每个 wiki 页面遵循统一格式：

```yaml
---
type: entity|concept
tags: [relevant, tags]
related: [[wikilink1]], [[wikilink2]]
sources:
  - url: https://...
    date: 2026-04-14
    reliability: high|medium|low
created: 2026-04-14
updated: 2026-04-14
---

# Title

内容...（至少包含 2 个 [[wikilink]] 引用）
```

## 使用方式

```bash
# 克隆仓库
git clone https://github.com/YueLich/aios-wiki.git

# 定期拉取最新内容
cd aios-wiki && git pull

# 在 Obsidian / Logseq 等工具中打开以获得 wikilink 支持
```

推荐用 [Obsidian](https://obsidian.md/) 打开，可以利用 wikilink 建立知识图谱导航。

## 自动化

本仓库由 Hermes Agent 的 cron job 自动维护：
- **Job ID:** `769328ef54d6`
- **Schedule:** `0 * * * *`（每小时整点）
- **Skill:** `mobile-ai-wiki-update`
- **去重策略:** 基于 `index.json` 的 `recently_processed_titles`（最近 100 条标题）

## License

MIT
