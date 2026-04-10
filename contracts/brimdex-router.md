# BrimdexRouter

The recommended user-facing entry point. Approve USDC once to the router, then trade across all markets without re-approving per-market.

**Source:** [`BrimdexRouter.sol`](https://github.com/deeakpan/Brimdex-contracts/blob/main/BrimdexRouter.sol)


## Why use the router?

Without the router, you would need to approve each market contract separately. The router batches this: you approve the router, the router handles per-market approval internally and revokes it after each trade.

The router also publishes trade data to Somnia Data Streams for analytics.


## Key functions

### `buyBound(marketAddress, amount, minTokensOut)`

```solidity
router.buyBound(marketAddress, amount, minTokensOut);
```

| Parameter | Description |
|---|---|
| `marketAddress` | Target market (must be registered in factory) |
| `amount` | USDC to spend (gross, 6 decimals) |
| `minTokensOut` | Minimum BOUND tokens to receive (slippage guard) |

### `buyBreak(marketAddress, amount, minTokensOut)`

Same parameters, mints BREAK tokens.


## Approval flow

```
1. User approves router for USDC
2. Router pulls USDC from user
3. Router approves market (exact amount)
4. Router calls market.buyBound / buyBreak
5. Tokens minted directly to user
6. Router revokes market approval
```

If the market call reverts for any reason, the router refunds USDC to the user and revokes the approval before re-reverting.


## Data Streams

After each successful buy, the router publishes trade data to Somnia Data Streams:

```
Schema: address user, address market, uint256 amount,
        uint256 tokens, uint64 timestamp, bool isBound
```

This is non-critical — if the publish fails, the trade still succeeds.
