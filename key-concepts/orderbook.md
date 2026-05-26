# Orderbook

Brimdex includes an **orderbook** as the secondary market for BOUND and BREAK positions.

The orderbook exists for one main reason: **early exit**.

The main Brimdex market gives you continuous buy access. The orderbook gives you a peer-to-peer venue to:

- reduce a position
- exit before expiry
- trade at your own limit price
- improve execution relative to the curve when there is resting liquidity

## What the orderbook is

The orderbook is:

- per market
- outcome-specific
- price / size based
- peer-to-peer

It does not replace the main market. It sits next to it.

## How it works

### Sell order

You choose:

- the market
- the side you want to sell
- a limit price
- a token amount

Your outcome tokens are approved and escrowed until the order fills or you cancel it.

### Buy order

You choose:

- the market
- the side you want to buy
- a limit price
- a token amount

Your USDC is approved and escrowed until matched or cancelled.

### Matching

Orders match on price compatibility:

- incoming buys cross resting asks
- incoming sells cross resting bids
- execution happens at the resting order price

## Why it matters

The orderbook is useful when:

- you want to exit without pushing the LMSR curve
- you want a tighter price than the live market-maker quote
- you want to trade around a specific view rather than accept immediate execution

## What it does not do

- it does not mint or settle the market
- it does not replace Somnia settlement
- it does not guarantee fills
- it does not determine the market winner

The winner still comes from the settlement flow on Somnia.
