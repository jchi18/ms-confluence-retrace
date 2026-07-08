# MS Confluence Retrace (Pine v5)

Two TradingView scripts for 1-minute market-structure retracement trading, gated by higher-timeframe bias and smart-money confluences (FVG / Order Block / Rejection Block / Fib pocket).

| File | What it is |
|---|---|
| [`ms_confluence_strategy.pine`](ms_confluence_strategy.pine) | Backtestable `strategy()` - real entries/exits, Strategy Tester report, breakeven + ATR trail + max-stop cap. |
| [`ms_confluence_indicator.pine`](ms_confluence_indicator.pine) | Alert-only `indicator()` twin - entry + exit alerts, live virtual stop/target, status table. |

## How to use
1. TradingView -> **Pine Editor** (bottom of the chart).
2. Open a file above, click the **copy** (raw) button, paste over the editor's contents.
3. **Add to chart.** Set the chart to **1m** to match the design.
4. Tune inputs from the settings gear (swing length, HTF timeframe, R:R, risk management).

> Study tool, not financial advice. Backtest and forward-test on your own symbols before risking capital.
