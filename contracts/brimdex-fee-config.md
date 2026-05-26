# Fee Config

`BrimdexFeeConfig` is the central fee-policy contract for Brimdex LMSR markets.

**Source:** `smart-contract/lmsr/BrimdexFeeConfig.sol`

## Why it exists

Brimdex keeps fee policy in one contract so markets can share one configuration surface for:

- standard trading fee
- discounted trading fee
- LP fee share
- staker fee share
- protocol fee share

## Current documented values

The current contract defines:

- `STANDARD_FEE = 0.9%`
- `DISCOUNTED_FEE = 0.675%`
- xBDX threshold for discount: `200,000 xBDX`

Default fee-share split basis points:

- `LP_BPS = 5333`
- `STAKER_BPS = 1111`
- `PROTOCOL_BPS = 3556`

These shares split the trade fee rather than acting as separate extra fees.

## Additional roles

The contract also stores:

- `protocolWallet`
- `stakingRewards`
- `votingEscrow`

This lets the stack direct protocol fees, staker emissions, and discount eligibility from one place.

## Why it matters

Fee policy affects:

- trader execution cost
- LP economics
- staker rewards
- protocol revenue

That is why the docs should reference `BrimdexFeeConfig` instead of hard-coding old fee text into every page.

## Related docs

- [Fees](../how-it-works/fees.md)
- [LMSR Market Maker](brimdex-market.md)
