# 移动端手机方向深挖

> 范围：通过分析用户在**移动端手机 OS**上的应用操作记录来做行为分析和推荐。
>
> 本文件深挖移动端专属方向，避开前一轮已覆盖的通用 app usage prediction 论文（App2Vec、DeepAPP、Appformer、MAPLE、CoSEM、WhatsNextApp、Federated SeqMF、Kang commute-aware、CTR ranking、Alruban、What and How long、Yu POI、MISApp、MobiGPT、Natarajan&dhillon、Frappe、Ouyang Dynamic Graph、AppTrends、TGT、Liao 2013、Learning Automata、REVAMP、MIDiff）和数据集（LiveLab、StudentLife、MIT Reality Mining、Friends&Family、PhoneLab、Nokia MDC、MobileRec、ETRI、ExtraSensory、SHL、UCI HAR）。
>
> 所有链接均经 Crossref / Semantic Scholar / arXiv / 官方文档核实。

## 1. 移动端 OS 级数据采集技术（API / 平台能力）

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 与"移动端 OS 行为分析/推荐"的关联 |
|---|---|---|---|---|---|
| TYDR – Track Your Daily Routine. Android App for Tracking Smartphone Sensor and Usage Data | Beierle, Tran, Allemand 等 (Würzburg) | 2018 | 论文 | https://arxiv.org/abs/1803.06720 | 给出 Android 端结合传感器 + 心理测量量表的数据采集框架，含伦理委员会/数据保护合规实践 |
| Context Data Categories and Privacy Model for Mobile Data Collection Apps (PM-MoDaC) | Beierle 等 (Würzburg) | 2018 | 论文 | https://arxiv.org/abs/1807.01515 | 提出 4 类（物理活动/设备状态/核心功能/应用使用）采集模型与 9 条隐私措施 |
| UsageStatsManager | Android Developers (Google) | – | 官方文档 | https://developer.android.com/reference/android/app/usage/UsageAccessManager | Android 5.0+ 系统级 app 使用统计入口，所有 OS 级行为研究的事实起点 |
| Family Controls | Apple Developer Documentation | 2021+ | 官方文档 | https://developer.apple.com/documentation/familycontrols | iOS 15+ 家庭控制/屏幕时间授权能力，是 iOS 上唯一合规的"应用使用/限额"采集入口 |
| DeviceActivity framework | Apple Developer Documentation | 2021+ | 官方文档 | https://developer.apple.com/documentation/DeviceActivity | iOS 16+ DeviceActivity API，让第三方 app 监听用户设备使用阈值与日程 |
| User Interaction Data in Apps: Comparing Policy Claims to Implementations | Tang & Østvold (NTNU) | 2023 | 论文 (IFIPSC) | https://arxiv.org/abs/2312.02710 | 对 Top 100 App 静态分析 swipe/zoom 等 in-app 交互数据采集与隐私政策一致性 |
| A Study on Screen Logging Risks of Secure Keyboards of Android Financial Apps | Liang & Ma (Nanjing U) | 2022 | 论文 (IEEE SANER) | https://doi.org/10.1109/SANER53432.2022.00024 | 直接揭示 AccessibilityService/屏幕日志在金融 App 上的隐私暴露面 |
| RPCDroid: Runtime Identification of Permission Usage Contexts in Android Applications | Guerra, Milanese, Oliveto, Fasano | 2023 | 论文 (ICISSP) | https://doi.org/10.5220/0011797200003405 | 运行时识别 Android 权限使用上下文，对应 OS 级权限-行为关联建模 |

