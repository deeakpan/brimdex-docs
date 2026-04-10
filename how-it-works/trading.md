# Trading

Buying a position on Brimdex takes a single transaction. You approve USDC to the `BrimdexRouter` once, then call `buyBound` or `buyBreak` for any active market.

## Step-by-step

### 1. Approve the router

```solidity
USDC.approve(routerAddress, amount);
```

You only need to do this once per approval amount. The router manages per-market approvals internally.

### 2. Buy your position

```solidity
// Buy BOUND tokens
router.buyBound(marketAddress, amount, minTokensOut);

// Buy BREAK tokens
router.buyBreak(marketAddress, amount, minTokensOut);
```

| Parameter | Description |
|---|---|
| `marketAddress` | The market you want to trade |
| `amount` | Gross USDC to spend (6 decimals) |
| `minTokensOut` | Minimum tokens to receive — reverts if slippage is too high |

### 3. Tokens arrive in your wallet

BOUND or BREAK tokens are minted directly to your address. The router never holds tokens.

## What happens onchain

```
You send $100 USDC
→ Router pulls USDC from you
→ Router approves market for $100
→ Market takes 2% fee ($1.80 to treasury, $0.20 to LP vault)
→ Net $98 enters the pool
→ Tokens minted = $98 / current price
→ Router revokes market approval
→ Tokens land in your wallet
```

## Estimating tokens before buying

Call `getEstimatedTokens` on the market before buying to preview output:

```solidity
market.getEstimatedTokens(isBound, grossUsdc)
```

Or call `getEstimatedPayout` to see your expected USDC return at settlement (snapshot estimate based on current pool state):

```solidity
market.getEstimatedPayout(isBound, grossUsdc)
```

## Checking your position

Your position is your token balance:

```solidity
IERC20(factory.marketToBoundToken(market)).balanceOf(yourAddress);
IERC20(factory.marketToBreakToken(market)).balanceOf(yourAddress);
```

## After the market settles

Call `redeem()` on the market contract if you hold the winning token:

```solidity
market.redeem(isBound, tokenAmount);
```

Specify `isBound = true` for BOUND tokens or `false` for BREAK. The call burns your tokens and sends USDC to your wallet.
