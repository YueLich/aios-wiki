## 2026-04-18 16:44 - Wiki 增量更新

**新增概念页面**：
1. `gui-perturbed-grounding-brittleness.md` — GUI-Perturbed: GUI Grounding 系统性脆弱性
   - 来源: arXiv 2604.14262 (2026-04-15)
   - 核心发现: 空间推理准确率崩溃 27-56pp; 70% 缩放导致显著退化; LoRA 微调反而退化
2. `gui-agent-focused-distraction-attack.md` — GUI Agent 注意力分散攻击: 语义级 UI 注入
   - 来源: arXiv 2604.07831 (2026-04-09)
   - 核心发现: 黑盒攻击 4.4x 优于随机; 漏洞模型无关; 战略图标是持久吸引子

**去重统计**：扫描 65 条候选 → 2 条新增（去重率 97%）


## 2026-04-17 21:30 Wiki Update
- Scanned: 212 items from arXiv (5 feeds + 5 API queries), 8 RSS feeds, 6 GitHub repos
- Stage 1 filter: 106 relevant
- Stage 2 filter: 44 high-relevance
- After 4-layer dedup: 0 genuinely new items
- Skipped: 35 (all duplicates in index.json)
- False positives filtered: EviSearch (clinical), AromaGen (olfactory), Simon Willison (quote), CSI paper (wireless networking)
- llama.cpp b8832 tracked but minor CUDA-only release — no mobile-specific changes
- Index size: 198 titles, 149 pages

## 2026-04-17 14:11 (cron)
- 扫描 16 个来源，217 条内容
- 去重后仅 1 条真正新增（HuoziIME）—— 其余 17 条均已在知识库中
- 新增页面：
  - entities/huoziime-ondevice-ime.md — 端侧 LLM 增强输入法（哈工大 Qwen3-0.6B）
- 已有页面确认最新：gemma4-ondevice.md, lacy-small-model-token-selection.md, google-translate-ios-live2.md, llamacpp-b8831.md
- GitHub 状态确认：llama.cpp b8831, ARM ComputeLibrary v53.0.0 均已收录
- 去重问题：Layer 2 slug 匹配未捕获 Gemma4/LaCy/Translate（slug 格式差异大），已手动清理

## 2026-04-17 14:06 (cron)
- 扫描 16 个来源，217 条内容
- 去重后 18 条新内容，5 条通过相关性过滤
- 新增 4 个页面：
  - entities/huoziime-ondevice-ime.md — 端侧 LLM 输入法（哈工大）
  - entities/gemma-4-google.md — Gemma 4 模型家族（Google）
  - concepts/lacy-slm-token-delegation.md — SLM token 委托策略（Apple Research）
  - entities/google-ios-live-translate.md — Google 实时翻译耳机 iOS 版
- GitHub 更新：llama.cpp b8831, ARM ComputeLibrary v53.0.0

## 2026-04-17 12:34

- 新增概念页: LLMOrbit LLM 分类体系 (llmorbit-llm-taxonomy.md)
- 新增实体页: llama.cpp b8829 (llamacpp-b8829.md)
- 扫描来源: arXiv RSS (cs.AI/CL/LG/CV/MA), arXiv API, GitHub releases, RSS feeds, HN
- 跳过重复: MiniCPM 2.4.2, coremltools 9.0, ARM ComputeLibrary v53.0.0 (已知版本)
- 跳过无关: Energy-Efficient Mobile (2017旧文), Simon Willison pelican (非实质性)

## 2026-04-17 07:10
- 新增: AgentOpt v0.1 客户端 Agent 优化框架 (概念页)
- 新增: llama.cpp b8827 OpenCL Adreno 重构 (实体页)
- 扫描来源: arXiv RSS (cs.AI/CL/LG/CV/MA) + API, 11 RSS feeds, 7 GitHub repos
- 原始收集: 230 条 → 去重后 221 → 两阶段过滤 36 → 手动审核 2 个新增


