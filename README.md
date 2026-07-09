# MS Confluence Retrace (Pine v5)

TradingView scripts for 1-minute market-structure retracement trading, gated by higher-timeframe bias and smart-money confluences (FVG / Order Block / Rejection Block / Fib pocket).

## Files

| File | What it is |
|---|---|
| [`ms_confluence_strategy_v2.pine`](ms_confluence_strategy_v2.pine) | **v2 strategy (recommended for testing).** Risk-based sizing, real slippage/commission + min-stop floor, displacement filter, liquidity-sweep filter, partial TP + runner, daily loss & losing-streak lockouts, on-chart performance table. Every addition is a toggle. |
| [`ms_confluence_indicator_v2.pine`](ms_confluence_indicator_v2.pine) | **v2 indicator (recommended for trading).** Alert-only twin with the same v2 filters. Tracks a virtual position with real R accounting; entry alert reports the size to trade for your account + risk %; partial / exit alerts; virtual performance table. |
| [`ms_confluence_strategy.pine`](ms_confluence_strategy.pine) | v1 strategy (kept for A/B comparison). Fixed % sizing, single target. |
| [`ms_confluence_indicator.pine`](ms_confluence_indicator.pine) | v1 alert-only indicator. |

## What v2 adds
1. **Risk-based sizing** - size from the stop distance so every loss risks the same amount (strategy sizes the order; indicator reports the size in the alert).
2. **Honest backtest** - default slippage + commission (overridable in Properties) and a *minimum* stop floor so hair-thin stops can't fake huge R.
3. **Displacement filter** - the breaking candle must be decisive (>= ATR x), not a slow drift-through.
4. **Liquidity-sweep filter** - entry only after price takes out recent lows/highs and reclaims.
5. **Partial TP + runner** - scale a % off at 1R, move to breakeven, trail the rest.
6. **Guardrails** - stop for the day after a loss limit, and lock out after N losing trades in a row.

Every filter is a toggle. Turn them on one at a time (in the strategy) to see what each is worth, then match the indicator's toggles to your winning config.

## How to use
1. TradingView -> **Pine Editor** (bottom of the chart).
2. Open a file above, click the **copy raw** button, paste over the editor's contents.
3. **Add to chart.** Set the chart to **1m**.
4. Strategy: open **Properties** and set commission/slippage to match your instrument before trusting any number.
5. Indicator: set **Account size** + **Risk %** if you want the entry alert to tell you position size. Create an alert on "Any alert() function call" to get the rich messages.

> Study tool, not financial advice. The backtest still won't perfectly model intrabar fills. Forward-test on a demo before risking capital.
