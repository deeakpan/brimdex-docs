# Overview

Brimdex is a range-market protocol built around **BOUND** and **BREAK** outcomes, with continuous pricing, fast settlement on **Somnia**, and **onchain agents** that help open and resolve markets.

Every market asks the same binary question:

- **BOUND**: does the asset settle inside the quoted range?
- **BREAK**: does the asset settle outside the quoted range?

Brimdex supports **crypto**, **stocks**, and **real-world asset / commodity** markets. Users can access the product from multiple chains, but Brimdex deliberately keeps market truth and settlement on **Somnia** for speed, consistency, and predictable automation.

## What Brimdex is designed for

| Capability | What Brimdex does |
|---|---|
| Market type | Binary range markets with BOUND / BREAK outcomes |
| Asset coverage | Crypto, stocks, and RWAs / commodities |
| Pricing | Continuous quotes while the market is live |
| Early exit | Secondary orderbook |
| Liquidity model | Launch commitments plus live market liquidity |
| Settlement chain | Somnia |
| Automation | Somnia Reactivity plus onchain agents |
| Settlement speed | Designed for sub-2s reactive settlement once the final trigger is available |
| Multichain access | Bridging / routing through Stargate into Somnia settlement |

## Examples

| Market | BOUND wins if | BREAK wins if |
|---|---|---|
| `ETH / USD · 10m · ±0.5%` | ETH settles inside the 0.5% band | ETH settles below the lower bound or above the upper bound |
| `NVDA / USD · 30m · ±1.5%` | NVDA remains inside the range at expiry | NVDA finishes outside the range |
| `XAU / USD · 2h · ±1.0%` | Gold remains inside the band | Gold breaks below or above the band |

## How the product works

1. A **launch vault** collects USDC commitments.
2. Once the target is met, **Somnia Reactivity** triggers the launch flow.
3. An **onchain agent** fetches the required price update.
4. The market opens on Somnia with a BOUND and BREAK range.
5. Users trade immediately or exit later through the orderbook.
6. At expiry, **onchain agents** help resolve the market on Somnia.
7. Winners redeem, and LPs redeem their share of the resolved vault.

## Why settlement stays on Somnia

Brimdex is multichain in **access**, but single-chain in **truth**:

- liquidity and users can route in through **Stargate**
- the market state, oracle writes, automation, and settlement finality all live on **Somnia**
- this keeps one canonical execution environment for market open, market close, and redemption

See [Agents & Reactivity](architecture/agents-and-reactivity.md), [Multichain with Stargate](architecture/multichain-and-stargate.md), and [Protocol Overview](protocol/protocol-overview.md) for more context.
