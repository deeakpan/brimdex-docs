# Brimdex 101

A plain-language intro to how Brimdex works.


## The core idea

Every market has a **price band** — an upper and lower boundary set at creation around the current oracle price. The market expires at a fixed timestamp.

At expiry, one of two things has happened:

- The asset price is **inside** the band → **BOUND wins**
- The asset price is **outside** the band → **BREAK wins**

You buy a position by purchasing BOUND or BREAK tokens. Winners split the entire trader pool at settlement.


## A simple example

> BTC is $65,000. A market opens with band $63,700 – $66,300 (±2%), expiring in 4 hours.

| You think | You buy | You win if |
|---|---|---|
| BTC stays calm | BOUND | Final price is $63,700–$66,300 |
| BTC makes a big move | BREAK | Final price is below $63,700 or above $66,300 |


## How prices work

Prices are set by the pool ratio — not an order book. The more USDC is in the BOUND pool relative to BREAK, the higher the BOUND price and the lower the expected payout per token.

```
BOUND price = boundPool / (boundPool + breakPool)
BREAK price = breakPool / (boundPool + breakPool)

BOUND price + BREAK price = 1.00
```

If BOUND price is 0.70, a BOUND token costs $0.70 and a BREAK token costs $0.30. If BOUND wins, each BOUND holder earns from the combined trader pool.

See [Prices](key-concepts/prices.md) for the full math.


## What is seed liquidity?

Both pools start with equal USDC — deposited by Liquidity Providers (LPs) via the `MarketLiquidityVault`. This seed ensures the market has a 50/50 starting price and prevents zero-liquidity edge cases.

LPs do **not** take a directional bet. Their principal is returned at settlement regardless of outcome. In return they earn **0.2% of every trade** that flows through the market.

See [Liquidity Providing](how-it-works/liquidity-providing.md).


## Early exit

Don't want to wait for settlement? You can sell your BOUND or BREAK tokens on the `BrimdexOrderBook` to another user at any time while the market is live.

See [The Orderbook](key-concepts/orderbook.md).


## Settlement

At expiry, the protocol keeper calls `settle()`. The contract reads the oracle price, determines the winner, and sets a redemption rate. Winners call `redeem()` to collect their USDC.

See [Settlement](how-it-works/settlement.md).


## Summary

1. A market opens with a price band and expiry
2. You buy BOUND (price stays in) or BREAK (price breaks out)
3. Pools are seeded by LPs; prices update with every trade
4. Hold to settlement and redeem, or sell early on the orderbook
5. Winners split the trader pool pro-rata at settlement
