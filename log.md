---
format: reverse-chronological
---
# Wiki 操作日志
- 2026-04-14 初始化 wiki 仓库 (github.com/YueLich/aios-wiki)

## 2026-04-14 10:51 — 首次运行：GitHub-backed Wiki 初始化

**统计**：扫描 6 个 arXiv 查询 + 5 个 RSS Feed + 6 个 GitHub 仓库
**新增**：16 个 Wiki 页面（12 概念 + 4 实体）

### 新增页面
**概念页面**：
- `concepts/edgeflow-cold-start.md` — 移动端 LLM 冷启动优化
- `concepts/pspa-bench-gui-agent.md` — 智能手机 GUI Agent 个性化评测
- `concepts/secagent-mobile-gui.md` — 语义增强的高效 GUI Agent
- `concepts/clawmobile-agentic.md` — 智能手机原生 Agent 系统
- `concepts/kv-cache-quantization-ondevice.md` — KV-Cache 自适应量化
- `concepts/sustainability-ondevice-intelligence.md` — 端侧智能的性能-能耗-隐私权衡
- `concepts/edge-cloud-offloading.md` — 世界模型辅助的边缘卸载
- `concepts/lcsb-finetuning-ondevice.md` — 端侧 LLM 内存高效微调
- `concepts/edgecim-hardware-codesign.md` — CIM 硬件-软件协同设计
- `concepts/gui-agent-privacy.md` — Agent 隐私保护个性化
- `concepts/multimodal-edge-pruning.md` — 多模态边缘推理优化
- `concepts/networking-energy-agentic.md` — Agent 推理网络能效综述

**实体页面**：
- `entities/gemma4-ondevice.md` — Gemma 4 端侧多模态模型
- `entities/ggml-llamacpp-hf.md` — GGML/llama.cpp 加入 HuggingFace
- `entities/gemini-flash-live.md` — Gemini 3.1 Flash Live
- `entities/personal-intelligence-google.md` — Google 个人智能

### 关键趋势
1. **GUI Agent 成熟化**：PSPA-Bench、SecAgent、ClawMobile 三篇论文显示手机 Agent 正从概念走向系统化
2. **端侧推理优化分化**：KV-Cache 量化、LCSB 微调、EdgeFlow 冷启动形成互补技术栈
3. **基础设施整合**：llama.cpp 加入 HuggingFace 标志着端侧推理进入成熟期
4. **多厂商竞争**：Google Gemma 4 vs Apple Intelligence 的端侧模型竞赛加剧

## 2026-04-14 14:00 — 增量更新

**统计**：扫描 arXiv API（5 组查询）、8 个 RSS 源、7 个 GitHub 仓库，发现 7 条高度相关新内容。

**新增概念页面**：
- `concepts/turing-test-mobile-gui.md` — 图灵测试屏幕版：GUI Agent 拟人化基准
- `concepts/mobiflow-benchmark.md` — MobiFlow：真实轨迹驱动的移动 Agent 基准
- `concepts/mga-memory-gui-agent.md` — MGA：记忆驱动的 GUI Agent
- `concepts/mana-mobile-ad-detection.md` — MANA：多模态 Agent 移动广告检测
- `concepts/sense-less-infer-more.md` — Sense Less, Infer More：Agent 驱动的边缘医疗智能
- `concepts/react-native-llm-edge.md` — React Native 端侧 LLM 推理

**新增实体页面**：
- `entities/anylanguagemodel-apple.md` — AnyLanguageModel：Apple 平台统一 LLM API

### 关键趋势
1. **GUI Agent 评估体系化**：从任务成功率扩展到拟人化（Turing Test on Screen）和真实轨迹（MobiFlow），评估维度日趋全面
2. **Agent 驱动的感知控制**：Sense Less, Infer More 提出 Agent 决定"何时感知"的范式，对可穿戴/手机端 AI 能耗优化意义重大
3. **开发者工具链成熟**：AnyLanguageModel 和 React Native llama.rn 说明端侧推理正从 ML 工程师走向普通开发者
4. **Agent vs Agent 对抗**：MANA 用 Agent 检测广告，显示 Agent 在安全领域的应用潜力

## 2026-04-14 12:07 Wiki 更新

扫描来源：arXiv (6 queries)、RSS (5 feeds)、GitHub (6 repos)
收集原始标题：48 → 去重后新内容：10 → 创建页面：8

### 新增实体页面
- `entities/gemma-4-google.md` — Gemma 4：端侧前沿多模态模型
- `entities/coremltools-9.md` — Apple coremltools 9.0 模型转换工具链
- `entities/minicpm-242.md` — MiniCPM 2.4.2：端侧模型 Intel 显卡加速
- `entities/google-translate-ios-live.md` — Google Translate iOS 实时耳机翻译

