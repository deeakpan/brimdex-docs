# Feeds & Coordinators

This page covers the contracts that make Brimdex asset pricing, launch automation, and settlement automation work on Somnia.

## Main contracts

| Contract | Role |
|---|---|
| `BrimdexAssetRegistry` | Maps `assetKey` to the feed key used by the stack |
| `BrimdexFeeds` | Stores feed values used by the protocol |
| `BrimdexFeedAssets` | Asset catalog and feed metadata helpers |
| `BrimdexFeedAgentPuller` | Creates and handles agent-driven feed pull requests |
| `BrimdexLaunchOpenCoordinator` | Coordinates the market-open path after vault target is met |
| `BrimdexReactivityCoordinator` | Coordinates reactive settlement-side execution |

## Asset registry

The asset registry is where Brimdex maps:

- `assetKey`
- feed key string such as `ETH/USD`

This is the contract-level bridge between a market template and the external price feed that launch / settlement use.

## BrimdexFeeds

`BrimdexFeeds` is the protocol-facing feed surface.

It exposes feed values and timestamps used by the rest of the stack and supports the product goal of keeping settlement decisions anchored to fresh data on Somnia.

## Agent puller

`BrimdexFeedAgentPuller` is the contract that creates agent requests and handles the pull-based path for external data updates.

This is important because launch and settlement often need a fresh asset update at a specific moment.

## Launch coordinator

`BrimdexLaunchOpenCoordinator` handles the reactive market-open path after a launch vault reaches its required notional.

It is part of the bridge between:

- launch vault commitments
- fresh oracle data
- the final call that opens the LMSR market

## Settlement coordinator

`BrimdexReactivityCoordinator` handles the reactive settlement-side path once a market reaches expiry.

This is the core automation surface behind the Brimdex goal of **sub-2s reactive settlement** once the final trigger and feed update are available.

## Why these contracts matter together

Without this group of contracts, Brimdex would not have:

- a consistent asset catalog
- a clean launch-open path
- a clean settlement trigger path
- Somnia-native automation

These contracts are what make Brimdex feel like a coordinated system instead of a set of isolated contracts.

## Related docs

- [Agents & Reactivity](../architecture/agents-and-reactivity.md)
- [Settlement on Somnia](../how-it-works/settlement.md)
- [Supported Assets](../supported-assets.md)
