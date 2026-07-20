# 学术研究论文

按 5 个主题分组。所有链接均经 CrossRef / arXiv / DBLP 核实。

## A1. 应用使用预测 / 下一应用推荐（App usage & next-app prediction）

1. **App2Vec: Context-Aware Application Usage Prediction** — Huandong Wang、Yong Li（清华）— 2021, ACM TKDD — https://doi.org/10.1145/3451396 — word2vec 学 app 嵌入 + 贝叶斯混合，预测"何时/何地/用什么"。
2. **DeepAPP: A Deep Reinforcement Learning Framework for Mobile Application Usage Prediction** — Zhihao Shen 等（西安交大/UC Merced）— 2021, IEEE TMC — https://doi.org/10.1109/TMC.2021.3093619 — 深度强化学习处理大动作空间的 app 使用预测。
3. **Appformer: A Novel Framework for Mobile App Usage Prediction Leveraging Progressive Multi-Modal Data Fusion** — Chuike Sun 等（中山大学）— 2024, Expert Systems with Applications — https://arxiv.org/abs/2407.19414 — Transformer 融合 POI/时间多模态做预测，关注隐私。
4. **MAPLE: Mobile App Prediction Leveraging Large Language Model Embeddings** — Yonchanok Khaokaew、Flora D. Salim（UNSW）— 2024, IMWUT — https://arxiv.org/abs/2309.08648 — LLM embedding 缓解冷启动。
5. **CoSEM: Contextual and Semantic Embedding for App Usage Prediction** — Yonchanok Khaokaew、Ryen White（Microsoft Research/UNSW）— 2021, CIKM — https://arxiv.org/abs/2108.11561 — 应用本体语义 + 历史上下文双通道。
6. **WhatsNextApp: LSTM-Based Next-App Prediction With App Usage Sequences** — Katerina Katsarou 等（TU Berlin）— 2022, IEEE Access — https://doi.org/10.1109/ACCESS.2022.3150874 — LSTM 对 app 使用序列做下一应用预测。
7. **Federated Privacy-preserving Collaborative Filtering for On-Device Next App Prediction** — Albert Sayapin 等（Skoltech）— 2023, arXiv — https://arxiv.org/abs/2303.04744 — 联邦 SeqMF 设备端预测下一 app，兼顾隐私。
8. **App usage on-the-move: Context- and commute-aware next app prediction** — Yufan Kang、Flora D. Salim、Ryen W. White（RMIT + Microsoft）— 2022, Pervasive and Mobile Computing — https://doi.org/10.1016/j.pmcj.2022.101704 — 通勤场景上下文感知预测。
9. **Optimizing Smartphone App Usage Prediction: A Click-Through Rate Ranking Approach** — Yuqi Zhang 等（哈工大）— 2024, KDD — https://doi.org/10.1145/3637528.3671567 — 把 app 使用预测建模为 CTR 排序问题。
10. **Prediction of Application Usage on Smartphones via Deep Learning** — Abdulrahman Alruban — 2022, IEEE Access — https://doi.org/10.1109/ACCESS.2022.3171579 — 深度学习预测智能手机应用使用。
11. **What and How long: Prediction of Mobile App Engagement** — Yuan Tian、Ke Zhou、Dan Pelleg — 2021, ACM TOIS — https://arxiv.org/abs/2106.01490 — 联合预测"下一个 app"和"停留多久"。
12. **Smartphone App Usage Prediction Using Points of Interest** — Donghan Yu、Yong Li、Fengli Xu（清华+Stanford）— 2018, IMWUT — https://doi.org/10.1145/3161413 — POI 上下文预测 app 使用。
13. **MISApp: Multi-Hop Intent-Aware Session Graph Learning for Next App Prediction** — Yunchi Yang 等 — 2026, arXiv — https://arxiv.org/abs/2603.21653 — 无 profile 冷启动下用多跳会话图刻画意图漂移。
14. **MobiGPT: A Foundation Model for Mobile Wireless Networks** — Xiaoqian Qi、Yong Li（清华）— 2025, arXiv — https://arxiv.org/abs/2509.18166 — 统一基础模型预测基站流量、用户 app 使用、信道质量。
15. **Which app will you use next? Collaborative filtering with interactional context** — Nagarajan Natarajan、Inderjit Dhillon（UT Austin）— 2013, RecSys — https://doi.org/10.1145/2507157.2507186 — 经典：带交互上下文的协同过滤做下一 app 推荐。
16. **Frappe: Understanding the Usage and Perception of Mobile App Recommendations In-The-Wild** — Linas Baltrunas、Karen Church（Telefonica Research）— 2015, arXiv — https://arxiv.org/abs/1505.03014 — 上下文感知 app 推荐野外研究。
17. **Learning Dynamic App Usage Graph for Next Mobile App Recommendation** — Yi Ouyang、Bin Guo、Zhiwen Yu（西北工业大学）— 2023, IEEE TMC — https://doi.org/10.1109/TMC.2022.3161114 — 动态 app 使用图做下一 app 推荐。
18. **AppTrends: A graph-based mobile app recommendation system using usage history** — Donghwan Bae 等 — 2015, BigComp — https://doi.org/10.1109/35021BIGCOMP.2015.7072833 — 基于使用历史的图推荐系统。
19. **TGT: A Temporal Gating Transformer for Smartphone App Usage Prediction** — Longlong Li、Cunquan Qu、Guanghui Wang — 2025, arXiv — https://arxiv.org/abs/2502.16957 — hour-of-day 时间门控处理稀疏/冷启动，超越 15 个基线并解释作息模式。
20. **On the Feature Discovery for App Usage Prediction in Smartphones** — Zhung-Xun Liao、Wen-Chih Peng、Philip S. Yu（NCTU）— 2013, ICDM — https://arxiv.org/abs/1309.7982 — 早期奠基：显式传感 + 隐式 app 转移图特征，服务于快速启动/省电。
21. **Learning Mobile App Usage Routine through Learning Automata** — Ramin Rahnamoun、Reza Rawassizadeh、Arash Maskooki — 2016, arXiv — https://arxiv.org/abs/1608.03507 — 在线学习 app 启动转移概率，对接 OS 缓存预加载。
22. **REVAMP: Modeling Spatial Trajectories using Coarse-Grained Smartphone Logs** — Vinayak Gupta、Srikanta Bedathur（IIT Delhi）— 2022, IEEE TBD — https://arxiv.org/abs/2208.13775 — 仅用粗粒度隐私友好日志做 POI 序列推荐。
23. **MIDiff: Tackling Sparsity and Imbalance in Mobile Usage Generation via Multivariate-Imaging Diffusion** — Yilai Liu 等（HKU）— 2026, arXiv — https://arxiv.org/abs/2607.14249 — 扩散模型生成移动使用日志服务推荐/预测。