## 2. App 启动预测与智能预加载

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| AppFlow: Memory Scheduling for Cold Launch of Large Apps on Mobile and Vehicle Systems | X. Li, S. Liu, B. Guo, Y. Ouyang 等 (Northwestern Polytechnical U) | 2026 | 论文 (MobiCom) | https://arxiv.org/abs/2603.17259 | 跨 Android 框架 + Linux 内核的预测式冷启动调度，把"app 启动预测"直接做成系统级工程 |
| STAP: A Shuffle-Tokenized App Predictor with Ultra Long Context for Vocabulary-Free Mobile App Prediction | C. Fan, H. Liu | 2026 | 论文 (preprint) | https://arxiv.org/abs/2605.29863 | 跨设备冷启动场景下的 next-app 预测，强调"无固定词表 + 超长上下文 + 低延迟部署" |
| AppStreamer: Reducing Storage Requirements of Mobile Games through Predictive Streaming | Theera-Ampornpunt, Suryavansh, Panta, Manchanda 等 (Purdue + Colgate) | 2020 | 论文 (EWSN) | https://arxiv.org/abs/2001.08169 | 预测式按需拉取 app 文件块，是"predictive caching"在 Android 文件系统层的代表工作 |
| Context-Aware Target Apps Selection and Recommendation for Enhancing Personal Mobile Assistants | Aliannejadi, Zamani, Crestani, Croft (UMass + USI) | 2021 | 论文 (ACM TOIS) | https://arxiv.org/abs/2101.03394 | 把"next app recommendation"和"unified mobile search"放进同一个智能助手框架，含公开数据集 |
| Smartphone Usage and Next App Prediction for Smart Interventions: A Quantum LSTM Approach | V S Harikrishnan, K Ganesh | 2025 | 论文 (Procedia CS) | https://doi.org/10.1016/j.procs.2025.04.303 | 量子 LSTM 做 next-app 预测，用于"干预而非只是推荐" |
| Predicting Smartphone Battery Life based on Comprehensive and Real-time Usage Data | H. Li, X. Liu (PKU), Q. Mei (Michigan) | 2018 | 论文 | https://arxiv.org/abs/1801.04069 | 51 用户 21 个月细粒度系统/传感器/app 轨迹，是公开采集规模的代表 |

## 3. 通知交互行为（Notification interaction）

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Intelligent Notification Systems | Mehrotra & Musolesi (UCL + Turing Institute) | 2020 | 综述书 | https://doi.org/10.1007/978-3-031-02487-0 | 移动通知系统的权威综述，覆盖打断成本、可中断性建模、排序调度 |
| Interpretable Machine Learning for Mobile Notification Management | Mehrotra, Hendley, Musolesi | 2017 | 论文 (GetMobile) | https://doi.org/10.1145/3131214.3131225 | 解释性 ML 做通知管理，端侧可解释是关键 |
| Continual Prediction of Notification Attendance with Classical and Deep Network Approaches | Katevas, Leontiadis, Pielot, Serrà (Telefonica Research) | 2017 | 论文 | https://arxiv.org/abs/1712.07120 | 279 用户 / 446k 通知 / 5 周，RNN 直接基于移动 sensor log 做持续可中断性预测 |
| Reachable but not receptive: Enhancing smartphone interruptibility prediction by modelling the extent of user engagement with notifications | Turner, Allen, Whitaker (Cardiff) | 2017 | 论文 (Pervasive & Mobile Computing) | https://doi.org/10.1016/j.pmcj.2017.01.011 | 区分"reachable vs receptive"两层，是通知建模维度的核心拓展 |
| A Survey of Attention Management Systems in Ubiquitous Computing Environments | Anderson, Hübener, Seipp, Ohly, David, Pejovic | 2018 | 综述 (IMWUT) | https://arxiv.org/abs/1806.06771 | 把通知/打断理论、注意模型、sensing 与 ML 串成完整工程化综述 |
| Investigating the Effects of Mood & Usage Behaviour on Notification Response Time | Heinisch, Gao, Anderson, Deldari, David, Salim | 2022 | 论文 | https://arxiv.org/abs/2207.03405 | 用 E4 手环生理信号 + 心情 + app 使用建模通知响应时间 |
| The Impact of Private and Work-Related Smartphone Usage on Interruptibility | Anderson, Heinisch, Ohly, David, Pejovic | 2019 | 论文 (UbiComp Adjunct) | https://arxiv.org/abs/1907.04739 | 用 app 序列对应社交角色与打断策略，是"行为角色"建模的切入点 |
| Smartphone Interruptibility Using Density-Weighted Uncertainty Sampling with RL | Fisher & Simmons (CMU) | 2011 | 论文 (ICMLA) | https://doi.org/10.1109/ICMLA.2011.128 | 早期主动学习+RL 通知调度工作 |
| Investigating the Role of Task Engagement in Mobile Interruptibility | Pejovic, Musolesi, Mehrotra | 2015 | 论文 (MobileHCI Adjunct) | https://doi.org/10.1145/2786567.2794336 | 任务卷入度作为可中断性特征 |

