# Developer Overview

This section is for developers integrating with the current Brimdex stack.

## What developers are integrating with

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

For most developers, the main touchpoints are:

- `BrimdexLMSRStackFactory` to discover markets and launch vaults
- `BrimdexLMSRRouter` to execute primary trades
- `BrimdexCTFOrderBook` to read or place secondary orders
- `BrimdexFeeds` or indexed APIs to inspect supported assets and feed state

## What to read first

- [Contract Overview](../contracts/contract-overview.md)
- [Architecture Overview](../architecture/architecture-overview.md)
- [Agents & Reactivity](../architecture/agents-and-reactivity.md)

Then continue through the `Developers` pages in the sidebar for market data, trading integration, events, and ABIs.