## A2. 桌面端用户行为分析（Desktop activity / window & task switching）

24. **The cost of interrupted work: more speed and stress** — Gloria Mark、Daniela Gudith、Ulrich Klocke（UC Irvine + Humboldt）— 2008, CHI — https://doi.org/10.1145/1357054.1357072 — 经典：工作中断的注意力/任务切换奠基研究。
25. **Leveraging characteristics of task structure to predict the cost of interruption** — Shamsi T. Iqbal、Brian P. Bailey（UIUC）— 2006, CHI — https://doi.org/10.1145/1124772.1124882 — 从任务结构预测桌面中断成本。
26. **Detecting Developers' Task Switches and Types** — André N. Meyer、Thomas Fritz（UZH）+ Microsoft Research — 2020, IEEE TSE — https://doi.org/10.1109/TSE.2020.2984086 — 从电脑交互日志自动检测开发者任务切换与类型（直接对应 OS 级操作记录做行为分析）。
27. **Supporting Software Developers' Focused Work on Window-Based Desktops** — Jan Pilzer、Thomas Fritz（UBC+UZH）— 2020, CHI — https://doi.org/10.1145/3313831.3376285 — 基于窗口的桌面专注工作支持，分析窗口/应用切换。
28. **Comparing episodic and semantic interfaces for task boundary identification** — Izzet Safer、Gail C. Murphy（UBC）— 2007, CASCON — https://doi.org/10.1145/1321211.1321235 — 从桌面交互日志识别任务边界。
29. **Improving Window Switching Interfaces** — Susanne Tak、Andy Cockburn、Keith Humm — 2009, INTERACT — https://doi.org/10.1007/978-3-642-03658-3_25 — 窗口切换界面的设计与评估。
30. **Exploring the Effectiveness of Time-lapse Screen Recording for Self-Reflection in Work Context** — Donghan Hu、Sang Won Lee（Virginia Tech）— 2024, CHI — https://doi.org/10.1145/3613904.3642469 — 屏幕录像做工作自我反思，连接 lifelogging 与桌面行为。

## A3. OS 级 / 系统级用户行为日志与用户建模

31. **Layered representations for learning and inferring office activity from multiple sensory channels** — Nuria Oliver、Ashutosh Garg、Eric Horvitz（Microsoft Research）— 2004, CVIU — https://doi.org/10.1016/j.cviu.2004.02.004 — 经典：多通道系统日志推断办公室（电脑）活动，OS 级行为建模代表工作。
32. **Private traits and attributes are predictable from digital records of human behavior** — Michał Kosinski、David Stillwell、Thore Graepel（Cambridge + Microsoft Research）— 2013, PNAS — https://doi.org/10.1073/pnas.1218772110 — 从数字行为记录预测用户特质，OS 行为日志用户建模的标志工作。
33. **A systematic review and meta-analysis of discrepancies between logged and self-reported digital media use** — Douglas A. Parry 等 — 2021, Nature Human Behaviour — https://doi.org/10.1038/s41562-021-01117-5 — 系统比较"系统日志"与"自报"数字媒体使用差异，方法学相关。
34. **App Usage Predicts Cognitive Ability in Older Adults** — Mitchell Gordon、Leon A. Gatys、Carlos Guestrin（Stanford + Apple）— 2019, CHI — https://doi.org/10.1145/3290605.3300398 — 用 OS 级 app 使用记录推断用户认知能力。

