# Contract Overview

Brimdex now runs on an **LMSR + conditional tokens + launch vault** stack, with settlement automation anchored on **Somnia**.

## Source of truth

The current contract source lives in:

- `smart-contract/`
- `LMSR/Brimdex/`

The current deployment data should be read from:

- `deployments.json`
- app contract maps such as `app/contracts.ts`

This page intentionally avoids freezing old addresses into static documentation.

## Contract groups

| Group | Main contracts | Purpose |
|---|---|---|
| Raise | `BrimdexStackLaunchVault` | Collect commitments and open markets from a vault |
| LMSR | `BrimdexLMSRStackFactory`, `LMSRMarketMaker`, `BrimdexLMSRRouter`, `BrimdexFeeConfig` | Create, quote, trade, and fee-configure the primary market |
| Conditional tokens | `BrimdexConditionalTokens`, `BrimdexAssetRegistry` | Outcome accounting and settlement state |
| Oracle / automation | `BrimdexFeeds`, `BrimdexReactivityCoordinator`, `BrimdexLaunchOpenCoordinator`, `BrimdexFeedAgentPuller` | Feed storage and reactive launch / settlement |
| Secondary market | `BrimdexCTFOrderBook` | Peer-to-peer trading of outcome positions |

## Canonical flow

1. `BrimdexStackLaunchVault` collects commitments
2. `BrimdexLMSRStackFactory` opens the market when authorized
3. `LMSRMarketMaker` handles live primary trading
4. `BrimdexCTFOrderBook` handles secondary exits
5. `BrimdexFeeds` plus the coordinator stack drive launch and settlement on Somnia
6. traders and LPs redeem from the settled state

## Network assumptions

- settlement chain: **Somnia**
- collateral: **USDC-style 6 decimal asset**
- automation: **Somnia Reactivity + agents**

## Pages in this section

| Page | What it covers |
|---|---|
| [LMSR Stack Factory](brimdex-factory.md) | Stack deployment and vault-authorized market opening |
| [LMSR Market Maker](brimdex-market.md) | Live primary market execution and resolution |
| [Stack Launch Vault](market-liquidity-vault.md) | Commitment collection and LP redemption |
| [LMSR Router](brimdex-router.md) | User-facing trading entry point |
| [CTF Orderbook](brimdex-orderbook.md) | Secondary market for outcome positions |
| [Fee Config](brimdex-fee-config.md) | Centralized fee policy |
| [Feeds & Coordinators](feeds-and-coordinators.md) | Feed storage and reactive automation |
