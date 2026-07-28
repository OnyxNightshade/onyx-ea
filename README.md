

**Silent entry. Profitable exit.**

[onyxnightshade.com](https://www.onyxnightshade.com/)

## Live Performance
Verified by MyFXBook — real trades, no demo, no backtest tricks.

## Features
- AI-Powered trading
- 24/7 market analysis
- Secure license system

## Installation
1. Purchase license from [official website](https://www.onyxnightshade.com/)
2. Install on MetaTrader 5
3. Activate with your license key

## Support
📧 info@onyxnightshade.com

# ONYX — System Architecture (Technical Overview)

> **A neutral technical overview of ONYX's internal architecture** — no source code, exact parameters, or strategy implementation details are disclosed.

ONYX is a fully autonomous, multi-strategy, self-learning trading engine. Its decision unit is each **closed candle** (not every intra-bar tick), and before any real order is placed, every signal must pass through **five independent control layers**.

---

## Decision Path

| # | Stage | Description |
|---|-------|-------------|
| 01 | **Data Ingestion & Filtering** | Price, volume, and volatility are read across multiple timeframes simultaneously; incomplete candles or connection errors halt the input before it reaches the decision engine. |
| 02 | **Multi-Strategy Engine** | Several price-action and trend-based pattern families are evaluated in parallel, each producing its own quality score. |
| 03 | **AI Core** | A set of machine learning models re-evaluates the same signal from a different statistical angle — reinforcing, weakening, or vetoing it. |
| 04 | **Risk Governor** | Position size, stop-loss, staged targets, and daily limits are calculated; this layer can fully reject an entry. |
| 05 | **Execution & Live Management** | The order is sent and continuously monitored from open to close, with adjustments applied as needed. |

---

## Multi-Strategy Engine

Rather than relying on a single method, several technical analysis families run in parallel on every candle:

- **Candlestick Reversal Patterns** — confirmed by volume and prior trend context
- **Breakout & Trend Continuation** — confirmed by higher-timeframe alignment and a clear volume increase
- **Moving Average System** — only valid once trend slope/strength crosses a defined threshold
- **Adaptive-Threshold Oscillator** — thresholds that self-adjust based on ranging vs. trending conditions
- **Momentum Exhaustion Detection** — identifies the end of a wave and the start of a reversal
- **Price-Range Zone Logic** — splits the recent range into top/mid/bottom zones, each with different confirmation rules

## AI Core

The AI layer does not replace the strategy engine — it re-reviews the final signal from a separate statistical perspective:

`~85 numerical features extracted` → `lightweight statistical base model` → `multi-layer neural network` → `sequential model (short-term market memory)` → `weighted ensemble → final probability & confidence`

- **Online Learning** — every closed trade becomes a labeled training sample; models are periodically retrained on real trade outcomes
- **Persistent Model Memory** — learned weights survive across sessions and restarts

## Risk Governor

Even when both the strategy and the AI core agree on a signal, this layer can reduce size, fully reject the entry, or close open trades early:

- **Dynamic position sizing** based on market volatility and recent performance
- **Hybrid stop-loss** (structural levels + volatility-based distance)
- **Staged exits** — partial close at first target, stop moved to breakeven, trailing stop beyond that
- **Daily limits** on profit/loss, automatically tightened after consecutive losing days
- **Independent guardians**: drawdown circuit breaker, pause during abnormal volatility spikes, slippage cost estimation
- **Adaptive cooldown** period after consecutive losses

## Context Filters

- **Multi-timeframe alignment** with higher-timeframe trend direction
- **Economic event awareness** — new entries are paused around high-impact calendar releases
- **News sentiment analysis** — automatic scoring of market-relevant headlines
- **Market-hours awareness** — live spread, active sessions, and a caution period after market open

## Live Monitoring & State Persistence

- Live status panel: trend, AI confidence level, running P&L, win rate, spread
- Structured decision-audit log for every trade, from initial signal to passed/rejected confirmations
- Trade history, learned weights, and timers persist across restarts

---

