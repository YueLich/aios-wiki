# 公开数据集

按 5 类分组。所有链接均经官方主页或 archive.org 快照核实。

## D1. 移动端应用使用数据集

1. **LiveLab** — Rice University，2010–2012，34 用户约 1 年 — `appusage/已装应用/通话/屏幕/电量/加速度/基站/WiFi/浏览历史` — 开放下载 — http://yecl.org/livelab/traces.html — 最直接的 app 会话时长 + 上下文序列，适合做 app 使用时长建模与跨应用切换分析。
2. **StudentLife** — Dartmouth，2014 (UbiComp)，48 学生 10 周 53GB — `app 使用/屏幕锁/通话/位置/活动/光照/音频/WiFi + 心理量表 + GPA` — 开放下载 — http://studentlife.cs.dartmouth.edu/ — 上下文感知的 app 使用预测/用户画像首选。
3. **MIT Reality Mining** — MIT Media Lab（Eagle & Pentland），2004，100 用户 9 个月 — `Symbian 通话/短信/基站/蓝牙邻近/屏幕` — 注册后开放下载 — http://realitycommons.media.mit.edu/realitymining.html — 用户行为序列与社交邻近建模鼻祖。
4. **Friends and Family (Social fMRI)** — MIT Media Lab（Aharony, Pan, Pentland），2011，130 用户约 1 年 — `通话/短信/蓝牙/位置/WiFi/app 使用 + 调查` — 开放下载 — http://realitycommons.media.mit.edu/friendsdataset.html — 社区场景 app 使用 + 社交邻近，适合社会化推荐。
5. **PhoneLab** — SUNY Buffalo，2013 起，数百用户 — `可修改 Android 平台本身并采集设备级日志` — 研究者申请 — https://phone-lab.org/ — 唯一可改 Android 平台层的开放测试床。
6. **Nokia MDC / Lausanne Data Collection Campaign (LDCC)** — Idiap + Nokia Research Center，2009–2011，近 200 用户约 1 年 — `app 使用/GPS/加速度/蓝牙/通话/麦克风` — 协议申请制 — https://web.archive.org/web/2015/https://www.idiap.ch/scientific-research/news/idiap-research-institute-and-nokia-research-center-lausanne-organize-the-mobile-data-challenge-2012 — 大规模真实 app 使用 + 移动/通信上下文。
7. **MobileRec** — UCF（Maqbool, Farooq, Foroosh），2023，1930 万交互 / 70 万用户 — `Google Play 序列化行为` — HuggingFace 开放下载 — https://arxiv.org/abs/2303.06588 — App 行为推荐最常用大规模基准。
8. **ETRI Lifelog Dataset 2024** — 韩国电子通信研究院，2025 — `智能手机+智能手表+睡眠传感器 24h 被动采集` — https://arxiv.org/abs/2508.03698 — 工业研究机构发布的行为建模基线数据。

## D2. 桌面端活动日志数据集

9. **Human Screenome Project / Screenomics** — Stanford（Ram 等），2020 (PNAS) — `每 5 秒一张截图序列 + 应用使用日志 + 交互历史 + 传感器` — 平台/代码开源，数据按研究获取 — https://screenomics.stanford.edu/ — 跨设备"屏幕内容+应用切换"细粒度序列，直接对应桌面/移动端 app 操作行为分析。

> 说明：纯"窗口切换/工作场所 PC 日志"开放数据集极其稀缺，目前仅 Screenomics 覆盖桌面侧。

## D3. Lifelog / 多模态行为数据集

10. **NTCIR Lifelog（NTCIR-12/13/14 Lifelog）** — DCU + NII，2016–2019 — `可穿戴相机图像/生物特征/通信活动/计算机使用日志/活动饮食标注` — 签协议后下载 — http://ntcir-lifelog.computing.dcu.ie/ — 多模态生活日志，适合 app/活动检索、识别、行为摘要。
11. **Lifelog Search Challenge (LSC)** — DCU + ACM ICMR，2018 起 — `连续图像 + 时间/位置/活动/生物特征` — 按挑战协议参与获取 — http://lifelog.dcu.ie/LSC/ — 面向"从生活日志中检索特定 app/活动片段"的检索基准。
12. **OpenLifelogQA** — DCU（Tran, Gurrin 等），2025，18 个月多模态 — https://arxiv.org/abs/2508.03583 — "行为日志 → 个人助理/问答"研究落地的 QA 基准。

## D4. 上下文感知 / sensor + app 联合数据集

