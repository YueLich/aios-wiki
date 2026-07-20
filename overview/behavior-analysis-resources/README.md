# OS 应用操作记录 → 行为分析与推荐：公开资源归档

> 范围：通过分析用户在操作系统（PC 桌面 / 移动端 OS）上的应用操作记录（应用启动、切换、使用时长、应用内交互、窗口/屏幕日志等）做行为建模、预测、推荐的相关论文、综述、数据集、专利、工业系统、开源工具与合规资料。
>
> 所有链接均为子代理通过 CrossRef / arXiv / Google Patents / 官方主页核实过的真实地址。

## 目录结构

| 文件 | 内容 | 条目数 |
|---|---|---|
| [01_papers.md](./01_papers.md) | 学术研究论文（按 5 个主题分组） | 51 篇 |
| [02_surveys.md](./02_surveys.md) | 综述论文 | 11 篇 |
| [03_industry_systems.md](./03_industry_systems.md) | 工业系统论文 / 工程资料 | 4 篇 |
| [04_datasets.md](./04_datasets.md) | 公开数据集（5 类分组） | 24 个 |
| [05_patents.md](./05_patents.md) | 专利（按 5 大厂 + 其他分组） | 23 条 |
| [06_tools_compliance.md](./06_tools_compliance.md) | 开源工具与合规资料 | 3 条 |
| [07_mobile_deep_dive.md](./07_mobile_deep_dive.md) | **移动端手机方向深挖**（10 个子方向） | 约 70 条 |
| [08_cn_patents.md](./08_cn_patents.md) | **国产厂商 CN 专利补轮**（华为/小米/OPPO/vivo/荣耀） | 40 条 |

合计：约 227 条真实可访问资源。

## 资源统计

- 研究论文 51 篇（应用使用预测 23 + 桌面行为 7 + OS 级建模 4 + 移动端挖掘 8 + Lifelogging 9）
- 综述 11 篇
- 工业系统论文 4 篇
- 数据集 24 个（移动端应用使用 8 + 桌面 1 + Lifelog 3 + 上下文联合 3 + Web/App 日志 9）
- 海外专利 23 条（Google 3 + Microsoft 6 + Apple 6 + Samsung 4 + Huawei 3 + 其他 1）
- 国产 CN 专利 40 条（华为 11 + 小米 5 + OPPO 9 + vivo 6 + 荣耀 9）
- 开源工具 2 个 + 合规资料 1 篇
- 移动端深挖约 70 条（10 个子方向）

## 主流技术路线（论文 + 专利共同揭示）

1. **序列建模占主导**：早期 Markov / 序列规则 / Learning Automata（Liao 2013、Rahnamoun 2016）→ LSTM（WhatsNextApp 2022）→ Transformer/Appformer/TGT/MISApp（2024-2026）→ 近两年的 LLM embedding（MAPLE）、基础模型（MobiGPT）、生成式数据增强（MIDiff）。
2. **上下文特征深度融合**：时间 / 位置 POI / 基站 / 通勤 / 已装 App 相似度 / 语义本体，代表 CoSEM、Appformer、REVAMP，均强调"context + history"双通道。
3. **协同过滤 / 矩阵分解**：跨用户共享模式（Natarajan & Dhillon 2013、Frappe、联邦 SeqMF）。
4. **图 / 知识图谱路线**：用动态图 / 多跳会话图刻画 App 转移高阶结构（Learning Dynamic App Usage Graph、MISApp），缓解稀疏与冷启动。
5. **深度强化学习**处理长序列/大动作空间（DeepAPP）。

## 大厂专利布局思路

- **上下文特征工程**：Apple（EP3779685B1、EP3966677B1）、Google（US9063811B2 情境效用分数）。
- **时序/序列预测模型**：Samsung（US11615302B2 时间感知哈希、US11972327B2 活动模式→动作规则）、Microsoft（US11429883B2 活动模式预测）。
- **应用使用画像与推荐**：Apple（US10474727B2 众包应用使用数据）、Microsoft（US9887894B2 数据使用画像）、Huawei（AU2021240234B2）。
- **智能预加载/预启动**：Microsoft（US9508040B2）、Tensera（US20210329089A1）——把行为预测落到性能优化（prefetch / pre-launch）。
- **跨设备画像**：Microsoft（"一组计算设备"信号）、Google（多设备用户操作）。
- **端侧个性化与隐私**：Google（US8429103B1 端侧 ML）、Huawei（US20230052903A1 端侧终身学习）。

### 国产厂商 CN 专利布局特点（见 08_cn_patents.md）

