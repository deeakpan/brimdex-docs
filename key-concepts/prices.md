# Pricing & Liquidity

Brimdex uses an automated pricing curve for continuous pricing.

That means:

- quotes are always available while the market is live
- price moves after every trade
- larger markets feel smoother than smaller markets
- seed size directly affects slippage and LP exposure

## Reading price

Brimdex prices BOUND and BREAK as values between `0` and `1`.

Examples:

- `BOUND = 0.50`, `BREAK = 0.50` -> market starts balanced
- `BOUND = 0.63`, `BREAK = 0.37` -> market is leaning toward the price finishing inside the range
- `BOUND = 0.22`, `BREAK = 0.78` -> market expects a breakout more than containment

These are best read as **market odds**, not guarantees.

## What makes prices move

The two main drivers are:

1. **trade flow**
2. **seed / funding depth**

More seed means:

- tighter execution
- slower price movement per trade
- better fills for larger users
- more capital at risk for LPs

Less seed means:

- sharper odds movement
- worse fills on bigger clips
- more expressive short-term markets
- lower absolute LP bankroll at risk

## Why your fill changes with size

Because Brimdex is curve-based, a `25 USDC` trade and a `500 USDC` trade do not get the same execution quality.

If seed is small relative to trade size:

- the order moves the market materially
- the average price paid is worse
- the displayed odds can jump quickly

This is why short-duration markets often need either:

- smaller clip sizes, or
- larger seed

## Odds versus displayed pool number

Two different ideas matter on the UI:

- **odds**: BOUND / BREAK percentages derived from the live market state
- **market cash-in display**: a more intuitive view of seeded capital plus trade flow

These are related, but not identical. Odds come from the curve; the bottom card number is a product display choice.

## LP trade-off

LPs earn fees, but they also underwrite the market.

So there is always a trade-off:

- small seed -> lower LP dollars at risk, poorer fills
- large seed -> better fills, higher LP dollars at risk

For very short markets, the wrong seed / trade-size combination can make LP outcomes swing hard.

## Settlement intuition

After expiry:

- one side wins
- winners redeem
- LPs redeem the resolved vault proceeds

LP return is not fixed principal plus fee. It depends on:

- trade volume
- fee capture
- how one-sided or balanced market flow was
- final payout dynamics at settlement

See [Liquidity & Vaults](../how-it-works/liquidity-providing.md) and [Settlement on Somnia](../how-it-works/settlement.md) for the full payout flow.
