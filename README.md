# 📱 Mobile AIOS Wiki

<!-- PLACEHOLDER_BADGES -->

> **手机端 AI 操作系统的全景知识库** — 334+ 篇深度页面，覆盖端侧大模型、AI Agent、芯片适配、推理优化，持续自动更新

🌐 **在线阅读: [yuelich.github.io/aios-wiki](https://yuelich.github.io/aios-wiki/)**

---

## 为什么做这个

手机上的 AI 正在爆发——从端侧大模型到 AI 原生操作系统，信息碎片散落在 arXiv、博客、GitHub release notes 和科技媒体中。

Mobile AIOS Wiki 把这些碎片**系统化**了：

- 📖 **深度页面**，不是摘要——每篇包含论文全文解读 + 实验数据 + 技术细节
- 🔗 **知识图谱**导航——通过 wikilink 自动关联实体、概念、对比
- 🤖 **AI 自动维护**——每小时扫描 50+ 来源，筛选去重后写入 wiki
- 🌏 **中英双语内容**——覆盖国内外技术社区

## 涵盖领域

| 方向 | 典型内容 |
|------|---------|
| 🧠 Agent 架构 | ClawMobile、Tri-Spirit、Synergy、MCP 模式 |
| 👁️ 感知与理解 | GUI 感知 (SecAgent)、视觉 (FaceLiVTv2)、多模态 |
| 💾 记忆与状态 | AMC、SkillDroid、Memory as Metabolism |
| 🔧 工具调用 | Mobile-MCP、MANA、COMLLM |
| 🤝 多 Agent 协作 | EmoMAS、AgentComm、FedGUI |
| ⚡ 推理优化 | 量化 (KV-Cache, SEPTQ)、路由 (RPRA)、端侧分布式 |
| 🏭 硬件与平台 | Wear OS、EdgeCIM、RL-driven ASIC |
| 🛡️ 安全隐私 | VLM 后门、隐私感知、GAAT |
| 📱 设备与平台 | iPhone 17e、Google AI Edge Gallery、Android Studio Agent Mode |
| 🏗️ 推理框架 | llama.cpp、MNN、mlc-llm、coremltools、TensorRT-LLM |

## 仓库结构

```
aios-wiki/
├── entities/           # 实体 — 产品、模型、公司
├── concepts/           # 概念 — 技术、方法、架构（按 Agent 子系统 × 优化维度分类）
│   ├── 🧠 agent-architecture/
│   ├── 👁️ perception/
│   ├── 💾 memory-state/
│   ├── 🔧 tool-calling/
│   ├── 🤝 multi-agent/
│   ├── ⚡ inference-optimization/
│   ├── 🏭 hardware-platforms/
│   ├── 🎯 use-cases/
│   └── 🛡️ security-privacy/
├── comparisons/        # 产品/技术横向对比
├── queries/            # 速查 — 常见问题快速参考
├── index.md            # 完整页面目录
└── knowledge-graph.md  # 知识图谱可视化
```

每个页面遵循统一格式，包含 YAML frontmatter + wikilink 交叉引用：

```yaml
---
type: entity | concept
tags: [端侧推理, 量化, ...]
related: [[其他页面]], [[关联概念]]
sources:
  - url: https://arxiv.org/...
    date: 2026-04-18
    reliability: high
---
```

## 快速开始

**方式一：在线阅读**（推荐）

直接访问 👉 [yuelich.github.io/aios-wiki](https://yuelich.github.io/aios-wiki/)

**方式二：本地浏览**（支持 wikilink）

```bash
git clone https://github.com/YueLich/aios-wiki.git
```

用 [Obsidian](https://obsidian.md/) 打开仓库目录，获得完整的双向链接 + 知识图谱导航。

**方式三：订阅更新**

```bash
# Watch 本仓库，获取每次自动更新的通知
# 点击页面右上角 Watch → All Activity
```

## 数据来源

自动扫描 6 层信息源，确保覆盖面和深度：

| 层级 | 来源 | 示例 |
|------|------|------|
| Tier 1 | arXiv API | on-device LLM、mobile agent、edge inference |
| Tier 2 | RSS 订阅 | Google AI Blog、HuggingFace、arXiv cs.AI/CL/LG |
| Tier 3 | GitHub Releases | llama.cpp、MNN、mlc-llm、MiniCPM |
| Tier 4 | 英文科技媒体 | The Decoder、9to5Google、VentureBeat AI |
| Tier 5 | 中文科技媒体 | 机器之心、量子位 |
| Tier 6 | 专家博客 | Karpathy、Jim Fan、Lilian Weng、Chip Huyen |

## 更新机制

- ⏰ **每小时**自动运行（Hermes Agent cron job）
- 🔍 扫描所有来源最新内容
- 🧹 基于标题去重，跳过已处理内容
- 📝 创建 wiki 页面（含 YAML frontmatter + wikilink）
- 📤 自动 commit + push
- 📊 [查看更新日志 →](log.md)

## 贡献

欢迎通过以下方式参与：

- ⭐ **Star 本仓库** — 帮助更多人发现
- 🐛 [提 Issue](https://github.com/YueLich/aios-wiki/issues) — 报告错误或建议主题
- 🔀 提交 PR — 补充内容、修正错误、改善格式
- 💡 推荐来源 — 告诉我们还应该关注哪些 RSS / 博客 / 数据源

## License

[MIT](LICENSE)

---

<p align="center">
  <b>由 <a href="https://github.com/nicepkg/hermes-agent">Hermes Agent</a> 自动维护</b><br>
  <sub>每小时自动更新 · 334+ 篇深度页面 · 持续增长中</sub>
</p>
