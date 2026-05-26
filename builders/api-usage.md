# API Usage

The public Brimdex API is the fastest way to bootstrap builder integrations before adding direct onchain reads.

## Base path

Start from:

- `https://brimdex.markets/api/`

So if a page below says `markets`, the full path is:

- `https://brimdex.markets/api/markets`

## Common paths

These are the main public paths builders will normally care about first:

| Path after `/api/` | Full example | What it is for |
|---|---|---|
| `markets` | `https://brimdex.markets/api/markets` | Market discovery and enriched live market rows |
| `market-activity?market=0x...` | `https://brimdex.markets/api/market-activity?market=0x1234...` | Trade history, chart points, and market activity summary for one market |
| `asset-spots` | `https://brimdex.markets/api/asset-spots` | Supported assets with spot and quote metadata |
| `positions?address=0x...&market=0x...` | `https://brimdex.markets/api/positions?address=0xabc...&market=0x123...` | User cost basis / purchase-side position data for one wallet and one market |
| `launch-vaults` | `https://brimdex.markets/api/launch-vaults` | Launch-vault discovery and raise status |
| `deployments` | `https://brimdex.markets/api/deployments` | Current deployment map |

## Query parameter examples

### Market activity

Use:

- `/api/market-activity?market=0x...`

Required:

- `market` = the market address

### Positions

Use:

- `/api/positions?address=0x...&market=0x...`

Required:

- `address` = the wallet address
- `market` = the market address

## What the API is useful for

The public API is useful for:

- market discovery
- market activity summaries
- supported asset lookups
- UI-friendly data hydration

## When to use the API first

Use the API first when you are building:

- dashboards
- market lists
- portfolio views
- lightweight bots
- internal tools that do not need full custom indexing

## When to add onchain reads

Add direct chain reads when you need:

- latest live odds
- latest redemption truth
- launch-vault phase checks
- event-driven automation

## Recommended builder pattern

The usual pattern is:

1. start with the Brimdex API
2. use contract reads for latency-sensitive state
3. use events or reactivity for live synchronization

See [Market Data](fetching-markets.md) and [Events & Reactivity](events-and-reactivity.md) for the next layer down.
