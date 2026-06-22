# Evidence Schema

Use this reference before scoring, ranking, rejecting, or upgrading any Serenity-style candidate.

## Field Schema

Use these fields when structuring a candidate:

- `theme`: durable expansion theme.
- `theme_certainty`: certainty of 2-5 year expansion.
- `demand_driver`: capex, architecture shift, customer demand, regulation, standard, cycle.
- `supply_chain_node`: exact supply-chain position.
- `bottleneck_type`: physical, technical, capacity, qualification, material, equipment, process, or architecture bottleneck.
- `why_unavoidable`: why the node cannot be easily bypassed.
- `company`: company name and ticker.
- `market_cap`: from Futu when available.
- `valuation`: Futu PE/PB/PS or best available valuation.
- `liquidity`: Futu turnover, volume, tradability.
- `plate_membership`: Futu sector, industry, concept plates.
- `revenue_base`: current revenue scale and relevant segment exposure.
- `earnings_elasticity`: whether one product/customer/program can move earnings.
- `technical_position`: product, process, route, or technology position.
- `customer_validation`: certification, sampling, qualification, customer entry.
- `order_signal`: order, contract, fixed-point award, purchase or ramp signal.
- `capacity_signal`: production line, facility, yield, ramp, expansion.
- `capex_signal`: equipment, project, facility, funding, construction.
- `mass_production_timeline`: pilot, batch, delivery, HVM, ramp schedule.
- `cross_checks`: upstream/downstream/customer/competitor corroboration.
- `evidence_level`: strongest verified evidence grade.
- `attention_gap`: hidden, emerging, crowded, or overpriced.
- `valuation_status`: cheap, reasonable, full, stretched, or unverified.
- `risk_flags`: key thesis risks.
- `degradation_triggers`: conditions that downgrade the thesis.
- `exit_triggers`: conditions that break the thesis.
- `classification`: A-list candidate, watchlist, or reject.

## Evidence Grades

- `A`: official filing, order, contract, customer qualification, production milestone, capex project, or management guidance with dates/numbers.
- `B`: reputable industry report, earnings-call cross-check, customer/supplier corroboration, credible repeated news, or independent channel evidence.
- `C`: broker research title/summary, product page, concept/sector tag, weak news, or reasonable inference.
- `D`: social media narrative, concept plate only, unsourced rumor, or price action.

Upgrade rules:

- `A-list candidate` usually needs at least one `A` evidence point or two independent `B` evidence points, plus usable Futu market context.
- `watchlist` can have plausible `B/C` evidence but missing timing, valuation, customer, or Futu confirmation.
- `reject` if the thesis depends mainly on `C/D` evidence, price action, or concept labels.

## Default Scorecard

Score each dimension from 0 to 5. Use judgement; do not pretend the result is mathematically precise.

| Dimension | 0 | 3 | 5 |
|---|---|---|---|
| Theme certainty | Hype only | Real demand but timing uncertain | Multi-year capex/demand/architecture driver |
| Chokepoint strength | Easy substitute | Some qualification or supply limits | Hard-to-bypass bottleneck |
| Company criticality | Incidental exposure | Relevant but not essential | Small but critical node |
| Evidence level | D only | B/C mix | A or multiple independent B |
| Earnings elasticity | Immaterial | Segment can help | One program/order can change earnings |
| Attention gap | Already consensus | Specialist attention rising | Evidence exists before broad recognition |
| Valuation setup | Perfect success priced | Reasonable but not cheap | Market not pricing evidence yet |
| Risk control | No clear invalidation | Some risks named | Clear downgrade/exit triggers |

Suggested classification:

- `A-list candidate`: total score usually 30+, no fatal evidence gap, Futu data does not show obvious overpricing/crowding.
- `watchlist`: total score usually 20-29, or one major missing evidence bucket.
- `reject`: total score below 20, missing hard evidence, weak chokepoint, crowded valuation, or fatal risk.

Do not auto-upgrade only because total score is high. A missing customer/order/capacity/timeline evidence bucket can cap the candidate at `watchlist`.

## Futu Market Data Requirements

Before final judgement, use the Futu skill when available to collect:

- `quote`: latest price, change, trading status.
- `recent_kline`: recent trend, volatility, drawdown or breakout context.
- `market_cap`: total/float market cap if available.
- `valuation`: PE/PB/PS or best available valuation fields.
- `liquidity`: volume, turnover, bid/ask or tradability.
- `plate_membership`: industry, sector, concept plates, peers.
- `fund_flow`: funds flow, heat, or attention proxy if available.

Interpretation:

- Futu can support `market_cap`, `valuation_status`, `liquidity_status`, `plate_confirmation`, `attention_gap`, and `crowding_risk`.
- Futu cannot prove `customer_validation`, `order_signal`, `capacity_signal`, `capex_signal`, `mass_production_timeline`, or `technical_position`.
- If Futu fields are missing or unavailable, label them `unverified` rather than substituting guesses.

## Reject Conditions

Reject or cap at watchlist when any of these hold:

- No product/customer/capacity/order/timeline evidence.
- The company is only loosely associated with the theme through a concept plate.
- Relevant segment is too small to change earnings.
- The company is already the obvious, fully covered consensus winner.
- Valuation already prices a best-case ramp without matching evidence.
- Customer technical route can bypass the company.
- Competitor substitution is fast or qualification barrier is weak.
- Liquidity is too poor for reliable interpretation, unless explicitly treated as a speculative watchlist item.
- The thesis rests on Serenity, KOL, or social media mention rather than independently verified evidence.

## Output Labels

Use these labels consistently:

- `A-list candidate`: high-quality research candidate with strong chokepoint, evidence, elasticity, and not fully priced market setup.
- `watchlist`: promising but incomplete; needs specified evidence or better market setup.
- `reject`: not Serenity-style, too narrative-driven, too crowded, too weakly evidenced, or poor risk/reward.

## Degradation And Exit Trigger Template

Always include:

- `degrade_if`: evidence weakens, customer timing slips, valuation stretches, competitor enters, Futu heat becomes crowded.
- `exit_if`: technical route changes, customer qualification fails, order does not materialize, margins collapse, dilution breaks upside, or thesis is fully priced.
