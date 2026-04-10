# Supported Assets

Brimdex uses `BrimdexFeeds` — an onchain oracle contract that stores price data for registered feed names. Any asset with a registered feed can have a market created against it.

## Current feeds (Somnia Testnet)

| Feed Name | Asset | Decimals |
|---|---|---|
| `SOL/USD` | Solana | 6 |
| `ETH/USD` | Ethereum | 6 |
| `BTC/USD` | Bitcoin | 6 |
| `SOMI/USD` | Somnia | 6 |
| `BNB/USD` | BNB | 6 |

## How feeds work

Each registered feed has a **price**, **last-updated time**, **precision (decimals)**, and metadata the oracle uses for freshness. Markets read that feed when the band is set and again when the outcome is finalized.

If an update is **too old** (roughly **more than five minutes** behind), the protocol won’t use it to open or close a market—so you’re not settled on a stale print.

## Adding a feed

The community will vote on new assets to be integrated. Feeds are registered onchain by the `BrimdexFeeds` contract owner once governance approves them. To propose a new asset, join the conversation on [Telegram](https://t.me/brimdex).
