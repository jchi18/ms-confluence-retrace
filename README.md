# MS Confluence Retrace (Pine v5)

TradingView scripts for 1-minute market-structure retracement trading, gated by higher-timeframe bias and smart-money confluences (FVG / Order Block / Rejection Block / Fib pocket).

## Files

| File | What it is |
|---|---|
| [`ms_confluence_strategy_v2.pine`](ms_confluence_strategy_v2.pine) | **Recommended.** v2 strategy: risk-based position sizing, real slippage/commission + min-stop floor, displacement filter, liquidity-sweep filter, partial TP + runner, daily loss & losing-streak lockouts, on-chart performance table. Every addition is a toggle so you can A/B it. |
| [`ms_confluence_strategy.pine`](ms_confluence_strategy.pine) | v1 strategy (kept for comparison). Fixed % sizing, single target. |
| [`ms_confluence_indicator.pine`](ms_confluence_indicator.pine) | v1 alert-only `indicator()` twin - entry + exit alerts, live virtual stop/target. |

## What changed in v2
1. **Risk-based sizing** - size comes from the stop distance so every loss risks the same % of equity (default 0.5%), instead of a flat % of equity per trade.
2. **Honest backtest** - default slippage (2 ticks) + commission (0.04%), both overridable in the Properties tab, plus a *minimum* stop floor so hair-thin stops can't fake huge R.
3. **Displacement filter** - the breaking candle must be decisive (>= 1.2x ATR range), not a slow drift-through.
4. **Liquidity-sweep filter** - entry only after price takes out recent lows/highs and reclaims (a stop-hunt), not just any touch of a zone.
5. **Partial TP + runner** - scale 50% off at 1R, move to breakeven, trail the rest.
6. **Guardrails** - stop trading for the day after a set loss %, and lock out after N losing trades in a row.

## How to use
1. TradingView -> **Pine Editor** (bottom of the chart).
2. Open a file above, click the **copy raw** button, paste over the editor's contents.
3. **Add to chart.** Set the chart to **1m**.
4. On the strategy, open **Properties** and set commission/slippage to match your instrument before trusting any number.
5. Tune filters from the settings gear - each is a toggle, so turn them on one at a time to see what each is worth.

> Study tool, not financial advice. The backtest still won't perfectly model intrabar fills. Forward-test on a demo before risking capital.
