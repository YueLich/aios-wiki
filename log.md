
## 2026-04-16 Wiki Update

**新增页面 (6):**
- concepts/kl-quantization-ssm-transformer.md — KL 散度量化透镜：混合精度 SSM-Transformer 快速敏感度分析
- concepts/trispirit-cognitive-architecture.md — Tri-Spirit 三层认知架构驱动的Agent硬件协同设计
- concepts/ati-physical-ai.md — ATI 仿生传感器优先的具身AI三层架构
- concepts/lacy-small-model-token-selection.md — LaCy 小语言模型 Token 选择哲学 (Apple)
- concepts/synergy-open-agentic-web.md — Synergy 开放Agent网络的下一代通用Agent
- entities/llamacpp-b8808.md — llama.cpp b8808 最新推理引擎版本

**数据源:** arXiv RSS/API, Apple ML Research, GitHub Releases, HuggingFace Blog, Google AI Blog, Android Dev Blog, Simon Willison, MIT Tech Review, IEEE Spectrum, Wired, VentureBeat, Google DeepMind
**统计:** 187 raw → 91 keyword filtered → 64 deduped → 6 pages created

---
format: reverse-chronological
---
# Wiki 操作日志
- 2026-04-14 初始化 wiki 仓库 (github.com/YueLich/aios-wiki)

## 2026-04-16 02:00 — 增量更新

**统计**：扫描 arXiv RSS (3 feed) + GitHub releases (7 repos) + arXiv API (4 queries)，共 73 条 → 2 新增（去重后）
**新增**：3 个 Wiki 页面（1 概念 + 2 实体）

### 新增页面
- `concepts/synergy-open-agentic-web.md` — 开放代理网络的下一代通用 Agent（arXiv 2603.28428），提出 Agentic Citizen 概念
- `entities/llamacpp-b8807.md` — llama.cpp b8807，Vulkan 后端 im2col 优化
- `entities/paddle-lite-v214.md` — 百度飞桨端侧推理引擎 v2.14-rc

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


## wiki update: 2026-04-14 UTC

**新增页面：**
- `concepts/e-grm-efficient-generative-reward-modeling.md` — E-GRM 高效生成式奖励建模，按需推理减少端侧 LLM 开销
- `concepts/septq-post-training-quantization.md` — SEPTQ 简单高效后训练量化，降低端侧部署门槛

**更新页面：**
- `entities/ggml-llamacpp-hf.md` — 追加 b8789 版本信息（ARM NEON nvfp4 dot product 修复）

**去重统计：** 扫描 59 条来源条目，3 条通过去重和过滤进入 wiki。

---

## wiki update: 2026-04-14 21:00 UTC

**统计**：扫描 arXiv RSS (3 feeds)、RSS (6 feeds)、GitHub (7 repos)
**原始收集**: 143 条 → 去重后 30 条 → 二次过滤后 4 条 → 最终更新 1 页

### 更新页面
- `entities/ggml-llamacpp-hf.md` — 追加 b8790 版本信息（BoringSSL vendor 更新，安全维护）

### 跳过（已处理）
- OpenBMB/MiniCPM: 2.4.2、apple/coremltools: 9.0 — 旧发布，已处理
- Android Dev "Get inspired and take your apps to desktop" — 非 AI 核心内容（桌面设计资源）
- arXiv RSS 中本轮新论文均不匹配端侧 AI 关键词

### 备注
- llama.cpp b8790 仅为单次 vendor 更新（BoringSSL），无功能性变更
- 本轮更新量极小，主要来源未产出新的端侧 AI 相关内容

## 2026-04-14_19:05 — 增量更新

**统计**：扫描 arXiv RSS (3 feeds) + RSS (6 feeds) + GitHub (7 repos) + HN = 132 条原始 → 48 Stage1 → 29 去重 → 7 Stage2 → 3 最终新增

### 新增页面
- `entities/llamacpp-b8791.md` — llama.cpp b8791：Metal XIELU 激活函数 + ARM NEON nvfp4 修复，端侧推理效率提升
- `concepts/qwen35-small.md` — Qwen 3.5 Small 系列：0.8B-9B 端侧多模态模型（image-text-to-text），Apache 2.0
- `entities/zuver.md` — Zuver：10MB 内存的开源 Agentic AI 框架，Go 实现

### 跳过（已处理）
- MiniCPM 2.4.2, coremltools 9.0 — 旧版本，已在 index 中
- Meta Muse Spark — 云端托管模型，非端侧
- Manex Hub — macOS 研究工具，非移动 AIOS