## 4. App 会话与切换模式

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Cohort Modeling Based App Category Usage Prediction | Tian, Zhou, Lalmas (Spotify), Liu (THU), Pelleg (Yahoo) | 2020 | 论文 (UMAP) | https://doi.org/10.1145/3340631.3394849 | 用 cohort 模型做 app 类别使用预测，是商业 streaming 平台与学术合作的代表 |
| AppGen: Mobility-aware App Usage Behavior Generation for Mobile Users | Huang, Li (THU) | 2024 | 论文 | https://arxiv.org/abs/2412.07267 | 用扩散模型生成符合移动轨迹的 app 使用序列，解决隐私+稀缺数据 |
| Predicting App Usage Based on Link Prediction in User-App Bipartite Network | Tan, Yu, Wu, Pan, Liu | 2018 | 论文 (SmartCom) | https://doi.org/10.1007/978-3-319-73830-7_20 | 把 next-app 预测当二部图链路预测，是切换模式建模的非序列视角 |
| Tracking Smartphone App Usage for Time-Aware Recommendation | Bahrainian & Crestani (USI) | 2017 | 论文 | https://doi.org/10.1007/978-3-319-70232-2_14 | 时间感知的 app 使用追踪 → 推荐，对 session/时间槽建模很直接 |
| What's in the apps for context? | Böhmer, Lander, Krüger (DFKI) | 2013 | 论文 (UbiComp Adjunct) | https://doi.org/10.1145/2494091.2496038 | 早期把 app 使用当上下文信号的研究 |
| Mobile App Usage Pattern prediction using Hierarchical Flexi-Ensemble Clustering (HFEC) | Priyanga & Kamal (Alagappa U) | 2021 | 预印本 | https://doi.org/10.21203/rs.3.rs-272906/v1 | 用聚类做 app 使用 pattern，对长尾用户画像 |
| Speed as context of app usage in daily life | Hsieh & Yu (NTU) | 2017 | 论文 (PNC) | https://doi.org/10.23919/PNC.2017.8203539 | 把"移动速度"当 context 对 app session 切分 |
| Apps, Places and People: strategies, limitations and trade-offs in the physical and digital worlds | De Nadai, Cardoso, Lima, Lepri, Oliver (Fondazione Bruno Kessler) | 2019 | 论文 | https://arxiv.org/abs/1904.09350 | 40 万人 6 个月，发现"app 容量守恒"——研究 app 使用强度的稀缺大规模证据 |

