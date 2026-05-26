# Trading Integration

**Audience:** integrators and developers. For the user-facing flow, see [AMM Trading](../trading/amm-trading.md).

## Recommended path

Use `BrimdexLMSRRouter` for primary-market execution.

The current core entry point is:

- `tradeLmsr(LMSRMarketMaker market, int256[] outcomeTokenAmounts, int256 collateralLimit)`

## What the trade call expresses

At a high level, the trade call communicates:

- which market you are trading against
- which outcome inventory change you want
- how much collateral you are willing to spend or receive

Because this is an LMSR / conditional-token style trade surface, the router uses outcome token deltas rather than the old dedicated `buyBound` / `buyBreak` helpers.

## Approval model

Builders should:

1. approve the collateral token
2. call the router with the desired trade shape
3. inspect the resulting market and position state

## Slippage and limits

The `collateralLimit` parameter is the core user-protection input.

Your integration should set it conservatively so the transaction reverts if execution is materially worse than expected.

## Reading before trading

Before sending a trade, most builders should read:

- current marginal price from `LMSRMarketMaker`
- current market stage
- expiry state
- user allowance and balance

## Secondary trading

If you want price-specific execution instead of immediate LMSR execution, integrate `BrimdexCTFOrderBook` instead of the router.
