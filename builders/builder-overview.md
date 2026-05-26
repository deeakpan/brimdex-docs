# Builder Overview

This section is for developers integrating with the current Brimdex stack.

## What builders are integrating with

The live architecture is:

- `BrimdexLMSRStackFactory`
- `BrimdexStackLaunchVault`
- `LMSRMarketMaker`
- `BrimdexLMSRRouter`
- `BrimdexCTFOrderBook`
- `BrimdexFeeds` and the coordinator contracts

## What you need

| Item | Value |
|---|---|
| Canonical execution chain | Somnia |
| Collateral | USDC-style 6 decimals |
| Market maker | LMSR |
| Outcome model | CTF-backed BOUND / BREAK |
| Settlement automation | Somnia Reactivity + agents |

## Typical integration entry points

For most builders, the main touchpoints are:

- `BrimdexLMSRStackFactory` to discover markets and launch vaults
- `BrimdexLMSRRouter` to execute primary trades
- `BrimdexCTFOrderBook` to read or place secondary orders
- `BrimdexFeeds` or indexed APIs to inspect supported assets and feed state

## What to read first

- [Contract Overview](../contracts/contract-overview.md)
- [Architecture Overview](../architecture/architecture-overview.md)
- [Agents & Reactivity](../architecture/agents-and-reactivity.md)

## Builders section map

| Section | Page | What it covers |
|---|---|---|
| Data & APIs | [Market Data](fetching-markets.md) | Market discovery, vault state, and live odds |
| Data & APIs | [API Usage](api-usage.md) | How to use the public Brimdex API surface |
| Data & APIs | [Positions & Redemptions](reading-positions.md) | Reading trader and LP state |
| Integration | [Trading Integration](trading.md) | Executing primary trades programmatically |
| Integration | [Events & Reactivity](events-and-reactivity.md) | Event-driven sync and reactive update patterns |
| Integration | [Contracts & ABIs](contract-interfaces.md) | Artifact sources and high-signal interfaces |

The contract section is still the source of truth for exact stack naming and contract responsibilities, but `Builders` is now the practical integration path.
