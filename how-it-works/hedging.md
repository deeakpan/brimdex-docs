# Hedging

Because BOUND and BREAK prices always sum to 1.00, you can use the two sides of a market to hedge an existing position or reduce your directional risk.


## The basic hedge

If you hold BOUND tokens and the price is moving toward the band boundary, you can buy BREAK tokens to offset potential losses.

```
You hold: 500 BOUND @ avg price 0.60
Market now: BOUND = 0.45, BREAK = 0.55

You buy BREAK to hedge your BOUND exposure.
If BREAK wins → BREAK payout offsets BOUND loss
If BOUND wins → BOUND payout, BREAK is worthless
```

A full hedge (buying both sides in proportion) locks in a small loss equal to the 2% trade fee, but eliminates binary outcome risk.


## Partial hedge

Buying a smaller BREAK position relative to your BOUND holding reduces volatility without fully neutralizing the position. You still profit if BOUND wins, but your downside is capped.


## Selling on the orderbook

An alternative to buying the other side: **sell** your existing tokens on the **orderbook** at a price you choose. This exits the position entirely rather than creating a two-sided hedge.

Whether to hedge or sell depends on:
- Current token prices on the orderbook vs primary market
- Transaction cost (two buys vs one sell)
- Whether you think the position will recover


## Hedging as a market maker

Advanced users can buy both sides at the same time when they believe the market is mispriced. If BOUND is at 0.30 and BREAK is at 0.70, but you think the true probability is 50/50, buying BOUND adds pressure that pushes prices back toward equilibrium — and your BOUND position profits when the price normalizes.


## Important note on parimutuel hedging

Unlike a prediction market with fixed odds, Brimdex prices shift with every buy. A large hedge buy moves the price of both sides. Factor in price impact when sizing hedge positions.