### 新增概念页面
- `concepts/gemma4-audio-mlx.md` — Gemma 4 端侧音频处理（MLX + Apple Silicon）
- `concepts/melotune-ondevice-music.md` — MeloTune：端侧 Agent 情感感知音乐推荐
- `concepts/fastshade-mobile-denoising.md` — FastSHADE：移动端实时图像去噪
- `concepts/facelivtv2-mobile-face.md` — FaceLiVTv2：移动端高效人脸识别

### 关键趋势
1. **端侧多模态模型成熟**：Gemma 4 支持视觉+音频，MiniCPM-V 支持图文，端侧多模态进入实用阶段
2. **Agent 进入端侧**：MeloTune 展示了完整的端侧 Agent 协作系统（P2P 情感耦合）
3. **Apple 生态 ML 工具链更新**：coremltools 9.0 支持 Python 3.13，端侧部署工具持续迭代
4. **端侧 CV 模型专业化**：FastSHADE（去噪）和 FaceLiVTv2（人脸识别）展示端侧视觉模型的垂直深耕

## 2026-04-14 13:06
- 新增页面：3 个
  - entities/melotune-ondevice-music.md — MeloTune: 端侧音乐 AI Agent
  - entities/google-translate-ios-live2.md — Google Translate Live for iOS
  - entities/android-studio-agent-mode.md — Android Studio Agent Mode (Panda 3)
- 已存在跳过：4 个（FastSHADE, MANA, Sense Less Infer More, FaceLiVTv2）
- 扫描来源：arXiv × 6 queries, RSS × 10 feeds, GitHub × 7 repos
- 去重后新增标题：13 → 创建页面 3


## [2026-04-14 14:06] 增量更新

**扫描来源**: arXiv API (6 queries), RSS (10 feeds), GitHub (7 repos)
**原始收集**: 143 条 → 去重后 130 条 → 过滤后 9 条 → 最终新增 1 条

### 新增页面
- `entities/iphone-17e.md` — iPhone 17e: A19 芯片 16 核 Neural Engine，$599 价位端侧 AI 平民化

### 跳过（已处理）
- Gemma 4 系列（AICore Developer Preview、Welcome Gemma 4）— 已有页面
- ggml-org/llama.cpp: b8784 — b8783 已处理
- MacBook Neo 产品页面 — 非 AI 核心内容，无端侧 AI 相关信息
- OpenBMB/MiniCPM: 2.4.2, apple/coremltools: 9.0, google/gemma.cpp: v0.1.4 — 均为旧发布

### 备注
- arXiv API 查询全部失败（code=0），仅通过 RSS 获取 arXiv 论文
- RSS arXiv cs.AI/CL/LG 中新论文均已被去重过滤

## 2026-04-14 18:00 — 增量更新

**统计**：扫描 arXiv RSS/API (9 组)、RSS (6 feeds)、GitHub (7 repos)
**原始收集**：41 条 → 去重后 17 条 → 二次过滤后 13 条 → 最终新增 1 条

### 新增页面
- `entities/google-ai-edge-gallery.md` — Google AI Edge Gallery：Google 官方 iPhone 端侧 AI 应用，支持 Gemma 4 E2B/E4B 多模态推理 + tool calling

### 跳过（已处理）
- Gemma 4 AICore Developer Preview / Welcome Gemma 4 — 已有页面
- OpenBMB/MiniCPM 2.4.2、apple/coremltools 9.0 — 旧发布
- google/gemma.cpp v0.1.4 — 2025年3月发布，旧版本
- Android 17 Beta 3 — 平台稳定性里程碑，无新增 AI 特性
- Android Dev 其他文章（Room 3.0、Contact Picker、TikTok 代码优化等）— 非 AI 核心内容

### 备注
- arXiv API 仍全部失败（code=0），仅通过 RSS 获取论文
- 本次更新量较小，主要新内容为 Google AI Edge Gallery
- 该应用首次将模型厂商的端侧体验从「模型发布」推进到「官方应用」阶段

## wiki update: 2026-04-14_16:05 UTC

**新增页面：**
- `concepts/gemma-cpp-inference.md` — gemma.cpp v0.1.4，Google Gemma 轻量级 C++ 推理引擎

**更新页面：**
- `entities/ggml-llamacpp-hf.md` — 追加 llama.cpp b8786 版本信息（修复推理预算采样器性能回归）

**去重统计：** 扫描 126 条来源条目，2 条通过去重和过滤进入 wiki。

