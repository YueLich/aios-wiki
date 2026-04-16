---
type: concept
tags: [gui-agent, open-source, rl-training, evaluation, deployment, mobile, android, harmonyos, ios]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[clawmobile-agentic]], [[turing-test-mobile-gui]], [[lamo-scalable-gui-agents]], [[mga-memory-gui-agent]]
sources:
  - url: https://arxiv.org/abs/2604.11784
    title: "ClawGUI: A Unified Framework for Training, Evaluating, and Deploying GUI Agents"
    date: 2026-04-13
    reliability: high
  - url: https://github.com/zju-real/ClawGUI
    title: "ClawGUI GitHub Repository"
    date: 2026-04-13
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# ClawGUI: GUI Agent 全栈开源框架

> 浙江大学 ZJU-REAL 实验室提出的 GUI Agent 统一框架，解决训练、评估、部署三大断层

## 核心问题

GUI Agent 研究领域存在三大瓶颈：

1. **训练基础设施缺失**：在线 RL 训练面临环境不稳定和封闭管线问题，多数研究无法复现
2. **评估协议漂移**：不同论文的评估标准不一致，结果不可比
3. **训练到部署的鸿沟**：训练好的 Agent 鲜少能真正到达用户的真实设备上

**核心矛盾**：GUI Agent 进步受限的不是模型能力，而是缺乏连贯的全栈基础设施。

## 方法/架构

ClawGUI 包含三个统一子系统：

### ClawGUI-RL（训练）
- **首个开源 GUI Agent RL 基础设施**
- 同时支持**并行虚拟环境**和**真实物理设备**
- 集成 GiGPO（Group-in-Group Policy Optimization）+ Process Reward Model
- 提供密集的步骤级（step-level）奖励监督
- 解决了在线 RL 训练的环境稳定性问题

### ClawGUI-Eval（评估）
- **完全标准化的评估管线**
- 覆盖 **6 个基准** 和 **11+ 模型**
- 达到 **95.8% 的官方基线复现率**
- 消除评估协议漂移问题

### ClawGUI-Agent（部署）
- 将训练好的 Agent 部署到 **Android、HarmonyOS、iOS**
- 支持 **12+ 聊天平台**集成
- 混合 **CLI-GUI 控制**模式
- **持久化个性化记忆**（persistent personalized memory）

### ClawGUI-2B：统一管线的成果
- 在 ClawGUI 全管线中端到端训练的 2B 参数模型
- **MobileWorld GUI-Only 上 17.1% 成功率**
- 超过同规模 MAI-UI-2B 基线 **6.0%**

## 实验结果/关键数据

| 指标 | ClawGUI-2B | MAI-UI-2B | 提升 |
|------|-----------|-----------|------|
| MobileWorld GUI-Only SR | 17.1% | 11.1% | +6.0% |
| 评估复现率 | 95.8% | - | - |
| 支持平台 | Android/HarmonyOS/iOS | - | 12+ 聊天平台 |

## 关键洞察

**ClawGUI 的独特价值**：

1. **全栈统一**：不是单点工具，而是训练→评估→部署的完整管线。这是当前 GUI Agent 领域最缺的东西
2. **开源 RL 基础设施**：之前 GUI Agent 的在线 RL 训练几乎都是闭源的，ClawGUI-RL 填补了这一空白
3. **跨平台部署**：支持 Android、HarmonyOS、iOS 三大移动 OS，是真正的移动端全栈方案
4. **2B 模型超越基线**：证明好的训练管线比堆参数更重要——这对端侧部署至关重要
5. **与浙大 LAMO 同期**：两篇论文都来自浙大，可能共享底层数据和实验平台

## 对手机端 AI 生态的意义

- **端侧 GUI Agent 的工程化落地**：ClawGUI-Agent 直接支持 Android/iOS/HarmonyOS 部署
- **开源生态建设**：首个完整的开源 GUI Agent RL 训练管线
- **标准化评估**：解决不同研究间不可比的问题，加速领域进步
- **2B 模型的实用价值**：证明轻量模型在好管线支持下可以达到可用水平

## 关联
- [[secagent-mobile-gui]] — 同为移动端 GUI Agent，SecAgent 侧重语义上下文效率
- [[pspa-bench-gui-agent]] — 个性化 GUI Agent 基准，ClawGUI-Eval 可集成
- [[clawmobile-agentic]] — 手机原生 Agent 系统理念，ClawGUI 提供了工程实现
- [[turing-test-mobile-gui]] — 人性化基准，ClawGUI 可在此基准上评估
- [[lamo-scalable-gui-agents]] — 同期浙大多角色编排方案，ClawGUI 提供训练基础设施
- [[mga-memory-gui-agent]] — 记忆驱动 GUI Agent，ClawGUI-Agent 的持久化记忆可借鉴
- [[mobiflow-benchmark]] — 移动 Agent 基准，ClawGUI-Eval 可纳入