## 2026-04-17 — Wiki Update

**新增 3 个页面：**
- 📝 [[skilldroid-skill-compilation]] — SkillDroid: 将成功的 GUI 轨迹编译为可复用技能模板（概念）
- 📱 [[ondevice-streaming-asr]] — 微软端侧流式 ASR：0.67GB, 8.20% WER, CPU 推理（实体）
- ☁️ [[cloudflare-agent-cloud-openai]] — Cloudflare Agent Cloud + OpenAI 企业级 Agentic 工作流（概念）

**来源统计：**
- arXiv RSS: cs.AI/CL/LG/CV/MA (75 entries)
- Expert blogs: Chip Huyen, Simon Willison, Lilian Weng 等 13 个 RSS
- GitHub releases: 9 repos checked
- arXiv API: 2 targeted queries
- 合计采集: 249 条 → 96 stage-1 → 19 stage-2 → 3 新页面

**关键发现：**
- SkillDroid 解决了移动 GUI Agent 的根本性无状态问题，85.3% 成功率，49% 更少 LLM 调用
- 微软 CoreAI 在端侧 ASR 领域建立新帕累托前沿：0.67GB + CPU + 8.20% WER
- Cloudflare + OpenAI 为企业级 Agentic 工作流提供边缘基础设施


## 2026-04-17 08:00 Wiki Update

**新增页面**: 1
- `docs/concepts/fedgui-federated-gui-agents.md` — FedGUI: 跨平台联邦 GUI Agent 基准 (arXiv:2604.14956)

**来源扫描**: 257 条 → 115 (Stage 1) → 22 (Stage 2) → 13 (去重后) → 1 (深度研究)
**关键词**: 联邦学习, GUI Agent, 跨平台, 隐私保护, 边缘部署

## 2026-04-17 02:00

## 2026-04-17 04:07 — Wiki Update

**新增 3 个页面：**
- `entities/huoziime-ondevice-ime.md` — HUOZIIME 端侧 LLM 输入法（arXiv 2604.14159）
- `entities/gemma4-ondevice.md` — Gemma 4 端侧模型家族（DeepMind Blog）
- `concepts/llm-numerical-instability.md` — LLM 数值不稳定性（arXiv 2604.13206）

**来源：** arXiv RSS (cs.AI/CL/LG/CV/MA), DeepMind Blog, 技术博客
**状态：** ✅ 推送成功

### 新增页面 (5)
- **entities/vllm-mlx-apple-silicon.md** — vllm-mlx: Apple Silicon 原生 LLM/MLLM 推理框架 (arXiv:2601.19139)
- **concepts/cora-mobile-gui-safety.md** — CORA: 共形风险控制移动 GUI Agent 安全框架 (arXiv:2604.09155)
- **concepts/knowu-bench-personalized-agent.md** — KnowU-Bench: 个性化移动 Agent 评测基准 (arXiv:2604.08455)
- **concepts/lifedialbench-lifelog-memory.md** — LifeDialBench: 连续 Lifelog 记忆评估 (arXiv:2604.11182)
- **concepts/profinfer-llm-profiling.md** — ProfInfer: eBPF 推理性能分析器 (arXiv:2601.20755)

### 来源
- arXiv RSS (cs.AI/CL/LG/CV/MA) + targeted API queries
- Simon Willison, Sebastian Raschka, DeepMind blogs
- GitHub releases (llama.cpp b8816, ARM ComputeLibrary v53)

### 去重统计
- 扫描: 246 raw → 137 relevant → 104 new → 16 strict → 5 written

## 2026-04-17 Wiki Update

