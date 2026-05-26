# Supported Assets

Brimdex is built for a mixed asset universe. Markets can be launched across **crypto**, **stocks**, and **real-world assets / commodities**.

## Asset classes

### Crypto

| Feed | Asset |
|---|---|
| `BTC/USD` | Bitcoin |
| `ETH/USD` | Ethereum |
| `SOL/USD` | Solana |
| `BNB/USD` | BNB |
| `SOMI/USD` | Somnia |
| `ARB/USD` | Arbitrum |

### Stocks and indices

| Feed | Asset |
|---|---|
| `TSLA/USD` | Tesla |
| `AAPL/USD` | Apple |
| `NVDA/USD` | NVIDIA |
| `MSFT/USD` | Microsoft |
| `GOOGL/USD` | Alphabet |
| `AMZN/USD` | Amazon |
| `META/USD` | Meta |
| `NFLX/USD` | Netflix |
| `AMD/USD` | AMD |
| `SPY/USD` | SPDR S&P 500 ETF |

### RWAs and commodities

| Feed | Asset |
|---|---|
| `XAU/USD` | Gold |
| `XAG/USD` | Silver |
| `WTI/USD` | WTI crude oil |

## What a supported asset means

A supported asset has:

- a registered `assetKey`
- a mapped price feed
- a curated UI symbol and metadata entry
- a launch path through the stack factory and launch vault flow

Markets do not have to be live for every asset all the time. Brimdex can list a wider asset universe than the currently active market set.

## Example markets by asset class

| Category | Example market |
|---|---|
| Crypto | `ETH / USD · 10m · ±0.5%` |
| Stock | `NVDA / USD · 30m · ±1.5%` |
| RWA / commodity | `XAU / USD · 2h · ±1.0%` |

## Oracle freshness

Brimdex launches and settles markets against fresh prices only.

- prices are written onchain
- stale prices are rejected for launch and settlement
- Somnia agents and Somnia Reactivity are used to keep launch and settlement automation tight

## Multichain access, single settlement chain

Brimdex can route users and liquidity from other ecosystems through **Stargate**, but the market itself still settles on **Somnia**. That means the asset universe can be accessed from multiple chains while the canonical market state remains on one execution chain.

## Adding assets

Adding a new asset means registering the feed and metadata needed for:

- launch vault creation
- market deployment
- Somnia settlement
- UI discovery and filtering

The exact feed wiring is covered in [Feeds & Coordinators](contracts/feeds-and-coordinators.md).