### 备注
- arXiv RSS 新论文均已被去重过滤（与已知标题重叠）
- HN Qwen 3.5 Small 来自 ai-tldr.dev（SPA）和 HuggingFace API
- Zuver 社区关注度低（HN 3 points），需后续跟踪验证



## 更新 2026-04-14 20:05

### 新增
- **MNN 3.5.0** — 阿里端侧推理引擎重大更新
  - Vulkan LLM 推理、TurboQuant KV Cache 量化、异步 Token2Wav 语音流水线
  - Tokenizer 20x 加速、Qwen3.5 Smooth/Omni 支持、RISC-V RVV 落地

### 跳过（已处理/不相关）
- llama.cpp b8792 — 仅 CI 修复，非功能性更新
- TensorRT-LLM v1.2.0 — 主要面向服务端/云端，移动端相关性有限
- gemma.cpp v0.1.4 — 小版本更新（Gemma ctor 重构 + NUMA）
- Manex Hub — macOS 研究工具，非移动 AIOS

### 备注
- arXiv RSS 新论文均已被去重过滤（无新移动端相关论文）
- HN 无高质量移动端 AI 新闻

## 2026-04-15 00:00 — 增量更新

**统计**：扫描 arXiv API (6 queries)、RSS (9 feeds)、GitHub (7 repos)、HN
**原始收集**：193 条 → 关键词过滤 64 条 → 去重后 31 条 → 二次过滤后 1 条深度内容

### 新增页面
- `concepts/on-device-inference-memory-pressure.md` — 端侧 Gen-AI 推理的内存硬件解决方案（HBS + SRAM 键合芯粒）

### 跳过（已处理/不相关）
- Gemma 4 AICore Developer Preview — 已有页面
- llama.cpp b8792 — 仅 CI 修复，已加入索引跟踪
- MiniCPM 2.4.2、coremltools 9.0 — 旧版本，已处理
- E-GRM、SEPTQ — RSS 重复出现，已处理
- ALTK-Evolve、Granite 4.0 3B Vision — 通用 AI，非端侧特定
- 其余 arXiv 论文 — 医疗/机器人/安全，非移动 AIOS

### 备注
- arXiv API 仍全部失败（code=0），RSS 获取论文
- 本轮核心收获：IMEC 团队首次量化端侧 LLM 推理对 HBS/芯粒的带宽延迟需求
- 关键洞察：HBS 带宽需 > 40% LPDDR6 才能摆脱瓶颈；小模型应优先缓存 MLP 权重而非 Q/K/V


### 2026-04-15 01:00 — 增量更新

**新增 4 个页面：**

1. **[[llamacpp-b8793]]** (entity) — llama.cpp b8793 发布：Vulkan 后端 RoundingModeRTE 支持
2. **[[rl-asic-exploration]]** (concept) — RL 驱动的 ASIC 架构探索，让 Llama 3.1 8B 在 3nm 跑出 29809 tok/s
3. **[[comllm-mec-offloading]]** (concept) — 用多轮推理 LLM 做 MEC 任务卸载，零样本拓扑泛化
4. **[[emommas-edge-negotiation]]** (concept) — 贝叶斯多 Agent 情感协商系统，端侧可部署

**来源扫描：** arXiv (6 queries)、RSS (10 feeds)、GitHub (7 repos)
**去重后新内容：** 8 条 → 4 条写入 wiki

## 2026-04-15 08:00

**新增页面**: 2
- `entities/llamacpp-b8797.md` — llama.cpp b8797 Qualcomm Hexagon HMX 矩阵乘法异步优化
- `concepts/wearos-64bit.md` — Wear OS 64-bit 架构要求（2026-09-15 生效）

**来源统计**:
- arXiv RSS (cs.AI/CL/LG): 扫描 60 篇，2 篇相关但非移动 AIOS 核心
- RSS Feeds (Google AI/Android Dev/HF/Decoder/VB/SW): 扫描 ~87 篇
- GitHub Releases: 7 个仓库，1 个新版本 (llama.cpp b8797)
- Hacker News: API 超时

**新增去重索引**: ggml-org/llama.cpp: b8797, Wear OS 64-bit

## 2026-04-16 01:07 — 增量更新

**新增页面:**
- `concepts/pairzero-wireless-llm-fl.md` — pAirZero: 无线联邦LLM微调 (通信-内存-隐私三难)
- `concepts/memory-worth-governance.md` — Memory Worth: Agent记忆治理轻量级原语

**来源:**
- arXiv API: 2604.12401 (pAirZero), 2604.12007 (Memory Worth)
- GitHub: llama.cpp b8808 (minor, skipped — 已有页面)

**统计:** 扫描 ~50 来源，2 条新增，0 条更新

