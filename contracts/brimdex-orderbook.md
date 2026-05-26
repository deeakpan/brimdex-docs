# CTF Orderbook

`BrimdexCTFOrderBook` is the secondary market for Brimdex outcome positions.

**Source:** `smart-contract/orderbook/BrimdexCTFOrderBook.sol`

## What it does

The orderbook lets users trade existing BOUND / BREAK exposure peer-to-peer instead of always crossing the LMSR curve.

It is built for:

- early exit
- price-specific orders
- secondary liquidity

## Key behavior

The orderbook:

- escrows tokens or USDC
- matches bids and asks by price
- settles fills between users
- keeps market books isolated by market address and side

## Why it is called CTF orderbook

The orderbook is designed around the conditional-token outcome model used by the Brimdex stack. It is therefore the secondary venue for the same BOUND / BREAK market state that the LMSR market maker prices.

## Main actions

- place a buy order
- place a sell order
- cancel an open order
- fill against resting liquidity

## Important limits

The orderbook does **not**:

- mint new market exposure
- determine the winning side
- settle the market itself

Settlement still happens through the Somnia settlement path, not through the orderbook.

## Relationship to LMSR

The LMSR gives immediate execution.

The orderbook gives:

- limit prices
- peer-to-peer exits
- an alternative execution surface

Both can coexist for the same market.
