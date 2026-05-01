**MTF Confluence Dashboard — Multi-Timeframe Scoring Engine**

**Free & Open Source | Pine Script v5 | Works on Every Asset**

**One Sentence Summary**

This is a **free, open-source, no-BS TradingView indicator** that lets you see the market direction across 5 timeframes at a single glance. No more flipping between 5 open tabs.

**The Annoying Problem It Solves**

Every trader knows the rule:

Trade with the higher timeframe, and your win rate goes up.

But actually doing it is a nightmare:

- You end up with 5 tabs open: 15min, 1h, 4h, Daily, Weekly
- You manually check EMA crossovers and RSI levels on every single one
- You miss one, mix up another, and end up trading against the trend anyway

This indicator crunches all 5 timeframes for you, non-stop, and sticks a tiny dashboard right in the corner of your main chart. One quick look tells you: ✅ Is the overall environment bullish, bearish, or messy? ✅ How strong is the trend? ✅ Should you even be looking for trades right now?

**How The Scoring Actually Works (The Smart Part)**

This is not some dumb "count how many timeframes agree" counter. It splits every timeframe into **two completely independent votes**. No more "both must be true or nothing counts".

**1. Structure Vote (Where is price right now?)**

- Price above the 5-period EMA → +1 point
- Price below the 5-period EMA → -1 point

That's it. No crossovers, no lag — instant result the second this bar closes.

**2. Momentum Vote (Is strength increasing or decreasing?)**

This is what makes this indicator different from every other MTF tool on the platform: ❌ Everyone else uses: RSI > 55 = bull, RSI < 45 = bear (fixed forever, becomes long-only in bull markets) ✅ We use: RSI above its own 20-period average → +1; below average → -1

What does that mean? Even if weekly RSI is at 65 (which everyone calls "overbought bullish"), if it's falling from 70, it votes **bearish**. It measures **where RSI is going**, not where it is right now. It works exactly the same in bull markets, bear markets, and sideways chop. No built-in bias.

**3. Weighted Total Score**

Not all timeframes are created equal:

- Weekly & Daily: 2.0x weight (they define the big picture)
- 4h: 1.5x weight
- 1h: 1.0x weight
- 15min: 0.5x weight (only for entry timing)

Add them all up, and you get a final score from roughly **-14 (extreme bearish)** to **+14 (extreme bullish)**. Every single weight and parameter is fully adjustable in the settings.

**How It Gives You Signals**

- Score ≥ +7 → Green up triangle on your chart (Long signal)
- Score ≤ -7 → Red down triangle on your chart (Short signal)

You can tweak this threshold however you want:

- Set it to 5 → More signals, more sensitive, more noise
- Crank it up to 9 → Fewer signals, higher conviction, misses some moves

**Critical note:** Signals are perfectly symmetric. The exact same rules apply to longs and shorts. No secret bias towards buying.

**⚠️ Important:** Signal arrows only fire for Symbol 1 (the chart's current symbol). Symbols 2 and 3 in the dashboard are for monitoring only — they show scores but do not generate arrows or alerts. If you want signals for AAPL, make sure AAPL is your chart symbol and set it as Symbol 1 in the settings.

**How To Read The Corner Dashboard**

This little table is the whole point. It tracks 3 symbols at once, updating in real time:

**Cell Color**

**Symbols Inside**

**What It Means**

Dark Green

▲▲

This timeframe is fully bullish — both structure and momentum agree

Light Green

▲– or –▲

Partial bullish evidence — one says up, one is neutral

Grey

--

Completely neutral — no direction at all

Light Red

▼– or –▼

Partial bearish evidence — one says down, one is neutral

Dark Red

▼▼

This timeframe is fully bearish — both structure and momentum agree

The last two columns:

- **WScore**: The final weighted total for that symbol. Turns bright green above +7, bright red below -7. You can see if a signal has fired in 0.1 seconds.
- **Vol**: Status of the optional volume filter (OFF by default).

**About That Volume Filter**

We kept the old volume filter, but **it's OFF BY DEFAULT, with a big fat disclaimer**:

This filter will kill valid signals during stock midday lulls and crypto weekends. Only enable it if you trade assets with perfectly clean, consistent volume data, and you've tested it yourself.

**What Makes This Better Than Every Other MTF Indicator**

99% of MTF indicators have the same fatal flaw:

They use fixed RSI thresholds. In a long bull market, weekly RSI stays above 55 forever. The indicator becomes permanently long-only, no matter what is actually happening. That's not intelligence — that's bias.

We replaced fixed thresholds entirely with **relative RSI momentum**. Backtest results speak for themselves (BTC-USD 1h, April 2024 – April 2026):

- Hit -14 (max bearish) during both the March 2025 and Feb-Mar 2026 corrections
- Hit +12 (strong bullish) during the Oct-Nov 2024 rally
- Long signal +24h win rate: 71%
- Short signal +4h win rate: 62%

It catches both sides. No exceptions.

**The Most Important Thing: It's A Foundation, Not A Black Box**

This indicator will **never tell you "buy this exact bar right now"**. It only tells you:

The environment is now aligned for a long / short trade.

The exact entry bar — using volume spread analysis, liquidity sweeps, support/resistance, or whatever you prefer — is up to you. This is the first layer of your system, filtering out all the garbage counter-trend trades before you even look for an entry.

And it's **100% open source and transparent**:

- ✅ Does not repaint — signals are locked the moment the bar closes, they never change
- ✅ No lookahead bias — future bars play zero role in current calculations
- ✅ No hidden calculations — every line of logic is in the open source code
- You can read, modify, and build on it however you want. Just credit the original.

**⚠️ Important:** **⚠️ Important:** **⚠️ Important:**

**Why am I only seeing green arrows even when price is dropping?**

Because price dropping for a few candles on your chart is not the same thing as the market environment turning bearish.

This indicator gives much heavier weight to the Daily and Weekly timeframes. Those move slowly by design — they define the big picture, not the noise. A 4H correction inside a Weekly bull trend will not flip the score negative. The indicator will keep pointing you towards longs because statistically, that is still the right side to be on.
Red arrows appear when the environment genuinely shifts — when Daily and Weekly momentum both turn south and stay there. That is a regime change, not a dip.

**If you’re looking to trade say every 4H short-term wiggle, this isn’t the right tool.**

**This indicator is built for those who follow the bigger trend — not trade against it.**

**Important Disclaimer**

**This indicator is for informational and educational purposes only. It is not financial advice, investment advice, or a recommendation to buy or sell any asset.**

Past backtest performance does not guarantee future results. All win rates and returns shown are from historical testing on specific assets and timeframes only. Markets change. Always do your own research and manage your own risk.

**Open Source**

Published under the Mozilla Public License 2.0. Copyright © 2026 WiseManAlgo. Free to use, study, modify, and distribute.


