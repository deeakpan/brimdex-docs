# LMSR Stack Factory

`BrimdexLMSRStackFactory` is the deployment and orchestration contract for the Brimdex LMSR stack.

**Source:** `smart-contract/lmsr/BrimdexLMSRStackFactory.sol`

## What it does

The factory is responsible for:

- creating launch vaults
- authorizing vault-driven opens
- opening markets once launch conditions are satisfied
- registering the market with the conditional-token system
- deploying and wiring the LMSR market maker
- binding the market maker to the condition

## Why it matters

Brimdex does not open markets as isolated contracts with hand-managed setup.

The factory creates a repeatable stack so every market follows the same path:

1. launch vault exists
2. vault reaches target
3. factory opens the market
4. market is registered against the asset key and range
5. the LMSR becomes live on Somnia

## Important inputs

The factory works with:

- `assetKey`
- `lowerBound`
- `upperBound`
- `expiryTimestamp`
- collateral asset
- fee config
- vault authorization

It also records launch telemetry such as:

- `launchOracleSpot6`
- `launchBandBps`
- `launchHorizonSeconds`

## Key responsibilities

| Responsibility | Description |
|---|---|
| Vault creation | Deploys a `BrimdexStackLaunchVault` for a future market |
| Market open | Calls the path that registers the market and boots the LMSR |
| Stack wiring | Connects the vault, LMSR, fee config, and conditional-token system |
| Asset enforcement | Uses the registered `assetKey` / feed path |

## Related contracts

- [Stack Launch Vault](market-liquidity-vault.md)
- [LMSR Market Maker](brimdex-market.md)
- [Feeds & Coordinators](feeds-and-coordinators.md)
