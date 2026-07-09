# MS Confluence Retrace

Smart-money tools for trading 1-minute retracements into institutional confluence.

## Files

| File | What it is | Use it for |
|---|---|---|
| **`aplus_confluence.pine`** | **A+ Confluence Marker** (indicator) | **The focus tool.** Draws only A+ zones = a Fair Value Gap **and** an Order Block of the same direction whose ranges overlap. It does **not** mark OTE — you draw your own OTE, this shows whether it lands on real confluence. Alerts when price taps a fresh A+ zone. |
| `ms_confluence_indicator_v2.pine` | Full alert-only indicator | Optional. The complete engine (structure, all confluences, displacement, sweep, virtual R accounting, guardrails) if you want a signal + performance readout rather than just the confluence map. |
| `ms_confluence_strategy_v2.pine` | Backtestable strategy | Optional. Same engine wired to `strategy.*` with risk-based sizing, honest costs (commission + slippage), partial TP + runner, daily guardrails and a performance table. For backtesting only. |

## A+ Confluence Marker — how it reads

- **A+ zone** = the overlap of an FVG (imbalance) and an OB (last institutional candle) pointing the same way. That overlap is where both agree on price.
- Teal zones = bullish A+, red zones = bearish A+.
- A small `A+` triangle prints when price wicks into a zone (this is your "check my OTE" cue), and an alert fires once per bar close.
- Zones grey out and stop extending once price closes fully through them (mitigated).

### Key inputs
- **Swing length / displacement** — how strict OB creation is (bigger swing + displacement on = only meaningful breaks build OBs).
- **Ignore overlaps thinner than ATR x** — hide paper-thin A+ zones.
- **Only pair fresh FVGs & OBs** — ignore already-mitigated levels.
- **HTF bias filter** — optionally show only A+ zones agreeing with the higher-timeframe trend.
- **Also draw raw FVG / OB** — faint, off by default, for when you want to see the components behind each A+.

## Install
1. TradingView → Pine Editor → paste the file's contents.
2. **Add to chart**.
3. For alerts: create an alert, condition = the indicator, pick "Bull A+ tap" / "Bear A+ tap" (or use the built-in `alert()` messages).

*Cannot be compiled outside TradingView — if the editor flags a line, send the line number + message.*
