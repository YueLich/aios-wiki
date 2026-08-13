

# 📱 Mobile AIOS Wiki

<!-- PLACEHOLDER_BADGES -->
[![Star History Chart](https://api.star-history.com/svg?repos=YueLich/aios-wiki&type=Date)](https://star-history.com/#YueLich/aios-wiki&Date)

**A curated knowledge base on mobile/on-device AI operating systems** — agent architectures, on-device LLMs, chip-level inference optimization, and the frameworks that run them.

🌐 **Read online: [yuelich.github.io/aios-wiki](https://yuelich.github.io/aios-wiki/)**

[中文说明见下](#-mobile-aios-wiki-中文)

---

## Why this exists

Mobile AI is moving fast — on-device LLMs, GUI agents, edge inference engines — and the coverage is scattered across arXiv, GitHub release notes, and tech blogs. This wiki curates that firehose into pages you can actually trust: each entry cites its sources, links to related concepts via wikilinks, and is either **reviewed** (cross-checked against ≥2 independent sources) or clearly marked as a **draft** awaiting review — see [AGENTS.md](AGENTS.md) for the exact bar.

## Featured: on-device inference engines, 2026

| Engine | Maintainer | Platform focus | Notable in latest release | Notes |
|---|---|---|---|---|
| [llama.cpp](docs/entities/llamacpp.md) | ggml-org (OSS) | Cross-platform — CPU, Metal, Vulkan, OpenCL, Android/iOS | Continuous quantization + backend work across 30+ tracked builds (b8791–b8880) | The reference runtime most other engines get compared against |
| [MNN 3.5.0](docs/entities/mnn-350.md) | Alibaba | Mobile-first — Android/iOS, any Vulkan-capable GPU | Vulkan LLM inference without vendor SDKs; TurboQuant TQ3/TQ4 KV-cache quantization | Full LLM inference stack, not just a generic tensor runtime |
| [coremltools 9.0](docs/entities/coremltools-9.md) | Apple | iOS/macOS | Python 3.13 support | A **model converter**, not a runtime — bridges PyTorch/TF models into Core ML |
| [TensorRT-LLM v1.2.1](docs/entities/tensorrt-llm-v121.md) | NVIDIA | Server GPU (not mobile) | PagedAttention, continuous batching, FP8/INT8/INT4 | Included for reference — its quantization/batching techniques inform mobile engine design |

More comparisons live in [docs/comparisons/](docs/comparisons/) as the wiki grows.

## What's covered

| Area | Examples |
|---|---|
| 🧠 Agent architecture | ClawMobile, Tri-Spirit, Synergy, MCP patterns |
| 👁️ Perception | GUI perception (SecAgent), vision (FaceLiVTv2), multimodal |
| 💾 Memory & state | AMC, SkillDroid, Memory as Metabolism |
| 🔧 Tool calling | Mobile-MCP, MANA, COMLLM |
| 🤝 Multi-agent | EmoMAS, AgentComm, FedGUI |
| ⚡ Inference optimization | Quantization (KV-Cache, SEPTQ), routing (RPRA), on-device distribution |
| 🏭 Hardware & platforms | Wear OS, EdgeCIM, RL-driven ASIC |
| 🛡️ Security & privacy | VLM backdoors, privacy-aware inference, GAAT |
| 📱 Devices & platforms | iPhone 17e, Google AI Edge Gallery, Android Studio Agent Mode |
| 🏗️ Inference frameworks | llama.cpp, MNN, mlc-llm, coremltools, TensorRT-LLM |

## Repository layout

```
aios-wiki/
├── docs/                # the wiki — this is what mkdocs builds and deploys
│   ├── entities/        # products, models, companies
│   ├── concepts/        # techniques, methods, architectures
│   ├── comparisons/      # head-to-head comparisons
│   ├── queries/          # quick-reference lookups
│   ├── index.md          # full page index
│   └── knowledge-graph.md
├── overview/            # standalone reports (PPTX/HTML)
├── .meta/               # crawler config (sources.json) — not wiki content
├── AGENTS.md            # rules the maintenance agent follows
├── CONTRIBUTING.md
└── mkdocs.yml
```

Every page follows a consistent format — YAML frontmatter + wikilink cross-references:

```yaml
---
type: entity | concept
tags: [on-device-inference, quantization, ...]
related: [[other-page]], [[related-concept]]
sources:
  - url: https://arxiv.org/...
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-20
---
```

## Getting started

**Read online** (recommended): [yuelich.github.io/aios-wiki](https://yuelich.github.io/aios-wiki/)

**Browse locally with backlinks**: clone the repo and open the `docs/` folder in [Obsidian](https://obsidian.md/) for full bidirectional-link navigation.

```bash
git clone https://github.com/YueLich/aios-wiki.git
```

**Follow updates**: Watch this repo (top-right → Watch → Custom → Releases) to get the weekly digest without the commit noise.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to suggest a source, report an error, or submit a page. Short version:

- ⭐ Star the repo — helps others find it
- 🐛 [Open an issue](https://github.com/YueLich/aios-wiki/issues) to report an error or suggest a topic
- 🔀 PRs welcome for corrections and formatting fixes
- 💡 Tell us about RSS feeds / blogs / sources we're missing

## Maintenance

This wiki is drafted by an automated agent and curated by hand — see [AGENTS.md](AGENTS.md) for the full maintenance contract (draft/review gates, dedup rules, cadence). In short: new pages land as drafts, get promoted only after source cross-checking, and a weekly digest is published as a [GitHub Release](https://github.com/YueLich/aios-wiki/releases).

## License

[MIT](LICENSE)

---

# 📱 Mobile AIOS Wiki（中文）

**手机端 AI 操作系统的精选知识库** — 覆盖 Agent 架构、端侧大模型、芯片级推理优化，以及支撑它们的推理框架。

🌐 在线阅读：[yuelich.github.io/aios-wiki](https://yuelich.github.io/aios-wiki/)

## 为什么做这个

手机上的 AI 正在爆发，信息碎片散落在 arXiv、博客、GitHub release notes 和科技媒体中。这个 wiki 把碎片**筛选、验证**成可信的知识页面：每篇标注来源，通过 wikilink 关联相关实体/概念，并明确区分**已审核**（交叉验证过 ≥2 个独立来源）和**草稿**（等待审核）两种状态——具体标准见 [AGENTS.md](AGENTS.md)。

## 仓库结构

```
aios-wiki/
├── docs/                # wiki 正文 —— mkdocs 构建/部署的就是这里
│   ├── entities/         # 实体 — 产品、模型、公司
│   ├── concepts/         # 概念 — 技术、方法、架构
│   ├── comparisons/       # 横向对比
│   ├── queries/           # 速查
│   └── index.md
├── overview/             # 独立报告（PPTX/HTML）
├── .meta/                # 抓取器配置（sources.json），非 wiki 内容
├── AGENTS.md             # 维护 agent 遵循的规则
└── CONTRIBUTING.md
```

## 快速开始

**在线阅读**（推荐）：[yuelich.github.io/aios-wiki](https://yuelich.github.io/aios-wiki/)

**本地浏览**（支持 wikilink）：用 [Obsidian](https://obsidian.md/) 打开 `docs/` 目录。

```bash
git clone https://github.com/YueLich/aios-wiki.git
```

**订阅更新**：Watch 本仓库并选择 Custom → Releases，即可只收到每周精选摘要，不受逐日 commit 打扰。

## 数据来源

自动扫描分层信息源，配置见 [.meta/sources.json](.meta/sources.json)：arXiv API、RSS（Google AI Blog、HuggingFace 等）、GitHub Releases（llama.cpp、MNN、mlc-llm...）、中英文科技媒体、专家博客。

## 贡献

欢迎 star、提 issue、提 PR 修正内容或推荐来源，详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 维护机制

内容由自动化 agent 起草、人工把关，完整规则见 [AGENTS.md](AGENTS.md)：新页面先进草稿区，交叉验证后才晋升正文；每周日发布一次精选摘要（GitHub Release）。

## License

[MIT](LICENSE)