13. **ExtraSensory** — UCSD（Vaizman, Ellis, Lanckriet），2015–2016，60 用户 30 万+ 分钟样本 — `加速度/陀螺/磁力/手表/位置/音频 MFCC/手机状态(含 app)/光照/气压 + 51 类上下文标签` — 免费开放下载 — http://extrasensory.ucsd.edu/ — "什么上下文下用哪类 app"联合建模基准。
14. **Sussex-Huawei Locomotion (SHL)** — Sussex + Huawei，2017，3 用户 7 个月 750 小时标注 — `多模态传感器 + 身戴相机 + 8 类交通方式` — 注册后开放下载 — http://www.shl-dataset.org/ — 交通/活动上下文识别，可作"移动上下文→app 使用场景"的上下文源。
15. **UCI HAR (Smartphones)** — UCI ML Repository，2012，30 用户 10,299 窗口 — `加速度+陀螺 50Hz + 561 维特征 + 6 类活动标签` — CC BY 4.0 开放下载 — https://archive.ics.uci.edu/dataset/240/human+activity+recognition+using+smartphones — 活动识别入门基准，作 app 行为序列的"活动上下文"特征源。

## D5. 公开 web / app 日志数据集（推荐建模相关）

16. **MovieLens** — GroupLens (UMN)，32M 评分 / 20 万+ 用户，多个版本 — `用户-影片-评分-时间戳 + tag genome` — 开放下载 — https://grouplens.org/datasets/movielens/ — 推荐系统黄金基准，可做 app/内容会话推荐原型。
17. **Netflix Prize** — Netflix，2006–2009，1 亿评分 / 48 万用户 — `用户-影片-评分-日期` — 官方已停办，数据广为镜像 — https://web.archive.org/web/2015/http://www.netflixprize.com/ — 评分预测经典对照。
18. **Last.fm Dataset - 1K users** — Òscar Celma / MTG-UPF，2010，992 用户 1915 万收听事件 — `<user, timestamp, artist, song> + 用户画像` — 非商业开放下载 — https://web.archive.org/web/2015/http://www.dtic.upf.edu/~ocelma/MusicRecommendationDataset/lastfm-1K.html — 带时间戳的隐式反馈序列，适合序列/会话推荐与长尾研究。
19. **ListenBrainz** — MetaBrainz Foundation，持续，数百万用户 — `用户收听事件 dump` — 公有领域开放下载 — https://listenbrainz.org/data — Last.fm 的开放替代。
20. **KKBox (WSDM Music Recommendation)** — KKBox + Kaggle，2017，~310 万会员 ~230 万歌曲 — `用户歌曲收听/复听事件 + 元数据` — Kaggle 开放下载 — https://www.kaggle.com/competitions/kkbox-music-recommendation-challenge — 隐式音乐行为 + 上下次推荐，适合 app"下次会否使用"预测。
21. **Amazon Reviews (2018)** — UCSD（Ni, McAuley），233.1M 评论 1996–2018 — `评分/评论/有用投票 + 商品元数据 + also-viewed/also-bought 图` — 开放下载 — https://nijianmo.github.io/amazon/index.html — 显式+隐式商品行为 + 浏览图，适合行为序列推荐与可解释推荐。
22. **YOOCHOOSE (RecSys Challenge 2015)** — YOOCHOOSE + ACM RecSys，~33M 事件 / ~1.4M session — `session 化点击 + 购买事件` — 开放下载 — https://web.archive.org/web/2015/http://2015.recsyschallenge.com/ — session-based/next-item 推荐经典基准（最贴近"app 操作序列"）。
23. **Retailrocket E-commerce Dataset** — Retailrocket，~1.4M 事件 — `view/addtocart/transaction` — Kaggle 开放下载 — https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset — 真实电商行为序列，适合 next-click/session 推荐与冷启动评估。
24. **Taobao/Tmall UserBehavior** — Alibaba/Aliyun Tianchi，2017，约 1 亿条 / ~100 万用户 / ~400 万商品 — `user_id, item_id, category_id, behavior_type(pv/fav/cart/buy), timestamp` — Tianchi 实名下载 — https://tianchi.aliyun.com/dataset/624 — 国内电商隐式行为序列，与 DIN/DIEN 同源，极适合"行为序列→推荐"。

## 未列入正表（无法确认当前开放可下载）

- **Device Analyzer (Cambridge)**：官方站 `deviceanalytics.cl.cam.ac.uk` 当前不可访问，archive.org 无任何快照，无法确认是否仍开放。
- **CERT Insider Threat (CMU/SEI)**：确有合成内部威胁数据集(r4.2/r5/r6.2)，含 logon/USB/web/email/file 等 PC 使用日志；但未找到明确公开下载资产页。
- **Yandex 搜索/App 日志**：Yandex 曾发布 WSDM 2013 个性化搜索数据，未确认当前有稳定公开链接。
