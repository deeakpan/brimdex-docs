# Positions & Redemptions

Brimdex positions come from two different places:

- trader outcome exposure
- LP commitment / redemption state

## Trader positions

For trader-facing positions, read:

- outcome token balances from the conditional-token side
- market resolution status
- whether the market is still live or already settled

In practice, most frontends should use the indexed position layer first and then hydrate important edge cases fromchain.

## Useful position inputs

A useful position view normally combines:

- user outcome balances
- market odds
- entry / trade history
- settlement status
- redeemability status

## LP positions

LP state lives in `BrimdexStackLaunchVault`.

The most important reads are:

- commitment token balance
- current vault phase
- whether the market opened or aborted
- whether LP redemption is available

## Position reading strategy

### For app-like views

Use indexed APIs for:

- historical trades
- entry price / cost basis
- portfolio aggregation

### For settlement-critical views

Hydrate fromchain for:

- current redeemable balance
- whether the vault or market has already resolved
- whether the user has already redeemed

## Why a mixed approach is best

Brimdex position UX usually needs both:

- indexed history for speed and portfolio assembly
- direct onchain reads for live redemption truth

That is especially important around expiry, settlement, and recent redemptions.
