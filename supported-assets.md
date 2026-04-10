# Supported Assets

Brimdex uses `BrimdexFeeds` — an onchain oracle contract that stores price data for registered feed names. Any asset with a registered feed can have a market created against it.

## Current feeds (Somnia Testnet)

| Feed Name | Asset | Decimals |
|---|---|---|
| `BTC/USD` | Bitcoin | 6 |
| `ETH/USD` | Ethereum | 6 |
| `STT/USD` | Somnia Token | 6 |

## How feeds work

The `BrimdexFeeds` contract stores a `PriceData` struct per feed:

```solidity
struct PriceData {
    int256  price;      // scaled by decimals
    uint64  timestamp;  // last updated
    uint80  roundId;    // source round
    uint8   decimals;   // price precision
}
```

Markets read the feed at creation (to set the band) and at settlement (to determine the winner). If the feed timestamp is more than **5 minutes old**, the transaction reverts — ensuring no stale price can open or close a market.

## Adding a feed

The community will vote on new assets to be integrated. Feeds are registered onchain by the `BrimdexFeeds` contract owner once governance approves them. To propose a new asset, join the conversation on [Telegram](https://t.me/brimdex).
