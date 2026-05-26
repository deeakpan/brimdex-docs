# Market Data

For frontends, the easiest source is the Brimdex API / indexed layer.

For lower-level integrations, the current onchain discovery flow is built around the LMSR stack contracts.

## Preferred sources

### 1. Public Brimdex API

For product-quality market discovery, start with the public Brimdex API under:

- `https://brimdex.markets/api/`

Use it as the higher-level discovery layer before dropping down to direct chain reads.

### 2. Onchain events

For direct indexing, watch `BrimdexLMSRStackFactory` events such as:

- `VaultCreated`
- `MarketOpened`

That gives you the lifecycle from launch vault to live market.

## Reading launch vault state

The launch vault exposes the market template and phase information:

- `phase()`
- `assetKey`
- `bandBps`
- `horizonSeconds`
- `requiredNotional`
- `commitmentDeadline`

This is the best place to understand a market before it is opened.

## Reading live market odds

Once a market is live, the core odds surface comes from `LMSRMarketMaker`.

The main read most integrations care about is:

- `calcMarginalPrice(uint8 outcomeTokenIndex)`

Use outcome `0` / `1` according to your integration's side mapping and ABI.

## Reading market state

A complete market view usually combines:

- factory / event discovery
- launch vault metadata
- LMSR marginal prices
- orderbook state if you support secondary trading
- conditional-token balances for user positions

## Practical recommendation

If you are building a UI, use the Brimdex API layer for discovery and hydrate selected live values fromchain only where latency matters most.
