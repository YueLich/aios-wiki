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

