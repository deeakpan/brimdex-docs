# Fees

Brimdex has two main fee surfaces:

- **primary trading fees**
- **orderbook fees**

## Primary trading fee

The default market fee is configurable and can change over time.

At a high level, the fee is split between:

- LP incentives
- staking incentives, when active
- protocol revenue

In the current fee model, Brimdex uses a base trading fee with a discounted path for eligible users. The exact live numbers should be read from the deployed fee config rather than hard-coded in front-end copy.

## How fee splits work

The fee config controls:

- standard fee rate
- discounted fee rate
- LP share
- staker share
- protocol share

This keeps fee policy upgradeable without forcing every market contract to carry its own immutable fee table.

## Orderbook fee

The orderbook uses its own matched-notional fee model.

That means:

- buyers pay a fee on matched notional
- sellers pay a fee on matched notional
- the orderbook fee path is separate from the main trading fee path

## Why fees matter to LPs

LP return comes from a combination of:

- fee capture
- final market outcome
- how balanced or one-sided flow was

So LP economics are not "fixed APY." They are market-structure dependent.

## Best practice for documentation

When documenting production fee numbers:

- quote the live config values
- reference the live fee configuration
- avoid old static copy from earlier market designs

See [Fee Config](../contracts/brimdex-fee-config.md) for the technical specification.
