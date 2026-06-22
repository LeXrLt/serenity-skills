---
name: serenity-stock-method
description: Apply Serenity / @aleabitoreddit's stock-picking methodology as a reusable research skill. Use when the user asks to analyze a stock, sector, supply-chain bottleneck, AI infrastructure theme, or candidate list in Serenity's style; screen for overlooked supply-chain chokepoints; rank candidates by evidence, Futu market data, valuation, attention gap, and exit risk; or turn Serenity's trading and research behavior into a repeatable workflow. This skill depends on the Futu skill for quotes, market data, sector/plate data, valuation, liquidity, and other live market information.
---

# Serenity Stock Method

Use this skill to find overlooked but unavoidable supply-chain chokepoints inside durable expansion themes. The default output language is Chinese unless the user asks otherwise.

This is a research and screening skill, not investment advice. Never output direct buy/sell commands or guaranteed returns.

## When To Load References

- Read `references/methodology.md` when the user asks for a full Serenity-style thesis, sector map, stock analysis, or explanation of the method.
- Read `references/evidence_schema.md` before scoring, ranking, rejecting, or upgrading any ticker or candidate list.
- For project status, captured Serenity/X data, or available local artifacts, inspect `README.md` only when the user asks about this repository.

## Required Futu Dependency

This skill depends on the Futu skill for market-facing data. Before final ranking or judgement, use Futu when available to collect:

- `quote`: latest price, change, trading status.
- `recent_kline`: recent price trend and volatility.
- `market_cap`: market capitalization or closest available field.
- `valuation`: PE/PB/PS or relevant available valuation fields.
- `liquidity`: volume, turnover, bid/ask or tradability.
- `plate_membership`: industry, sector, concept plates, peer group.
- `fund_flow`: funds flow or attention/heat proxies where available.

If Futu is unavailable, say so explicitly and mark all market-data, valuation, liquidity, and attention-gap conclusions as unverified. Do not invent Futu data.

Futu plate membership is only a discovery hint. It does not prove customer qualification, orders, capex, capacity, product readiness, or production timelines.

## Fast Workflow

1. Define the durable theme: confirm a 2-5 year expansion driver, not a short-term topic.
2. Map the supply chain: identify physical, technical, capacity, qualification, or architecture chokepoints.
3. Generate candidates: prefer small or underfollowed companies where one product/customer/program can change earnings.
4. Verify hard evidence: filings, announcements, calls, IR, industry reports, customer/supplier cross-checks.
5. Pull Futu market data: quote, valuation, liquidity, plates, price trend, funds flow or heat proxies.
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
- Futu 状态：已验证 / 未连通 / 部分缺失
- 需要补证：...

## 方法论拆解

| 维度 | 判断 | 证据 |
|---|---|---|
| 主线确定性 | ... | ... |
| 供应链窄门 | ... | ... |
| 公司关键性 | ... | ... |
| 订单/客户/产能 | ... | ... |
| Futu 行情/估值 | ... | ... |
| 认知差 | ... | ... |
| 降级/退出触发 | ... | ... |

## 下一步验证清单

1. ...
2. ...
3. ...
```

For screening multiple companies:

```markdown
| 排名 | 公司 | 供应链节点 | 分类 | 关键证据 | Futu 市场状态 | 最大风险 | 下一步 |
|---|---|---|---|---|---|---|---|
| 1 | ... | ... | ... | ... | ... | ... | ... |
```

## Guardrails

- Separate verified facts from Serenity-style inference.
- Do not claim Serenity personally endorses a ticker unless directly sourced.
- Do not treat social media, concept plates, or price action as hard evidence.
- Do not upgrade a candidate without evidence that maps to product, customer, capacity, order, route, or timeline.
- Replace "建仓/加仓" language with "观察条件/升级条件/降级条件/退出触发" unless the user explicitly asks for portfolio planning.
- If evidence and market data conflict, explain the conflict instead of forcing a bullish conclusion.
