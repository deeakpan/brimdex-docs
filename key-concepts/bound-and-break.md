# Bound vs Break

Every Brimdex market resolves to exactly one of two outcomes:

- **BOUND**: the final settlement price is inside the quoted range
- **BREAK**: the final settlement price is outside the quoted range

That structure stays the same across crypto, stocks, and RWAs.

## How to read a market

Take this market:

`NVDA / USD · 30m · ±1.5%`

Brimdex starts from a launch spot, then computes:

- a lower bound
- an upper bound
- one expiry timestamp

At expiry:

- if NVDA settles between those bounds, **BOUND** wins
- if NVDA settles below the lower bound or above the upper bound, **BREAK** wins

## Examples

### Crypto

`ETH / USD · 10m · ±0.5%`

- choose **BOUND** if you expect low short-term volatility
- choose **BREAK** if you expect a fast move in either direction

### Stocks

`AAPL / USD · 30m · ±1.5%`

- choose **BOUND** if you expect price containment
- choose **BREAK** if you expect a breakout or breakdown

### RWA / commodity

`XAU / USD · 2h · ±1.0%`

- choose **BOUND** if you expect gold to stay inside the launch range
- choose **BREAK** if you expect it to finish outside that range

## Important nuance

BREAK is not "bearish only."

BREAK wins when the asset settles:

- below the lower bound, or
- above the upper bound

So BREAK is a view on **range escape**, not just downside.

## Why Brimdex uses BOUND / BREAK

This framing works well for:

- short-duration volatility expression
- event-driven trading
- mean-reversion views
- breakout views without forcing traders to choose up-only or down-only

See [Pricing & Liquidity](prices.md) for how odds move, and [Market Lifecycle](market-lifecycle.md) for what happens from vault launch to settlement.