## A4. 移动端应用使用数据挖掘（Mobile app usage mining）

35. **By their apps you shall understand them** — Trinh-Minh-Tri Do、Daniel Gatica-Perez（EPFL/Idiap）— 2010, ICMI — https://doi.org/10.1145/1899475.1899502 — 从 app 使用挖掘用户特征。
36. **Smartphone usage in the wild** — Trinh Minh Tri、Jan Blom、Daniel Gatica-Perez（Idiap/EPFL）— 2011, MobileHCI — https://doi.org/10.1145/2070481.2070550 — 大规模真实 app 使用行为分析。
37. **Falling asleep with Angry Birds, Facebook and Kindle: A large scale study on mobile application usage** — Matthias Böhmer、Brent Hecht、Johannes Schöning（DFKI 等）— 2011, MobileHCI — https://doi.org/10.1145/2037373.2037383 — 大规模 app 使用时间模式挖掘。
38. **Predicting user traits from a snapshot of apps installed on a smartphone** — Suranga Seneviratne 等（UNSW + Data61）— 2014, ACM SIGMOBILE MC2R — https://doi.org/10.1145/2636242.2636244 — 从已安装 app 快照预测用户特质。
39. **RecencyMiner: mining recency-based personalized behavior from contextual smartphone data** — Iqbal H. Sarker 等（Swinburne）— 2019, Journal of Big Data — https://doi.org/10.1186/s40537-019-0211-6 — 上下文感知的近期个性化行为挖掘。
40. **Effectiveness analysis of machine learning classification models for predicting personalized context-aware smartphone usage** — Iqbal H. Sarker 等 — 2019, Journal of Big Data — https://doi.org/10.1186/s40537-019-0219-y — 上下文感知个性化手机使用分类模型评估。
41. **Understanding individual behaviour: from virtual to physical patterns** — Marco De Nadai、Bruno Lepri、Nuria Oliver — 2020, ECAI — https://arxiv.org/abs/2002.05500 — 发现 app 使用流与物理移动惊人的相似性，"explorers vs keepers"用户画像。
42. **Composite Social Network for Predicting Mobile Apps Installation** — Wei Pan、Nadav Aharony、Alex Pentland（MIT Media Lab）— 2011, AAAI — https://arxiv.org/abs/1106.0359 — 早期奠基：用手机传感 + 行为数据预测 App 安装。

## A5. Lifelogging / 个人信息学（Personal informatics / quantified self）

43. **A stage-based model of personal informatics systems** — Ian Li、Anind Dey、Jodi Forlizzi（CMU）— 2010, CHI — https://doi.org/10.1145/1753326.1753409 — 经典：个人信息学系统的阶段模型。
44. **Personal tracking as lived informatics** — John Rooksby、Mattias Rost、Alistair Morrison（Glasgow）— 2014, CHI — https://doi.org/10.1145/2556288.2557039 — 个人追踪视为"生活信息学"。
45. **A Quantified Past: Toward Design for Remembering With Personal Informatics** — Chris Elsden、David Kirk、Abigail Durrant（Newcastle）— 2015, HCI — https://doi.org/10.1080/07370024.2015.1093422 — 用个人量化数据做记忆/回顾设计。
46. **Personal Informatics, Self-Insight, and Behavior Change: A Critical Review** — Elisabeth T. Kersten-van Dijk 等（TU Eindhoven）— 2017, HCI — https://doi.org/10.1080/07370024.2016.1276456 — 个人信息学与行为改变批判性综述。
47. **Dealing With Information Overload in Multifaceted Personal Informatics Systems** — Simon Jones、Ryan Kelly（Bath）— 2017, HCI — https://doi.org/10.1080/07370024.2017.1302334 — 多维个人信息系统的信息过载处理。
48. **Uncovering Bias in Personal Informatics** — Sofia Yfantidou、Pavlos Sermpezis、Athena Vakali 等 — 2023, IMWUT — https://doi.org/10.1145/3610914 — 揭示个人量化数据中的偏差。
49. **A Meta-Synthesis of the Barriers and Facilitators for Personal Informatics Systems** — Kazi Sinthia Kabir、Jason Wiese（Utah）— 2023, IMWUT — https://doi.org/10.1145/3610893 — 个人信息系统障碍/促进因素元综合。
50. **HeartSpace: Representation Learning on Variable Length and Incomplete Wearable-Sensory Time Series** — Xian Wu、Chao Huang、Nitesh Chawla（Notre Dame）— 2020, arXiv — https://arxiv.org/abs/2002.03595 — 用稀疏可穿戴时序推断人口统计/人格/身份，"行为 → 用户画像"示范。
51. **A Natural Language Query Interface for Searching Personal Information on Smartwatches** — Reza Rawassizadeh、Chelsea Dobbins、Michael Pazzani — 2016, arXiv — https://arxiv.org/abs/1611.07139 — 个人量化数据上 NL 查询接口，"操作记录 → 行为检索"早期代表。