**新增 3 个页面：**
1. **litertlm-swift-ios.md** (entity) — LiteRTLM-Swift: 社区项目将 Google LiteRT-LM C API 封装为 Swift 接口，在 iOS 上运行 Gemma 4 多模态推理。支持文本/视觉/音频/多模态，KV Cache 复用实现 1-2s TTFT。
2. **transformers-to-mlx.md** (concept) — HuggingFace 发布 Skill + 测试框架自动移植 transformers 模型到 MLX，加速 Apple Silicon 端侧 AI 生态。核心洞察：AI Agent 在开源中的正确协作模式。
3. **nanowakeword-wake-word.md** (entity) — 下一代唤醒词检测框架，< 1 MB 模型，支持 ONNX/TFLite/Core ML 输出，适用于 MCU 到手机全设备。

**来源：** Hacker News, HuggingFace Blog, Simon Willison
**统计：** 扫描 171 条来源，过滤后 3 条新增
# Wiki 更新日志

## 2026-04-16 — 增量更新

- 新增 4 个页面
- 来源：arXiv RSS (cs.AI/CL/LG/CV/MA) + GitHub releases
- 新页面：dronescan-yolo, lossless-prompt-compression, mcp-deployment-patterns, llamacpp-b8815

## 2026-04-16 15:08 Wiki 更新

**新增/更新页面：**
- `docs/entities/gemma4-ondevice.md` — Gemma 4 多模态端侧模型全面更新（架构、基准、部署支持）
- `docs/entities/ggml-llamacpp-hf.md` — 新增 b8811 版本记录（WebGPU iOS 优化）

**数据来源：**
- HuggingFace Blog: Gemma 4 详解
- GitHub API: llama.cpp b8811

**统计：** 扫描 123 个来源，2 个新内容（1 页面丰富化 + 1 版本更新）


## 2026-04-16 — 增量更新

新增 4 个 wiki 页面：

### 概念页
- **Mobile-MCP** (`concepts/mobile-mcp.md`) — 基于 Android Intent 框架的 MCP 实现，运行时动态工具发现
- **移动 Agent 生态系统摩擦** (`concepts/mobile-agent-ecosystem-friction.md`) — Sova AI 被 Google Play 下架事件分析
- **SLMs vs LLMs** (`concepts/slms-vs-llms.md`) — 小模型 vs 大模型系统性对比

### 实体页
- **NavixMind** (`entities/navixmind.md`) — 开源 Android 本地优先 AI Agent
- **Sova AI** (`entities/sova-ai-android-agent.md`) — Accessibility-based 移动 Agent

### 数据源
- arXiv RSS (cs.AI/CL/LG/CV/MA): 75 items → 0 relevant after filter
- arXiv API: 15 items → 1 picked (wrong paper on lookup)
- GitHub releases: b8809 (已知), ComputeLibrary v53.0.0 (已知)
- HackerNews: 8 items → 4 relevant
- Google AI Blog, HuggingFace, The Decoder, VentureBeat, Simon Willison: ~52 items → 0 mobile AI relevant



## 2026-04-16 12:00 (cron)

**新增页面**: 3 个概念页面
- `concepts/memory-as-metabolism-companion-ks.md` — 伴侣知识系统记忆治理框架
- `concepts/amc-adaptive-memory-crystallization.md` — 自适应记忆结晶化（62% 内存降低）
- `concepts/memp-agent-procedural-memory.md` — Agent 过程性记忆探索

**来源**: arXiv RSS (cs.AI/CL/LG/CV/MA), arXiv API, GitHub releases, HuggingFace blog
**统计**: 扫描 112 项，去重后 107 新，关键词过滤后 7 项，最终新增 3 页

## 2026-04-16 增量更新

新增页面 (2):
- concepts/kv-packet-kv-caching.md
- concepts/agentcomm-semantic-communication.md

新增标题:
- KV Packet: Recomputation-Free Context-Independent KV Caching for LLMs
- AgentComm: Semantic Communication for Embodied Agents

来源统计: arXiv RSS (cs.AI/CL/LG/CV/MA/eess.SP) + Google/Android/Apple/DeepMind RSS + GitHub releases
过滤后候选: 42 条 → 深度研究 2 篇论文

