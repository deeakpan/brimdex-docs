# Builder Overview

This section is for **developers** integrating with Brimdex (bots, dashboards, scripts). It includes **contract calls, ABIs, and code**.

**Using the product?** Read [How it works](../how-it-works/how-it-works-overview.md) and [Key concepts](../key-concepts/key-concepts-overview.md) first—they describe the **UI** (wallet prompts, approvals, trading steps). Technicalities live here and under [Contracts](../contracts/contract-overview.md).

## What you need

| Item | Value |
|---|---|
| Network | Somnia Testnet (Chain ID `50312`) |
| RPC | `https://dream-rpc.somnia.network` |
| Factory address | See [Contract Addresses](../contracts/contract-overview.md) |
| Router address | See [Contract Addresses](../contracts/contract-overview.md) |
| Collateral | USDC (6 decimals) |

## Entry points

For most integrations, you only need two contracts:

- **`BrimdexFactory`** — enumerate markets, get token addresses, check market state
- **`BrimdexRouter`** — execute buys with slippage protection

If you want lower-level control (e.g., direct market interaction), you can call `BrimdexMarket` directly — but you'll need to handle per-market USDC approvals yourself.

## Pages in this section

| Page | What it covers |
|---|---|
| [Fetching Markets](fetching-markets.md) | Reading market list, state, prices |
| [Trading via Contract](trading.md) | Executing buys programmatically |
| [Reading Positions](reading-positions.md) | Token balances, pending payouts |
| [Contract Interfaces](contract-interfaces.md) | Minimal ABIs for integration |
