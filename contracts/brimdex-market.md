# LMSR Market Maker

The live primary market on Brimdex is implemented by `LMSRMarketMaker`, which extends the shared `MarketMaker` base.

**Sources:**

- `smart-contract/lmsr/LMSRMarketMaker.sol`
- `smart-contract/lmsr/MarketMaker.sol`

## What it does

`LMSRMarketMaker` is responsible for:

- pricing BOUND and BREAK continuously
- executing primary-market trades
- tracking the live market state
- resolving the market after expiry
- sending residual LP value back to the vault

## Key state

The market maker is built around:

- `collateralToken`
- `feeConfig`
- `assetKey`
- `lowerBound`
- `upperBound`
- `expiryTimestamp`
- vault reference
- conditional-token system reference

## Important behavior

### Continuous pricing

The contract exposes LMSR pricing, including `calcMarginalPrice(...)`, so the app can show live odds.

### Trade execution

Trades are normally routed through `BrimdexLMSRRouter`, but the market maker is where the actual execution and accounting happen.

### Expiry-aware resolution

After expiry, the contract resolves the market through the conditional-token / oracle path and closes the AMM state.

### LP settlement path

When the market resolves, residual value and LP-fee value are returned toward the vault redemption path.

## Why this contract matters

This is the contract that turns Brimdex from a static range definition into a tradable market:

- it owns the live odds
- it owns the trade path
- it is the bridge between trading and settlement

## Related contracts

- [LMSR Router](brimdex-router.md)
- [Fee Config](brimdex-fee-config.md)
- [Stack Launch Vault](market-liquidity-vault.md)
- [Feeds & Coordinators](feeds-and-coordinators.md)