## 2026-04-16 16:00 增量更新

**新增 4 个概念页面：**

1. **pAirZero 联邦微调** (`pAirZero-federated-finetuning.md`) — 解决端侧 LLM 联邦微调的通信-内存-隐私三难题，通过零阶优化+OTA实现75%内存缩减、位级通信、内嵌DP保护
2. **RPRA LLM-Judge 推理优化** (`rpra-llm-judge-inference.md`) — 让小模型预测 LLM-Judge 评分实现智能推理路由，报告卡+事后训练两种方案
3. **DeFakeQ 边缘 Deepfake 检测** (`defakeq-edge-deepfake-detection.md`) — 首个 Deepfake 检测器专用量化框架，10-20%模型大小保留90%精度，已验证移动端实时部署
4. **RePAIR 交互式机器遗忘** (`repair-interactive-unlearning.md`) — 用户通过自然语言让LLM遗忘特定知识，STAMP算法实现训练无关的推理时模型修复

**来源：** arXiv API 搜索 (cs.AI/cs.CL/cs.LG RSS + targeted queries)
**去重：** index.json 81 标题 + existing pages 70 页


## 2026-04-16 Wiki Update

**新增页面 (6):**
## 2026-04-16 03:05 — 增量更新（无新增）

**统计**：扫描 arXiv RSS (3 feed) + RSS feeds (10) + GitHub releases (7 repos) + arXiv API (5 queries)，共 134 条原始 → 65 关键词过滤 → 19 严格过滤 → 0 新增（全部去重）
**结果**：Wiki 已是最新，无新内容需要添加
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


## 2026-04-16 04:06

**新增页面：**
- `concepts/biotrain-ondevice-finetuning-mcu.md` — BioTrain: MCU 上的全网络反向传播训练框架
  - 来源: arXiv 2604.13359
  - 关键数据: 8× 内存压缩, EEG 86.4% 准确率, 43.8mW 功耗, 320mAh 电池支持 211 次训练

**来源统计：**
- arXiv RSS: 45 items (cs.AI/CL/LG)
- arXiv API: 15 items (5 targeted queries)
- RSS Feeds: ~137 items (11 sources)
- GitHub Releases: 7 repos checked
- Hacker News: 12 items

**去重：** 221 → 183 (dedup) → 97 (stage-1) → 17 (stage-2) → 1 新增

## 2026-04-16 自动更新
- 新增 7 个概念页面
- DanceMoE: 分布式 MoE 边缘推理框架
- GenAI 智能手机隐私感知研究
- DRIFT: 移动端 ISP 流水线
- Synergy: 开放 Agentic Web Agent 架构
- LSTM 步态分析 ASIC 加速器
- 可穿戴 LLM 压力对话支持
- BadgeX: IoT 可穿戴 × LLM 协作学习

## 2026-04-16 Wiki Update
- 新增页面：2个
  - `concepts/gaat-agent-governance.md` — GAAT治理感知Agent遥测架构（Apple ML Research）
  - `entities/gemini-31-flash-tts.md` — Gemini 3.1 Flash TTS（Google）
- 来源：Apple ML RSS, The Decoder, arXiv RSS
- 去重结果：159 raw → 23 stage-1 → 9 after dedup → 2 genuinely new
- 注意：Apple ML RSS解析问题已解决（需用RSS格式而非Atom）

## 2026-04-16_18:06
- Sources: arXiv RSS (cs.AI/CL/LG/CV/MA), Google AI Blog, Android Dev, Apple ML, HuggingFace, The Decoder, VentureBeat, GitHub releases
- Items scanned: 147 RSS + 6 GitHub
- Stage-1 filtered: 64
- Stage-2 filtered: 12
- New after dedup: 0 genuinely relevant
- Action: No wiki pages created (low yield run, dedup working correctly)
- Checked: English-Bangla sentiment (not mobile AIOS), Apple acoustic embeddings (SPA/no content), Gemini for Mac (thin headline), 3 GitHub releases (all known)

