# 💡 概念 (Concepts)

技术、方法、架构——按 **Agent 子系统 × 优化维度** 双维度组织。

---

## 🧠 Agent 架构与认知

Agent 系统设计与认知架构：

- [ClawMobile](clawmobile-agentic.md) — 原生 Agent 系统架构
- [Tri-Spirit](trispirit-cognitive-architecture.md) — 三层认知驱动的硬件协同设计
- [Synergy: 通用架构](synergy-agentic-web-agent.md) / [网络协作](synergy-open-agentic-web.md) — 开放 Agent 网络
- [ExecTune](exectune-guide-core-policy.md) — Guide 模型引导黑盒 LLM
- [LAMO](lamo-scalable-gui-agents.md) — 面向多角色编排的轻量 GUI Agent
- [ClawGUI](clawgui-unified-framework.md) — GUI Agent 全栈开源框架
- [MCP 生产部署模式](mcp-deployment-patterns.md)
- [OpenMobile](openmobile-agent-data-synthesis.md) — 开放移动 Agent 数据合成

## 👁️ 感知与理解

**GUI 感知**: [SecAgent](secagent-mobile-gui.md) · [PSPA-Bench](pspa-bench-gui-agent.md) · [图灵测试](turing-test-mobile-gui.md) · [MGA](mga-memory-gui-agent.md) · [CORA](cora-mobile-gui-safety.md)

**视觉感知**: [FaceLiVTv2](facelivtv2-mobile-face.md) · [FastSHADE](fastshade-mobile-denoising.md) · [DRIFT](drift-mobile-isp-pipeline.md) · [DroneScan-YOLO](dronescan-yolo.md)

**多模态感知**: [DERM-3R](derm3r-multimodal-agent.md) · [Chain of Modality](chain-of-modality.md) · [Sense Less Infer More](sense-less-infer-more.md)

## 💾 记忆与状态

- [AMC](amc-adaptive-memory-crystallization.md) — 自适应记忆结晶化与持续学习
- [Memory as Metabolism](memory-as-metabolism-companion-ks.md) — Companion 知识系统
- [Memory Worth](memory-worth-governance.md) — 记忆治理原语
- [Memp](memp-agent-procedural-memory.md) — Agent 过程性记忆探索
- [SkillDroid](skilldroid-skill-compilation.md) — GUI 技能编译与重放
- [SUMMER](summer-multimodal-memory.md) — 多模态记忆
- [LifeDialBench](lifedialbench-lifelog-memory.md) — Lifelog 记忆评估
- [MemGround](memground-benchmark.md) — 游戏化 LLM 长期记忆评估
- [Memento-Skills](memento-skills-agent-design.md) — Agent 设计 Agent

## 🔧 工具调用与执行

- [端侧 vs 云端工具调用](on-device-vs-cloud-agentic-tool-calling.md)
- [Mobile-MCP](mobile-mcp.md) — Android 动态工具发现
- [MANA](mana-mobile-ad-detection.md) — 多模态 Agent 广告检测
- [COMLLM](comllm-mec-offloading.md) — 边缘卸载决策
- [GAAT](gaat-agent-governance.md) — 治理感知的 Agent 遥测
- [Cloudflare Agent Cloud](cloudflare-agent-cloud-openai.md)

## 🤝 多 Agent 协作

- [EmoMAS](emommas-edge-negotiation.md) — 情感感知的边缘协商
- [AgentComm](agentcomm-semantic-communication.md) — 具身 Agent 语义通信
- [pAirZero: 无线 FL](pairzero-wireless-llm-fl.md) / [端侧 FL](pAirZero-federated-finetuning.md) — 联邦微调
- [FedGUI](fedgui-federated-gui-agents.md) — 跨平台联邦 GUI Agent
- [Interlat](interlat-latent-communication.md) — Agent 隐空间通信
- [CoDaS](codas-wearable-biomarker.md) — 穿戴传感器生物标志物发现

## ⚡ 推理优化

**模型量化**: [KV-Cache 量化](kv-cache-quantization-ondevice.md) · [SEPTQ](septq-post-training-quantization.md) · [KL 散度量化](kl-quantization-ssm-transformer.md) · [DeFakeQ](defakeq-edge-deepfake.md)

**内存与效率**: [EdgeFlow](edgeflow-cold-start.md) · [LCSB](lcsb-finetuning-ondevice.md) · [KV Packet](kv-packet-kv-caching.md) · [无损提示词压缩](lossless-prompt-compression.md) · [ProfInfer](profinfer-llm-profiling.md)

**模型路由**: [RPRA](rpra-self-assessment-inference.md) · [LaCy](lacy-small-model-token-selection.md) · [E-GRM](e-grm-efficient-generative-reward-modeling.md) · [小模型 vs 大模型](slms-vs-llms.md)

**边缘分布式**: [DanceMoE](dancemoe-distributed-moe-edge.md) · [AHC](ahc-mcu-continual-detection.md) · [gemma.cpp](gemma-cpp-inference.md)

## 🏭 硬件与平台

**设备适配**: [Wear OS 64-bit](wearos-64bit.md) · [端侧推理内存压力](on-device-inference-memory-pressure.md) · [可持续性权衡](sustainability-ondevice-intelligence.md) · [MCU 全网络训练](biotrain-ondevice-finetuning-mcu.md)

**芯片与加速器**: [EdgeCIM](edgecim-hardware-codesign.md) · [RL 驱动 ASIC](rl-asic-exploration.md) · [LSTM 步态 ASIC](lstm-gait-asic-accelerator.md) · [ATI](ati-physical-ai.md)

## 🎯 应用场景

**音频**: [Gemma 4 音频](gemma4-audio-mlx.md) · [MeloTune](melotune-ondevice-music.md)

**穿戴与健康**: [穿戴 LLM 心理健康](wearable-llm-stress-support.md) · [BadgeX](badgex-wearable-llm-learning.md) · [大传感器模型](wearable-large-sensor-models.md)

**框架与集成**: [Qwen 3.5 Small](qwen35-small.md) · [React Native 端侧 LLM](react-native-llm-edge.md) · [边缘卸载](edge-cloud-offloading.md) · [Android Hybrid Inference](android-hybrid-inference.md)

## 🛡️ 安全与隐私

- [Follow My Eyes](followmyeyes-vlm-backdoor.md) — VLM 后门攻击
- [GenAI 隐私感知](genai-smartphone-privacy-perception.md)
- [GUI Agent 隐私保护](gui-agent-privacy.md)
- [RePAIR](repair-interactive-unlearning.md) — 交互式机器遗忘修复
- [ECG 基础模型](ecg-foundation-models-edge.md) — 边缘心血管智能
- [TOPCELL](topcell-llm-hardware-topology.md) — LLM 驱动的拓扑优化
- [Corpus2Skill](corpus2skill-agent-knowledge-navigation.md) — Agent 知识库导航式检索

---

*本页面由 Hermes Agent 自动维护。最新条目按时间排序出现在各分类末尾。*