## 5. 从 app 使用预测用户特质

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Learning Language and Multimodal Privacy-Preserving Markers of Mood from Mobile Data | Liang, Liu, Cai 等 (CMU) | 2021 | 论文 (ACL) | https://arxiv.org/abs/2106.13213 | 从键盘+app 使用多模态预测青少年情绪，并做隐私脱敏 |
| Multimodal Privacy-preserving Mood Prediction from Mobile Data: A Preliminary Study | Liu, Liang 等 (CMU) | 2020 | 论文 | https://arxiv.org/abs/2012.02359 | ACL 论文的前置工作，提出 performance-privacy frontier |
| Predicting Privacy Attitudes Using Phone Metadata | Ghosh & Singh (Rutgers) | 2016 | 论文 (SBP) | https://arxiv.org/abs/1604.04167 | 用 phone metadata 预测隐私态度——是"特质→行为→特质"反向的稀缺研究 |
| Smartphone apps usage patterns as a predictor of perceived stress levels at workplace | Ferdous, Osmani, Mayora (Create-Net) | 2018 | 论文 | https://arxiv.org/abs/1803.03863 | 用 app 使用模式预测工作压力，准确率 75% |
| App Limits Bar: A Progress of App Limits for Overcoming Smartphone Overuse | Y. Wu | 2020 | 论文 | https://arxiv.org/abs/2011.14825 | 把"成瘾干预"做成 OS 级 App Limits 改进 |
| Usage Prediction and Effectiveness Verification of App Restriction Function for Smartphone Addiction | Yasudomi, Hamamura, Honjo, Yoneyama, Uchida (NTT) | 2021 | 论文 (IEEE HEALTHCOM) | https://doi.org/10.1109/HEALTHCOM49281.2021.9398974 | NTT 对"app 限制功能"的有效性做实测，工业视角 |
| Understanding the Social Context of Eating with Multimodal Smartphone Sensing | Kammoun, Meegahapala, Gatica-Perez (EPFL) | 2023 | 论文 (ICMI) | https://arxiv.org/abs/2306.00709 | 8 国 678 学生，用 app 使用+sensor 推断进餐社交场景，跨文化样本 |
| FedTherapist: Mental Health Monitoring with User-Generated Linguistic Expressions on Smartphones via Federated Learning | Shin, Yoon 等 (NVIDIA + SNU 等) | 2023 | 论文 (EMNLP) | https://arxiv.org/abs/2310.16538 | 端侧 FL 用键盘+应用做抑郁/压力/情绪预测，IRB 46 人 |

## 6. 移动端智能助手 / 负一屏推荐系统

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Next-generation of virtual personal assistants (Microsoft Cortana, Apple Siri, Amazon Alexa and Google Home) | Kepuska & Bohouta (Florida Atlantic) | 2018 | 论文 (IEEE CCWC) | https://doi.org/10.1109/CCWC.2018.8301638 | 对比四大主流助手的架构与个性化能力，是工业落地的参考综述 |
| Context-Aware Target Apps Selection and Recommendation for Enhancing Personal Mobile Assistants | Aliannejadi, Zamani, Crestani, Croft | 2021 | 论文 (ACM TOIS) | https://arxiv.org/abs/2101.03394 | 把智能助手 + app 推荐做联合建模，附公开 in situ 数据集 |
| Proactive Agent Research Environment: Simulating Active Users to Evaluate Proactive Assistants | Nathani, Zhang 等 (Apple ML Research) | 2026 | 工业研究 | https://machinelearning.apple.com/research/proactive-agent-research-environment | Apple 自家关于"proactive assistant"评测环境的公开研究页 |
| Federated Learning: Collaborative Machine Learning without Centralized Training Data | McMahan & Ramage (Google Research) | 2017 | 工业博客 | https://research.google/blog/federated-learning-collaborative-machine-learning-without-centralized-training-data/ | Gboard 上 FL 的官方首篇博客，是端侧个性化推荐的工业起点 |
| Google services for journalists and media: Recommendations for Google Discover and Google News | Lopezosa, Cordeiro, López-Munuera, Guallar | 2025 | 综述 | https://doi.org/10.2139/ssrn.5706382 | 公开讨论 Google Discover 推荐机制与内容策略 |
| Karma-based API on Apple Platforms – Siri and Search | Carrasco Molina | 2019 | 章节 (Springer) | https://doi.org/10.1007/978-1-4842-4291-9_7 | Apple 平台 Siri/搜索 API 工程视角的整理 |
| iPhone's Digital Marketplace: Characterizing the Big Spenders | Kooti, Grbovic, Aiello, Bax, Lerman (USC + Yahoo) | 2017 | 论文 (WSDM) | https://arxiv.org/abs/1701.07411 | 776M 笔 Apple 数字消费，是公开可查的"应用市场消费行为"最大规模工业研究 |