## 2026-04-16 - Wiki Update
- 新增 3 个页面：LAMO (轻量 GUI Agent 多角色编排), ClawGUI (GUI Agent 全栈开源框架), llama.cpp b8816
- 来源：arXiv (cs.AI), GitHub releases
- 去重：跳过已知的 114+ 标题

## 2026-04-16 增量更新
- 新增概念页: summer-multimodal-memory (SUMMER 多模态记忆框架)
- 新增实体页: gemini-robotics-er-16 (Gemini Robotics-ER 1.6)
- 来源: arXiv 2604.12081, DeepMind Blog

## 2026-04-17 - Wiki Update
- 新增: multimodal-sentence-transformers.md (概念页)
- 来源: HuggingFace Blog (Sentence Transformers v5.4 多模态支持)
- 扫描: arXiv, Google AI, DeepMind, HuggingFace, Simon Willison, Apple ML, VentureBeat, The Decoder, GitHub

## 2026-04-17 — 增量更新
- 新增: `android-cli-agent-workflow.md` — Android CLI 面向 Agent 工作流的开发工具
- 来源: Android Developers Blog (2026-04-16)

## 2026-04-17 Wiki Update
- **3 new pages**: long-horizon-task-mirage, mma2a-modality-native-routing, gemini-nano-chrome137
- Sources: arXiv (cs.AI, cs.MA), Swyx blog
- arXiv API rate-limited (429), relied on RSS for discovery
- 293 raw items -> 120 stage-1 -> 91 after dedup -> 3 genuinely new after deep filtering

## 2026-04-17 05:00

**新增页面：**
- `solver-sampler-mismatch-negotiation.md` — 当推理模型损害行为模拟：多Agent协商中的求解器-采样器错配 (arXiv 2604.11840)

**来源：** arXiv cs.MA RSS, DeepMind blog

**统计：** 扫描 247 条，Stage 1: 97，Stage 2: 34，去重后新增: 1

## 2026-04-17 13:00 - Wiki Update

新增页面:
- gemma4-android-studio-agent.md
- memorable-ondevice-photo-search.md
- gemini-personalized-images-nanobanana.md

来源: arXiv RSS, Android Dev Blog, Google AI Blog, DeepMind Blog, Hacker News, GitHub Releases
扫描: 288 raw → 115 stage1 → 70 stage2 → 3 new after dedup

## 2026-04-17 Wiki Update
- New pages: memground-benchmark, interlat-latent-communication, compressed-sensing-dynamic-reduction, memento-skills-agent-design
- Sources: arXiv RSS (cs.AI/CL/LG/CV/MA), targeted API queries
- 241 raw items → 44 after dedup → 4 new pages after manual review

## 2026-04-17 18:00
- 新增: OpenMobile (arXiv 2604.15093) — 移动Agent数据合成框架
- 新增: llama.cpp b8831 — Android arm64官方构建

## 2026-04-17 19:30 Wiki Update
- Sources: arXiv API (7 queries), arXiv RSS (5 feeds), GitHub (6 repos), HN, RSS (12 feeds)
- Collected: 188 raw → 84 stage-1 → 5 new after dedup
- New pages: 4 concept pages
  - wearable-large-sensor-models.md: 穿戴式AI与大传感器模型
  - codas-wearable-biomarker.md: CoDaS穿戴传感器生物标志物发现
  - mllm-multi-robot-networks.md: MLLM驱动的多机器人网络
  - navinote-spatial-annotation.md: NaviNote空间无障碍标注

## 2026-04-17 - Wiki Update

### New Pages
- Theory of Mind in Action: The Instruction Inference Task in Dynamic Human-Agent Collaboration
- Calibrate-Then-Delegate: Safety Monitoring with Risk and Budget Guarantees via Model Cascades
- Revisiting Token Compression for Accelerating ViT-based Sparse Multi-View 3D Object Detectors

