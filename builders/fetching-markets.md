# Fetching Markets

How to enumerate and read market state from `BrimdexFactory` and `BrimdexMarket`.


## Get all markets

```js
const markets = await factory.getAllMarkets();
// returns address[]
```

Paginated:

```js
const markets = await factory.getMarkets(offset, limit);
```


## Check if a market is active

```js
const active = await factory.isActiveMarket(name, timeframeDuration, bandPercent);
// returns bool
```

Or read market config directly:

```js
const [
  name,
  feedName,
  lowerBound,
  upperBound,
  expiryTimestamp,
  creationTimestamp,
  startPrice,
  initialized,
  settled
] = await market.marketConfig();

const isLive = initialized && !settled && expiryTimestamp > Date.now() / 1000;
```


## Get current prices

```js
const boundPrice = await market.getBoundPrice(); // 1e18 precision
const breakPrice = await market.getBreakPrice(); // 1e18 precision

// e.g. 650000000000000000n = 0.65 (65%)
const boundPct = Number(boundPrice) / 1e18;
```


## Get pool sizes

```js
const boundPool = await market.boundPool(); // USDC, 6 decimals
const breakPool = await market.breakPool();
const traderPool = await market.getDisplayPool(); // total minus seed
```


## Get token addresses

```js
const boundToken = await factory.marketToBoundToken(marketAddress);
const breakToken = await factory.marketToBreakToken(marketAddress);
const vault      = await factory.marketToLiquidityVault(marketAddress);
```


## Estimate trade output

```js
// Preview tokens for a given gross USDC spend
const tokens = await market.getEstimatedTokens(isBound, grossUsdc);

// Preview USDC payout at settlement (snapshot estimate)
const payout = await market.getEstimatedPayout(isBound, grossUsdc);
```


## Get settlement outcome

```js
const settled   = marketConfig.settled;
const boundWins = await market.boundWins();
const rate      = await market.redemptionRate(); // 1e18 precision
const price     = await market.resolvedPrice();
```
