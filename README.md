# Serenity 产业链分析金融工具

本项目用于开发一个对标 Serenity / `@aleabitoreddit` 方法论的可复用选股研究 skill。核心目标不是追逐 AI 概念本身，而是在确定性扩张的大产业趋势中，寻找“没人注意、但绝对绕不开”的供应链窄门。

> 说明：本项目只做研究框架、数据整理和证据验证，不构成投资建议。

## 当前结构

- `SKILL.md`: skill 入口。保留触发条件、Futu 依赖、快速工作流、输出模板和安全边界。
- `references/methodology.md`: Serenity 方法论完整说明，包括主线、供应链窄门、小而关键公司、订单前夜、认知差和退出触发。
- `references/evidence_schema.md`: 字段 schema、证据等级、评分表、Futu 数据要求、reject 条件和输出标签。
- `data/`: Serenity/X 抓取结果、处理后帖子、进度和分析输出。

原则：股票行情、估值、板块热度和资金状态日新月异，不能依赖静态统计脚本给出结论。skill 应优先调用 Futu 等实时能力，并用公告、研报、IR、行业资料等硬证据做交叉验证。

## 核心主旨

不买 AI 本身，买 AI 扩张过程中“没人注意、但绝对绕不开”的供应链窄门。

这个框架关注：

- 大主线是否确定扩张。
- 产业链是否出现物理、技术、认证、产能或供给瓶颈。
- 是否存在小而关键的公司卡住关键环节。
- 是否处在客户验证、订单、小批量或产能兑现前夜。
- 市场是否尚未充分定价。
- 是否能用供应链证据闭环验证。

## 数据源分工

### Futu 系列 skill

Futu 是本 skill 的必需依赖，负责市场侧数据：

- 实时行情、K 线、快照、交易状态。
- 板块列表、板块成分股、所属板块、概念标签。
- 市值、PE、PB、成交量、换手率、流动性。
- 资金流、资金分布、市场关注度代理指标。

映射字段：

- `market_cap`
- `valuation_status`
- `liquidity`
- `plate_membership`
- `attention_gap`
- 部分 `risk_flags`

注意：Futu 不适合作为供应链硬证据的主数据源。它无法直接证明客户认证、送样、客户订单、产能规划、量产时间表或技术路线。

### a-stock-data skill

`a-stock-data` 补足 A 股基本面、公告、研报和新闻层面的材料：

- 巨潮公告全文检索与下载。
- 东财研报列表和 PDF 下载。
- 同花顺一致预期 EPS。
- iwencai 主题研报 / 公告 / 新闻语义搜索。
- 东财个股新闻和全球资讯。
- mootdx F10 公司资料和公告摘要。
- 新浪财报三表。
- 东财个股信息、概念归属、龙虎榜、解禁、融资融券、大宗交易、股东户数、分红送转、资金流。

映射字段：

- `customer_validation`
- `order_signal`
- `capacity_signal`
- `capex_signal`
- `mass_production_timeline`
- `technical_position`
- `evidence_level`
- `risk_flags`

注意：`a-stock-data` 提供的是公告、研报、新闻、F10、财报等原始或半结构化材料。客户认证、送样、订单、产能、量产时间表等“供应链证据”需要二次抽取，不能默认视为已经结构化验证。

### 推荐组合

供应链证据闭环建议采用三层数据源：

1. Futu：行情、市值、估值、流动性、板块和市场状态。
2. a-stock-data：A 股公告、财报、研报、新闻、F10 和资金/筹码信号。
3. SEC / 巨潮本地库 / 公司 IR / 行业资料：客户、订单、产能、capex、量产时间表和技术路线的最终交叉验证。

## 已采集数据

已用本地 `xskill-fetch` 技能复用历史登录态抓取产物，整理 Serenity 的 X 账号 `@aleabitoreddit` 公开帖子语料。

账号信息：

- X URL: <https://x.com/aleabitoreddit>
- 显示名: Serenity
- userId: `1940360837547565056`
- 账号描述: AI/Semi Supply Chain Analyst
- 公开帖子数快照: `7267`

当前语料：

- 已抓取唯一帖子数: `534`
- 覆盖时间: `2026-04-17T16:48:32Z` 至 `2026-06-14T01:43:24Z`
- 抓取方式: 本地 `/home/lele/WorkingSpace/xskill-fetch` 技能，复用历史 `xskill-fetch` timeline 产物。
- 当前限制: 本轮 shell 未设置 `XSKILL_FETCH_X_TOKEN` 或 `GET_ID_X_TOKEN`，无法继续发起新的登录态 X 请求。
- 历史抓取限制: 原 timeline cursor 在 `534` 条后进入重复窗口，继续沿同一 cursor 翻页收益较低。

数据文件：

- 抓取报告: `data/serenity_x_crawl_report.md`
- 原始帖子 JSON: `data/serenity_x_posts_raw.json`
- 摘要 JSON: `data/serenity_x_posts_summary.json`
- 公开页面快照解析: `data/serenity_x_public_page_snapshot.json`
- 处理后 JSON: `data/processed/aleabitoreddit-tweets-20260614-123553.json`
- 处理后 CSV: `data/processed/aleabitoreddit-tweets-20260614-123553.csv`
- AI 产业链卡点快扫原始结果: `data/analysis/ai_chain_fast_probe.json`
- AI 产业链卡点快扫报告: `data/analysis/ai_chain_bottleneck_report.md`
- AI 产业链卡点证据版报告: `data/analysis/ai_chain_evidence_report.md`
- Futu 所属板块原始输出: `data/analysis/futu_owner_plate_raw.txt`
- Futu 股票快照原始输出: `data/analysis/futu_stock_info_raw.txt`

## 后续方向

- 使用有效 X auth token 后，优先做按日期窗口或关键词搜索式补抓。
- 对公开页面快照中的 tweet id 做 detail/thread 回填。
- 从长帖中抽取 ticker、供应链节点、瓶颈类型、客户验证、订单信号、产能信号和退出风险。
- 建立 Serenity 方法论知识库，而不是只保存原始 tweet 文本。
- 使用 `a-stock-data` 下载研报 PDF、公告全文和投资者关系记录，做客户、订单、认证、产能、capex、量产时间表的全文证据抽取。
- 启动 Futu OpenD 后，用 Futu 补行情、市值、估值、板块和资金流数据。

## 核心思想

在别人看到结果之前，找到决定结果的那颗“螺丝钉”。