国产厂商明显偏三个"中国特色"赛道，与海外差异化明显：
- **负一屏 / 智慧助手卡片生态**：华为 CN112559098B/CN112286147B/CN113225690B、vivo CN109814972B、荣耀 CN113508360B/CN117692507A——密度远超 Apple Today View/Widget。
- **跨设备协同 / 任务流转（华为"超级终端"系）**：CN117632060A/CN119130396A/CN116156044B/CN115884140B 一整族，把"跨账号跨设备流转"做得比 Samsung Continuity / Apple Handoff 更激进。
- **应用启动预测 / 预加载**：OPPO CN119829155A/CN119781782A、荣耀 CN119127342A——把"冷启动优化 + AI 预判下一应用"做进 OS 层。
- **国产相对薄弱的方向**：数字健康/应用限额（仅 vivo CN119739440A 一条强相关），海外 Apple Screen Time 系列反而更密。
- **国产比海外更超前的方向**：负一屏卡片化服务入口、跨设备任务流转、以及把"用户操作习惯→推荐文案"直接落到 OS 层（小米 CN121901403A）。

## 主要落地挑战

1. **数据稀疏与冷启动**——应用使用长尾且新用户历史缺失，MISApp/MAPLE/HeartSpace 专门设计 profile-free 或 LLM-similarity 机制。
2. **隐私与合规**——OS 级行为日志属高度敏感数据，多强调粗粒度 / 本地化 / 联邦化（Sayapin 2023、REVAMP），GDPR / CCPA 进一步抬高采集门槛。
3. **跨设备/跨场景同步**——ActivityWatch 把"去中心化同步"列为关键未竟事项，EdgeRec 强调端云分工降时延，反映设备异构与实时反馈张力。
4. **可解释性与稳定性**——Apple Fortress 与 TGT 的门控向量分析显示工业系统更关心推荐稳定性 / 漂移，而非单点精度。
5. **"系统日志"与"自报行为"不一致**——Parry 等 2021 (Nature Human Behaviour) 系统比较两者差异，ground truth 难获取。
6. **数据集缺口**：
   - 桌面端纯"窗口切换/工作场所 PC 使用"日志几乎无开放数据（仅 Screenomics 覆盖屏幕侧）；
   - 移动端 app 使用数据多为 2010 年前后（iPhone 3GS/Symbian/早期 Android），与现代多任务/小窗/分屏生态脱节；
   - 大规模"app 使用 + 语义内容（截图/UI 元素）"联合数据稀缺；
   - 多数含敏感上下文的数据走申请制（NTCIR/Nokia MDC/CERT），可复现性受限；
   - 跨设备（手机+桌面）同一用户的行为打通数据基本空白。

## 推荐组合（做"OS 应用操作行为分析与推荐"的取材建议）

- **推荐建模本体**：用 YOOCHOOSE / Retailrocket / Taobao UserBehavior（会话化点击序列，与"app 操作序列"同构），训练 next-item / 会话推荐模型；MovieLens / Netflix 作基线对照。
- **行为 + 上下文联合分析（为什么/何时用某 app）**：StudentLife / LiveLab / ExtraSensory / Friends & Family / Screenomics，做上下文感知的 app 使用预测与用户画像。
- **采集工具**：直接用 ActivityWatch 做桌面端 OS 行为日志采集原型。
- **隐私路径**：参考联邦推荐综述（02_surveys.md #6–9）+ Sayapin 2023 把模型搬到设备端。
- **专利风险规避**：重点关注 Microsoft（Windows Timeline 系列）、Apple（Siri 建议/众包应用使用）、Huawei（端侧终身学习）三条线。
- **移动端深挖**：见 07_mobile_deep_dive.md，覆盖 OS 级 API、App 启动预测、通知交互、会话切换、用户特质预测、智能助手、隐私保护、UI 事件流、跨设备、工业落地 10 个方向。

## 已知限制（搜集过程的真实约束）

1. **国产厂商专利已补轮但仍有限**——08_cn_patents.md 通过搜狗索引新闻稿反查拿到 40 条真实 CN 专利（华为 11 + 小米 5 + OPPO 9 + vivo 6 + 荣耀 9）。但 CNIPA 官网全程验证码、Google Patents XHR 接口出口 IP 被 503 限流，自动化批量拉取受限。若需更系统覆盖，建议申请 CNIPA / 智慧芽 / PatentGuru 的正规 API key。
2. **桌面端 PC 日志数据集基本空白**——这是该领域真实的数据缺口，目前只有 Stanford Screenomics 覆盖到桌面屏幕侧。
3. **Device Analyzer (Cambridge)** 官网当前不可访问且无 archive 快照，未列入正表。
4. **CERT Insider Threat (CMU/SEI)** 含 PC 使用日志（logon/USB/web/email/file）但未找到明确公开下载页，未列入。
5. **少量 arXiv 论文标的是 2026 年份**——这是 arXiv 上的提交年份标注（部分是预印本提前挂的年份），非正式发表年份，引用时请以实际 venue 为准。

## 文件生成时间

- 首次生成：2026-07-17（01-07 文件）
- 国产专利补轮：2026-07-17（08_cn_patents.md，新增 40 条 CN 专利）