## 7. 移动端隐私保护方法（FL / 端侧 ML / DP）

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Federated Learning of Gboard Language Models with Differential Privacy | Xu, Zhang, Andrew, Choquette-Choo, Kairouz, McMahan 等 (Google) | 2023 | 论文 (ACL Industry) | https://arxiv.org/abs/2305.18465 | Gboard 上 FL+DP 的工业实战，给出 ρ-zCDP 隐私保证 |
| Private Federated Learning in Gboard | Zhang, Ramage, Xu 等 (Google) | 2023 | 白皮书 | https://arxiv.org/abs/2306.14793 | Gboard FL+DP-FTRL+SecAgg 的工程白皮书 |
| Two Models are Better than One: FL Is Not Private For Google GBoard Next Word Prediction | Suliman & Leith (Trinity College Dublin) | 2022 | 论文 (ESORICS) | https://arxiv.org/abs/2210.16947 | 反方证据：揭示 Gboard FL 仍可重构用户键入，是隐私边界研究的关键警示 |
| Prompt Public LLMs to Synthesize Data for Private On-device Applications | Wu, Xu, Zhang 等 (Google) | 2024 | 论文 | https://arxiv.org/abs/2404.04360 | 用 LLM 合成预训练数据提升端侧 DP-FL 模型，A/B 上线验证 |
| Building a privacy-preserving Federated Recommender system for mobile devices | Singh (U. Montréal) | 2026 | 论文/硕士论文 | https://arxiv.org/abs/2605.22924 | Kotlin Multiplatform 实现的端侧+云两阶段 FR pipeline，可部署 |
| Beyond Centralization: User-Controlled Federated Recommendations in Practice | Slokom & Bellogin (TU Delft) | 2026 | 论文 | https://arxiv.org/abs/2605.12527 | 53 天 22 人 live FR 部署实验，研究"用户控制推荐目标" |
| A Scenario-Oriented Survey of Federated Recommender Systems | Mi, Shen, Zhao 等 (Xidian) | 2025 | 综述 | https://arxiv.org/abs/2508.19620 | 按推荐场景划分 FR 综述，最贴近工业落地视角 |
| FedFlex: Federated Learning for Diverse Netflix Recommendations | Lankester 等 (TU Delft + Netflix) | 2025 | 论文 | https://arxiv.org/abs/2507.21115 | Netflix + 学术合作的 FR 在线用户研究 |
| Personalized Federated Recommendation With Knowledge Guidance (FedRKG) | Lim 等 (POSTECH) | 2025 | 论文 | https://arxiv.org/abs/2511.12959 | 解决端侧 FR 的内存/个性化 trade-off |
| A Model-agnostic Strategy to Mitigate Embedding Degradation in Personalized FR (PLGC) | Shen, Mi, Zhao 等 (Xidian) | 2025 | 论文 | https://arxiv.org/abs/2508.19591 | 用 NTK 解决 FR 维度塌缩——端侧推荐特有问题 |

