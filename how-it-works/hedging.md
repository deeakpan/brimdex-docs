# Hedging & Risk

BOUND and BREAK are complementary outcomes, so traders can use them to shape risk rather than hold a pure one-sided view.

## Common ways users manage risk

### Add the other side

If you already hold BOUND and the market starts leaning BREAK, you can buy some BREAK to reduce your net exposure.

### Exit on the orderbook

If you do not want a two-sided position, you can instead reduce or close the trade on the orderbook.

### Scale into timeframes

Some users spread exposure across:

- different durations
- different band widths
- different assets

That can reduce reliance on one single short-term range outcome.

## What makes Brimdex hedging different

Brimdex is curve-based:

- every trade moves the LMSR state
- larger hedges can worsen your own execution
- small-seed markets are more sensitive to self-impact

So hedge sizing matters a lot.

## LP risk is different from trader risk

Traders choose BOUND or BREAK directly.

LPs do not, but LPs still carry:

- inventory risk
- path dependence from order flow
- settlement exposure through the resolved LP pool

That is why LP sizing should be matched to:

- expected trade size
- market duration
- expected volatility of the asset

## Practical takeaway

Shorter markets with larger average trades generally need:

- larger seed, or
- smaller clip sizes

Otherwise traders get poor fills and LP outcomes can swing hard.

See [Pricing & Liquidity](../key-concepts/prices.md) and [Liquidity & Vaults](liquidity-providing.md) for the capital trade-off.
