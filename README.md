# MTF Confluence Dashboard — Multi-Timeframe Scoring Engine

**Free & Open Source | Pine Script v5 | v1.7.9 | Works on Every Asset**

---

## One Sentence Summary

Not just a heatmap — **a transparent dual‑vote (EMA+RSI) scoring engine across 5 timeframes for up to 3 symbols for every asset class**, with fully adjustable weights, precise composite scoring, and an independent volume filter that gates signals without touching your scores. Free & open‑source.

---

## Screenshots

**BULL Market**

<img src="https://raw.githubusercontent.com/WiseManAlgo/MTF-Confluence-Dashboard/bea78e716abd1bc00231bcfba1179082e4178d0d/Bull_Market_Screenshot.png" width="800" alt="Bull Market Screenshot">


**BEAR Market**

![MTF Dashboard Bear Market Screenshot](https://raw.githubusercontent.com/WiseManAlgo/MTF-Confluence-Dashboard/6a0043298f3a157df7f2ba45edb2461581f67787/MTF_Dashboard%20_Bear_2026-05-01_23.25.34.png)

**Market Closed (CLO State)**

<!-- 📸 ADD THIS NEW SCREENSHOT: CLO cells on a closed stock/ETF row while a crypto row stays live -->

---

## The Annoying Problem It Solves

Every trader knows the rule: trade with the higher timeframe and your win rate goes up.

But actually doing it is a nightmare:

- You end up with 5 tabs open: 15min, 1h, 4h, Daily, Weekly
- You manually check EMA crossovers and RSI levels on every single one
- You miss one, mix up another, and end up trading against the trend anyway

This indicator crunches all 5 timeframes for you, non-stop, and sticks a tiny dashboard right in the corner of your main chart. One quick look tells you:

- ✅ Is the overall environment bullish, bearish, or messy?
- ✅ How strong is the trend?
- ✅ Should you even be looking for trades right now?

---

## How The Scoring Actually Works (The Smart Part)

This is not some dumb "count how many timeframes agree" counter. It splits every timeframe into **two completely independent votes**. No more "both must be true or nothing counts".

### 1. Structure Vote — Where is price right now?

- Price above the 5-period EMA → **+1 point**
- Price below the 5-period EMA → **-1 point**

No crossovers, no lag. Instant result the second this bar closes.

### 2. Momentum Vote — Is strength increasing or decreasing?

This is what makes this indicator different from every other MTF tool on the platform:

- ❌ Everyone else uses: RSI > 55 = bull, RSI < 45 = bear — fixed forever, becomes long-only in bull markets
- ✅ We use: RSI above its own 20-period average → **+1**; below average → **-1**

What does that mean? Even if weekly RSI is at 65 (which everyone calls "overbought bullish"), if it's falling from 70, it votes **bearish**. It measures **where RSI is going**, not where it is right now. It works exactly the same in bull markets, bear markets, and sideways chop. No built-in bias.

### 3. Weighted Total Score

Not all timeframes are created equal:

| Timeframe | Weight | Role |
|---|---|---|
| Weekly | 2.0× | Defines the big picture |
| Daily | 2.0× | Defines the big picture |
| 4h | 1.5× | Intermediate trend |
| 1h | 1.0× | Directional context |
| 15min | 0.5× | Entry timing only |

Add them all up → final weighted score from roughly **-14 (extreme bearish)** to **+14 (extreme bullish)**. Every weight and parameter is fully adjustable in settings.

---

## How It Gives You Signals

- Score ≥ **+7** → Green up triangle on your chart (Long signal)
- Score ≤ **-7** → Red down triangle on your chart (Short signal)

You can tweak the threshold in settings:

- Set it to **5** → More signals, more sensitive, more noise
- Set it to **9** → Fewer signals, higher conviction, misses some moves

**Signals are perfectly symmetric.** The exact same rules apply to longs and shorts. No hidden bias towards buying.

> ⚠️ **Signals follow your chart symbol automatically.** Arrows and alerts are computed for whichever instrument you are currently viewing — not a fixed Sym1. Symbols 1–3 in the dashboard are monitoring-only (scores displayed, no arrows).

---

## How To Read The Corner Dashboard

### Banner Row (Top of Dashboard)

The very first row tells you whether the base chart is receiving live data:

| Banner | Meaning |
|---|---|
| 🟢 `✓ Base chart active — live data` | The base chart bar is updating in real time. All scores reflect the current moment. |
| 🔴 `⚠ Base chart closed — data frozen` | The base chart session has ended. Scores across all symbols are anchored to the last closed bar and will not update until the market reopens. |

This works **on any asset class** — stocks, forex, crypto, indices. No configuration needed and no requirement to keep the chart on a crypto pair.

---

### Score Row

Directly below the three symbol rows, a full-width row shows:

```
Score: X.XX
```

This is the weighted composite score for Symbol 1 (The first symbol in the dashboard) 
Background turns bright green when the score reaches +7 (long threshold), bright red at -7 (short threshold), and lighter shades for intermediate readings.

---

### Symbol Rows

Each of the three configurable symbols gets one row. Every timeframe cell shows **two characters** — one for each independent vote:

| Characters | Meaning |
|---|---|
| ▲▲ | Both EMA and RSI vote bullish (+2 raw) |
| ▲– | EMA bullish, RSI neutral (+1 raw) |
| –▲ | EMA neutral, RSI bullish (+1 raw) |
| –– | Both neutral (0 raw) |
| –▼ | EMA neutral, RSI bearish (-1 raw) |
| ▼– | EMA bearish, RSI neutral (-1 raw) |
| ▼▼ | Both EMA and RSI vote bearish (-2 raw) |

**Cell background colour:**

| Colour | Raw Score | Meaning |
|---|---|---|
| Dark Green | +2 | Fully bullish |
| Light Green | +1 | Partially bullish |
| Grey | 0 | Neutral |
| Light Red | -1 | Partially bearish |
| Dark Red | -2 | Fully bearish |
| Dark Grey | CLO | Market closed |

---

### CLO — Market Closed State

When a symbol's market is closed, all its cells show **CLO** in dark grey. Fully automatic — no configuration needed.

**How it works:**
- The indicator checks the age of each symbol's most recent bar on TF1
- If that bar is more than 35 minutes old → **CLO**
- When the market reopens → CLO clears automatically, live scores resume

**What it covers — every asset class, every broker prefix:**
- US stocks & ETFs (NYSE/NASDAQ hours)
- Hong Kong stocks (HKEX hours, including `HKEX_DLY:` delayed feeds)
- Forex pairs (any broker: Pepperstone, OANDA, FXCM, etc.)
- Gold, Silver, Commodities
- Indices
- Crypto — **never shows CLO** (trades 24/7 by definition)

> No hardcoded market hours. No asset type lists. Zero maintenance.

---

### Last Two Columns

- **WScore** — The final weighted composite score for that symbol. Turns bright green above +7, bright red below -7.
- **Vol** — Status of the optional volume filter. Shows `OFF` when the filter is disabled (default), `OK` when volume passes the filter, and `LOW` when volume is below the threshold.

---

## About The Volume Filter

The volume filter is **OFF by default** with good reason:

This filter will suppress valid signals during stock midday lulls and crypto low-volume periods. Only enable it if you trade assets with clean, consistent volume data and have tested it yourself on your specific asset.

---

## What Makes This Better Than Every Other MTF Indicator

99% of MTF indicators share the same fatal flaw: fixed RSI thresholds.

In a long bull market, weekly RSI stays above 55 forever. The indicator becomes permanently long-only no matter what is actually happening. That is not intelligence — that is bias.

We replaced fixed thresholds entirely with **relative RSI momentum**. Backtest results (BTC-USD 1h, April 2024 – April 2026):

- Hit **-14** (max bearish) during both the March 2025 and Feb-Mar 2026 corrections
- Hit **+12** (strong bullish) during the Oct-Nov 2024 rally
- Long signal +24h win rate: **71%**
- Short signal +4h win rate: **62%**

It catches both sides. No exceptions.

---

## It's A Foundation, Not A Black Box

This indicator will **never tell you "buy this exact bar right now"**. It only tells you:

> The environment is now aligned for a long / short trade.

The exact entry bar — using volume spread analysis, liquidity sweeps, support/resistance, or whatever you prefer — is up to you. This is the first layer of your system, filtering out all the garbage counter-trend trades before you even look for an entry.

100% open source and transparent:

- ✅ **Does not repaint** — signals lock the moment the bar closes, they never change
- ✅ **No lookahead bias** — future bars play zero role in current calculations
- ✅ **No hidden calculations** — every line of logic is in the open source code
- ✅ **Works on every asset class** — stocks, ETFs, forex, gold, indices, crypto, any broker prefix

You can read, modify, and build on it however you want. Just credit the original.

---

## FAQ

**Why am I only seeing green arrows even when price is dropping?**

Because price dropping for a few candles on your chart is not the same thing as the market environment turning bearish.

This indicator gives much heavier weight to the Daily and Weekly timeframes. Those move slowly by design — they define the big picture, not the noise. A 4H correction inside a Weekly bull trend will not flip the score negative. The indicator will keep pointing you towards longs because statistically, that is still the right side to be on.

Red arrows appear when the environment genuinely shifts — when Daily and Weekly momentum both turn south and stay there. That is a regime change, not a dip.

**This indicator is built for those who follow the bigger trend — not trade against it.** If you want to trade every 4H wiggle, this is not the right tool.

---

**Why does the same symbol sometimes show different scores on different charts?**

This is a Pine Script engine behaviour: all `request.security()` data is anchored to the base chart's last bar time. If your base chart is a closed market, all scores reflect that market's last close — not the current moment.

The banner row at the top of the dashboard tells you instantly whether your data is live (green) or frozen (red).

---

**Do I need to keep the indicator on a crypto chart?**

No. As of v1.7.9, the live/closed detection works correctly on any base chart — stocks, forex, indices, or crypto. The banner uses Pine Script's `barstate.isrealtime` to detect live data directly, with no dependency on the asset type of the base chart.

---

## Important Disclaimer

**This indicator is for informational and educational purposes only. It is not financial advice, investment advice, or a recommendation to buy or sell any asset.**

Past backtest performance does not guarantee future results. All win rates and returns shown are from historical testing on specific assets and timeframes only. Markets change. Always do your own research and manage your own risk.

---

## Open Source

Published under the Mozilla Public License 2.0.
Copyright © 2026 WiseManAlgo. Free to use, study, modify, and distribute.