## 8. UI 事件流 / 细粒度交互挖掘（Mobile GUI Agents / RPA）

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Xiaomi-GUI-0 Technical Report | Cao 等 (Xiaomi) | 2026 | 技术报告 | https://arxiv.org/abs/2606.31410 | 小米自家 mobile GUI agent，real-device + sandbox 闭环——中国厂商工业代表 |
| PhoneWorld: Scaling Phone-Use Agent Environments | Tang 等 (中国人民大学 + Xiaomi) | 2026 | 论文 | https://arxiv.org/abs/2605.29486 | 把真实 GUI 轨迹转化为可控 mock 环境，可作行为日志合成 |
| UI-KOBE: Knowledge-Oriented Behavior Exploration for Lightweight Graph-Guided GUI Agents | Chai 等 (CUHK) | 2026 | 论文 | https://arxiv.org/abs/2605.29534 | 构建 app 状态图当知识库指导轻量 agent，端侧可部署 |
| MobileForge: Annotation-Free Adaptation for Mobile GUI Agents | Liu 等 (Ant Group) | 2026 | 论文 | https://arxiv.org/abs/2606.19930 | 无标注自适应到真实 app，工业级 agent 闭环 |
| PhoneHarness: Harnessing Phone-Use Agents through Mixed GUI, CLI, and Tool Actions | Li 等 (PKU + Xiaomi) | 2026 | 论文 | https://arxiv.org/abs/2606.14832 | 把 GUI/CLI/Tool 混合 agent 落到可验证执行 |
| PalmClaw: A Native On-Device Agent Framework for Mobile Phones | Cai, Li 等 (HKUST) | 2026 | 论文 | https://arxiv.org/abs/2607.13027 | 端侧原生 agent 框架，开源 |
| User Interaction Data in Apps: Comparing Policy Claims to Implementations | Tang & Østvold (NTNU) | 2023 | 论文 (IFIPSC) | https://arxiv.org/abs/2312.02710 | 静态分析 Top 100 App 实际采集的 swipe/zoom 等 in-app 交互日志 |
| AdaLog: Optimizing Storage Overhead of User Behavior Log for ML-embedded Mobile Apps | Gong, Zhuang 等 (Ant Group + SJTU) | 2025 | 论文 | https://arxiv.org/abs/2510.13405 | 工业上 ML 内嵌 app 行为日志存储优化，把"采集工程化"做透 |
| VenusBench-Mobile: A Challenging and User-Centric Benchmark for Mobile GUI Agents | Gong 等 (Ant Group) | 2026 | 论文 | https://arxiv.org/abs/2604.06182 | 用户意图视角的真实移动 GUI agent benchmark |

## 9. 跨应用 / 跨设备行为建模 + Digital Wellbeing

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Preference, context and communities: a smartphone preference learning framework using sensors | Xu, Lin, Lu 等 (Dartmouth + Intel) | 2013 | 论文 (ISWC) | https://doi.org/10.1145/2493988.2494333 | 手机+可穿戴 sensor 做 preference learning 的早期代表 |
| Exploring Context-Aware User Interfaces for Smartphone-Smartwatch Cross-Device Interaction | Kubo, Takada, Shizuki, Takahashi (U Tsukuba) | 2017 | 论文 (IMWUT) | https://doi.org/10.1145/3130934 | 手机+手表跨设备 UI 交互的工程化研究 |
| Cross-device task interaction framework between the smart watch and the smart phone | Xu, Wang 等 (Shandong U) | 2019 | 论文 (PUC) | https://doi.org/10.1007/s00779-019-01280-7 | 跨设备任务交互框架 |
| Understanding Digital Wellbeing Through Smartphone Usage Intentions and Regrettable Patterns | Islambouli, Ingram, Gillet (EPFL + HES-SO) | 2024 | 论文 (IEEE ICHI) | https://doi.org/10.1109/ICHI61247.2024.00061 | 把"行为意图"与"后悔模式"作为 wellbeing 度量 |
| "In my defense, only three hours on Instagram": Designing Toward Digital Self-Awareness and Wellbeing (WellScreen) | Bhat, Shi, Song, Yoo, Saha (Georgia Tech + Notre Dame) | 2026 | 论文 (CHI) | https://arxiv.org/abs/2509.21860 | 用每日自报 vs 实际使用差距做轻量反思干预 |
| ScreenTK: Seamless Detection of Time-Killing Moments Using Continuous Mobile Screen Text and On-Device LLMs | Fang, Zhang, Jia, Goncalves, Kostakos (U Melbourne) | 2024 | 论文 (UbiComp) | https://arxiv.org/abs/2407.03063 | 端侧 LLM + 屏幕文本持续监测"杀时间"行为，是干预闭环的关键一环 |
| Predicting Affective States from Screen Text Sentiment | Teng, Zhang, D'Alfonso, Kostakos (U Melbourne) | 2024 | 论文 (CHI) | https://arxiv.org/abs/2408.12844 | 屏幕文本情感→情绪，把 OS 上的文本流变成可推断信号 |
| Mobile Application Traffic Reveals Multifunctional Use Patterns in Parisian Parks | Zanella, Dietz, Šćepanović, Zhou, Smoreda, Quercia (Nokia Bell Labs + TU Eindhoven) | 2025 | 论文 | https://arxiv.org/abs/2508.15516 | 用 per-app 流量代理行为，是"无 OS 权限"采集的另一路径 |

