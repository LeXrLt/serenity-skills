---
name: serenity-stock-method
description: Apply Serenity / @aleabitoreddit's stock-picking methodology as a reusable research skill. Use when the user asks to analyze a stock, sector, supply-chain bottleneck, AI infrastructure theme, or candidate list in Serenity's style; screen for overlooked supply-chain chokepoints; rank candidates by evidence, market data, valuation, attention gap, and exit risk; or turn Serenity's trading and research behavior into a repeatable workflow. Prefer Futu for live quotes, market data, sector/plate data, valuation, liquidity, and other real-time market information; when Futu is unavailable, use the bundled a-stock-data and global-stock-data subdirectory skills as fallback data sources.
---

# Serenity Stock Method

Use this skill to find overlooked but unavoidable supply-chain chokepoints inside durable expansion themes. The default output language is Chinese unless the user asks otherwise.

This is a research and screening skill, not investment advice. Never output direct buy/sell commands or guaranteed returns.

## When To Load References

- Read `references/methodology.md` when the user asks for a full Serenity-style thesis, sector map, stock analysis, or explanation of the method.
- Read `references/evidence_schema.md` before scoring, ranking, rejecting, or upgrading any ticker or candidate list.
- For project status, captured Serenity/X data, or available local artifacts, inspect `README.md` only when the user asks about this repository.

## Data Source Dependencies

Prefer the Futu skill for market-facing data. Before final ranking or judgement, use Futu when available to collect:

- `quote`: latest price, change, trading status.
- `recent_kline`: recent price trend and volatility.
- `market_cap`: market capitalization or closest available field.
- `valuation`: PE/PB/PS or relevant available valuation fields.
- `liquidity`: volume, turnover, bid/ask or tradability.
- `plate_membership`: industry, sector, concept plates, peer group.
- `fund_flow`: funds flow or attention/heat proxies where available.

If Futu is unavailable, say so explicitly and use the bundled fallback data skills:

- `a-stock-data/`: use for A-share quotes, K-lines, market cap, valuation, concept plates, reports, announcements, news, finance, funds flow, and other A-share evidence.
- `global-stock-data/`: use for US/HK quotes, K-lines, valuation, financials, news, options, filings, and other overseas-market evidence.

When using fallback data, report the source explicitly, such as `Futu unavailable; market data verified via a-stock-data/Tencent/Eastmoney`. Do not invent missing Futu fields.

Futu or fallback plate membership is only a discovery hint. It does not prove customer qualification, orders, capex, capacity, product readiness, or production timelines.

## Fast Workflow

1. Define the durable theme: confirm a 2-5 year expansion driver, not a short-term topic.
2. Map the supply chain: identify physical, technical, capacity, qualification, or architecture chokepoints.
3. Generate candidates: prefer small or underfollowed companies where one product/customer/program can change earnings.
4. Verify hard evidence: filings, announcements, calls, IR, industry reports, customer/supplier cross-checks.
5. Pull market data: prefer Futu; if unavailable, use `a-stock-data/` for A shares or `global-stock-data/` for US/HK names.
6. Score with `references/evidence_schema.md`: classify as `A-list candidate`, `watchlist`, or `reject`.
7. Define degradation triggers: name what would weaken, delay, or break the thesis.

## Output Contract

For a single ticker:

```markdown
## 结论

- 分类：A-list candidate / watchlist / reject
- Serenity 一句话：...
- 最大加分项：...
- 最大扣分项：...
- 数据源状态：Futu 已验证 / Futu 未连通，已用 a-stock-data 补充 / Futu 未连通，已用 global-stock-data 补充 / 部分缺失
- 需要补证：...

## 方法论拆解

| 维度 | 判断 | 证据 |
|---|---|---|
| 主线确定性 | ... | ... |
| 供应链窄门 | ... | ... |
| 公司关键性 | ... | ... |
| 订单/客户/产能 | ... | ... |
| 行情/估值 | ... | ... |
| 认知差 | ... | ... |
| 降级/退出触发 | ... | ... |

## 下一步验证清单

1. ...
2. ...
3. ...
```

For screening multiple companies:

```markdown
| 排名 | 公司 | 供应链节点 | 分类 | 关键证据 | 市场数据状态 | 最大风险 | 下一步 |
|---|---|---|---|---|---|---|---|
| 1 | ... | ... | ... | ... | ... | ... | ... |
```

## Guardrails

- Separate verified facts from Serenity-style inference.
- Do not claim Serenity personally endorses a ticker unless directly sourced.
- Do not treat social media, concept plates, or price action as hard evidence.
- Do not upgrade a candidate without evidence that maps to product, customer, capacity, order, route, or timeline.
- When Futu is unavailable, use `a-stock-data/` or `global-stock-data/` as fallback and name the exact fallback source in the output.
- Replace "建仓/加仓" language with "观察条件/升级条件/降级条件/退出触发" unless the user explicitly asks for portfolio planning.
- If evidence and market data conflict, explain the conflict instead of forcing a bullish conclusion.