### Sources
- arXiv RSS (cs.CV, cs.LG, cs.MA)
- arXiv API (targeted queries)
- GitHub releases

### Stats
- Total pages: 193

## 2026-04-17 Wiki Update
- New pages: 6
- Entities: on-device-streaming-asr-microsoft, arm-computelibrary-v53
- Concepts: aipc-qualcomm-deployment-agent, cnn-optimization-edge-ai-early-exits, onestep-marl-ride-sharing, ecg-foundation-models-edge

## 2026-04-17 Wiki Update
- 新增 2 个页面：qwen36-35b-a3b（Qwen3.6 MoE 模型），llamacpp-b8833（llama.cpp WebGPU 修复）
- 来源：The Decoder, GitHub Releases
- 总计扫描 206 条目，Stage 1 过滤 95，Stage 2 过滤 36，去重后 2 个新页面

## 2026-04-17 Wiki 更新

**新增页面**: 6
- concepts/dharmaocr-specialized-slm-ocr.md — DharmaOCR: 面向结构化 OCR 的专用小型语言模型
- concepts/corpus2skill-agent-knowledge-navigation.md — Corpus2Skill: Agent 知识库导航式检索
- entities/android-17-beta4.md — Android 17 Beta 4
- entities/chrome-ai-mode-2026.md — Chrome AI Mode: 浏览器端 AI 搜索体验升级
- concepts/agent-exploration-exploitation-errors.md — Agent 探索-利用误差度量框架
- concepts/topcell-llm-hardware-topology.md — TOPCELL: LLM 驱动的标准单元拓扑优化

**来源**: arXiv (cs.AI, cs.CL, cs.LG, cs.CV, cs.MA), Google AI Blog, Android Developers Blog

## 2026-04-17 Wiki Update
- Added 3 new entity pages: NanoWakeWord, Sova AI, Memorable
- Sources: HN (Show HN posts), GitHub, Apple App Store
- All pages written to docs/ and root directories

## 2026-04-18
- Added 2 new pages: android-hybrid-inference (concept), llamacpp-b8836 (entity)
- Sources: Android Dev blog (Firebase hybrid inference), GitHub (llama.cpp b8836)
- Skipped: arXiv Gearbox-PHY (telecom PHY, not AIOS relevant)

## 2026-04-18 — b8838
- Added: entities/llamacpp-b8838.md (llama.cpp b8838 release)
- Changes: Android build modularization, multi-segment tensor read

## 2026-04-18 — Wiki Update

### Added Pages
- entities/gemma4-aicore.md — Gemma 4 端侧开源模型（DeepMind + AICore 集成）
- entities/gemini-31-flash-lite.md — Gemini 3.1 Flash-Lite 轻量级云端模型
- concepts/mixatlas-multimodal-data-mixture.md — MixAtlas 多模态数据混合优化（Apple Research）
- concepts/personalized-grpo-alignment.md — P-GRPO 个性化偏好对齐（Apple Research）
- concepts/vakra-agent-failure-modes.md — VAKRA Agent 失败模式分析（IBM Research）
- concepts/android-cli-agentic-development.md — Android CLI Agent 开发工具

### Sources
- arXiv: 2604.14198 (MixAtlas)
- DeepMind Blog: Gemma 4, Gemini 3.1 Flash-Lite
- Android Dev Blog: Android CLI, Gemma 4 AICore
- Apple ML Research: Personalized GRPO
- HuggingFace Blog: VAKRA

### Stats
- Scanned: ~104 raw items → 59 keyword filtered → 21 passed dedup → 6 new pages
- Dedup: 38 items skipped (index.json + existing pages)
- Skipped known: MixAtlas arXiv+Apple duplicate, Gemma 4 HuggingFace duplicate
