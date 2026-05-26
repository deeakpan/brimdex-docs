# Stack Launch Vault

`BrimdexStackLaunchVault` is the LP-side capital formation contract for Brimdex markets.

**Source:** `smart-contract/raise/BrimdexStackLaunchVault.sol`

## What it does

The launch vault:

- accepts USDC commitments for a future market
- mints commitment tokens to LPs
- tracks whether the required notional has been reached
- opens the committed market once the launch flow completes
- holds the resolved LP pool for post-settlement redemption

## Main phases

| Phase | Meaning |
|---|---|
| Funding | Vault is accepting commitments |
| Ready to open | Required notional has been reached |
| Live market | Vault has opened the market and LP capital is active |
| Aborted | Target was missed before the deadline |
| Redeemable | Market has resolved and LPs can claim their share |

## Key functions

### `commit(uint256 requested)`

Commits USDC into the vault during the funding window and mints commitment tokens.

### `openCommittedMarket()`

Moves the vault from commitment mode into the live market-open path once the conditions are satisfied.

### `redeemCommitment()`

Lets LPs redeem after:

- the vault aborts because target was missed, or
- the resolved LP pool is available after settlement

## Important vault properties

The vault carries the market template needed to open the market later:

- `assetKey`
- commitment deadline
- required notional
- band bps
- horizon seconds

It also tracks the LP-side pool that comes back after settlement.

## Why commitment tokens matter

Commitment tokens are the LP accounting unit for the market:

- they represent proportional ownership of the launch vault
- they are burned when LPs redeem
- they are separate from trader BOUND / BREAK positions

## Why this contract matters

This vault is the entry point for LP capital and the bridge between:

- pre-launch capital formation
- live LMSR market activation
- post-settlement LP redemption

See [Market Lifecycle](../key-concepts/market-lifecycle.md) for the product flow and [LMSR Stack Factory](brimdex-factory.md) for the opening path.