## 10. 移动端行为推荐工业落地

| 标题 | 作者/机构 | 年份 | 类型 | 链接 | 关联 |
|---|---|---|---|---|---|
| Mining smartphone data for app usage prediction and recommendations: A survey | Cao & Lin (RMIT) | 2017 | 综述 (Pervasive & Mobile Computing) | https://doi.org/10.1016/j.pmcj.2017.01.007 | 把 app usage prediction + recommendation 做过最系统的早期综述 |
| AppNet: understanding app recommendation in Google Play | Guo, Wang, Zhang, Guo, Xu (BUPT + PKU) | 2019 | 论文 (App Market Analytics Workshop) | https://doi.org/10.1145/3340496.3342757 | 直接刻画 Google Play 里的 app 推荐关系图 |
| Characterizing the app recommendation relationships in the iOS app store: a complex network's perspective | Huang, Lin, Ma, Wang, Wang, Tyson, Liu (PKU + Queen Mary) | 2025 | 论文 (Science China Information Sciences) | https://doi.org/10.1007/s11432-023-3973-1 | iOS App Store 推荐关系的复杂网络视角 |
| The Spillover of Spotlight: Platform Recommendation in the Mobile App Market | Liang, Shi, Raghu (UConn + ASU) | 2019 | 论文 (Information Systems Research) | https://doi.org/10.1287/isre.2019.0863 | 推荐位对 app 市场表现的溢出效应，工业经济学视角 |
| Mobile app store analytics | Nagappan & Shihab | 2016 | 章节 | https://doi.org/10.1016/B978-0-12-804206-9.00009-X | 移动应用市场分析的方法论起点 |
| Smartphone and Tablet Application (App) Life Cycle Characterization via Apple App Store Rank | Jia, Guo, Liu | 2020 | 论文 (Data and Information Management) | https://doi.org/10.2478/dim-2020-0002 | 用排行榜序列刻画 app 生命周期 |
| sensortowerR: Interface to 'Sensor Tower' Mobile App Intelligence API | P. Black | 2025 | 开源 | https://doi.org/10.32614/cran.package.sensortowerr | R 包对接 Sensor Tower API，是第三方分析公开方法论的入口 |
| One Size Does not Fit All: Quantifying the Risk of Malicious App Encounters for Different Android User Profiles | Dambra, Bilge, Kotzias, Shen, Caballero (Symantec + Stanford + IMDEA) | 2023 | 论文 | https://arxiv.org/abs/2301.07346 | 12M Android 设备安装日志做用户画像+恶意 app 风险——工业级数据 |
| Asymmetric Diffusion Recommendation Model (AsymDiffRec) | Zhu 等 (Douyin Music) | 2025 | 论文 (CIKM) | https://arxiv.org/abs/2508.12706 | Douyin Music 工业系统上线 A/B 实测，含用户活跃天数 +0.131% |
| AdaLog | Gong, Zhuang 等 (Ant Group) | 2025 | 论文 | https://arxiv.org/abs/2510.13405 | 把"采集→存储→推荐"工程化瓶颈量化，是端侧 ML 工业落地参考 |

---

## 总结

### 一、移动端 vs PC 桌面端的独特性

