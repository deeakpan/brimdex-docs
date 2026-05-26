# LMSR Router

`BrimdexLMSRRouter` is the recommended user-facing entry point for primary-market trading.

**Source:** `smart-contract/lmsr/BrimdexLMSRRouter.sol`

## Why it exists

The router gives the app and integrators a cleaner trading surface for LMSR markets.

It is the preferred place to send primary trades instead of wiring directly to every market-specific contract path.

## What it does

The router is responsible for:

- taking the user trade input
- moving approved collateral into the LMSR trade path
- executing the trade against the chosen market
- returning the resulting outcome exposure to the user

## Main action

### `tradeLmsr(...)`

This is the core trade entry point for the current stack.

The exact calldata shape depends on the deployed version and ABI, but conceptually it includes:

- target market
- outcome side
- collateral amount
- user protection parameters such as minimum acceptable output

## Why developers should use it

Using the router gives integrators:

- a stable trading entry surface
- easier approval management
- cleaner app-side execution logic

## Relationship to the market maker

The router does not own the market logic. It forwards the trade into the live `LMSRMarketMaker`, which performs:

- pricing
- fill accounting
- fee handling
- position mint / transfer effects

See [LMSR Market Maker](brimdex-market.md) for the execution contract underneath.