PC 端的"行为采集"基本都靠浏览器/系统侧的被动日志（URL、窗口标题），权限分散在每家 ISV 手里；移动端则呈现"OS 垄断+设备感知+权限闸口"的三重差异：

1. **采集能力被 Google/Apple 收敛**到 `UsageStatsManager`、`Screen Time API`、`DeviceActivity`、`AccessibilityService` 等少数几个系统 API，研究方与厂方都得围绕这套权限模型做文章；
2. **端上具备远比 PC 丰富的多模态信号**——IMU、位置、屏幕文本、键盘计时、生理手环，让"行为→特质/情绪"的反向推断（CMU、EPFL、Trinity、Apple ML 的工作）成为可能；
3. **iOS 15/16+ 的 Family Controls 与 Android 隐私沙箱**让"端侧 ML + FL + DP"成为唯一合规路径，Gboard 已成事实标杆——但 Suliman & Leith 的攻击又提醒这条路并非天然安全。

### 二、工业落地路径（采集 → 建模 → 推荐 → 干预）

**已成熟**：
- **通知可中断性预测**（Mehrotra 综述、Katevas 数据集、Turner "reachable/receptive"），Google/Apple 已经在系统通知排序里使用；
- **联邦学习+DP 在 Gboard 上线**（Google 2023 ACL/白皮书），是端侧个性化的事实标准；
- **应用商店推荐**（Guo AppNet、Huang iOS 复杂网络、Sensor Tower API），既存在 OEM 自家 ranking，也存在第三方数据方法论。

**半成熟**：
- **app 启动预测与预加载**（AppFlow 在 MobiCom 2026 才把"预测式冷启动"做成系统调度，Xiaomi/Apple 都在试）；
- **UI 事件级 RPA**（Xiaomi-GUI-0、MobileForge、PhoneHarness 等大量 2026 年技术报告，仍处于 benchmark→可用之间）。

**仍处研究阶段**：
- 把"app 使用 → 心理特质/情绪"做端侧联邦部署（FedTherapist 是早期）；
- Digital Wellbeing 闭环（WellScreen、ScreenTK 在做轻量探针，但缺少持续 RCT 证据）；
- 跨手机+手表+车机的统一行为建模，Kubo/Xu 之后基本没有公开工业系统跟进。

### 三、最值得做的 3 个机会点

1. **OS 级"通知 × app 会话 × 屏幕文本"的端侧联合建模**：当前 ScreenTK 把屏幕文本、Katevas 把通知、Tian 把 cohort 类别使用，三条线是分开走的；但端侧 LLM 已经能跑（Apple ML、Xiaomi-GUI-0），把这三类信号统一进一个端侧小模型，做"用户当下处于何种卷入度/可中断度"的实时状态机，再触发通知排序与负一屏推荐，是工业上"可上手机、可被法务通过"的高价值空缺。
2. **"采集工程化"作为研究子方向本身**：AdaLog（Ant Group, 2025）揭示"行为日志存储"在端侧 ML 上是真正的瓶颈，国内大厂在 ML 内嵌 app 上普遍卡在这一层；同时 iOS 的 DeviceActivity / Android 的 Privacy Sandbox 让"采集-存储-特征-推理"链路需要重新设计。围绕这条链路做存储-压缩-特征工程联合优化（含 differential privacy 编码），是工程学术两栖的稀缺机会。
3. **国产厂商 OS 个性化助手 → 行为闭环的公开方法论缺口**：Xiaomi-GUI-0 已经把端侧 GUI agent 的训练-沙箱-真机闭环公开化，但"华为负一屏/OPPO 智慧助手/vivo OriginOS 负一屏/小米焦点相机推荐"这些产品的"行为→推荐"算法侧方法论几乎没有公开论文或可核验专利索引；这块有大量内嵌的产品行为数据但学术上完全空白，可从 CNIPA 公开专利 + 高校合作论文（Xidian、PKU、THU、BUPT）反推方法论框架，是研究-产品双向最容易出"first-of-its-kind"的方向。
